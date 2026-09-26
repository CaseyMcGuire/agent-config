# Kotlin conventions

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
