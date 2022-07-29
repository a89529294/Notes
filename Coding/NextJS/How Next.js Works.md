### What NextJs takes care of

- ***Compiling*** refers to the process of taking code in *one language* and **outputting** it in *another language* or another version of that language.
- ***Minification*** is the process of *removing* unnecessary code formatting and comments without changing the code’s functionality. 
- ***Bundling*** is the process of resolving the web of dependencies and merging (or ‘packaging’) the files (or modules) into *optimized bundles* for the browser, with the goal of reducing the number of requests for files when a user visits a web page.
- ***Code-splitting*** is the process of *splitting* the application’s bundle into *smaller chunks* required by each *entry point*. The goal is to improve the application's initial load time by only loading the code required to run that page.
	- Next.js has built-in support for code splitting. Each file inside your `pages/` directory will be automatically code split into its own JavaScript bundle during the *build step*.
	- After the initial page load, Next.js can start [pre-loading the code](https://nextjs.org/docs/api-reference/next/link#:~:text=Defaults%20to%20false-,prefetch,-%2D%20Prefetch%20the%20page) of other pages users are likely to navigate to.

### Three Types of Rendering
There is an unavoidable unit of work to convert the code you write in React into the HTML representation of your UI. This process is called **rendering**.

#### Server-Side Rendering, Static Site Generation, and Client-Side Rendering
- *SSR* and *SSG* are also referred to as **Pre-Rendering** because the fetching of external data and transformation of React components into HTML happens before the result is sent to the client.

#### SSR
- With server-side rendering, the HTML of the page is generated on a server for **each** request. The generated *HTML*, *JSON data*, and *JavaScript* instructions to make the page interactive are then sent to the client.
- On the client, the *HTML* is used to show a fast non-interactive page, while React uses the *JSON data* and *JavaScript* instructions to make components interactive (for example, attaching event handlers to a button). This process is called **hydration**.
- In Next.js, you can opt to server-side render pages by using [getServerSideProps](https://nextjs.org/docs/basic-features/data-fetching/get-server-side-props).

#### SSG
- the *HTML* is generated on the server, but unlike server-side rendering, there is no server at runtime. Instead, content is generated once, at build time, when the application is deployed, and the *HTML* is stored in a [CDN](https://nextjs.org/learn/foundations/how-nextjs-works/cdns-and-edge) and re-used for each request.
- In Next.js, you can opt to statically generate pages by using [getStaticProps](https://nextjs.org/docs/basic-features/data-fetching/get-static-props).
- You can use [Incremental Static Regeneration](https://nextjs.org/docs/basic-features/data-fetching/incremental-static-regeneration) to create or update static pages _after_ you’ve built your site. However this depends on hosting providers.

### Where can a NextJS app be deployed?
Your application code can be distributed to **origin servers**, **Content Delivery Networks (CDNs)**, and **the Edge**.
- **Origin server** refers to the main computer that stores and runs the original version of your application code.
- **CDN** store static content (such as HTML and image files) in multiple locations around the world and are placed between the client and the origin server.
- **Edge** servers are distributed to multiple locations around the world similar to CDNs. But unlike CDNs, which store static content, some *Edge servers can run code*. [See examples with Next.js here](https://vercel.com/features/edge-functions#:~:text=or%20steps%20required.-,CODE%20EXAMPLES,-Unlock%20the%20potential)


