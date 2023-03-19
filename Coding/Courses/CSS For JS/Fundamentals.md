- A *declaration* is a combination of a property and a value.
```css
.code-snippet {
	padding: 32px;
	white-space: pre-wrap;
}
```
In the above snippet, `padding: 32px;` is a *declaration*; `white-space: pre-wrap;` is another *declaration*.
- A *rule*, also known as a style, is a collection of declarations, targeting one or more selectors. A stylesheet is made up of multiple rules. The snippet above is a *rule*.
- *Pseudo-classes* let us apply a chunk of CSS based on an element's current *state*. `:hover`, `:focus`, `:last-child`, etc.
- *Pseudo-elements* are like pseudo-classes, but they don't target a specific state. Instead, they target "*sub-elements*" within an element. `::placeholder`, `::before`