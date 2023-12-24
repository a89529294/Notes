By default all pages start out as _static_.

Here are four ways to turn a page _dynamic_:
1. Calling a dynamic function or referencing a dynamic variable when your route renders. 
```js
cookies().get()
cookies().delete()
headers()
useSearchParams()
searchParams prop
```
2. Assigning specific route segment config
```js
export const dynamic = 'force-dynamic'
export const revalidate = 0
```
3. Calling fetch and opting out of caching of the response
```js
fetch('...', {next: revalidate: 0})
```
4. Using a dynamic route
```js
/snippets/[id]/page.tsx
```

The best way is to run `npm run build` once in a while and checking the output.
