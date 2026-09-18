---
name: feature-workflow
description: >-
  Plan and implement features with user-reviewed checklists and a review pause
  before committing each stage. Use for feature development or when the user
  explicitly requests the collaboration workflow.
---

# Feature workflow

Apply this workflow throughout the selected task, including subsequent turns.
Use it for the whole session only when the user requests that scope. Follow
the project's instructions for task scope, coding conventions, validation, and
Git operations. Skip design discussion only when the user explicitly asks to
skip it. Ordinary requests to implement or continue do not waive design review.

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

## Discuss the design before each stage

- Before writing code for a stage, inspect the relevant code and present
  the consequential design decisions that stage requires.
- For each decision, explain the proposed approach, the credible
  alternatives, the main trade-off, and your recommendation.
- Include choices that affect dependencies, external integrations,
  public interfaces, persistence, execution boundaries, resource
  ownership, or operational behavior. For example: Docker CLI versus
  an HTTP client, or one JVM per case versus one JVM per suite.
- Keep this proportional to the work. Routine implementation details
  do not need approval. If there are no new consequential decisions,
  say so briefly.
- Wait for agreement on unresolved consequential decisions before
  implementing the affected work. Read-only investigation can proceed
  before that agreement.
- Approval of a stage's scope does not approve design choices that
  have not been presented. A request to "continue" does not waive
  this discussion.
- Reuse decisions already agreed in the conversation; do not ask for
  approval again unless new evidence materially changes the trade-off.
- If implementation reveals a new consequential decision, present it
  before committing to that approach.

## Implement and review each stage

- Implement one agreed stage at a time. Complete routine decisions within that
  stage autonomously.
- Validate the stage, summarize the decisions, and leave the changes
  uncommitted for user review. Stop before making any commit. Each top-level
  checklist item is a separate review point. Apply this process to every stage.
- Incorporate review feedback and revalidate. Commit only after the user has
  reviewed the finished changes and authorized committing them. Agreement on
  the plan or permission to implement is not approval of the finished code or
  authorization to commit it.
- Wait until the user asks to continue before starting the next stage.

When a stage is ready for review, report before committing:

1. The full agreed stage checklist again. Mark a stage `- [x]` only when all
   its planned work is implemented, reviewed by the user, and committed.
   Leave other stages unchecked (`- [ ]`), including stages with code
   implemented but not yet committed. For those stages, state whether they
   are awaiting review or awaiting a commit. The checkbox definition does not
   authorize committing. Use plain text for routine confirmations and
   validation summaries; do not invent extra checklists.
2. A brief summary of what will be implemented in the next stage. If all stages
   are complete, say so.
3. What changed, by file. Identify generated files separately.
4. Decisions made and why, including any assumption the request did not cover.
5. Validation run, with the command and result.
6. Open questions and anything not verified.
