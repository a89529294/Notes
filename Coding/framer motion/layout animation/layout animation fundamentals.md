In Framer Motion, you can animate a `motion` component between distinct _layouts_ by setting the `layout` prop to `true`. This will result in what we call a **layout animation**.

When we're talking about animating the "layout" or a "layout property" we mean updating any of the following properties:
- Position-related, such as CSS `flex`, `position` or `grid`
- Size-related, such as CSS `width` or `height`
- The overall position of an element within a list for example. This can useful if you want to animate sorting/reordering a list.

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