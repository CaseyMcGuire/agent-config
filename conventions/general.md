# General coding conventions

- Prefer straightforward, readable code.
- Avoid clever abstractions and unnecessary indirection.
- In languages with braced control flow, use braces for every branch of
  an `if`/`else if`/`else` statement. Put the body on its own line,
  even for a single `return` or `throw`.
- Expand dense argument lists, arrays, and chained calls when helpful.
- Do not refactor unrelated code.
- Run focused validation appropriate to the change.
- Follow the patterns already in the codebase before introducing new
  ones. When deviating, say why.
- Do not add dependencies without asking.
- Document the public API of library code.
- Keep supporting implementation and tests together.
- Use existing generated types, constants, and route builders for API
  contracts, field names, and navigation instead of duplicating those
  contracts by hand.

## Naming

- Choose names that make calls and conditions read like ordinary English.
  Read the receiver, function name, and arguments together. A caller
  should understand the operation without opening the implementation.
- Name variables and parameters for their roles. When moving a page,
  `sourceFolderId` and `destinationFolderId` explain how each ID is used.
- Give actions verbs that describe what they do. Name predicates for the
  question they answer. For example, `inv.check(d)` becomes
  `invoice.isOverdue(today)`, and `notify(inv)` becomes
  `sendPaymentReminder(invoice)`.
- Use full words when an abbreviation would make the reader guess.
  Familiar domain terms such as `id` and short names such as `i` for
  an index in a small loop are clear in context.

## Method structure and readability

- Make methods that coordinate multiple steps read as a clear sequence
  of operations at a consistent level of abstraction.
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
