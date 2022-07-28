## How to access form elements
- `formElement.elements.elementId`
- `formElement.elements.elementName`
- `formElement.elements[index]`
- `formElement[index]`

## A few things about select tag
- Native `<select>` makes it almost impossible to style the dropdown menu. It also lacks the *value* attribute.
- In *React JSX*, `<select` does have the *value* attribute but it is still impossible to style the dropdown menu.
- Consider using a third party library or implement your own.
