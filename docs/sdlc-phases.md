# SDLC Phases: Agent-Based Breakdown

Each phase of the agile lifecycle is supported by a dedicated sub-agent. This document details the inputs, outputs, agent behavior, and human touchpoints for each phase.

---

## Discovery & Vision

**Goal:** Transform raw inputs (RFPs, interviews, policy documents) into a structured product brief and initial story candidates.

### Inputs
- RFP or statement of work
- Stakeholder interview notes
- Regulatory or policy documents
- Prior project artifacts (if available)

### Agent Behavior
<!-- Detail how the Discovery Agent processes inputs, what prompts/tools it uses, how it structures output -->
TBD

### Outputs
- Draft product vision statement
- Initial user story candidates
- Key constraints and compliance flags

### Human Touchpoints
- Review and approve product vision before backlog work begins
- Validate that compliance flags are accurate and complete

---

## Backlog Refinement

**Goal:** Convert vision and requirements into a prioritized, well-structured backlog with acceptance criteria and compliance tags.

### Inputs
- Product vision and story candidates from Discovery
- Regulatory requirements and compliance flags
- Existing backlog (if iterating on a live project)

### Agent Behavior
<!-- Detail story generation logic, acceptance criteria format, compliance tagging taxonomy -->
TBD

### Outputs
- Refined user stories with acceptance criteria
- Prioritized and dependency-mapped backlog
- Compliance and regulatory tags per story

### Human Touchpoints
- Product owner review and story approval
- Compliance officer sign-off on tagged items

---

## Sprint Planning

**Goal:** Compose a sprint from the backlog that balances velocity, risk, and dependencies.

### Inputs
- Prioritized backlog
- Team velocity history
- Open risks and dependencies

### Agent Behavior
<!-- Detail sprint composition logic, risk scoring, how velocity data is ingested -->
TBD

### Outputs
- Draft sprint plan with story assignments
- Risk flags and dependency warnings
- Capacity utilization summary

### Human Touchpoints
- Team review and commitment to sprint plan
- Risk acceptance or escalation decisions

---

## Design & Architecture

**Goal:** Produce design artifacts that translate stories into implementable specifications.

### Inputs
- Approved sprint stories
- Existing architecture and design system documentation
- Prior ADRs

### Agent Behavior
<!-- Detail ADR generation, data model drafting, API contract format, consistency checking logic -->
TBD

### Outputs
- Architecture decision records (ADRs)
- Data models and entity relationships
- API contracts
- Design consistency report

### Human Touchpoints
- Architecture review and ADR approval
- Design system compliance sign-off

---

## Development

**Goal:** Translate specifications into working, tested, documented code.

### Inputs
- Approved design artifacts and API contracts
- Story acceptance criteria
- Codebase context

### Agent Behavior
<!-- Detail code generation approach, test generation strategy, PR review logic, documentation generation -->
TBD

### Outputs
- Implementation code
- Unit and integration tests
- PR with agent-generated review comments
- Inline and API documentation

### Human Touchpoints
- Human code review after agent pre-review
- Merge approval

---

## Testing & QA

**Goal:** Validate that the implementation meets acceptance criteria, security standards, and compliance requirements.

### Inputs
- Implemented code and tests
- Acceptance criteria from stories
- Security and compliance requirements

### Agent Behavior
<!-- Detail test case generation from acceptance criteria, security scanning tools/approach, compliance check logic -->
TBD

### Outputs
- Full test suite with coverage report
- Security scan results
- Compliance attestation artifacts

### Human Touchpoints
- QA lead review of scan results and coverage gaps
- Compliance officer sign-off on attestation

---

## Sprint Review & Release

**Goal:** Communicate what was built and prepare artifacts for stakeholder review and release.

### Inputs
- Merged PRs and commit history
- Sprint stories and acceptance criteria
- Previous release notes (for continuity)

### Agent Behavior
<!-- Detail release notes generation from commits/PRs, demo script structure, stakeholder summary format -->
TBD

### Outputs
- Release notes
- Demo script
- Stakeholder-ready sprint summary

### Human Touchpoints
- Product owner review before stakeholder presentation
- Release approval

---

## Retrospective

**Goal:** Identify patterns and generate actionable improvements from the completed sprint.

### Inputs
- Sprint metrics (velocity, bug rate, cycle time, etc.)
- Team retro notes
- Prior retro action items

### Agent Behavior
<!-- Detail metrics analysis approach, pattern detection across sprints, action item generation format -->
TBD

### Outputs
- Sprint metrics summary
- Pattern analysis across recent sprints
- Draft action items for next sprint

### Human Touchpoints
- Team review and prioritization of action items
- Carry-forward tracking of open items
