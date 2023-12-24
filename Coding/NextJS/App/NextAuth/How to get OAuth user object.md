For complete setup refer to `/Users/albert/Desktop/code/courses/grider-nextjs-course/discuss`

### server component
```tsx
import { auth } from "@/auth";
import * as actions from "@/actions";

// auth function reads from headers(), which makes the whole 
// page dynamic
export default async function Home() {
	const session = await auth();

	return <div>{session?.user}</div>
}		
```

### client component
In `root layout`
```tsx
import Providers from "@/app/providers";
import { ReactNode } from "react";

export default function RootLayout({
children,
}: {
	children: React.ReactNode;
}) {

return (
	<html lang="en">
		<body className={`${inter.className} light`}>
			<Providers>{children}</Providers>
		</body>
	</html>
	);
}
```
In `providers`
```tsx
"use client";
import { SessionProvider } from "next-auth/react";
import { ReactNode } from "react";

export default function Providers({ children }: { children: ReactNode }) {

return (
	<SessionProvider>{children}</SessionProvider>
	);
}
```
In a `client component`
```tsx
"use client";
import { useSession } from "next-auth/react";

// useSession makes a request from client browser to the 
// backend
export default function Profile() {
	const session = useSession();
	return <div>From client: {JSON.stringify(session.data?.user)}</div>;
}
```


