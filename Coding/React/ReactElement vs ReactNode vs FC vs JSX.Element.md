**React.ReactElement** is the type for elements in React, either created via **JSX** or **React.createElement**.
```js
const a = <div/> // ReactElement
const b = React.createElement('div') // ReactElement
```

**React.ReactNode** is wider, it can be text, number, boolean, null, undefined, a portal, a ReactElement, or an array of ReactNodes. It represents **anything that React can render**.
```js
const a = (
	<div>
	  Hello World! // ReactNode
	</div>
)
```

**JSX.Element** is an internal hook for Typescript. It is _set equal to_ **ReactElement** to tell Typescript that every JSX expressions should be typed as ReactElements. But if we'd use Preact, or other technologies using JSX it would be set to something else.

**React.FC** returns `ReactElement | null`, so it cannot return a bare string or an array of ReactElements. It is a [known](https://github.com/DefinitelyTyped/DefinitelyTyped/issues/33006) [limitation](https://github.com/DefinitelyTyped/DefinitelyTyped/issues/20544). The workaround is to use **Fragments**.
```js
const Foo: FC = () => {
  return <>hello world!</>  
}
```

