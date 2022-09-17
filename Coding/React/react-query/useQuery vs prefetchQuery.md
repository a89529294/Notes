- The syntax are the same `useQuery([key],fetcher)` & `prefetchQuery([key],fetcher)`
- One is declarative *useQuery*; the other is imperative *prefetchQuery*
- `useQuery` returns an obj with a lot of keys *isLoading*, *data*, etc. `prefetchQuery` only returns a *Promise* object that resolves to *void*. Its only purpose it to load data into cache.