# GraphQL conventions

## Mutation responses

- Prefer response unions that describe the mutation's supported outcomes:
  a success variant and variants for expected application failures.
- Add a distinct failure variant when callers benefit from its specific
  meaning, structured data, or recovery behavior.
- Group ordinary field validation failures into a validation variant
  containing field-level errors.
- Include useful structured fields; do not require clients to parse
  human-readable messages to determine what happened.
- Map known domain and validation failures deliberately. Do not turn
  every unexpected exception into a validation failure.
- Keep unexpected internal failures in the application's standard
  error-handling path.
- Clients should handle result variants explicitly through `__typename`,
  while retaining handling for GraphQL and transport errors.

Example schema for a `createProject` mutation:

```graphql
type Mutation {
  createProject(name: String!): CreateProjectResponse!
}

union CreateProjectResponse =
    CreateProjectSuccess
  | ValidationError
  | PermissionDenied
  | ProjectNameAlreadyExists

type CreateProjectSuccess {
  projectId: ID!
}

type ValidationError {
  fieldErrors: [FieldError!]!
}

type FieldError {
  field: String!
  message: String!
}

type PermissionDenied {
  message: String!
}

type ProjectNameAlreadyExists {
  suggestedName: String!
}
```
