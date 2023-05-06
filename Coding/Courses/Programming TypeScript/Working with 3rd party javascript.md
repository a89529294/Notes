When you npm install third-party JavaScript code into your project, there are three possible scenarios:
1. The code you installed comes with *type declarations out of the box*.
2. The code you installed doesn’t come with type declarations, but *declarations are available on DefinitelyTyped*.
3. The code you installed *doesn’t come with type declarations*, and declarations are *not available on DefinitelyTyped*.

## case one
Nothing to do.

## case two
```bash
npm install lodash --save
npm install @types/lodash --save-dev
```

## case three
Three possible solutions, from least safe to safest:
1. _Whitelist the specific import_ by adding a `// @ts-ignore` directive above your untyped import. TypeScript will let you use the untyped module, but the module and all of its contents will be typed as `any`:
```ts
// @ts-ignore
import Unsafe from 'untyped-module'

Unsafe  // any
```
2. _Whitelist all usages of this module_ by creating an empty type declaration file and stubbing out the module. For example, if you installed the rarely used package `nearby-ferret-alerter`, you could make a new type declaration (e.g., _types.d.ts_) and add to it the ambient type declaration:
```ts
// types.d.ts
declare module 'nearby-ferret-alerter'
```
This tells TypeScript that there exists a module that you can import (`import alert from 'nearby-ferret-alerter'`), but it doesn’t tell TypeScript anything about the types contained in that module.
3. _Create an ambient module declaration_. Like in the previous approach, create a file called _types.d.ts_ and add an empty declaration (`declare module 'nearby-ferret-alerter'`). Now, fill in the type declaration. For example, the result might look like this:
```ts
// types.d.ts
declare module 'nearby-ferret-alerter' {
  export default function alert(loudness: 'soft' | 'loud'): Promise<void>
  export function getFerretCount(): Promise<number>
}
```
