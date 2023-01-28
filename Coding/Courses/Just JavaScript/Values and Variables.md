**Primitive Values Are Immutable**

**in JavaScript, you can only pass a value**.

In our JavaScript universe, a variable is a **wire** that _points to_ a value.

## Rules of assignment
1. The left side of an assignment must be a “**wire**”—such as the `pet` variable.
2. The right side of an assignment must be an expression, so it always results in a value. Note `'the kraken'` or `5` are also expressions, they are called *literals*.

Note that `y = x` did not mean point `y` to `x`. We can’t point variables to each other! Variables always point to _values_. When we see an assignment, we “ask” the right side’s value, and point the “wire” on the left side to _that value_.

###### Summary
- **Primitive values are immutable.** They’re a permanent part of our JavaScript universe—we can’t create, destroy, or change them. For example, we can’t set a property on a string value because it is a primitive value. Arrays are not primitive, so we can set their properties.
    
- **Variables are not values.** Each variable _points to_ a particular value. We can change _which_ value it points to by using the `=` assignment operator.
    
- **Variables are like wires.** A “wire” is not a JavaScript concept—but it helps us imagine how variables point to values. When we do an assignment, there’s always a wire on the left, and an expression (resulting in a value) on the right.
    
- **Look out for contradictions.** If two things that you learned seem to contradict each other, don’t get discouraged. Usually it’s a sign that there’s a deeper truth lurking underneath.
    
- **Language matters.** We’re building a mental model so that we can be confident in what _can_ or _cannot_ happen in our universe. We might speak about these ideas in a casual way (and nitpicking is often counterproductive) but our understanding of the meaning behind the terms needs to be precise.