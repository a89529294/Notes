1. using `useEffect`
```js
const [isClient,setIsClient] = useState(false);

useEffect(()=>{
	setIsClient(true)
},[])
```
2. using `typeof window`
```js
const isClient = typeof window === 'object' 
```
3. Only render a component on the client side
```js
import dynamic from "next/dynamic";
const Highlight = dynamic(() => import("./components/Highlight"), {
	ssr: false,
});
```
Now If you use `<Highlight/>` it will only run on the client side.