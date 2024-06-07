## Hydration
The process of turning the initial static HTML file into an interactive web application is called _hydration._

## RSC
- _React Server Components_ is about "pre-rendering" components so that the component itself isn't included in the JS bundle
- _Server-Side Rendering_ is about generating HTML that will be served to the user while the app is hydrating.

In short, RSC hands the browser the _produced react element_ instead of the component function that is used to produce the react element.

