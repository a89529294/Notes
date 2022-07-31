- `npm create vite@latest <projectName> -- --template react-ts`
- In project *root* `npm install -D tailwindcss postcss autoprefixer`
- In project *root* `npx tailwindcss init -p`
- In *tailwind.config.cjs* replace `content:[]` with `content: ["./index.html", "./src/**/*.{js,ts,jsx,tsx}"],`
- In *index.css* replace everything with 
```css
@tailwind base; @tailwind components; @tailwind utilities;
```
