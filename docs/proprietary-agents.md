# Proprietary Agent Ownership

This document makes the case for building and owning proprietary agents rather than relying on off-the-shelf AI tools, and outlines the ownership strategy and build roadmap.

---

## The Strategic Argument

Off-the-shelf AI tools provide general-purpose capability. They do not encode your firm's methodology, your compliance expertise, or your delivery patterns. Every engagement starts from scratch.

Proprietary agents change that. Each agent built is an investment that:

- **Captures institutional knowledge in code** — methodology, compliance rules, and delivery patterns live in the agent, not in individual consultants
- **Compounds over time** — agents improve with each project, getting better at your specific domain
- **Creates repeatable quality** — every engagement benefits from the accumulated expertise of all prior engagements
- **Differentiates the firm** — competitors using generic tools cannot replicate agents trained on your firm's unique knowledge and history

---

## AI-Native vs. Traditional Agile

| Traditional Agile | Agent-Based Agile |
|---|---|
| Requirements written manually | Agents draft from source documents |
| Stories written in planning meetings | Agents generate from requirements |
| Tests written after code | Tests generated alongside code |
| Docs written at the end | Docs generated continuously |
| Reviews bottlenecked by bandwidth | Agent pre-review before human review |

---

## Why Off-the-Shelf Isn't Enough

| Capability | Off-the-Shelf | Proprietary Agent |
|---|---|---|
| General task execution | Yes | Yes |
| Firm-specific process knowledge | No | Yes |
| Federal compliance rules baked in | No | Yes |
| Improves with your project history | No | Yes |
| Client data stays in-house | Depends | Yes |
| Differentiated IP | No | Yes |
| Consistent output format across teams | No | Yes |

The strategy is not to replace general-purpose AI tools — it's to wrap them with proprietary orchestration, prompt engineering, and process logic that reflects your firm's unique expertise.

---

## What "Ownership" Means

Owning an agent means owning:

1. **The system prompt** — the instructions, constraints, and domain knowledge baked into each agent
2. **The process logic** — how inputs are structured, how outputs are formatted, how context is passed between phases
3. **The evaluation criteria** — how you measure whether an agent is performing well and improving
4. **The improvement loop** — the process for updating agents based on project feedback

Ownership does not require owning the underlying model. The Anthropic API provides the model; you own the layer on top.

---

## Build Roadmap

### Phase 1: Foundation (Build First)
Start with the agents that have the highest toil reduction and clearest input/output contracts.

- [ ] **Development Agent** — highest frequency of use, clear inputs (specs + codebase), measurable outputs (code + tests)
- [ ] **Backlog Agent** — high toil, structured inputs (requirements), structured outputs (stories + acceptance criteria)
- [ ] **QA Agent** — directly tied to development, acceptance criteria → test cases is a well-defined transform

### Phase 2: Workflow Integration
Connect phase agents through the orchestrator to enable artifact flow.

- [ ] **Orchestrator Agent** — state management, routing, human gate enforcement
- [ ] **Design Agent** — ADRs and API contracts from stories
- [ ] **Planning Agent** — sprint composition from backlog

### Phase 3: Full Lifecycle
Complete coverage from discovery through retrospective.

- [ ] **Discovery Agent** — RFP/document ingestion (high complexity, high value)
- [ ] **Release Agent** — release notes and stakeholder summaries
- [ ] **Retro Agent** — metrics analysis and pattern detection

---

## How Agents Improve Over Time

Each completed project is a source of training signal:

- **Feedback loops** — human reviewers flag agent outputs that needed significant correction; these become examples for prompt refinement
- **Output quality tracking** — measure how much humans edit agent outputs over time; declining edits = improving quality
- **Domain expansion** — as the firm takes on new types of work, agents are updated with new domain knowledge

<!-- Detail the specific process for collecting feedback, updating prompts, and versioning agent improvements -->
TBD

---

## IP and Competitive Moat

The proprietary value is in the **prompt engineering, process design, and domain knowledge** — not the model itself. This means:

- Agents can be migrated to newer/better models as they become available without losing the proprietary layer
- The IP is portable and durable across model generations
- Each new engagement adds to the moat, not just the revenue

<!-- Add notes on how agent IP is documented, protected, and transferred across the firm -->
TBD
