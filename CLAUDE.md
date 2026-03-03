# ai-driven-product

AI starts with product.

## Project Overview
A reference implementation and workflow guide for a federal software consulting firm demonstrating how to transform a traditional software development process into an AI-native, agent-based workflow.

The goal is to show how AI tooling (primarily Claude) can be embedded at every stage of the SDLC — from requirements and design through development, testing, and delivery — increasing speed, consistency, and quality for federal software engagements.

## Agent System

The system is a two-layer hierarchy:

**Orchestrator Agent** — manages the full SDLC lifecycle, routes work to phase agents, carries context between phases, enforces human approval gates. Design details TBD.

**Phase Sub-Agents** — 8 specialized agents, one per SDLC phase:

| Agent | Model | Primary Inputs | Primary Outputs |
|---|---|---|---|
| Discovery | `claude-opus-4-6` | RFPs, interview notes, policy docs | Product brief, story candidates, compliance flags |
| Backlog | `claude-sonnet-4-6` | Product brief, story candidates | Refined stories, acceptance criteria, prioritized backlog |
| Planning | `claude-sonnet-4-6` | Prioritized backlog, velocity data | Draft sprint plan, risk flags |
| Design | `claude-sonnet-4-6` | Sprint stories, architecture docs, ADRs | ADRs, data models, API contracts |
| Development | `claude-sonnet-4-6` | Design artifacts, acceptance criteria, codebase | Code, tests, PR review, documentation |
| QA | `claude-sonnet-4-6` | Implementation, acceptance criteria, compliance reqs | Test suite, security scan, compliance attestation |
| Release | `claude-sonnet-4-6` | Merged PRs, commit history, sprint stories | Release notes, demo script, stakeholder summary |
| Retro | `claude-sonnet-4-6` | Sprint metrics, retro notes, prior action items | Metrics summary, pattern analysis, action items |

Human approval gates are enforced between every phase — no phase begins without explicit human sign-off on the previous phase's output.

## SDLC Design Principles

1. **Agents handle toil; humans handle judgment** — drafting, formatting, searching, and summarizing are agent tasks; decisions, approvals, and accountability stay human
2. **Every agent output is a starting point, not a final answer** — humans review and refine
3. **Artifacts flow between phases** — agents carry context forward (requirements inform tests, stories inform docs)
4. **Federal context is first-class** — compliance, security, and auditability are built into every phase, not bolted on at the end

## Proprietary Agent Strategy

Competitive advantage comes from building and owning the agents, not just using AI tools. Ownership means owning: the system prompts, the process logic, the evaluation criteria, and the improvement loop. Agents improve with each project through feedback loops and prompt refinement.

**Build roadmap priority:**
1. Phase 1: Development Agent, Backlog Agent, QA Agent
2. Phase 2: Orchestrator, Design Agent, Planning Agent
3. Phase 3: Discovery Agent, Release Agent, Retro Agent

## Federal Context

Engagements operate under: FedRAMP, FISMA, NIST 800-53, Section 508, CMMC (where applicable).

Key design constraints:
- No client data sent to third-party services beyond the approved AI API (Anthropic)
- Artifacts stored in client-controlled infrastructure
- Every agent action is logged — inputs, outputs, human review actions, version history
- Compliance tagging on every story at creation time (not discovered during QA)
- Security scanning (SAST, dependency, secrets, container) runs every sprint

## Agent Memory & Context Distribution

Firm-wide baseline context is distributed via CLAUDE.md files:
- `~/.claude/CLAUDE.md` — global, per machine (name, role, firm-wide standards)
- `CLAUDE.md` (repo root) — project-level, committed, shared with team (this file)
- `CLAUDE.local.md` — personal, gitignored, individual preferences

Agent system prompts are the other memory vector — firm knowledge baked into each phase agent's prompt.

## Skills

Custom skills live in `skills/` — each subfolder contains a `SKILL.md` with instructions.
When the user says "use the [name] skill" or "run the [name] skill", read `skills/[name]/SKILL.md` and execute it.

| Skill | Path | Description |
|---|---|---|
| sop-creator | `skills/sop-creator/SKILL.md` | Guides user through creating a Standard Operating Procedure |
| brand-apply | `skills/brand-apply/SKILL.md` | Applies company branding to any document |

## Documentation Map

| Topic | File |
|---|---|
| Agent architecture & Mermaid flowchart | `docs/agent-architecture.md` |
| SDLC phase details (inputs, outputs, touchpoints) | `docs/sdlc-phases.md` |
| Federal compliance design | `docs/federal-considerations.md` |
| Proprietary agent strategy & build roadmap | `docs/proprietary-agents.md` |
| Agent memory & CLAUDE.md distribution | `docs/agent-memory.md` |

## What's Decided vs. TBD

**Decided:**
- Two-layer agent hierarchy (orchestrator + 8 phase sub-agents)
- Model assignments per agent (see Agent System table above)
- Human approval gate at every phase transition
- Federal compliance frameworks in scope
- Build roadmap phase order
- CLAUDE.md as the memory distribution mechanism

**TBD:**
- Technical stack and infrastructure
- Orchestrator prompt design and state management
- Sub-agent prompt engineering approach
- Context passing format between phases
- Compliance tag taxonomy
- Logging and audit architecture
- Specific security scanning tools
- Feedback loop and prompt improvement process

## Commands
<!-- Update these as the project takes shape -->
- **Install:** TBD
- **Dev server:** TBD
- **Build:** TBD
- **Test:** TBD
- **Lint/Format:** TBD

## Architecture
- Stack: TBD
- AI model(s): Claude (via Anthropic API) — default to `claude-sonnet-4-6` or `claude-opus-4-6`
- Key directories: TBD

## Code Conventions
- Keep code simple and focused — avoid over-engineering
- Prefer editing existing files over creating new ones
- No unnecessary comments or docstrings on unchanged code
- Validate only at system boundaries (user input, external APIs)

## AI / Anthropic API
- Use the latest Claude models: Sonnet 4.6 (`claude-sonnet-4-6`) for most tasks, Opus 4.6 (`claude-opus-4-6`) for complex reasoning
- Store API keys in `.env` (never commit secrets)

## Environment Variables
- Copy `.env.example` to `.env` (file TBD)
- Never commit `.env` or secret keys

## Git
- Main branch: `main`
- Remote: https://github.com/eganpg/ai-driven-product
