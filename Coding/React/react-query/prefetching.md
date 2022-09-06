```js
const qc = useQueryClient();

useEffect(()=>{
	qc.prefetch(['posts',page+1], ()=>fetchPosts(page+1))
},[qc,page])
```
All this does is whenever *page* changes, fetch the data for the next page.