# Relay conventions

## Data requirements

- Colocate fragments with the components that consume their data.
- Accept generated fragment `$key` types as props and read the data with
  `useFragment`.
- Have parent queries and fragments spread child fragments so each
  component declares the fields it needs.

## Mutations

- Prefer `switch` statements on a response's `__typename` over individual `if` checks to keep return-type handling explicit and type-safe.
- Prefer Relay directives and other idiomatic built-in mechanisms when they
  support the required behavior. Manipulate the store directly only when no
  such approach is available.
- When direct store manipulation is necessary, add a code comment explaining
  why an idiomatic built-in approach does not suffice.
