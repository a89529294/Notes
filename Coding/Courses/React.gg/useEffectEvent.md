A way to extract _reactive_ but not _synchronizing_ values out of the dependency array of _useEffect_.

```js
const onURLChange = React.useEffectEvent((url)=>{
	previewURL(url, state)
})

React.useEffect(()=>{
	onURLChange(url)
},[url])
```
Here `url` is a _synchronizing_ value and _state_ is a reactive value. We want to notify the outside world every time _url_ changes but not when _state_ changes.
_useEffect_ is used to synchronize our component with some outside system.