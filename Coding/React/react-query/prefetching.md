

# Ways of Prefetching
## Saved to Cache
- `queryClient.prefetchQuery([key], queryFn)` The syntax is exactly the same as `useQuery([key], queryFn)`. The main difference is this is not a hook.
- `queryClient.setQueryData([key], data)` This is used when you already have the data. `data` can also be a synchronous function that returns some value
- `useQuery([key], queryFn, {initialData:data})` `data` can also be a synchronous function that returns some value 
## Not saved to Cached
- `useQuery([key], queryFn, {placeholderData:data})` `data` can also be a synchronous function that returns some value 
- The only difference is that `placeholderData` do *Not* get persisted to cache.

## Example
```js
const qc = useQueryClient();

useEffect(()=>{
	qc.prefetchQuery(['posts',page+1], ()=>fetchPosts(page+1))
},[qc,page])
```
All this does is whenever *page* changes, fetch the data for the next page.