We are trying to pass in a `onClick` prop which contains the latest `value` without breaking the memoization of `React.memo(HeavyComponent)`.
```tsx
const HeavyComponentMemo = React.memo(HeavyComponent);

export default function App() {
  const [value, setValue] = useState<string>();
  const ref = useRef<() => void>();

  useEffect(() => {
    ref.current = () => {
      console.log(value);
    };
  });

  const onClick = useCallback(() => {
    ref.current?.();
  }, []);

  return (
    <div className="App">
      <h1>Closures example</h1>

      <>
        <input type="text" value={value} onChange={(e) => setValue(e.target.value)} />
        <HeavyComponentMemo title="Welcome closures" onClick={onClick} />
      </>
    </div>
  );
}
```