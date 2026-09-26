# TypeScript conventions

- Use discriminated unions when a value can represent a fixed set of
  cases with different meanings or data. Give each variant a literal
  discriminant, such as `type`.
- Handle the variants explicitly with `switch` on the discriminant.
