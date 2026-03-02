# Agent Memory: Building and Distributing Baseline Context

Agents are only as good as the context they start with. This document explains how to create a shared memory baseline — firm-wide knowledge, standards, and process context — that can be distributed to everyone in the company so every agent session starts from the same foundation.

---

## What Is Agent Memory?

Agent memory is the context an AI agent has before a conversation or task begins. It shapes how the agent behaves, what it knows about your firm, and how it formats its outputs.

There are two types:

- **Implicit memory** — instructions and knowledge embedded in system prompts and configuration files that the agent reads automatically
- **Explicit memory** — context files, reference documents, and knowledge bases that are passed to the agent at runtime

This document focuses on **implicit memory** via configuration files — specifically how Claude Code loads context through `CLAUDE.md` files.

---

## The Memory Hierarchy

Context loads in layers, from broad to specific. Each layer inherits from the one above and can override or extend it.

```
Global (applies to all projects on a machine)
└── ~/.claude/CLAUDE.md

Firm-wide (applies to all projects cloned from your firm's GitHub org)
└── Distributed via a shared template repo

Project-level (applies to everyone working on this specific project)
└── CLAUDE.md  ← this file, at the repo root

Personal (applies only to the individual, not committed to the repo)
└── CLAUDE.local.md  ← gitignored, for personal preferences
```

The project-level `CLAUDE.md` is the primary distribution mechanism for firm-wide standards. Everyone who clones the repo gets the same baseline.

---

## What Goes in Each Layer

### Global (`~/.claude/CLAUDE.md`)
Set once per machine during onboarding. Contains:
- The engineer's name and role
- Personal tool preferences
- Any firm-wide standards that aren't project-specific

```markdown
# Global Context

I am [Name], a [Role] at [Firm Name].

## Always
- Follow the firm's coding standards
- Never commit secrets or credentials
- Default to Claude Sonnet 4.6 for most tasks
```

### Firm-Wide (distributed via template)
The shared baseline every project starts from. Contains:
- Firm identity and methodology
- Standard code conventions
- AI model defaults
- Compliance and security rules
- How agents should behave across all engagements

This is what lives in this repo's `CLAUDE.md` and gets copied into each new project.

### Project-Level (`CLAUDE.md` at repo root)
Extends the firm baseline with project-specific context:
- Client name and engagement context
- Tech stack and architecture decisions
- Project-specific compliance requirements
- Sprint cadence and team norms

### Personal (`CLAUDE.local.md`, gitignored)
Individual preferences that shouldn't be shared:
- Personal shortcuts and aliases
- Local environment paths
- Notes that are only relevant to one person

---

## Building the Firm Baseline

The firm baseline is a `CLAUDE.md` template that captures everything an agent needs to work on any engagement at your firm. Think of it as the onboarding document for every AI session.

### What to Include

**Firm Identity**
```markdown
## Firm Context
[Firm Name] is a federal software consulting firm. We build systems for
civilian and defense agencies. Our methodology is AI-native agile — agents
support every phase of the SDLC, with humans approving at each gate.
```

**Code Conventions**
```markdown
## Code Conventions
- Keep code simple — avoid over-engineering
- Prefer editing existing files over creating new ones
- Validate only at system boundaries (user input, external APIs)
- No unnecessary comments on unchanged code
```

**Federal Compliance Defaults**
```markdown
## Compliance
- Every user story must be tagged with applicable compliance frameworks
- Security scanning runs every sprint — never skip it
- No client data leaves approved infrastructure
- Auditability is non-negotiable — log all agent actions
```

**AI Behavior**
```markdown
## AI Models
- Default: claude-sonnet-4-6
- Complex reasoning tasks: claude-opus-4-6
- Never store API keys in code — use environment variables
```

**Agent Roles**
```markdown
## Agent Roles
When acting as a phase agent, always:
1. State your inputs before beginning
2. Produce structured output in the defined format
3. Flag compliance issues explicitly
4. Note what requires human review before the next phase
```

---

## Distributing to the Team

### Option 1: Template Repository (Recommended)

Create a firm-wide template repo (e.g., `firm/project-template`) that contains:
- A baseline `CLAUDE.md` pre-filled with firm standards
- A `CLAUDE.local.md.example` for personal setup guidance
- Global memory setup instructions in `README.md`

When starting a new project:
```bash
# Clone the template to start a new engagement
gh repo create firm/new-project --template firm/project-template
```

Everyone who clones the project repo gets the firm baseline automatically.

### Option 2: Dotfiles Repository

Maintain a shared `dotfiles` repo with a `~/.claude/CLAUDE.md` template. Engineers run a setup script during onboarding that installs it globally.

```bash
# Onboarding script installs global Claude memory
cp dotfiles/.claude/CLAUDE.md ~/.claude/CLAUDE.md
```

### Option 3: Both (Layered)

Use the dotfiles approach for firm-wide rules that apply everywhere, and the template repo for project-specific context. The two layers compose automatically.

---

## Keeping Memory Current

Memory that's out of date is worse than no memory — agents will confidently do the wrong thing.

### Ownership
Assign one person (or a small working group) as the memory maintainer. Their job is to:
- Review the firm `CLAUDE.md` template quarterly
- Update it when conventions change
- Publish a changelog so engineers know what changed

### Update Process
1. Changes to firm-wide memory are proposed as PRs to the template repo
2. The working group reviews and merges
3. Existing projects pull the update manually or via a script
4. Engineers update their global `~/.claude/CLAUDE.md` during onboarding re-runs

### Signal That Memory Needs Updating
- Agents consistently produce output in the wrong format
- Engineers are adding the same corrections repeatedly in their sessions
- A new compliance requirement came into effect
- The firm's methodology or tooling changed

---

## Onboarding a New Team Member

When a new engineer joins:

1. Clone the dotfiles repo and run the setup script to install global memory
2. Review `~/.claude/CLAUDE.md` and personalize with name and role
3. Create a `CLAUDE.local.md` in any active project for personal preferences
4. Read this document to understand the memory hierarchy

Expected result: their first Claude Code session on any project starts with the full firm context, with no manual setup.

---

## Memory File Reference

| File | Scope | Committed? | Who Manages |
|---|---|---|---|
| `~/.claude/CLAUDE.md` | Global, per machine | No | Individual (from template) |
| `CLAUDE.md` (repo root) | Project, all contributors | Yes | Project team |
| `CLAUDE.local.md` (repo root) | Project, individual only | No (gitignored) | Individual |
| Agent system prompts | Per agent, all users | Yes | Memory maintainer |
