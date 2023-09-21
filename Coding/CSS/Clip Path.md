- *clip-path* is a css property like *transform* that accepts many different keyword values. 
```css
	.ele {
		clip-path:circle(...);
		/* clip-path:polygon(...); */
		/*clip-path:path(...); */
	}
```
- `clip-path:polygon(50% 0%, 100% 50%, 50% 100%, 0% 50%)`, each pair refers to a point. The origin is at the top left of the element, `(0,0)`. `(50% 0%)` refers to 50% along the x-axis and 0% along the y-axis. For *x-axis*, right is positive. For *y-axis*, down is positive.
- You can *animate* clip-path, but you need to make sure the *number* of points are the *same*. If you want to animate between clip-paths with *different* number of point[]()s, you need to duplicate some points. Below animates from a diamond to a triangle.
```css
	.ele {
		clip-path:polygon(50% 0%,100% 50%,50% 100%,0% 50%);
		transition: clip-path 500ms;
	}
	.ele:hover {
		clip-path:polygon(0% 0%, 100% 50%, 100% 50%,0% 100%)
	}
```
- *Rounded* shapes can be achieved by using `clip-path:circle` or `clip-path:ellipse`, the syntax is `ellipse(xRadius yRadius at xPos yPos)`
```css
.ele{
	clip-path:ellipse(20px 30px at 50% 50%)
}
```

## Misc.
- *box-shadow* do not work well with *clip-path* since it adds the shadow to the rectangular shape not the clipped shaped.
- *drop-shadow* follows the clipped shaped but needs to be added the a parent container, not the actual clipped element. This is because *filter* happens first then the filter gets clipped.
