The default value of the `position` property is `static`.

## relative positioning
Applying `position: relative;` does two things:
1. Constrains certain children
2. Enables addition css properties, including `top,left,bottom,right`. Those values are _relative to its natural position.

The browser acts like the element is still in its original position. The displacement is purely cosmetic.

## absolute positioning
Applying `position: absolute;`
1. Makes the element incorporeal, i.e. the browser acts as if the element isn't there.
2. `top,left,bottom,right` are *relative to its containing block*.
3. By default, i.e. no `top,left,bottom,right` specified, the element will stay in its default *in flow* position. Although other elements will act as if the *absolutely positioned* element does not exist.

*Centering trick*: 
1. absolute positioning (`position: absolute`)
2. Equal distances from each edge (ideally `0px`), `inset: 0;`
3. A fixed size (defined `width` and `height` properties)
4. Hungry margins (`margin: auto`)

## fixed positioning
It is positioned relative to the initial [containing block](https://developer.mozilla.org/en-US/docs/Web/CSS/Containing_block) established by the [viewport](https://developer.mozilla.org/en-US/docs/Glossary/Viewport), except when one of its ancestors has a `transform`, `perspective`, or `filter` property set to something other than `none`, or the [`will-change`](https://developer.mozilla.org/en-US/docs/Web/CSS/will-change) property is set to `transform`, in which case that ancestor behaves as the containing block.

In many ways, “fixed” can be thought of as _spicy absolute_. It's very similar in principle — it's taken out-of-flow and positioned according to some sort of parent boundary — but the boundary it uses is different. Instead of the closest non-static ancestor, it listens to the _“initial containing block”_, a box the size and position of the viewport.

If we don't set an anchor point(no top/right etc), **they sit in their in-flow position**. Though fixed positioning still works! When we scroll the RESULT pane, the box stays locked in place.

## Notes
1. When we say `top:50px` we are measuring the distance between the top of the element and the top of the containing block. Likewise for the other sides. e.g. `right:50px` measures the distance between the right of the element and the right of the containing block.
2. *Absolute elements* ignore padding of the containing block; *static elements* respect padding of the containing block;
3. Use this to find out the *containg block* of a *fixed element*
```js
// Replace “.the-fixed-child” for a CSS selector
// that matches the fixed-position element:
const selector = '.the-fixed-child';

function findCulprits(elem) {
if (!elem) {
throw new Error(
'Could not find element with that selector'
);
}

let parent = elem.parentElement;

while (parent) {
	const {
		transform,
		willChange,
		filter,
	} = getComputedStyle(parent);

	if (
		transform !== 'none' ||
		willChange === 'transform' ||
		filter !== 'none'
	) {
		console.warn(
		'🚨 Found a culprit! 🚨\n',
			parent,
	{ transform, willChange, filter }
);
}

	parent = parent.parentElement;
}
}

findCulprits(document.querySelector(selector));
```

