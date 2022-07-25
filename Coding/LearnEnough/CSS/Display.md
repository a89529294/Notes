## display: inline;
- only `mx` and `px` are accepted
- `height` and `width` has no effect
- Technically `py` works but it won't affect other elements. You can see the effect by applying a `background-color` to the element.

## display:block;
- `float: <value>` any value other than `none` causes the element to become `display:block;`
- `margin` collapses only between *vertical margins* of *block* elements.

## display:inline-block;
- acts like *inline* to the outside world, but to the element itself it is a *block* element, i.e. you can use *width*, *height*, etc on it.

### Misc.
- You can position *inline-block*, and *inline* elements with `text-align` property.
