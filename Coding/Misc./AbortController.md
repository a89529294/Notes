```js
const controller = new AbortController(); // Create a new AbortController instance
fetch('...', { signal: controller.signal }); // Make a fetch request with the controller's signal
// Some other code...
controller.abort(); // Call the abort method to cancel the fetch request

```