# React conventions

- Default to one component per `.tsx` file and name the file after the
  component. Parts of a compound component that form one API, such as
  `PostShell.Title` and `PostShell.Contents`, can share a file.
- Prefer named function declarations for components.
- Default-export a file's main component, using
  `export default function Component(props: Props)` when it accepts props.
- Keep a component's styles and small pure helpers in its file. Shared
  themes and tokens can live separately.
- Put style declarations above the component.
- Keep JSX and component configuration arrays readable.

## Component props

- In a single-component file, name the file-local props type `Props`
  and use it in the function signature.
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
