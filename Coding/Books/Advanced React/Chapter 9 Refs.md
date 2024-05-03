- A __Ref__ is just a mutable object that can store any value. That value will be preserved between re-renders.
- A Ref's update _doesn't trigger re-renders_ and is synchronous.

## When to use Refs
- Is this value used for rendering components, now or in the future?
- Is this value passed as props to other components in any way, now or in the future?

If the answer to both of these questions is "no", then Ref is okay to use.

### useImperativeHandle
1. Decide how the imperative API will look like
2. attach a ref to it
```tsx
type Api = {
  focus: () => void;
  shake: () => void;
};

type InputFieldProps = {
  onChange: (val: string) => void;
  apiRef: RefObject<Api>;
};

const InputField = ({ onChange, apiRef }: InputFieldProps) => {
  const inputRef = useRef<HTMLInputElement>(null);
  const [shouldShake, setShouldShake] = useState(false);

  useImperativeHandle(
    apiRef,
    () => ({
      focus: () => {
        inputRef.current?.focus();
      },
      shake: () => {
        setShouldShake(true);
      },
    }),
    [],
  );

  const className = shouldShake ? 'shake' : '';

  return (
    <input
      ref={inputRef}
      type="text"
      onChange={(e) => onChange(e.target.value)}
      className={className}
      onAnimationEnd={() => {
        setShouldShake(false);
      }}
    />
  );
};

const Form = () => {
  const [name, setName] = useState('');
  const inputApiRef = useRef<Api>(null);

  const onSubmitClick = () => {
    if (!name) {
      inputApiRef.current?.focus();
      inputApiRef.current?.shake();
      console.log('Input should be focused and shaken if empty!');
    } else console.log('Submit the name here!', name);
  };

  return (
    <form>
      <label>Name</label>
      <br />
      <InputField onChange={setName} apiRef={inputApiRef} />
      <Button onClick={onSubmitClick}>Submit!</Button>
    </form>
  );
};
```

Simply put, we are attaching the returned object from the second argument to `useImperatievHandle` to the first argument's `current` property.
In other words, we can simply do if we don't want to use `useImperativeHandle`
```js
React.useEffect(()=>{
	apiRef.current = {
		focus: () => {
			inputRef.current?.focus();
	      },
	    shake: () => {
	        setShouldShake(true);
	      },
	}
},[apiRef])
```

### usePrevious
```js
function usePrevious(value){
	const ref = React.useRef();

	React.useEffect(()=>{
		ref.current = value;
	}, [value])

	return ref.current
}
```

