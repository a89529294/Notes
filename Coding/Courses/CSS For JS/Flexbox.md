- There are two important sizes when dealing with Flexbox: the _minimum content size_, and the _hypothetical size_.
- The minimum content size is the smallest an item can get without its contents overflowing.
- Setting `width` in a flex row (or `height` in a flex column) sets the _hypothetical_ size. It isn't a guarantee, it's a suggestion.
- `flex-basis` has the same effect as `width` in a flex row (`height` in a column). You can use them interchangeably, but `flex-basis` will *win* if there's a conflict.
- There is one more difference between `width` and `flex-basis`: `flex-basis` can't scale an element below its minimum content size, but `width` can.
- `flex-grow` will allow a child to consume any excess space in the container. It has no effect if there *isn't* any excess space.
- `flex-shrink` will pick which item to consume space from, if the container is too small. It has no effect if there _is_ any excess space. One way of making the container to small is to set children's *hypothetical sizes* to be bigger than the container. 
- `flex-shrink` can't shrink an item below its minimum content size. You can change this by setting `min-width: 0;`.

## flex shorthand
```css
flex: 1 1 0;
/* same as */
flex-grow: 1;
flex-shrink: 1;
flex-basis: 0;
```
- `flex: 2;` is the same as `flex: 2 1 0`;

## align-content
- *Only* applies when there are *multiple lines*, this can be enabled by setting `flex-wrap: wrap;`.
- `align-content` applies to how the *lines* place themselves in the cross axis direction. `align-items` applies to the *items* place themselves within each line in the cross axis direction.

## Notes
1. *flex-grow* only cares about how much *extra space* and the *values of flex-grow* on each child. Say we have `100px` of extra space, and child A has `flex-grow: 2;` child B has `flex-grow: 1;` child A gets `66.6px` and child B get `33.4px` no matter the hypothetical size of each child.
2. *flex-shrink* cares about *deficit space* and *values of flex-srhink* and *hypothetical sizes* of each child. Say we have `100px` of deficit space, child A has `flex-shrink: 1` hypothetical size of `100px`, child B has `flex-shrink: 1` hypothetical size of `200px`. Child A will get a reduction of `33.4px` and child B will get a reduction of `66.6px`. It will try to preserve the *proportions between siblings*.
3. 
	1. `flex-grow` controls how the _extra space is distributed_ when the items are smaller than their container.
	2. `flex-shrink` controls how _space is removed_ when the items are bigger than their container.
	3. **only _one_ of these properties can be active at once.**
4. In addition to the _hypothetical_ size, there's another important size that the Flexbox algorithm cares about: _the minimum size_. The Flexbox algorithm refuses to shrink a child below its minimum size. The content will overflow rather than shrink further. We can override this by setting `min-width: 0;`. 
5. When we set `flex-wrap: wrap`, **items won't shrink below their hypothetical size**.
6. When there is a conflict between layout modes, **positioned layout always wins.**
7. _Margin collapse is exclusive to Flow layout._ It doesn't happen when elements are laid out inside a flexbox parent.
8. CSS is comprised of layout modes, and each layout mode decides what each property should do. *Positioned*, *Flexbox*, and *Grid* all implement *support for z-index*. Flow layout does not.
9. 