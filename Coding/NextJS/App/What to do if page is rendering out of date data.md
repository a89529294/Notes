There are several ways to control caching
- _time based_: every x seconds, ignore the cached response and fetch new data.
```js
// from a page
export const revalidate = 10
```
- _force purge_: forcibly purge a cached response
```js
import { revalidatePath } from "next/cache";

revaludatePath('/')
```
- _disable_: disable caching completely
```js
// from a page
export const dynamic = 'force-dynamic'
// or
export const revalidate = 0
```