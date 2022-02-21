# Remix.run Snippets

Set of snippets for a faster [Remix](https://remix.run/) development.

## Features

![remix snippet default function example](https://raw.githubusercontent.com/amimaro/remix-run-snippets/main/remix-fast-track.gif)

Get access to the set of snippets by typing `remix` prefix to start developing.

Simple as that. :D

Also feel free to open an issue for any feature request, bugs, etc.

[Check out the Remix Docs for more information.](https://remix.run/docs/en/v1)

### Snippets

Currently, this package has support for the following snippets:

- `remix-default-function`

```
export default function App() {
  return (
    <div></div>
  );
}
```

- `remix-loader`

```
export const loader: LoaderFunction = async () => {
  return {}
};
```

- `remix-loader-session`

```
export const loader: LoaderFunction = async ({ request }) => {
  const session = await getSession(request.headers.get("Cookie"));
  return json({}, {
    headers: {
      "Set-Cookie": await commitSession(session),
    },
  });
};
```

- `remix-loader-params`

```
export const loader: LoaderFunction = async ({ request }) => {
  const url = new URL(request.url);
  const term = url.searchParams.get("term")
  return {}
};
```

- `remix-action`

```
export const action: ActionFunction = async ({ request }) => {
  const formData = await request.formData();
  redirect('');
};
```

- `remix-headers`

```
export const headers = ({ loaderHeaders, parentHeaders }) => {
  return {
    "": ""
  };
};
```

- `remix-meta`

```
export const meta: MetaFunction = () => {
  return {
    title: "",
    description: ""
  };
};
```

- `remix-links`

```
export const links: LinksFunction = () => {
  return [
    { rel: "", href: "" }
  ];
};
```

- `remix-catch-boundary`

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

- `remix-error-boundary`

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

- `remix-handle`

```
export const handle = {
};
```

- `remix-session`

```
import { createCookieSessionStorage } from "remix";

const sessionSecret = process.env.SESSION_SECRET;
if (!sessionSecret) {
  throw new Error("SESSION_SECRET must be set");
}

const { getSession, commitSession, destroySession } =
  createCookieSessionStorage({
    // a Cookie from `createCookie` or the CookieOptions to create one
    cookie: {
      name: "__session",

      // all of these are optional
      domain: "remix.run",
      expires: new Date(Date.now() + 60),
      httpOnly: true,
      maxAge: 60,
      path: "/",
      sameSite: "lax",
      secrets: [sessionSecret],
      secure: true
    }
  });
export { getSession, commitSession, destroySession }
```

- `remix-a-link`

```
<Link prefetch="none,intent,render" to={``}></Link>
```

- `remix-a-link-pending`

```
function PendingLink({ to, children }: { to: string; children: any }) {
  const transition = useTransition();
  const path = useResolvedPath(to);

  const isPending =
    transition.state === "loading" &&
    transition.location.pathname === path.pathname;

  return (
    <Link
      data-pending={isPending ? "true" : null}
      to={to}
      children={children}
    />
  );
}
```

- `remix-btn-transition`

```
function SubmitButton() {
  const transition = useTransition();

  const text =
    transition.state === "submitting"
      ? "Saving..."
      : transition.state === "loading"
      ? "Saved!"
      : "Go";

  return <button type="submit">{text}</button>;
}
```

- `remix-btn-transition-action`

```
function SubmitButton() {
  const transition = useTransition();

  const loadTexts: any = {
    actionRedirect: "Data saved, redirecting...",
    actionReload: "Data saved, reloading fresh data..."
  };

  const text =
    transition.state === "submitting"
      ? "Saving..."
      : transition.state === "loading"
      ? loadTexts[transition.type] || "Loading..."
      : "Go";

  return <button type="submit"></button>;
}
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

### 1.0.5

Update example gif.

### 1.0.6

Updated `remix-action`.

Added new snippets:

- `remix-loader-session`
- `remix-loader-params`
- `remix-session`
- `remix-a-link`
- `remix-a-link-pending`
- `remix-btn-transition`
- `remix-btn-transition-action`

### 1.0.7

Update `remix-headers` to be a const function like the others. ([#1](https://github.com/amimaro/remix-run-snippets/issues/1))

---

**Enjoy!**
