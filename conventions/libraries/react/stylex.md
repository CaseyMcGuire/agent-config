# StyleX conventions

- Declare styles with `stylex.create` at module scope.
- Use the `sx` prop on JSX elements that support it, for example
  `<div sx={styles.container} />`.
- Share styles only when they are part of a common theme. Otherwise, repeat them in each file.
- Put StyleX properties on separate lines.
