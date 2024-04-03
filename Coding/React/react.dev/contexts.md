Subscribing to a context causes the consumer component to re-render if the value changes, even if the consumer component only uses a part of the value that did not change. We can solve it by splitting up the contexts.
```jsx
// store the state here
const ContextData = React.createContext({ isNavExpanded: false });
// store the open/close functions here
const ContextApi = React.createContext({ open: () => {}, close: () => {} });

const NavigationController = ({ children }: { children: ReactNode }) => {
  const [isNavExpanded, setIsNavExpanded] = useState(false);

  const open = useCallback(() => setIsNavExpanded(true), []);

  // no dependencies, close won't change
  const close = useCallback(() => setIsNavExpanded(false), []);

  // that one has a dependency on state
  const data = useMemo(() => ({ isNavExpanded }), [isNavExpanded]);

  // that one never changes - no dependencies
  const api = useMemo(() => ({ open, close }), [close, open]);

  return (
    <ContextData.Provider value={data}>
      <ContextApi.Provider value={api}>
	      {children}
      </ContextApi.Provider>
    </ContextData.Provider>
  );
};
```
- Note we are memoizing the values passed into the contexts.