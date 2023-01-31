modify `next.config.js`
```js
/** @type {import('next').NextConfig} */
const nextConfig = {
	reactStrictMode: true,
	swcMinify: true,
	async rewrites() {
		return {
			afterFiles: [{ source: "/:path*", destination: "/_404/:path*" }],
		};
	},
};

module.exports = nextConfig;
```
add `pages/_404/[...path].tsx`
```tsx
export const Custom404 = () => <div></div>;

export const getServerSideProps = () => {
	return { redirect: { destination: "/", permanent: false } };
};

export default Custom404;
```