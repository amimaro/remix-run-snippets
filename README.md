# Remix.run Snippets

Set of snippets for a faster [Remix](https://remix.run/) development.

## Features

![remix snippet default function example](https://raw.githubusercontent.com/amimaro/remix-run-snippets/main/remix-default-function.gif)

Get access to the set of snippets by typing `remix` prefix to start developing.

Simple as that. :D

Also feel free to open an issue for any feature request, bugs, etc.

Currently, this package has support for the following snippets:

- Default Function

```
export default function App() {
  return (
    <div></div>
  );
}
```

- Loader Function

```
export const loader: LoaderFunction = async () => {
  return {}
};
```

- Action Function

```
export const action: ActionFunction = async () => {
};
```

- Headers

```
export function headers({ loaderHeaders, parentHeaders }) {
  return {
    "": ""
  };
};
```

- Meta

```
export const meta: MetaFunction = () => {
  return {
    title: "",
    description: ""
  };
};
```

- Links

```
export const links: LinksFunction = () => {
  return [
    { rel: "", href: "" }
  ];
};
```

- CatchBoundary

```
export function CatchBoundary() {
 const caught = useCatch();
  return (
    <div>
      <h1>Caught</h1>
      <p>Status: {caught.status}</p>
      <pre>
        <code>{JSON.stringify(caught.data, null, 2)}</code>
      </pre>
    </div>
  );
}
```

- ErrorBoundary

```
export function ErrorBoundary({ error }: { error: Error }) {
  return (
    <div>
      <h1>Error</h1>
      <p>{error.message}</p>
      <p>The stack trace is:</p>
      <pre>{error.stack}</pre>
    </div>
  );
}
```

- Handle

```
export const handle = {
};
```

## Release Notes

### 1.0.0

Initial release of `remix-run-snippets` with the following snippets for `.js`, `.jsx`, `.ts` and `.tsx` file extensions:

- Default Function
- Loader Function
- Action Function
- Headers
- Meta
- Links
- CatchBoundary
- ErrorBoundary
- Handle

### 1.0.1

Just fixed the README.md gif path.

### 1.0.2

Added extension icon.

### 1.0.3

Update README and added more tags.

### 1.0.4

Fix typescript links snippet

---

**Enjoy!**
