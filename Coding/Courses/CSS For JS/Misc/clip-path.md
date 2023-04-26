- `clip-path` has no effect on layout. An element with `clip-path` applied will still take up the same amount of space in the DOM.
- `clip-path` can be transitioned. In order for `transition` to work, both `polygon` definitions need to have the same number of points. It works by interpolating each point.
- If you do wish to animate between two elements with a *different number of points*, you'll need to cheat by adding multiple points in the same spot. 
- Transforming a rectangle into a triangle:
```css
.triangle {
    clip-path: polygon(
      0% 0%,
      100% 0%,
      100% 100%,
      0% 100%
    );
    transition: clip-path 250ms;
  }
  
  .triangle-wrapper:hover .triangle,
  .triangle-wrapper:focus .triangle {
    clip-path: polygon(
      0% 0%,
      100% 50%,
      100% 50%,
      0% 100%
    );
  }
```

## clip-path functions
- `polygon()`, `ellipse()`, `circle()`. 
```css
 .ellipse {
    clip-path: ellipse(100px 80px at 50% 50%); /* xRadius yRadius at xPosition yPosition */
  }
.circle {
	clip-path: circle(100px at 50% 50%);
}
```

## clip-path with shadows
```html
<style>
  .wrapper {
    filter: drop-shadow(
      1px 2px 4px hsl(0deg 0% 0% / 0.5)
    );
  }
  .triangle {
    clip-path: polygon(
      0% 100%,
      50% 0%,
      100% 100%
    );
  }
</style>

<div class="wrapper">
  <div class="triangle"></div>
</div>
```
We need to move `drop-shadow` to a parent element, otherwise the shadow will get cliped by `clip-path`.