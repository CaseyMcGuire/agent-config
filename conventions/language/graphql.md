# GraphQL conventions

- Prefer union types for mutation responses, with a success variant and a distinct variant for each possible failure.

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
