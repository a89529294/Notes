- `npm i -D prisma`
- `npx prisma init`
- add .env file to .gitignore
- add `DATABASE_URL=****` to .env
- After creating prisma/schema.prisma file run `npx prisma migrate dev --name <migration_name>`
- After creating prisma/seed.ts file we need to use `ts-node` to run it. `npm i -D ts-node`
- modify package.json by adding `"prisma": {"seed": "ts-node --compiler-options {\"module\":\"CommonJS\"} prisma/seed.ts"},` right after scripts.
- `npx prisma db seed`
- In order to upload to vercel update package.json scripts build command to `"build": "prisma generate && next build",`
- If you updated schema.prisma, make sure to run `npx prisma generate`