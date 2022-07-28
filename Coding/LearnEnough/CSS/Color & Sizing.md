## hexadecimal color
- `#ff00ee` can be shorten to `#f0e` only if char at index *1* is same as char at index *0*, char at index *3* is same as char at index *2*, char at index *5* is same as char at index *4*
- If all three pairs are the same like `565656`, `f3f3f3` it will represent some shade of grey
- Faster for browser to render than *rgb*

## Font Sizing
- Always use relative units *rem*/*em* instead of *px*, easier when you refacter later on.
- *em* represents the calculated [`font-size`](https://developer.mozilla.org/en-US/docs/Web/CSS/font-size) of the element. If used on the [`font-size`](https://developer.mozilla.org/en-US/docs/Web/CSS/font-size) property itself, it represents the _inherited_ font-size of the element
- *rem* is equal to the computed value of font-size on the root element. **When specified on the font-size property of the root element, the rem units refer to the property’s initial value.**

