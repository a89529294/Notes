### in client components
#### option 1
```ts
// actions.ts
'use server'
export async function editSnippet(code:string, formData:FormData) {
	console.log("edit snipped called");
}
```

```ts
// MyClientComponent.ts
'use client'
export default function MyClientComponent(){
	const [code, setCode] = React.useState('')
	const editSnippetAction = editSnippet.bind(null,code)
	return <form action={editSnippetAction}></form>
}

```

#### option 2
```ts
// actions.ts
'use server'
export async function editSnippet(code:string) {
	console.log("edit snipped called");
}
```

```ts
// MyClientComponent.ts
'use client'
export default function MyClientComponent(){
	const [code, setCode] = React.useState('')
	const handleClick = () => {
		React.startTransition(async()=> await editSnippet(code))
	}
	return <button onClick={handleClick}>Submit</button>
}
```