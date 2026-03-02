# ai-driven-product

> AI starts with product.

A reference implementation and workflow guide demonstrating how a federal software consulting firm can transform a traditional agile development process into an AI-native, agent-based workflow.

## The Shift

Every phase of the agile lifecycle gets an agent layer that handles toil, generates artifacts, and accelerates human decision-making. Humans stay in the loop at decision gates — agents do the drafting, structuring, and analysis.

## Agent-Based SDLC

### Discovery & Vision
- Agents synthesize stakeholder interviews, prior project data, and domain documents into a product brief
- Claude ingests RFPs, regulations, and policy documents and extracts structured requirements
- **Output:** draft product vision, initial user story candidates

### Backlog Refinement
- Agents parse raw requirements into structured stories with acceptance criteria
- Dependency mapping and compliance tagging (critical for federal engagements)
- **Output:** refined, prioritized backlog ready for sprint planning

### Sprint Planning
- Agents suggest sprint composition based on velocity, dependencies, and risk signals
- Complexity and risk flagging before work begins
- **Output:** draft sprint plan for team review

### Design & Architecture
- Agents draft architecture decision records (ADRs) from requirements
- Generate user flow descriptions, data models, and API contracts
- Consistency checks against existing design systems and prior decisions
- **Output:** design artifacts ready for human review

### Development
- Agentic coding: specs → code, with tests generated alongside
- PR review agents flag issues before human review
- Documentation generated from code, not written separately
- **Output:** working code with tests and docs

### Testing & QA
- Agents generate test cases directly from acceptance criteria
- Security scanning and compliance checks run automatically
- **Output:** test suite, scan reports, compliance attestation

### Sprint Review & Release
- Agents draft release notes from commits and PRs
- Demo scripts generated from stories
- **Output:** release artifacts and stakeholder-ready summaries

### Retrospective
- Agents analyze sprint metrics and identify patterns across sprints
- Draft action items from retro notes
- **Output:** structured retro summary with improvement signals

## Proprietary Agent Ownership

Off-the-shelf AI tools provide a foundation, but sustainable competitive advantage in federal consulting comes from **building and owning the agents themselves**. Proprietary agents encode your firm's process knowledge, compliance expertise, and delivery patterns — and compound in value over time.

### Why Ownership Matters

- **Institutional knowledge is captured in code**, not locked in individual consultants' heads
- **Repeatable quality** across engagements and teams, not dependent on who's available
- **Competitive differentiation** — your agents reflect your methodology, not a vendor's generic workflow
- **Data sovereignty** — federal clients require control over where data flows; owned agents keep that control in-house
- **Continuous improvement** — agents get better with every project, creating a compounding advantage

### The Agent Hierarchy

A proprietary agent system has two layers:

**Orchestrator Agent**
A top-level agent that manages the full SDLC lifecycle. It routes work to the appropriate phase agents, carries context between phases, tracks artifact state, and surfaces blockers to human reviewers. This agent embodies your firm's end-to-end delivery methodology.

**Phase Sub-Agents**
Specialized agents, one per SDLC phase, each trained on the specific domain knowledge and output format required for that phase:

| Sub-Agent | Owns |
|---|---|
| Discovery Agent | RFP/requirements ingestion, product brief generation |
| Backlog Agent | Story writing, acceptance criteria, compliance tagging |
| Planning Agent | Sprint composition, risk flagging, velocity analysis |
| Design Agent | ADRs, data models, API contracts, design consistency |
| Development Agent | Code generation, PR review, documentation |
| QA Agent | Test case generation, security scanning, compliance attestation |
| Release Agent | Release notes, demo scripts, stakeholder summaries |
| Retro Agent | Metrics analysis, pattern detection, action item drafting |

### Build vs. Buy

| Capability | Off-the-Shelf | Proprietary Agent |
|---|---|---|
| General task execution | Yes | Yes |
| Firm-specific process knowledge | No | Yes |
| Federal compliance rules baked in | No | Yes |
| Improves with your project history | No | Yes |
| Client data stays in-house | Depends | Yes |
| Differentiated IP | No | Yes |

The strategy is not to replace general-purpose AI tools — it's to wrap them with proprietary orchestration, prompt engineering, and process logic that reflects your firm's unique expertise.

## Key Principles

1. **Agents handle toil; humans handle judgment** — drafting, formatting, searching, and summarizing are agent tasks; decisions, approvals, and accountability stay human
2. **Every agent output is a starting point, not a final answer** — humans review and refine
3. **Artifacts flow between phases** — agents carry context forward (requirements inform tests, stories inform docs)
4. **Federal context is first-class** — compliance, security, and auditability are built into every phase, not bolted on at the end

## The Value Proposition

| Traditional Agile | Agent-Based Agile |
|---|---|
| Requirements written manually | Agents draft from source documents |
| Stories written in planning meetings | Agents generate from requirements |
| Tests written after code | Tests generated alongside code |
| Docs written at the end | Docs generated continuously |
| Reviews bottlenecked by bandwidth | Agent pre-review before human review |

## Tooling

- **AI:** Claude (Anthropic) — `claude-sonnet-4-6` for most tasks, `claude-opus-4-6` for complex reasoning
- **Interface:** Claude Code for agentic development workflows
- Stack, infrastructure, and integrations TBD as the project evolves
