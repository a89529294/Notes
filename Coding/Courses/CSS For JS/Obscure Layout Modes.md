## column
```css
.container{
	columns: 3;
}
```
- automatically split content across multiple columns, in a manner that allows the parent container to grow and shrink accordingly.
- If you wish to avoid breaking up children just add `break-inside:avoid;` to the child elements.
- https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Columns
	- can use it to make masory layouts.

## float
```css
.container {
	float: left;
}
```
- a floated element allows other content to flow around it.