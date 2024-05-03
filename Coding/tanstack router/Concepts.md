### dynamic route segments
```tsx
import { createFileRoute } from '@tanstack/react-router'

export const Route = createFileRoute('/posts/$postId')({
  // In a loader
  loader: ({ params }) => fetchPost(params.postId),
  // Or in a component
  component: PostComponent,
})

function PostComponent() {
  const { postId } = Route.useParams()
  return <div>Post ID: {postId}</div>
}
```

### catch all routes
A route with a path of only `$` is called a "splat" route because it _always_ captures _any_ remaining section of the URL pathname from the `$` to the end. The captured pathname is then available in the `params` object under the special `_splat` property.

For example, our route tree above has a `files/$` splat route. If the URL pathname is `/files/documents/hello-world`, the `params` object would contain `documents/hello-world` under the special `_splat` property.

### pathless / layout routes
File routes that are _prefixed with an underscore (`_`)_ are considered "pathless" / a "layout". Pathless/Layout routes can be used to wrap child routes with additional components and logic, without requiring a matching `path` in the URL.

- Wrap child routes with a layout component
- Enforce a `loader` requirement before displaying any child routes
- Validate and provide search params to child routes
- Provide fallbacks for error components or pending elements to child routes
- Provide shared context to all child routes

for example, if you have a route tree like this
- \_layout.tsx
- \_layout (dir)
	- home.tsx
	- about.tsx
When the url is `/home` the rendered component looks like
```jsx
<Layout>
	<Home/>
</Layout>
```

### non nested routes
Non-nested routes can be created by _suffixing a parent file route segment with a `_`_. Non-nested routes are valuable because you don't always want a route to be nested, but instead you need it to "break out" of the parent route's path and render its own completely different component tree.

Use this when you want the urls to be similar but you don't want one to be nested under another component.

#### directory structure
- `posts_/$postId/edit`
- `/posts`
	- `$postId`

#### url structure
- `posts/1/edit`
- `posts/1`
#### component structure
```tsx
// `posts_.$postId.edit.tsx`
<EditPost postId={postId} />

// `posts.$postId.tsx`
<Posts>
  <Post postId={postId} />
</Posts>
```

