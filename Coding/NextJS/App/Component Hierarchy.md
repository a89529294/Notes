The React components defined in special files of a route segment are rendered in a specific hierarchy:
-   `layout.js`
-   `template.js`
-   `error.js` (React error boundary)
-   `loading.js` (React suspense boundary)
-   `not-found.js` (React error boundary)
-   `page.js` or nested `layout.js`

## layout
- The top-most layout is called the [Root Layout](https://nextjs.org/docs/app/building-your-application/routing/pages-and-layouts#root-layout-required). This **required** layout is shared across all pages in an application. Root layouts must contain `html` and `body` tags.
- You can use [Route Groups](https://nextjs.org/docs/app/building-your-application/routing/defining-routes#route-groups) to opt specific route segments in and out of shared layouts.