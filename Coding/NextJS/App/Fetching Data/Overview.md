1.  [Fetch data on the server](https://nextjs.org/docs/app/building-your-application/data-fetching#fetching-data-on-the-server) using Server Components.
2.  [Fetch data in parallel](https://nextjs.org/docs/app/building-your-application/data-fetching#parallel-and-sequential-data-fetching) to minimize waterfalls and reduce loading times.
3.  For Layouts and Pages, [fetch data where it's used](https://nextjs.org/docs/app/building-your-application/data-fetching#automatic-fetch-request-deduping). Next.js will automatically dedupe requests in a tree.
4.  Use [Loading UI, Streaming and Suspense](https://nextjs.org/docs/app/building-your-application/data-fetching#streaming-and-suspense) to progressively render a page and show a result to the user while the rest of the content loads.

## Fetching Data on the Server
Whenever possible, we recommend fetching data in [Server Components](https://nextjs.org/docs/getting-started/react-essentials#server-components). Server Components **always fetch data on the server**.

## Fetching Data at the Component Level
In the App Router, you can fetch data inside [layouts](https://nextjs.org/docs/app/building-your-application/routing/pages-and-layouts#layouts), [pages](https://nextjs.org/docs/app/building-your-application/routing/pages-and-layouts#pages), and components. Data fetching is also compatible with [Streaming and Suspense](https://nextjs.org/docs/app/building-your-application/data-fetching#streaming-and-suspense).

