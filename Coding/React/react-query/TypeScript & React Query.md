*Type* for the `useQuery` hook
```ts
export function useQuery<
	TQueryFnData = unknown,
	TError = unknown,
	TData = TQueryFnData,
	TQueryKey extends QueryKey = QueryKey
>
```
1. `TQueryFnData` type returned from the `queryFn`
2. `TError` type of Errors to expect from the _queryFn_
3. `TData` the type our _data_ property will eventually have. Only relevant if you use the _select_ option, because then the _data_ property can be different from what the _queryFn_ returns. Otherwise, it will default to whatever the _queryFn_ returns.
4. `TQueryKey` the type of our _queryKey_, only relevant if you use the _queryKey_ that is passed to your _queryFn_.

