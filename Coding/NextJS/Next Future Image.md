`import Image from "next/future/image";`

Some observations about the new `<Image>`
1. You can set *style* or *className* prop directly on `<Image>` and it will style the `<img>` directly.
2. In some cases you have to set *width* and *height* but you can override them with *style*/*className*.

Example 1:
```jsx
<Image width={500} 
	   height={1} 
	   style={{width:'100%', height:'auto'}}
/>
```
Notes: 
1. width has to be big enough, i.e. the biggest size the image might become across desktop/mobile, otherwise the image will be blurry.
2. another more precies way is to use the *sizes* attrbibute

Example 2:
```jsx
<Image width={1} 
	   height={1} 
       sizes="(max-width: 768px) 100vw,
              (max-width: 1200px) 50vw,
              33vw"
	   style={{width:'100%', height:'auto'}}
/>
```
Notes:
1. Using the size attribute to tell Next how to generate and select images.
2. [Read more](https://nextjs.org/docs/api-reference/next/future/image#sizes)