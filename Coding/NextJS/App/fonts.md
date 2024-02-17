## local fonts
1. put font file in `public` folder
2. go to component where you intend to use that font
```tsx
import localFont from "next/font/local";

// Note you have to use relative path
const myFont = localFont({
	src: "../../public/fonts/font.woff2",
});

export default function MyPage(){
	return <div className={myFont.className}>...</div>
}
```

## google fonts
1. import font in component
```tsx
import { Poppins } from "next/font/google";

const myFont = Poppins({
	subsets: ["latin"],
	weight: ["100", "200", "300", "400", "500", "600", "700", "800", "900"],
});

export default function MyPage(){
	return <div className={myFont.className}>...</div>
}
```