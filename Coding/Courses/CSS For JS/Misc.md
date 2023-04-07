- [chrome user-agent stylesheet](https://source.chromium.org/chromium/chromium/src/+/main:third_party/blink/renderer/core/html/resources/html.css)

```js
function findElementsWiderThanViewport(element) {

const elementsToCheck = Array.from(element.children)

const elementsWiderThanViewport = []

for (let i = 0; i < elementsToCheck.length; i++) {

if (elementsToCheck[i].clientWidth > window.innerWidth) elementsWiderThanViewport.push(elementsToCheck[i])

const currentElementChildren = Array.from(elementsToCheck[i].children)

for (let j = 0; j < currentElementChildren.length; j++) {

elementsToCheck.push(currentElementChildren[j])

}

}

return elementsWiderThanViewport

}
```

- *justify texts* - this means that the spacing between each word is tweaked so that each line fills the available horizontal space. `text-align: justify;`

