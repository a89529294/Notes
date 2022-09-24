- `npm create vite@latest <projectName> -- --template react-ts`
	- check npm version first, if using `6.x` run `npm create vite@latest <projectName> --template react-ts`, if `7.x` run above
- In project *root* `npm install -D tailwindcss postcss autoprefixer`
- In project *root* `npx tailwindcss init -p`
- In *tailwind.config.cjs* replace `content:[]` with `content: ["./index.html", "./src/**/*.{js,ts,jsx,tsx}"],`
- In *index.css* replace everything with 
```css
@tailwind base; @tailwind components; @tailwind utilities;
```
- To view on mobile add change *dev* script in `package.json` to `"dev": "vite --host"`

