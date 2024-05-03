```jsx
const boxVariants = {
  out: {
    y: 600,
  },

  in: {
    y: 0,
    transition: {
      duration: 0.6,
      // first child will appear 1.2s AFTER the parent has appeared
      delayChildren: 1.2,
      // after the first child, following children will appear after 2s after their previous sibling
      staggerChildren: 2,
    },

  },

};

const iconVariants = {
  out: {
    x: -600,
  },
  in: {
    x: 0,
  },
};

return (

  <motion.div variants={boxVariants} initial="out" animate="in">
    <motion.span
      role="img"
      aria-labelledby="magic wand"
      variants={iconVariants}
    >
      🪄
    </motion.span>

    <motion.span role="img" aria-labelledby="sparkles" variants={iconVariants}>
      ✨
    </motion.span>
  </motion.div>
);
```
