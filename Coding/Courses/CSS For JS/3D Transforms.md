By default, the 3D engine in CSS will assume that we want to use **orthographic projection**. Everything will be the same size, no matter how far away it is.

We can switch to a **perspective projection** using the `perspective` CSS property.

`perspective` takes in a length value, e.g. `500px`. The value we pass to `perspective` can be thought of as a measure of how close the user is to the screen. The *smaller* the values is, the *closer* the user is to the screen, the *larger* the effect will appear to be.

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