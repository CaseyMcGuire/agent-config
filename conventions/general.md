# General coding conventions

- Prefer straightforward, readable code.
- Avoid clever abstractions and unnecessary indirection.
- Do not use single-line `if` statements.
- Give code room to breathe: use blank lines between logical steps.
- Expand dense argument lists, arrays, and chained calls when helpful.
- Split large functions and components around clear responsibilities.
- Do not refactor unrelated code.
- Run focused validation appropriate to the change.
- Follow the patterns already in the codebase before introducing new
  ones. When deviating, say why.
- Do not add dependencies without asking.
- Comment on why, not what. Document the public API of library code.
- Keep supporting implementation and tests together.

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
