```tsx
function modal(){
	return createPortal(<>
	<div className="absolute inset-0 bg-gray-300 opacity-80"></div>
	<div className="absolute inset-40 p-10 bg-white">I'm a modal</div>
</>, document.querySelector('.modal-container'))
}
```
- The key is instead of just returning `<div>...</div>` return the invocation of the function `createPortal`.
- As a first argument pass in the modal, and the 2nd argument is the modal container you just added to `index.html`.