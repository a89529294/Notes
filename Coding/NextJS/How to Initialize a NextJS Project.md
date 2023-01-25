```bash
npx create-next-app@latest --ts --use-npm project_name
```

Tweak pathing to use absolute paths (tsconfig.json)
```json
{
	"compilerOptions":{
		"baseUrl": ".",
		"paths": {
			"@/*": ["./src/*"],
	}
}
// src/components is the same as @/components
```
Now you have multiple ways of importing
1. `src/../..` start with the file or foldername that is in root folder.
2. `@/xyz` same as `src/xyz`.
3. `../../xyz` you can still use relative path.
4. `/images/xyz` if you start with `/` it will look into `pulbic` folder.
