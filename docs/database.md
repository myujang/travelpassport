# Database Schema & Migrations

## Overview
This document outlines the D1 database schema and how to manage it using Drizzle ORM.

## Schema Outline
- **users**: User info (linked to Clerk)
- **states**: Malaysian states
- **passports**: Each state’s travel passport
- **places**: Places of interest, linked to passports
- **user_passports**: Which user enrolled in which passport
- **orders**: Booklet purchase orders

## Example Drizzle ORM Schema
```ts
// users
table.users = {
  id: uuid().primaryKey(),
  clerk_id: varchar().unique(),
  name: varchar(),
  email: varchar().unique(),
  created_at: datetime()
};
// ... (other tables as described above)
```

## Migration Workflow
1. Update schema in Drizzle ORM models.
2. Run `npx drizzle-kit generate` to create migration files.
3. Run `npx drizzle-kit push` to apply migrations to D1.

## References
- [Drizzle ORM Docs](https://orm.drizzle.team/docs)
- [Cloudflare D1 Docs](https://developers.cloudflare.com/d1/) 