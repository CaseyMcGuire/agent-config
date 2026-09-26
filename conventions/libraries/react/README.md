# React conventions

- Prefer named function declarations for components.
- Default-export a file's main component, using
  `export default function Component(props: Props)` when it accepts props.
- Keep styles local to their component, except shared themes or tokens.
- Put style declarations above the component.
- Keep JSX and component configuration arrays readable.

## Component props

- Prefer a named props type, such as `Props`, over an inline object type
  in the component's function signature.
- Prefer accepting a single `props` parameter over destructuring in the
  function signature.
- Destructuring is fine in the component if it makes sense.

```tsx
type Props = {
  prop1: string;
  prop2: number;
};

export default function Component(props: Props) {
  const { prop1, prop2 } = props;

  return (
    <div>
      {prop1}: {prop2}
    </div>
  );
}
```

## Forms and input components

- Keep editing state local when it is only needed by that input or form.
- Expose meaningful callbacks such as `onSubmit(text)` or
  `onSubmit(title, content)`. Let the caller coordinate saving or submitting
  those values.
