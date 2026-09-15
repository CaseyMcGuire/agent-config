# React conventions

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

function Component(props: Props) {
  const { prop1, prop2 } = props;

  return (
    <div>
      {prop1}: {prop2}
    </div>
  );
}
```
