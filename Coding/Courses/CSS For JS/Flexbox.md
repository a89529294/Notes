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