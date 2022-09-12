- `useIsFetching()` can be used to enable app wide loading
- default `onError` can be used to enable app wide error handling. For example you can invoke a `toast` inside the `errorHandler`
```js
const queryClient = new QueryClient({
		defaultOptions: {
				queries:{
					onError:errorHandler
				},
			}
	})
```