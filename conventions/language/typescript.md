# TypeScript conventions

## Discriminated unions

- Use discriminated unions when a value can represent a fixed set of
  cases with different meanings or data. Give each variant a literal
  discriminant, such as `type`.
- A variant containing only the discriminant can stay inline. Give each
  variant with additional fields its own named type and use that name in
  the union.
- Handle the variants explicitly with `switch` on the discriminant.

```ts
type Loaded = { type: "loaded"; value: string };
type Failed = { type: "failed"; message: string };

type LoadState = { type: "idle" } | Loaded | Failed;
```

## Frontend imports

- When a frontend app has a configured source root or alias, use it for
  imports across feature directories. For example, an app that resolves
  imports from its frontend root can import `"components/MenuItem"`.
