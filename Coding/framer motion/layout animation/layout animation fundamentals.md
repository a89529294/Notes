In Framer Motion, you can animate a `motion` component between distinct _layouts_ by setting the `layout` prop to `true`. This will result in what we call a **layout animation**.

When we're talking about animating the "layout" or a "layout property" we mean updating any of the following properties:
- Reordering of a list.
- A style set on the component itself, for example a change in `width` or `position`.
- A change in the parent's layout, e.g. flexbox or grid.
- Or any other change in the component's layout.

You can customize the transition of the layout animations by 
```jsx
<motion.div
  layout
  transition={{
    layout: {
      duration: 1.5,
    },
  }}
/>
```