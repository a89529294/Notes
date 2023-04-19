## Color Manipulation
```css
.brightness {
    filter: brightness(150%);
  }
.contrast {
    filter: contrast(60%);
  }
.sepia {
    filter: sepia(100%);
  }
.mixed {
    filter: contrast(200%) grayscale(90%) hue-rotate(180deg);
  }
```
- Works on any DOM nodes.

## blur
```html
<style>
  .wrapper {
    position: relative;
  }
  .gradient {
    position: relative;
    width: 200px;
    height: 200px;
    border-radius: 50%;
    background-image: linear-gradient(
      deeppink,
      red,
      coral,
      gold,
      white
    );
  }
  .blurry {
    position: absolute;
    filter: blur(40px);
    transform: scale(1.3) translateX(10%) rotate(30deg);
  }
</style>

<div class="wrapper">
  <div class="gradient blurry"></div>
  <div class="gradient"></div>
</div>
```
- Two copies of the same element occupying the same space.
- The one in the back has `filter: blur(40px);` applied to it.
- The `transform: scale(1.3)...` is extra tweaks.

## backdrop filters
The `filter` property will apply an SVG filter to the selected element, but what if we want to blur everything _behind_ the element?
We can accomplish this task using the `backdrop-filter` property.

`backdrop-filter` supports the same set of functions that `filter` supports.

One thing to watchout for is make sure the element that `backdrop-filter` is applied to has a *transparent*/*semi-transparent* background. Otherwise the blurred elements *behing* the element will not be shown.


