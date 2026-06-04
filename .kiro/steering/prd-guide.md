---
inclusion: manual
---

# PRD Guide (Kiro Spec Format)

This steering file guides PRD creation with output to Kiro's native spec format. The PRD content maps to `requirements.md` and `design.md` in the spec structure.

## Input Required

Before creating PRD, ensure you have:
- Completed PRFAQ (or product concept description)
- Market research summary (if available)
- AI Framing document (for ML products)

## Challenge Check (run BEFORE writing)

Before writing the PRD, critically examine the PRFAQ and research:
1. Would a skeptical VP with budget authority actually fund this? What would they push back on?
2. What's the most likely way this product FAILS in market? (not a small setback — total failure)
3. Is there a simpler version that validates the core hypothesis without the full feature set?
4. What regulatory/political risk did we acknowledge but not actually mitigate in the solution?
5. Are we solving the right problem for the right persona, or did we drift from the research?

Use findings to identify requirements gaps, tighten acceptance criteria, and ensure the PRD addresses real objections.

## Technology Research (REQUIRED — do this BEFORE writing technical sections)

**Purpose:** Validate that all technology recommendations reflect what's available in the current year, not stale training data assumptions.

**Step 1:** Determine the current year from the system date.

**Step 2:** Run web searches across two tracks:

**Track A — Build Stack (what to build WITH):**
- "[capability area] frameworks [current year]"
- "AWS [service category] new features [current year]"
- "best [technology category] [current year]"
- Focus on: frontend frameworks, backend runtimes, databases, AI/ML services, auth, infrastructure

**Track B — Product Capabilities (what tech ENABLES features):**
- "generative AI capabilities [product domain] [current year]"
- "[feature type] API services available [current year]"
- "Amazon Bedrock models [current year] capabilities"
- Focus on: AI models, APIs, platform capabilities, third-party services

**Step 3:** For every tech recommendation in the PRD:
- Confirm it exists and is GA (or note if preview/beta)
- Include a source link to documentation or announcement
- Note the specific version or release date

**Quality gate:** No tech recommendation without a current-year source link. If you can't verify availability, note it as "unverified — requires validation" and suggest alternatives.

**Output:** Include a "Technology Landscape" section in the PRD documenting:
- Recommended AWS services with current capabilities
- Framework/runtime versions
- AI model availability and capabilities
- Any emerging tech that enables product features

## Dual Output Strategy

Generate TWO outputs:

1. **Traditional PRD** → `documents/PRD_[Product]_[Date].html`
2. **Kiro Spec** → `.kiro/specs/[product-slug]/requirements.md`

**Note:** The PRD document must be HTML (for browser viewing). The Kiro spec remains markdown (required by Kiro's spec format).

## EARS Syntax for Requirements

Kiro uses EARS (Easy Approach to Requirements Syntax). Convert user stories to this format:

### Ubiquitous Requirements (always true)
```
THE SYSTEM SHALL [capability]
```

### Event-Driven Requirements
```
WHEN [event occurs]
THE SYSTEM SHALL [response]
```

### State-Driven Requirements
```
WHILE [state is active]
THE SYSTEM SHALL [behavior]
```

### Conditional Requirements
```
IF [condition is true]
THE SYSTEM SHALL [action]
```

### Complex Requirements
```
WHEN [event] WHILE [state] IF [condition]
THE SYSTEM SHALL [response]
```

## Requirements.md Template

```markdown
# [Product Name] Requirements

## Overview
[2-3 sentence product description from PRFAQ]

## User Stories

### US-001: [Story Title]
**As a** [persona]
**I want to** [capability]
**So that** [benefit]

**Acceptance Criteria:**
WHEN user [action]
THE SYSTEM SHALL [response]

WHEN user [invalid action]
THE SYSTEM SHALL [error handling]

### US-002: [Story Title]
...

## Functional Requirements

### FR-001: [Requirement Title]
**Priority:** P0 | P1 | P2
**Persona:** [Primary user]

WHEN [trigger event]
THE SYSTEM SHALL [expected behavior]

**Rationale:** [Why this requirement exists]

### FR-002: [Requirement Title]
...

## Non-Functional Requirements

### NFR-001: Performance
THE SYSTEM SHALL respond to user actions within 200ms

### NFR-002: Availability
THE SYSTEM SHALL maintain 99.9% uptime

### NFR-003: Security
WHEN user session is inactive for 30 minutes
THE SYSTEM SHALL automatically log out the user

## Data Requirements

### DR-001: [Data Entity]
THE SYSTEM SHALL store [data fields]
THE SYSTEM SHALL retain data for [duration]

## Integration Requirements

### IR-001: [Integration Name]
THE SYSTEM SHALL integrate with [external system]
WHEN [trigger] THE SYSTEM SHALL [action]

## Constraints

- [Technical constraint 1]
- [Business constraint 2]
- [Regulatory constraint 3]

## Out of Scope
- [Feature explicitly excluded]
- [Capability deferred to future phase]

## Success Metrics
| Metric | Target | Measurement |
|--------|--------|-------------|
| [KPI 1] | [Value] | [How measured] |
```

## Persona to User Story Mapping

For each PRD persona, create corresponding user stories:

| Persona | Primary Workflows | User Stories |
|---------|------------------|--------------|
| [Name] | [Workflow 1] | US-001, US-002 |
| [Name] | [Workflow 2] | US-003, US-004 |

## Priority Definitions

| Priority | Meaning | Kiro Treatment |
|----------|---------|----------------|
| P0 | Must have for MVP | Include in initial spec |
| P1 | Should have | Add after P0 complete |
| P2 | Nice to have | Separate spec or backlog |

## AI/ML Product Requirements

For ML products, add these sections:

```markdown
## ML Requirements

### MLR-001: Model Performance
THE SYSTEM SHALL achieve [metric] >= [threshold]
THE SYSTEM SHALL maintain [latency] <= [value]ms

### MLR-002: Data Pipeline
WHEN new training data is available
THE SYSTEM SHALL trigger model retraining

### MLR-003: Monitoring
THE SYSTEM SHALL alert when model performance degrades by [X]%

## Data Requirements (ML-Specific)

### Training Data
THE SYSTEM SHALL require minimum [N] labeled examples
THE SYSTEM SHALL validate data quality before training

### Inference Data
WHEN input data is received
THE SYSTEM SHALL validate against expected schema
```

## Generating Kiro Spec

After creating PRD, generate the Kiro spec:

1. Create directory: `.kiro/specs/[product-slug]/`
2. Generate `requirements.md` with EARS-formatted requirements
3. Kiro will auto-generate `design.md` when you advance the spec
4. Kiro will auto-generate `tasks.md` from design

## Quality Checklist

Before completing:
- [ ] Technology Research completed (current-year validated)
- [ ] Every tech recommendation has a source link confirming current-year availability
- [ ] **Inline SVG architecture diagram included** (service boxes, arrows, data flow — styled with CSS variables)
- [ ] **SVG diagram actually paints** — `<defs>` is closed and all shapes are AFTER `</defs>`; verified with `xmllint --noout` (well-formed) + a shape-count outside `<defs>` ≥1 (commands in `#steering/product-workflow.md` → Syntax Gate), NOT just `grep '<svg'`
- [ ] All PRFAQ features have corresponding requirements
- [ ] Requirements use EARS syntax correctly
- [ ] Acceptance criteria are testable
- [ ] Personas map to user stories
- [ ] Priorities are assigned (P0/P1/P2)
- [ ] ML requirements included (if applicable)
- [ ] Both PRD document and Kiro spec created
