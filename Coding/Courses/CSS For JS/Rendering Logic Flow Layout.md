- `currentColor` is always a reference to the element's derived text color (whether set explicitly or inherited), and it can be used anywhere a color might be used
- `border` vs `outline` The core difference is that _outline doesn't affect layout_. 
	- Outlines are stacked outside border. 
	- Outlines will follow the curve set with `border-radius`
	- Outlines have a special `outline-offset` property. It allows you to add a bit of a gap between the element and its outline.
- `margin-left:auto; margin-right:auto;` can be used to *horizontally cetner* an element as long as the element has an explicit width.
- *Replaced elements* like `<img/>`,`<video/>`,`<canvas/>` are *inline* elements that can be affected by `width, height, margin-block`. Think of them as *foreign objects within an inline wrapper*.

## Flow Layout
- `inline` elements are not affected by `width,height, margin-block`. `margin-inline` has an effect since its in the inline direction.
- `block` elements always start and occupy a new line. You can resize the `block` element but no other element will naturally occupy the same line.
- An `inline-block` element is a block-level element that can be placed in an inline context. From the outside it acts like an *inline* element, From the inside it acts like a *block* element. One thing to note is it *cannot line wrap*, unless it cannot be avoided.

## Width Algorithm
- When we use percentage-based widths, those percentages are **based on the parent element's content space**.
- `Block` elements have a default `width` of `auto` NOT `100%`. it will take up as much width as possible while respecting constraints like margin. For instance, if a parent element has *available width of 300px* and the child has a *margin-inline of 10px* it will take up `280x` of width with `width:auto` but it will take up `300px` of width with `width:100%`.
- `width: min-content`: we want our element to become as narrow as it can, _based on the child contents_.
- `width: max-content`: The element's width will be the smallest value that contains the content, without breaking it up. It _never_ adds any line-breaks.
- `width: fit-content`: If that width can fit within the parent container, it behaves just like `max-content`, not adding any line-breaks. If the content is too wide to fit in the parent, however, it adds line-breaks as-needed.
- *min-content*,*max-content*, *fit-content* are *intrinsic* units since it depends on the element itself. In contrast *auto* is based on the parent.

## Height Algorithm
How to make sure a wrapper is at last as tall as the view port.
```css
html, body {
  height: 100%;
}
.wrapper {
  min-height: 100%;
}
```
1. Note you need to put `height: 100%;` on every element above the wrapper.
2. You *cannot use % based height* in the wrapper.

By default(i.e. when we don't set width/height), width looks _up_ the tree, while height looks _down_ the tree. An element's width is calculated based on its _parent's size_, but an element's _height_ is calculated based on its _children_.