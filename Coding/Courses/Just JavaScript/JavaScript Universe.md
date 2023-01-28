What is a value?
- numbers, strings, functions, objects, etc.
What is not a value?
- if statements, loops, variable declarations, etc.

One of the first common misconceptions we need to clear up is that values _are_ our code. Instead, we need to think of them *separately*—our code interacts with values, but **values exist in a completely separate space**.

## Values
There are two kinds of values, *primitives* and *object and functions*.
### Primitive Values
They are a *permanent* part of our JavaScript universe. I can point to them, but I can’t create, destroy, or change them.
### Objects and Functions
You can manipulate them from our code.

## All JavaScript Types
You can get the types of any value using `typeof`, except for null, which gives 'object'. 
- Primitive
	- Undefined (undefined)
	- Null (null)
	- Booleans (true, false)
	- Numbers (-1.00, 3.14,...)
	- BigInts
	- Strings ("hello",...)
	- Symbols
- Functions and Objects
	- Objects ({},...)
	- Functions (x=>x+1,...)

## Expressions
*Expressions are questions that JavaScript can answer*. JavaScript answers expressions in the only way it knows how—with values.

In other words, *expression is just a piece of code that evaluates to a single value*. Value itself is an expression! it's a *literal*.

## Summary
1.  **There are values, and then there’s code.** We can think of values as different things “floating” in our JavaScript universe. They don’t exist _inside_ our code, but we can refer to them from our code.
2.  **There are two categories of values: there are _Primitive Values_, and then there are _Objects and Functions_.** In total, there are nine separate types. Each type serves a specific purpose, but some are rarely used.
3.  **Some values are lonely.** For example, `null` is the only value of the Null type, and `undefined` is the only value of the Undefined type. As we will learn later, these two lonely values are quite the troublemakers!
4.  **We can ask questions with expressions.** Expressions exist in our code, so they are not values. Rather, JavaScript will _answer_ our expressions with values. For example, the `2 + 2` _expression_ is answered with the _value_ `4`.
5.  **We can inspect the type of something by wrapping it in a `typeof` expression.** For example, `typeof(4)` results in the string value `"number"`.

###### Misc
[All return values of typeof](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof#description)

