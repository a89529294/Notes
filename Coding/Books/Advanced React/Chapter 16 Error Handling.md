### setting up error boundary
```tsx
type Props = { children: ReactNode; fallback: ReactElement };
type State = { hasError: boolean };

class ErrorBoundary extends React.Component<Props, State> {
  constructor(props: Props) {
    super(props);
    // initialize the error state
    this.state = { hasError: false };
  }

  // if an error happened, set the state to true
  static getDerivedStateFromError() {
    return { hasError: true };
  }

  componentDidCatch(error: any, errorInfo: any) {
    // send error to somewhere here
    console.log(error, errorInfo);
  }

  render() {
    // if error happened, return a fallback component
    if (this.state.hasError) return this.props.fallback;

    return this.props.children;
  }
}
```

### using error boundary
```jsx
export default function App() {
  return (
    <div className="App">
      <h1>Hello Simple ErrorBoundary</h1>
      <p>click on a button to trigger state update and as a result - error</p>
      <p>
        <b>Ignore</b> and close error overlay - it's just in dev mode and can't
        be removed
      </p>
      <ErrorBoundary fallback={<h3>Something happened!</h3>}>
        <Component />
      </ErrorBoundary>
    </div>
  );
}
```

### limitations
Error boundaries _only catch errors that happen during the React lifecycle_. Things that happen outside of it, like resolved promises, async code with setTimeout, various callbacks, and event handlers, will disappear if not dealt with explicitly.

### solving the limitations
We can just re throw the error back in any React lifecycle.
```tsx
const useThrowAsyncError = () => {
  const [state, setState] = useState();

  return (error: any) => {
    setState(() => {
      throw error;
    });
  };
};
```
Now when we catch an error outside of React, we can just use normal try/catch then call above function.
```tsx
const ComponentWithAsyncThrower = () => {
  const throwAsyncError = useThrowAsyncError();

  const onClick = () => {
    try {
      throw new Error('break things');
    } catch (e) {
      throwAsyncError(e);
    }
  };

  return (
    <button className="button" onClick={onClick}>
      click me to cause an error
    </button>
  );
};
```

### react-error-boundary
We can also just use https://www.npmjs.com/package/react-error-boundary. 


