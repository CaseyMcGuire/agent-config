---
name: feature-workflow
description: >-
  Plan and implement features with user-reviewed checklists and a review pause
  after each stage. Use for feature development or when the user explicitly
  requests the collaboration workflow.
---

# Feature workflow

Apply this workflow throughout the selected task, including subsequent turns.
Use it for the whole session only when the user requests that scope. Follow
the project's instructions for task scope, coding conventions, validation, and
Git operations. An explicit request to implement directly overrides this
workflow's planning and review pauses.

## Plan the work

- Propose reviewable stages, each centered on a coherent responsibility,
  behavior, or important design decision. For work spanning an API, backend,
  and frontend, use separate review stages for the API contract, backend
  implementation, frontend components, and frontend integration. Each area
  can span multiple stages around distinct responsibilities. Let scope and
  reviewability determine stage size. Do not split work merely to meet a
  line-count target.
- Present the full plan as one Markdown checklist (`- [ ]`), with one
  top-level checkbox per stage. Give each item a short name and a brief
  summary of what it will entail. Explain supporting tasks beneath the item
  in prose or ordinary bullets when needed. Include appropriate tests and
  required code generation in the stage they support.
- Pause so the user can review and, if needed, revise the stage checklist.
  Wait for agreement on a stage's scope before coding it. Reuse agreement
  already given in the conversation; revisit it when the plan materially changes.
- A task can be one stage when it covers one coherent, reviewable responsibility.

Choose stage boundaries and order based on the feature's scope and
dependencies. This is an example, not a fixed template; omit irrelevant
stages and split areas further when they contain distinct responsibilities:

- [ ] **GraphQL API:** Define the schema, inputs, outputs, and expected failures.
- [ ] **Backend:** Implement business logic, validation, permissions,
  transactions, and resolver/controller integration.
- [ ] **Frontend components:** Build components and layout, including loading
  existing data.
- [ ] **Frontend mutation hookup:** Connect actions to mutations and handle
  results, errors, and navigation.

## Implement and review each stage

- Implement one agreed stage at a time. Complete routine decisions within that
  stage autonomously.
- Validate the stage, summarize the decisions, and stop for review. Each
  top-level checklist item is a separate review point. Apply this process to
  every stage.
- Incorporate feedback before proceeding. Wait until the user asks to continue
  before starting the next stage.

After each stage, report:

1. The full agreed stage checklist again. Mark a stage `- [x]` only when all
   its planned work is implemented and committed. Leave other stages unchecked
   (`- [ ]`), including stages with code implemented but not yet committed.
   Use plain text for routine confirmations and validation summaries; do not
   invent extra checklists.
2. A brief summary of what will be implemented in the next stage. If all stages
   are complete, say so.
3. What changed, by file. Identify generated files separately.
4. Decisions made and why, including any assumption the request did not cover.
5. Validation run, with the command and result.
6. Open questions and anything not verified.
