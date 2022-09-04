## staleTime
- Data *refecth* only triggers for *stale* queries
- *Stale* queries are refetched automatically in the background when
	- window refocus
	- new instances of the query mount
	- network reconnection
	- the query is configured with the `refetchInterval` option
- by default, `staleTime` is 0. Which means queries become *instantly stale* after fetch. You can change this by providing a `staleTime` option when using *useQuery()*
```js
const {data} = useQuery(['posts'],fetchPosts,
	{staleTime:1000 * 60 * 60})
```

## cacheTime
- refers to the time an *inactive query* can stay in the cache
- an *inactive query* is one where there is no active `useQuery`, `useInfiniteQuery` or *query observers*.
- in most cases that means no component that uses that query is mounted.
- by default, `cacheTime` is 1000 * 60 * 5

### Conclusion
- Usually there is no need to configure `cacheTime`. 
- A query will be *refetched* **automcatically** *iff* the query is *stale* and one of the following four conditions is met:
	- window refocus
	- new instances of the query mount, e.g. a component that uses that query remounts
	- network reconection
	- the query is configured with the `refetchInterval` option
- A query can be *refetched* **imperatively** if
	- manually triggering the refetch function
	- query invalidation after a mutation