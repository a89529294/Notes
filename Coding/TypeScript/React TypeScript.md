- *ForwardRef*
```typescript
const Component = React.forwardRef<RefType, PropsType>((props, ref) => {
  return someComponent;
});
```
- *as prop*
```tsx
function Component({as}:{as:keyof JSX.IntrinsicElements}){
	const Ele = as
	return <Ele>...</Ele>
}
```
- *passing down all props to wrapped html element* (extend `ComponentPropsWithoutRef<'element_name'>`)
```ts
// usage
function App() {
  return <Button type="button" specialProp='I am special'> text </Button>;
}

// implementation
export interface ButtonProps extends React.ComponentPropsWithoutRef<"button"> {
  specialProp?: string;
  children:React.ReactNode
}
export function Button(props: ButtonProps) {
  const { specialProp, children,...rest } = props;
  // do something with specialProp
  return <button {...rest} >{children}</button>;
}
```
