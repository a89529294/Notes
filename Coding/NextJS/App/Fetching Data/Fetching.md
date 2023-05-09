## async/await in Server Components
```tsx
// app/page.tsx
async function getData() {
  const res = await fetch('https://api.example.com/...');
  // The return value is *not* serialized
  // You can return Date, Map, Set, etc.
 
  // Recommendation: handle errors
  if (!res.ok) {
    // This will activate the closest `error.js` Error Boundary
    throw new Error('Failed to fetch data');
  }
 
  return res.json();
}
 
export default async function Page() {
  const data = await getData();
 
  return <main></main>;
}
```

**Async Server Component TypeScript Error**
- An `async` Server Components will cause a `'Promise<Element>' is not a valid JSX element` type error where it is used.
- This is a known issue with TypeScript and is being worked on upstream.
- As a temporary workaround, you can add `{/* @ts-expect-error Async Server Component */}` above the component to disable type checking for it.

## Client Components
Use `tanstack-query` for now.

## fetch
```js
fetch('https://...', { cache: 'force-cache' }); // default
fetch('https://...', { next: { revalidate: 10 } });
fetch('https://...', { cache: 'no-store' });
```

