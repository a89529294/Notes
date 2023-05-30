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
- *css custom properties*
```tsx
<span
style={{
	'--before-color': s.color,
	  } as CSSProperties }
>
```
- _extracting prop types from 3rd party libraries_
```tsx
import { ComponentProps } from "react";
import { Button } from "some-external-library";

type MyButtonProps = ComponentProps<typeof Button>;
```