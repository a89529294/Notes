A __MotionValue__ is an internal value to the Framer Motion library that **"tracks the state and the velocity of an animating value"**. For more complex animation we may want to **create our own MotionValue** (quote from the [docs](https://www.framer.com/api/motion/motionvalue/#usemotionvalue)), and then **add them as inline style** to a given component. To define a MotionValue, we need to use the `useMotionValue` hook.

## composing motion values
- Using the `useTransform` hook, we can pass the latest value through an update function that can take the latest parent value and transform it before returning it to update the child.
```js
const x = useMotionValue(0);
const y = useTransform(x, latest => latest * 2);
```
- `useTransform` can also accept value ranges that can map from a linear series of numbers into non-linear series of numbers, colors or a complex string.
```js
const x = useMotionValue(0);
const xInput = [-100, 0, 100];
const opacityOutput = [0, 1, 0]; 
const colorOutput = ["#f00", "#fff", "#0f0"];
const opacity = useTransform(x, xInput, opacityOutput); const color = useTransform(x, xInput, colorOutput);
```

## example
```jsx
import { motion, useMotionValue, useTransform } from 'framer-motion';
import './scene.css';

const Example = () => {
  const blockVariants = {
    initial: {
      rotate: 0,
    },
    target: {
      rotate: 360,
    },
  };

  const rotate = useMotionValue(0);
  const scale = useTransform(rotate, [0, 270], [0, 1]);

  return (
    <motion.div
      style={{
        background: 'linear-gradient(90deg,#ffa0ae 0%,#aacaef 75%)',
        height: '100px',
        width: '100px',
        borderRadius: '10px',
        rotate,
        scale,
      }}
      variants={blockVariants}
      initial="initial"
      animate="target"
      transition={{
        ease: 'easeInOut',
        duration: 4,
      }}
    />
  );
};
```
