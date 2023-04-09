## translate
```css
.sth {
    /* move to the right by 5px, down by 100% of element's
	   own height 
    */ 
	transform: translate(5px, 100%); 
}
```
- Critically, _the item's in-flow position doesn't change_. As far as our layout algorithms are concerned, from Flow to Flexbox to Grid, this property has no effect. i.e. other elements don't react to it.
- *percentages* refer to the elements own size.

## scale
```css
.sth {
	transform: scale(2, 3);
}
```
- `scale` will stretch/squash the element's contents
- if we _don't_ want our text to squash/stretch, we can apply an _inverse transform_ to the child.

## skew
```css
.sth {
	transform: skew(ax);
	transform: skew(ax, ay);

	transform: skewX(ax);
	transform: skewY(ay);
}
```

## transform origin
Every element has an _origin_, the anchor that the transform functions execute from.

## multiple transform values
```css
.sth {
	transform: rotate(80deg) translate(100px);
}
```
- applied from right to left
- *transform origin* does not move with the translate functions!

## misc
- This reveals an important truth about transforms: **elements are flattened into a texture**. All of these transforms essentially treat our element like a flat image, warping and contorting it as you might in Photoshop.
- `transforms` *don't work with inline elements in Flow layout*. 