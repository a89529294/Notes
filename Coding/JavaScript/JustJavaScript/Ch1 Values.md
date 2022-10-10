*Primitive Values* They are a permanent part of our JavaScript universe. I can point to them, but I can’t create, destroy, or change them.

*Objects and functions* are also values but, unlike primitive values, **I can manipulate them from my code**.

**Types of Values**
*Primitive*
1. `undefined`
2. `null
3. Booleans: `true` `false`
4. Numbers
5. BigInts
6. Strings
7. Symbols
*Object & Functions*
1. Objects
2. Functions

**Expressions**
*Expressions* are questions that JavaScript can answer. JavaScript answers expressions in the only way it knows how—with values.

*Expressions* always result in a single value.

## Summary
1.  **There are values, and then there’s code.** We can think of values as different things “floating” in our JavaScript universe. They don’t exist _inside_ our code, but we can refer to them from our code.
2.  **There are two categories of values: there are _Primitive Values_, and then there are _Objects and Functions_.** In total, there are nine separate types. Each type serves a specific purpose, but some are rarely used.
3.  **Some values are lonely.** For example, `null` is the only value of the Null type, and `undefined` is the only value of the Undefined type. As we will learn later, these two lonely values are quite the troublemakers!
4.  **We can ask questions with expressions.** Expressions exist in our code, so they are not values. Rather, JavaScript will _answer_ our expressions with values. For example, the `2 + 2` _expression_ is answered with the _value_ `4`.
5.  **We can inspect the type of something by wrapping it in a `typeof`expression.** For example, `typeof(4)` results in the string value `"number"`.


