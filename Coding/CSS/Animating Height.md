```css
.ele {
	max-height:0;
	overflow:hidden;
	transition:all 0.5;		
}

.ele:hover {
	max-height:9999px; //set a number that is guaranteed to be taller than
	                   //actual height
}
```
The reason we are using `max-height` instead of `height` is to animate *height* we need to give specific values, we cannot use keywords like `auto`. But we might not know *height* beforehand so we animate *max-height* instead. 