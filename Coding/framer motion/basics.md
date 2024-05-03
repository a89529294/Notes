First, let's take a look at the **main elements that define an animation**. When working on one, whether it's to move an element, changing its shape, or color, I always try to answer the following 3 questions:

1. "Where/how is my element at the beginning?" i.e **the initial state**    
2. "Where it needs to go or which shape it needs to take by the end?" i.e. **the target state**
3. "How it's going to transition from the initial state to the end state?" i.e. **the transition state**

In the case of _Framer motion_, the library gives us a `motion` component which takes 3 properties (props) that let us define an answer to the 3 questions above:
`initial`: the state of our element at mount time.
`animate`: the state in which our element will be at the end of the animation.
`transition`: how our element goes from the initial state to the target state.

