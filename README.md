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
