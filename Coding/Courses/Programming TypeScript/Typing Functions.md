```ts
// Shorthand call signature
type Log = (message: string, userId?: string) => void

// Full call signature
type Log = {
  (message: string, userId?: string): void
}
```

## function overload
In general, each overload signature has to be assignable to the implementation’s signature when declaring an overloaded function type.
```ts
function createElement(tag: 'a'): HTMLAnchorElement
function createElement(tag: 'canvas'): HTMLCanvasElement
function createElement(tag: 'table'): HTMLTableElement
function createElement(tag: string): HTMLElement
function createElement(tag: string) {
	if (tag === 'a') return document.createElement('a')
	if (tag === 'canvas') return document.createElement('canvas')
	if (tag === 'table') return document.createElement('table')
	return document.createElement(tag)
}
```
