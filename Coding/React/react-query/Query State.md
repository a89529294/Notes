- A *query* will be in **exactly one** of the following states
	- `success`
	- `loading`
	- `error`
- Queries *can* be in addtional states such as `isFetching`, `isPaused`, `isRefetching`

## status vs FetchStatus
There are three statuses, *loading*, *error*, *success*.
- `status === 'loading'` corresponds to *isLoading*, it means the query has **no data**.
- `status === 'error'` corresponds to *isError*, it means the query **encountered an error**.
- `status === 'success'` corresponds to *isSuccess*, it means **data is available**.

There are three fetchStatuses, *fetching*, *paused*, *idle*.
- `fetchStatus === 'fetching'`, the query is currently **running**.
- `fetchStatus === 'paused'`, the query wanted to run, but is **paused**.
- `fetchStatus === 'idle'`, the query is **not doing anything**.
