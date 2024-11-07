**Variants are sets that have predefined animation objects**, the kind of object we passed in the examples above in the `animation` prop. You can also define a `transition` property in each variant.

You can also *use functions instead of objects*, just make sure the function return an animation object. *The function receives one argument, which can be passed in via `custom` prop on the motion object*. One exception is for the function passed to the `exit` prop you need to pass the `custom` prop on `AnimatePresence` .



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

For exit animation, if you need access to the custom prop in the function in the variants object, pass in the custom prop on the `AnimatePresence` component.
```jsx
import {motion, AnimatePresence} from 'framer-motion';
import React from 'react';

function AnimatedButton(){
	const [btnKey, setBtnKey] = React.useState(0);
	const [exitAnimation, setExitAnimation] = React.useState('fadeOut'); // 'slideLeft' or 'fadeOut'

	const variant = {
		exit: (exitAnimation)=> exitAnimation === 'fadeOut' ? {opacity:0} : {x:'-100%'},
		
	}

	return <div>
		<AnimatePresence custom={exitAnimation}>
			<motion.button
			 key={btnKey}
			 exit={'exit'}
			 variants={variant}
			>
		</AnimatePresence>
		<button
			onClick={()=>setExitAnimation(curr=>curr === 'fadeOut' ? 'slideLeft' : 'fadeOut')}
		> 		
			Click to change exit animation
		</button>
	</div>
}
```