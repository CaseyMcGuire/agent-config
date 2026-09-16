# General coding conventions

- Prefer straightforward, readable code.
- Avoid clever abstractions and unnecessary indirection.
- Do not use single-line `if` statements.
- Expand dense argument lists, arrays, and chained calls when helpful.
- Do not refactor unrelated code.
- Run focused validation appropriate to the change.
- Follow the patterns already in the codebase before introducing new
  ones. When deviating, say why.
- Do not add dependencies without asking.
- Document the public API of library code.
- Keep supporting implementation and tests together.

## Method structure and readability

- Make methods that coordinate multiple steps read as a clear sequence
  of operations at a consistent level of abstraction.
- Use descriptive names that make each method's purpose clear at the
  call site, without requiring the reader to inspect its implementation.
- Keep high-level flow separate from implementation details. Extract
  cohesive steps into helpers when doing so makes the coordinating method
  easier to follow.
- Prefer guard clauses and early returns when they reduce nesting and
  make the main path easier to follow.
- Group related statements together and separate distinct steps with
  blank lines.
- Split methods and components by responsibility, not arbitrary line counts.
  Avoid extracting trivial statements that are clearer inline.
- Comment on non-obvious intent and important constraints. Explain intent
  rather than narrating individual statements.

When an example would help clarify these guidelines, read the
[order-service example](./examples/method-structure.md).

## Communication

- Lead with the recommendation and the reason. Mention alternatives only
  when they were close, and say what would tip the choice.
- Do not present options as equal when the evidence favors one.
- Distinguish what was verified from what is inferred. Name the file,
  test, or command behind a claim.
- Say what was not checked.
- Keep summaries proportional to the decision. Routine choices get one
  line; trade-offs get the trade-off.
- Do not restate the diff.
- When asking a question, state the default you would choose and why.
- If the requested approach has a concrete problem, say so before
  implementing.

## Failures and findings

- If validation fails, fix the cause. Do not weaken tests, delete
  assertions, suppress warnings, or loosen types to get a pass.
- Report bugs or debt found outside the task. Do not fix them.
- If the task turns out larger than expected, stop and say so before
  continuing.
