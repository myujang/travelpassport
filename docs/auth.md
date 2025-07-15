# Authentication

## Overview
Authentication is managed by Clerk for both web and mobile clients.

## User Model
- Clerk user ID is the primary identifier in the database (`clerk_id` field in `users` table).
- Additional user info (name, email, etc.) is synced from Clerk.

## Auth Flows
- **Sign Up / Sign In**: Users authenticate via Clerk UI (web/mobile SDKs).
- **Session Management**: Clerk handles sessions and JWTs.
- **API Access**: API worker validates Clerk tokens for protected endpoints.

## References
- [Clerk Docs](https://clerk.com/docs) 