```bash
npx create-next-app@latest --ts --use-npm project_name
```

Tweak pathing to use absolute paths
```json
"baseUrl": ".",
"paths": {
	"@/*": ["./src/*"],
	"@/components/*": ["./src/components/*"],
	"@/assets/*": ["./src/assets/*"],
	"@/utilities/*": ["./src/utilities/*"]
}
```
Now you have multiple ways of importing
1. `src/../..` start with the file or foldername that is in root folder.
2. `@/xyz` this will look into `xyz` folder/file that is in `src`.
3. `@/components/xyz` this will look into `xyz` folder/file in `src/components`.
4. `../../xyz` you can still use relative path.
5. `/images/xyz` if you start with `/` it will look into `pulbic` folder.
