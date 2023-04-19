By default, the 3D engine in CSS will assume that we want to use **orthographic projection**. Everything will be the same size, no matter how far away it is.

We can switch to a **perspective projection** using the `perspective` CSS property.

`perspective` takes in a length value, e.g. `500px`. The value we pass to `perspective` can be thought of as a measure of how close the user is to the screen. The *smaller* the values is, the *closer* the user is to the screen, the *larger* the effect will appear to be.t

## Applying perspective
1. Using `perspective` property on the parent element. 
	- It's kind of like `display: grid`; we set `perspective` to control how the _children_ will be presented. 
	- The cool thing about the `perspective` property is that it _groups the children into the same environment_.
	- the box's position within the perspective-parent will control what angle we see it at.
```html
<style>
  .container {
    perspective: 250px;
  }
  .box {
    transform: rotateX(45deg);
  }
</style>

<div class="container">
  <div class="box"></div>
  <div class="box"></div>
  <div class="box"></div>
</div>
```
2. Using the *perspective* transform function. 
	- the `perspective()` function will give each transformed element its own little environment.
```css
.box{
	transform: perspective(250px) rotateX(45deg);
}
```

## transform-style
When we set `transform-style: preserve-3d`, we opt into a different stacking algorithm. Instead of being based purely on stacking contexts and `z-index` layers, we _position the elements in 3D space_.

`transform-style` property is not inheritable. So if we have a grandchild element that is being transformed we need to apply `transform-style: preserve-3d;` to the middle element.

1. Locate the ancestor that creates the 3D rendering context (this will be the element that sets `perspective`).
2. Locate the descendant that applies a 3D transform (eg. `transform: rotateX()`).
3. Apply the following CSS declaration to each element between the two: `transform-style: preserve-3d;`. This will ensure that the 3D rendering context is passed through all the layers, and can be used by the transformed descendant.

## Summary
- `perspective` is all about the visuals of how items are presented. By default, CSS uses _orthographic projection_, like that “Where's Waldo?” drawing, but we can flip to _perspective projection_ with the `perspective` attribute.
- `transform-style` creates a 3D rendering context, which allows items to be moved around in 3D space, changing which elements show up “in front”, and allowing elements to intersect.
- We usually apply the above two properties on a *parent element*.
- The following properties will *disable* `transform-style` if applied on the same element that applies `transform-style`:
	- `overflow  
	- `clip-path`
	- `opacity`
	- `filter`  
	- `mix-blend-mode`
