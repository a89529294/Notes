- `position: absolute` sometimes behaves unexpectedly when the parent has `overflow:scroll` and the content overflows. To deal with this wrap the *absolutely positioned* element it a *relative* wrapper.
```html
	<div style='height:100px; overflow:scroll; position:relative'>
		<div style='
		position:absolute; top:0; left:0; bottom:0; 
		width:50px; background:red'
		></div>
		lorem * 100
	</div>
```
In the above snippet the *absolute* element will not extend across the total height of its container, in order to fix this wrap it in a *relative* wrapper
```html
	<div style='height:100px; overflow:scroll; position:relative'>
		<div style='position:relative'>
			<div style='
		position:absolute; top:0; left:0; bottom:0; 
		width:50px; background:red'
		></div>
		lorem * 100
		</div>
		
	</div>
```