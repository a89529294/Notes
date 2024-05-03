When performing a layout animation that affects the _size_ of a component, some distortions may appear during the transition for some properties like `borderRadius` or `boxShadow`.

In such a case you have to set those properties inline
```jsx
<motion.div
  layout
  className="box"
  data-expanded={expanded}
  style={{
    borderRadius: '20px' // cannot use css varaibles
  }}
/>
```

#### The content stretches undesirably
This is a natural side-effect of animating width and height with scale. Some elements, like those containing elements changing between different aspect ratios (commonly text elements), might be better animated with `layout="position"`, which only animates the position of the element.

