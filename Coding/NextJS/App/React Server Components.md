*Server Components are the default*, all components are part of the Server Component module graph *unless defined or imported in a module* that starts with the `"use client"` directive.

## when to use client components
1. Adding interactivity (`onClick, onChange`)
2. Use state and lifecycle effects( `useState`, `useReducer`, `useEffect`)
3. Use browser only api
4. custom hooks using state and lifecycle effects or browser only api

## patterns
1. Moving client components to the leaves.
2. Pass a Server Component as a child or prop of a Client Component
```js
// app/ChildComponent.js
'use client';
 
export default function ClientComponent({ children }) {
  return <>{children}</>;
}

// app/page.js
import ClientComponent from './ClientComponent';
import ServerComponent from './ServerComponent';
 
// Pages are Server Components by default
export default function Page() {
  return (
    <ClientComponent>
      <ServerComponent />
    </ClientComponent>
  );
}
```
3. use `server-only` and `client-only` packages
```js
// lib/data.js
import 'server-only';
 
export async function getData() {
  let resp = await fetch('https://external-service.com/data', {
    headers: {
      authorization: process.env.API_KEY,
    },
  });
 
  return resp.json();
}
```
Above code is only intended to be run on the server because `process.env.API_KEY` will be an empty string on the client side. with the `import 'server-only'` line now `npm run build` will fail if `getData` is used in a *client component*.
4. Using 3rd party packages
Many components from npm packages that use client-only features do not yet have the directive `use-client`. You need to put in in a file with `use-client` at top then re-export it.
```js
// app/carousel.js
'use client';
 
import { AcmeCarousel } from 'acme-carousel';
 
export default AcmeCarousel;
```
5. Using contexts
Since *context* uses `createContext` which is not supported in *server components*, you need to move it into a seperate file marked with `use client`
```js
// app/theme-provider.jsx
'use client';
 
import { createContext } from 'react';
 
export const ThemeContext = createContext({});
 
export default function ThemeProvider({ children }) {
  return <ThemeContext.Provider value="dark">{children}</ThemeContext.Provider>;
}

// app/layout.jsx
import ThemeProvider from './theme-provider';
 
export default function RootLayout({ children }) {
  return (
    <html>
      <body>
        <ThemeProvider>{children}</ThemeProvider>
      </body>
    </html>
  );
}
```
With the provider rendered at the root, all other *Client Components* throughout your app will be able to consume this context.
6. Sharing data between server components
Since *Server Components are not interactive* and therefore do not read from React state, you don't need the full power of context to share data. You can use native JavaScript patterns like *global singletons within module scope* if you have common data that multiple Server Component need to access.
```js
// utils/database.js
export const db = new DatabaseConnection(...);

// app/users/layout.js
import { db } from "@utils/database";
 
export async function UsersLayout() {
  let users = await db.query(...);
  // ...
}

// app/users/[id]/page.js
import { db } from "@utils/database";
 
export async function DashboardPage() {
  let user = await db.query(...);
  // ...
}
```
