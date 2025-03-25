At any given moment, *exactly one element* on the page will be considered “**active**”. We refer to this as the element being **focused**. 

There are *many ways that focus can move between elements*, including:
1.  Hitting the “Tab” key will cycle to the next interactive element
2.  Clicking an interactive element will focus it

## :focus
The **`:focus`** [CSS](https://developer.mozilla.org/en-US/docs/Web/CSS) [pseudo-class](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes) represents an element (such as a form input) that has received focus. It is generally triggered when the user clicks or taps on an element or selects it with the keyboard's Tab key.

## :focus-visible
The **`:focus-visible`** pseudo-class applies while an element matches the [`:focus`](https://developer.mozilla.org/en-US/docs/Web/CSS/:focus) pseudo-class and the UA ([User Agent](https://developer.mozilla.org/en-US/docs/Glossary/User_agent)) determines via heuristics that the focus should be made evident on the element.

These days, browser default **focus indicators are applied to `:focus-visible` instead of `:focus`.**

## : focus-within
The **`:focus-within`** [CSS](https://developer.mozilla.org/en-US/docs/Web/CSS) [pseudo-class](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes) matches an element if the element or any of its descendants are focused. In other words, it represents an element that is itself matched by the [`:focus`](https://developer.mozilla.org/en-US/docs/Web/CSS/:focus) pseudo-class or has a descendant that is matched by `:focus`.

## When does an element receive :focus-visible
It depends on two things, *element type* and *input device* used to select the element.
- Inputs usually receive :focus-visible when focused by any method, though mouse clicks might not trigger it in some browsers.
- For anything else, the element receives `:focus-visible` only when selected by a *non pointer device(not mouse/trackpad)*. For example, via *keyboard navigation* or *programatic focus*. Except for being *clicked on*.

## Focus Outline
If you wish to change the browser's default *focus outline* styles 
```css
a:focus-visible {
	outline: 1px solid red;
}
```

### Summary
- `:focus` is always applied when user selects an element. `:focus-visible` depends on the *element type* and the user's *input device*.
- *Browser default focus styles* are applied on the `:focus-visible` class.
- If you want to change *focus styles*, target the `:focus-visible` class.


✅ stands for if the element receives `focus-visible`

|                          | Input | Anything Else That Is Focusable |
| ------------------------ | ----- | ------------------------------- |
| Clicked On               | ✅     |                                 |
| Tabbed Into              | ✅     | ✅                               |
| Programmatically Focused | ✅     | ✅                               |


