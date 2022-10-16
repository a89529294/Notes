## Syntax
- `npm install package_name` or `npm update package_name`

## Rules
- If you *specify a version* npm will override `package.json` entry for that package
`npm i jest@29.2.0`.
- If you *omit the version*, npm will respect the `package.json` entry

## Version Ranges
- `3.1.8` 3 = major; 1 = minor; 8 = patch
- `*` means update to latest version
- `^` means update to latest minor version
- `~` means update to latest patch version
```json
// package.json
"dependencies":{
	"jest":"*", // note you cannot specify a 
                // version with *
	"react":"^16.0.0",
	"tailwindcss":"~2.0.0"
}
```
Alternate syntax
```json
//package.json
"dependencies":{
	"jest":"x.0.0",
	"react":"16.x.0",
	"tailwindcss":"2.0.x"
}
```
