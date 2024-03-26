How does the browser decide which element to render "on top" when elements overlap?

## flow layout
1. *DOM order*, the later one overlaps the previous one.
2. However, the content will float on top, e.g. content in previous elements will be above background of later elements.

## How browser determines who is on top
1. As a general rule, **positioned elements will always render on top of non-positioned ones**.
2. First, all of the non-positioned elements are rendered (everything using Flow, Flexbox, Grid…). Next, all of the positioned elements are rendered on top (relative, absolute, fixed, sticky).
3. If we set _both_ elements to use relative positioning? In that case, the DOM order wins. We can tweak this using z-index. 

## Summary
- When all siblings are rendered in Flow layout, the DOM order controls how the background elements overlap, but the content will always float to the front. 
- If one sibling uses positioned layout, it will appear above its non-positioned sibling, no matter what the DOM order is. 
- If both siblings use positioned layout, the DOM order controls which element will be on top. Unlike in Flow layout, the content does not float to the front.
- The above is the default behavior. We can override it using `z-index`.
- Keep `z-index` *positive*. This makes sure that all positioned elements will be *on top of* non positioned elements.

## z-index
*z-index* works with *positioned* elements, *flex* & *grid* children.

- The default value of `z-index` is `auto`, which is equivalent to `0`.
- The higher the number, the closer it is the the viewer.

## stacking context
We can only compare `z-index` of elements if they are in the same *stacking context*.

Ways of creating a *stacking context*
1. `relative`,`absolute` position with a `z-index` not `auto`
2. Setting `opacity` to a value less than `1`
3. Setting `position` to `fixed` or `sticky` (No z-index needed for these values!)
4. Applying a `mix-blend-mode` other than `normal`
5. Adding a `z-index` to a child inside a `display: flex` or `display: grid` container
6. Using `transform`, `filter`, `clip-path`, or `perspective`
7. Setting `isolatoin: isolate;`
