# Remix.run Snippets

Set of snippets for a faster [Remix](https://remix.run/) development.

## Features

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
import type { LoaderArgs } from "@remix-run/node"
export async function loader() {
  return {}
};
```

- `remix-loader-session`

```
import type { LoaderArgs } from "@remix-run/node"
export async function loader({ request }: LoaderArgs) {
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
import type { LoaderArgs } from "@remix-run/node"
export async function loader({ request }: LoaderArgs) {
  const url = new URL(request.url);
  const term = url.searchParams.get("term");
  return {}
};
```

- `remix-action`

```
import type { ActionArgs } from "@remix-run/node"
export async function action({ request }: ActionArgs) {
  const formData = await request.formData();
  return redirect();
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

---

**Enjoy!**
