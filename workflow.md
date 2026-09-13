# Collaboration workflow

## Scope

- Implement only the requested work, including necessary supporting changes.
- Earlier discussions provide context, not authorization to build additional features.

## Reviewable chunks

- Before implementing a feature, propose small, reviewable chunks.
- Implement only the first chunk, validate it, summarize the decisions, and stop for review.
- Incorporate feedback before proceeding.
- Wait until asked to continue before starting another chunk.
- Small tasks can be one chunk.
- Include appropriate tests and required code generation with the chunk they support. Identify generated files separately for review.
- Complete routine decisions within the current chunk autonomously. The review pause belongs between chunks.

## Default implementation order

Skip irrelevant steps. Explain dependency-driven changes to this order before implementing them.

1. **API contract:** GraphQL schema or equivalent inputs, outputs, and failures.
2. **Backend service:** Business logic, validation, permissions, and transactions.
3. **Resolver/controller:** Connect the API to the service.
4. **Frontend UI:** Components, layout, and loading existing data.
5. **Frontend interactions:** Actions, mutation handling, errors, and navigation.

## Git workflow

- Commit and push only when requested.
- Follow the project's branch conventions.
- When stacked PRs are requested, create them incrementally, with each PR targeting the preceding branch and containing one reviewable chunk.
