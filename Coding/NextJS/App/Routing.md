## route groups
The hierarchy of the `app` folder maps directly to URL paths. However, it’s possible to break out of this pattern by creating a **route group**. *A route group can be created* by wrapping a folder’s name in parenthesis: `(folderName)`

Three main uses of a *route group*:
1. Organize routes without affecting the URL structure.
2. Opting-in specific route segments into a [layout](https://nextjs.org/docs/app/building-your-application/routing/pages-and-layouts).
3. Create multiple [root layouts](https://nextjs.org/docs/app/building-your-application/routing/pages-and-layouts#root-layout) by splitting your application.

For detailed uses check [route group](https://nextjs.org/docs/app/building-your-application/routing/route-groups)

## dynamic routes
When you don't know the exact segment names ahead of time and want to *create routes from dynamic data*, you can use **Dynamic Segments** that are filled in at request time or [prerendered](https://nextjs.org/docs/app/building-your-application/routing/dynamic-routes#generating-static-params) at build time.

A Dynamic Segment can be created by wrapping a folder's name in square brackets: `[folderName]`.

Dynamic Segments are passed as the `params` prop to [`layout`](https://nextjs.org/docs/app/api-reference/file-conventions/layout), [`page`](https://nextjs.org/docs/app/api-reference/file-conventions/page), [`route`](https://nextjs.org/docs/app/building-your-application/routing/router-handlers), and [`generateMetadata`](https://nextjs.org/docs/app/api-reference/file-conventions/metadata#generatemetadata) functions.

Sometimes you want to *statically generate routes* at build time, use the `generateStaticParams` function in combination with [dynamic route segments](https://nextjs.org/docs/app/building-your-application/routing/defining-routes#dynamic-segments).
```js
// app/blog/[slug]/page.tsx
export async function generateStaticParams() {
  const posts = await fetch('https://.../posts').then((res) => res.json());
 
  return posts.map((post) => ({
    slug: post.slug,
  }));
}
```

Dynamic Segments can be extended to **catch-all** subsequent segments by adding an ellipsis inside the brackets `[...folderName]`.
For example, `app/shop/[...slug]/page.js` will match `/shop/clothes`, but also `/shop/clothes/tops`, `/shop/clothes/tops/t-shirts`, and so on.
*Catch-all Segments* can be made **optional** by including the parameter in double square brackets: `[[...folderName]]`. The only difference with the one above is `app/shop/[[...slug]]/page.js` also matches `/shop`, in addition to the above routes.

Using *typescript* to type params:
- `app/blog/[slug]/page.js` - `{ slug: string }`
- `app/shop/[...slug]/page.js` - `{ slug: string[] }`
- `app/[categoryId]/[itemId]/page.js` - `{ categoryId: string, itemId: string }`

## loading ui and streaming
In the same folder, `loading.js` will be nested inside `layout.js`. It will automatically wrap the `page.js` file and any children below in a `<Suspense>` boundary.

You can also *manually create Suspense Boundaries* for your own UI components.
```tsx
// app/dashboard/page.tsx
import { Suspense } from 'react';
import { PostFeed, Weather } from './Components';
 
export default function Posts() {
  return (
    <section>
      <Suspense fallback={<p>Loading feed...</p>}>
        <PostFeed />
      </Suspense>
      <Suspense fallback={<p>Loading weather...</p>}>
        <Weather />
      </Suspense>
    </section>
  );
}
```

## error handling
To handle errors *within a specific layout* or template, place an `error.js` file in the layouts *parent segment*.
To handle errors *within the root layout* or template, use a variation of `error.js` called `global-error.js`. 
Unlike the root `error.js`, the `global-error.js` error boundary wraps the **entire** application, and its fallback component replaces the root layout when active. Because of this, it is important to note that `global-error.js` **must** define its own `<html>` and `<body>` tags.
Even if a `global-error.js` is defined, it is still recommended to define a root `error.js` whose fallback component will be rendered **within** the root layout, which includes globally shared UI and branding.
```tsx
// app/global-error.tsx
'use client';
 
export default function GlobalError({
  error,
  reset,
}: {
  error: Error;
  reset: () => void;
}) {
  return (
    <html>
      <body>
        <h2>Something went wrong!</h2>
        <button onClick={() => reset()}>Try again</button>
      </body>
    </html>
  );
}
```

## parallel routes
Basically *slots*. Parallel routes are created using named **slots**. Slots are defined with the `@folder` convention, and are passed to the same-level layout as props.
> Slots are _not_ route segments and _do not affect the URL structure_. The file path `/@team/members` would be accessible at `/members`.

Assuming you have `app/@dashboard/page.tsx` and `app/@login/page.tsx`
```tsx
// app/layout.tsx
import { getUser } from '@/lib/auth';
 
export default function Layout({ params, dashboard, login }) {
  const isLoggedIn = getUser();
  return isLoggedIn ? dashboard : login;
}
```

## intercepting routes
*Intercepting routes* allows you to load a route within the current layout while keeping the context for the current page. This routing paradigm can be useful when you want to "intercept" a certain route to show a different route.
[modal example](https://github.com/vercel-labs/nextgram)

## route handlers
You can consider a `route` the lowest level routing primitive.
- They **do not** participate in layouts or client-side navigations like `page`.
- There **cannot** be a `route.js` file at the same route as `page.js`.

Route Handlers are _statically evaluated_ by default when using the `GET` method with the `Response` object.
Route handlers are *evaluated dynamically* when:
-   Using the `Request` object with the `GET` method.
-   Using any of the other HTTP methods.
-   Using [Dynamic Functions](https://nextjs.org/docs/app/building-your-application/routing/router-handlers#dynamic-functions) like `cookies` and `headers`.
-   The [Segment Config Options](https://nextjs.org/docs/app/building-your-application/routing/router-handlers#segment-config-options) manually specifies dynamic mode.
