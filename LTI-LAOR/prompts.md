# Prompts Used to Generate LTI ATS System Design

Claude Code was used to generate the prompts and outputs for this project.
Skills from https://github.com/deanpeters/Product-Manager-Skills
---

## Prompt 1: Product Description, Value Proposition & Lean Canvas


```bash
claude --context skills/press-release/SKILL.md \
  "Apply this skill to write a press release for LTI ATS using this brief: @docs/project-brief.md"

claude --context skills/business-health-diagnostic/SKILL.md \
  "Using the output above, define the key metrics and unit economics for the Lean Canvas"
```

---

## Prompt 2: Use Cases and Diagrams

```prompt
Based on the product description and feature set generated in Phase 1:

[Phase 1 output]

Define the 3 most important use cases that together cover the end-to-end hiring workflow:
- Use Case 1: Job creation, publishing, and candidate reception
- Use Case 2: Evaluation, testing, and interviews
- Use Case 3: Final selection and hiring

For each use case provide:
- Actors
- Preconditions
- Main flow (8-12 numbered steps, active voice: "The [Actor] does X")
- Postconditions
- 2-3 alternative flows
- A PlantUML use case diagram

The 3 use cases must be complementary with minimal overlap.
Output in Markdown.
```

---

## Prompt 3: Data Model

```prompt
Based on the use cases and features from Phases 1 and 2:

[Phase 1 + Phase 2 output]

Design a relational data model for LTI ATS. Requirements:
- Multi-tenancy with company-level isolation
- Configurable hiring pipelines (not hardcoded stages)
- Structured scorecards with per-competency ratings
- AI matching scores per application
- Activity timeline / audit trail per application

For each entity, provide a Markdown table with: Attribute | Type (PostgreSQL) | Description.
Mark foreign keys as "UUID (FK)". Note nullable fields.

Then provide:
1. An ASCII ER diagram showing entities and relationships.
2. A full list of relationships (1:1, 1:N, N:M) with one-line explanations.

Target 12-16 entities. Keep it practical for a startup MVP — don't over-normalize.
Output in Markdown.
```

---

## Prompt 4: High-Level System Architecture

```prompt
You are a senior software architect. Based on Phases 1-3:

[Phase 1 + Phase 2 + Phase 3 output]

Design a high-level system architecture for LTI ATS. Produce:

1. Written description (4-6 paragraphs) covering:
   - Architecture pattern and why it fits a startup context
   - Each service and its single responsibility
   - Sync (REST/gRPC) vs async (event bus) communication and the rationale
   - Storage strategy: databases, caching, file storage, search
   - Cross-cutting concerns: auth, observability, CI/CD, multi-tenancy

2. ASCII architecture diagram with all layers:
   - Clients → API Gateway → Microservices → Event Bus → Storage
   - Supporting services (AI, notifications, analytics)

Optimize for: independent scalability, partial failure resilience, and fast iteration for a 5-15 person team.
Output in Markdown.
```

---

## Prompt 5: C4 Diagram (Application Service Deep Dive)

```prompt
Based on the architecture from Phase 4:

[Phase 4 output]

Create a C4 diagram set for the Application Service (candidate pipeline management). Produce 4 levels as ASCII diagrams with labeled arrows:

Level 1 — Context: LTI ATS, its 3 user personas, and external systems (Job Boards, HRIS, Calendars, AI Provider).

Level 2 — Containers: All services within LTI ATS. Highlight Application Service as the C4 focus.

Level 3 — Components inside Application Service:
- API Layer (list endpoints)
- Application Intake Controller
- Pipeline Manager
- Knockout Filter Engine
- Application Repository
- Event Publisher
- Show which external services consume the events

Level 4 — Code inside Pipeline Manager:
- PipelineManagerService (public methods)
- StageTransitionValidator
- AutoAdvanceRuleEngine
- TimelineRecorder
- StageChangeEventPublisher

Output in Markdown with fenced code blocks for each diagram.
```

---