- The full short hand syntax takes 8 values; first four are the *horizontal radii* starting from *top left*, then *vertical radii*.
- If using *percentages*, the *horizontal radii* are based on *width* of the element; *vertical radii* are based on *height* of the element.
- This is why setting `border-radius: 50%` on a *square element* results in a *circle*.
- Generally speaking setting `border-radius: 50%` on an element results in  an ellipse the same size as the element.
```css
/* These three are equivalent */
.x {
	border-radius: 100px;
	border-radius: 100px 100px 100px 100px;
	border-radius: 100px 100px 100px 100px /
				   100px 100px 100px 100px;	
}
```
![[border-radius.svg]]
- The above diagram shows what happens when you set `border-radius: 32px;`
- If you have *nested radii* like wrapper and content both having `border-radius`, make sure the wrapper has a bigger `border-radius`. For example if the content has `16px` border radius, and the wrapper has a `8px` padding, simply set `border-radius: 24px` on the wrapper. 

## circular radius
- If you want *circular radius* and the element has *fixed width/height*, just set `border-radius` to *half of the smaller side*.
- If you want *circular radius* but the element has *dynamic width/height* just set an *extremely large px number*. e.g. `border-radius: 5000px;`
- What happens here is once the combined corner radii exceed either height or width, they become ratio numbers, i.e. if all border radius are `5000px` they will end up all the same maximum size, *half of the smaller side of width/height*.
- You can also do something like `border-radius: 5000px 5000px 1000px 1000px` on an element to produce a shape like a mountain. Remember, once the `border-radius` is given numbers bigger than *half the smaller side* they become *ratio numbers*.
