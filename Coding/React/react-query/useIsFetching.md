```js
const {useIsFetching} from 'react-query'

function Loading(){
	const fetching = useIsFetching()
	return fetching ? <Spinner/> : null
}
```

`useIsFetching` returns a number representing the number of queries currently being fetched.
