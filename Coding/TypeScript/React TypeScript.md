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
