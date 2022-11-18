`_document.tsx_`
```tsx 
import Document, { Html, Head, Main, NextScript } from "next/document";

class MyDocument extends Document {

render() {
	return (
	<Html>
		<Head>
			<link
				href="https://fonts.googleapis.com/css2? 
		        family=Noto+Sans+TC:wght@400;700&display=optional"
				rel="stylesheet"
			/>
		</Head>
		<body>
			<Main />
			<NextScript />
		</body>
	</Html>);
	}
}

export default MyDocument;
```
