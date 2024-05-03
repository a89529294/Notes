Simply use the `.lazy.tsx` suffix.
Note however, only the following can be lazily loaded:
**Non-Critical/Lazy Route Configuration** - The code that is not required to match the route, and can be loaded on-demand.
    - Route Component
    - Error Component
    - Pending Component
    - Not-found Component

## example
### before code splitting
```tsx
// posts.tsx
import { createFileRoute } from '@tanstack/react-router'
import { fetchPosts } from './api'

export const Route = createFileRoute('/posts')({
  loader: fetchPosts,
  component: Posts,
})

function Posts () {
  ...
}
```
### after code splitting
```tsx
// posts.tsx
import { createFileRoute } from '@tanstack/react-router'
import { fetchPosts } from './api'

export const Route = createFileRoute('/posts')({
  loader: fetchPosts,
})
```
```tsx
// posts.lazy.tsx
import { createLazyFileRoute } from '@tanstack/react-router'

export const Route = createLazyFileRoute('/posts')({
  component: Posts,
})

function Posts () {
  ...
}
```

