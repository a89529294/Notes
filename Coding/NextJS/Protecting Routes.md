```jsx
// utils/auth.js
import { getSession } from 'your-session-library'; // Replace with your session library

export async function getServerSideProps(context) {
  const session = await getSession(context.req); // Fetch session data using your library
  const isUserAuthenticated = !!session;

  return {
    props: {
      isUserAuthenticated
    }
  };
}
```
```jsx
// pages/_app.js
import { useRouter } from 'next/router';

function MyApp({ Component, pageProps }) {
  const router = useRouter();

  // Redirect unauthenticated users to the login page
  if (!pageProps.isUserAuthenticated && router.pathname !== '/login') {
    router.push('/login'); // Replace with your login page path
    return null;
  }

  return <Component {...pageProps} />;
}

export default MyApp;
```
```jsx
// pages/protected-page.js
import { getServerSideProps } from '../utils/auth';

function ProtectedPage() {
  return (
    <div>
      {/* Content of your protected page */}
    </div>
  );
}

export { getServerSideProps };
export default ProtectedPage;

```