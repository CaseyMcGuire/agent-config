---
name: feature-workflow
description: >-
  Plan and implement features with user-reviewed checklists and a review pause
  after each chunk. Use for feature development or when the user explicitly
  requests the collaboration workflow.
---

# Feature workflow

Apply this workflow throughout the selected task, including subsequent turns.
Use it for the whole session only when the user requests that scope. Follow
the project's instructions for task scope, coding conventions, validation, and
Git operations. An explicit request to implement directly overrides this
workflow's planning and review pauses.

## Plan the work

- Propose reviewable chunks, each centered on a coherent part of the task,
  behavior, or important design decision. API, backend, and frontend work can
  each be split into multiple chunks around distinct responsibilities. Let
  scope and reviewability determine chunk size. Do not split work merely to
  meet a line-count target.
- Give a brief summary of what each chunk will entail, then present its steps
  as a Markdown checklist (`- [ ]`). Include the supporting implementation,
  appropriate tests, and required code generation in the same chunk.
- Pause so the user can review and, if needed, revise the checklists. Wait for
  agreement on a chunk's checklist before coding that chunk. Reuse agreement
  already given in the conversation; revisit it when the plan materially changes.
- A task can be one chunk when its scope is coherent and reviewable.

Use this implementation order where applicable. Skip irrelevant steps and
explain dependency-driven changes to the order before implementing them:

1. **API contract:** GraphQL schema or equivalent inputs, outputs, and failures.
2. **Backend service:** Business logic, validation, permissions, and transactions.
3. **Resolver/controller:** Connect the API to the service.
4. **Frontend UI:** Components, layout, and loading existing data.
5. **Frontend interactions:** Actions, mutation handling, errors, and navigation.

## Implement and review each chunk

- Implement one agreed chunk at a time. Complete routine decisions within that
  chunk autonomously.
- Validate the chunk, summarize the decisions, and stop for review. Apply this
  process to every chunk.
- Incorporate feedback before proceeding. Wait until the user asks to continue
  before starting the next chunk.

After each chunk, report:

1. The full agreed implementation checklist again, with completed steps marked
   `- [x]` and remaining steps left unchecked (`- [ ]`). Use plain text for
   routine confirmations and validation summaries; do not invent extra checklists.
2. A brief summary of what will be implemented in the next chunk. If all chunks
   are complete, say so.
3. What changed, by file. Identify generated files separately.
4. Decisions made and why, including any assumption the request did not cover.
5. Validation run, with the command and result.
6. Open questions and anything not verified.
