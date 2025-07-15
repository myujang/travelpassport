# FAQ

## How do I run database migrations?
- Use Drizzle ORM: `npx drizzle-kit generate` and `npx drizzle-kit push`

## How do I test locally?
- Use Wrangler for local development of Workers.

## How do I deploy?
- Use Wrangler for manual deploys; GitHub Actions for CI/CD (coming soon).

## Where is the API defined?
- In the API worker (see `/docs/api.md`).

## How is authentication handled?
- Via Clerk (see `/docs/auth.md`). 