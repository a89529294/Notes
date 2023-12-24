1. `github.com/settings/applications/new` Create an OAuth app and generate a _client_id_ and _client_secret_.
2. Add _AUTH_SECRET_, _GITHUB_CLIENT_ID_, _GITHUB_CLIENT_SECRET_ to `.env.local`. 
3. Install `@auth/core`, `@auth/prisma-adapter`, `next-auth`.
4. Make `auth.ts` in `src` folder. See `/Users/albert/Desktop/code/courses/grider-nextjs-course/discuss/src/auth.ts` for complete example.
5. Set up `app/api/auth/[...nextauth]/route.ts` to handle the requests between _Github server_ and _our server_. 
6. Make sever actions to sign in/sign out users. See `/Users/albert/Desktop/code/courses/grider-nextjs-course/discuss/src/actions/index.ts` for complete example.