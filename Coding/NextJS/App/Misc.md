- Metadata can be defined by exporting a [`metadata` object](https://nextjs.org/docs/app/api-reference/file-conventions/metadata#static-metadata) or [`generateMetadata` function](https://nextjs.org/docs/app/api-reference/file-conventions/metadata#generatemetadata) in a [`layout.js`](https://nextjs.org/docs/app/api-reference/file-conventions/layout) or [`page.js`](https://nextjs.org/docs/app/api-reference/file-conventions/page) file.
```js 
// app/page.js
export const metadata = {
  title: 'Next.js',
};
 
export default function Page() {
  return '...';
}
```