- When it comes to `grid-template-rows`, the following values are equivalent
	- `1fr 200px`
	- `minmax(auto, 1fr) 200px`
- In other words the first column cannot be smaller than its content size. To ensure the firs column only takes up `100% - 200px` of width use *minmax(0, 1fr)*.