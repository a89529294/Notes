**Variants are sets that have predefined animation objects**, the kind of object we passed in the examples above in the `animation` prop. You can also define a `transition` property in each variant.

```jsx
import { motion } from 'framer-motion';

const AnimatedButton = () => {
  const buttonVariants = {
    hover: {
      scale: 1.5,
      transition:{
	      duration:1
      }
    },
    pressed: {
      scale: 0.5,
    },
    rest: {
      scale: 1,
    },
  };

  return (
    <motion.button
      initial="rest"
      whileHover="hover"
      whileTap="pressed"
      variants={buttonVariants}
    >
      Click me!
    </motion.button>
  );
};
```