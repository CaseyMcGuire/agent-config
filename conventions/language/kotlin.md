# Kotlin conventions

## File organization

- By default, give each top-level class or interface its own file named
  after the type, such as `UserPolicy.kt`.
- Keep a private implementation type in its owner's file when moving it
  would require wider visibility or obscure which type owns it.

## Multiline calls and chains

- In a multiline call with named arguments, put one argument on each
  line. Keep `name = value` together when the value fits on one line.
- When a fluent chain wraps, put each modifier on its own continuation
  line.

```kotlin
val problemLanguage by belongsTo<ProblemLanguage>("problem_language")
  .field(problemLanguageId)
  .unique()
  .inverse(ProblemLanguage::judgeConfiguration)
  .onDelete(OnDelete.RESTRICT)
```

## Mapping functions

- Prefer small, explicit mapping functions such as `toGraphqlType()` and
  `fromTableRow()` that show the field mappings directly.
- Use extension functions for conversions from an existing type, or a
  companion factory when constructing a model from another representation.
- Prefer named arguments when constructing models with several fields.

## Dependency injection

- When using dependency injection, such as Spring, prefer declaring
  dependencies in the primary constructor as `private val` properties.

## Distinct cases

- Use sealed hierarchies when a value can represent a fixed set of cases
  with different meanings or data.
- Handle the variants explicitly with `when`.
