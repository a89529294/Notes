The *default value* of *overflow* is `visible`.
The `body` (and `html`) tag are special cases, being at the root of the DOM hierarchy, and browsers must render these as if they were set to `auto`.
Five values: `visible`, `hidden`, `scroll`, `auto`, `clip`.

## scroll containers
When we set the `overflow` property to `scroll`, `hidden`, or `auto`, it becomes a *scroll container*.
A *scroll container* is like a portal to a pocket dimension. When an element is contained by a scroll container, it's guaranteed to be stuck inside. It will never overflow beyond the 4 corners of the scroll container.
When a container becomes a scroll container, it manages overflow in _both directions_. The moment we set `overflow-x` _or_ `overflow-y` to anything other than `visible` or `clip`, it becomes a portal to an alternative dimension, and all children/descendants will be affected.

Note `overflow: hidden;` is identical to `overflow: scroll;` but with the scrollbar removed! i.e. an element with `overflow: hidden` is literally a *scroll container without scrollbars*.

## overflow: clip
- With `overflow: clip`, no scroll container is created. Any content that spills outside the bounds of this containing block is made invisible. 
- *Because there is not scroll container, we can manage both directions individually.*
- In chrome however, if the element has `border-radius` set, the *clipping will happen in both directions*.

## overflow and positioned elements
- *Absolutely-positioned* elements act just like static-positioned elements when it comes to overflow, _as long as that parent with overflow:auto/scroll is the containing block_.
- Using this we can have an *absolute element pop out of scroll container!
- Same thing applies to `fixed` elements, as long as the containing scroll container acts as a *containing block*. We can make the scroll container into one by applying `will-change: transform;` refer to [[Rendering Logic Positioned Layout]]

The trick is the `.scroll-container` is a non positioned element. The element we wish to pop out is *absolutely positioned*. Just add a *positioned* wrapper around the `.scroll-container`, then the `.tooltip` will be popped out and anchored to the *positioned* wrapper.
```html
<style>
  .containing-block {
    position: relative;
  }

  .scroll-container {
    overflow: auto;
  }

  .tooltip {
    position: absolute;
  }
</style>
<div class="containing-block">
  <div class="scroll-container">
    <ol>
      <!-- Imagine a list here -->
    </ol>
    <div class="tooltip">
      Boop
    </div>
  </div>
</div>
```




