- **Enums** are one of the few features TypeScript has which is *NOT* a type-level extension of JavaScript.
- **Enums** allow a developer to define a set of *named constants*.
- *Watch out!*, at runtime, enums become objects instead of being removed like types.
- Values auto increment from 0 if not supplied.

```ts
enum LogLevel {
	ERROR,
	WARN,
	INFO,
	DEBUG
}

// 'ERROR' | 'WARN' | 'INFO' | 'DEBUG'
const LogLevelStrings = keyof typeof LogLevel;
// 0 | 1 | 2 | 3
const LogLevelValues = `${LogLevel}`
```