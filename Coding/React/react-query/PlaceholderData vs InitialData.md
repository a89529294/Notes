`initialData` works on the *cache* level; `placeholderData` works on the *observer* level.

`initialData` is REAL, it gets persisted to the cache. While `placeholderData` is FAKE. This means when we provide `placeholderData` a background *fetch* will always happen; otoh, if we have `initialData` a background `fetch` will only happen if the data is *stale*.

## Cache
- For each Query Key, there is only one cache entry.

## Observer
- An *observer* in React Query is, broadly speaking, a *subscription* created for one cache entry.
- The basic way to create an observer is to call _useQuery_.
- We can have *multiple* *observers* watching the *same cache entry*.