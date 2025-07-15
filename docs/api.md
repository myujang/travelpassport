# API Design

## Overview
The API worker exposes business logic via:
- **REST endpoints** (for mobile app and public API)
- **RPC methods** (for internal web app communication)

## REST Endpoints (Hono)
- `GET /user/:id/passports` — Get user’s passports
- `POST /order` — Create a new order
- ... (add more as needed)

## RPC Methods (WorkerEntrypoint)
- `getUserPassports(userId)` — Returns user’s passports
- `createOrder(orderData)` — Creates a new order
- ... (add more as needed)

## Example: Calling RPC from Web Worker
```ts
const userPassports = await context.cloudflare.env.API.getUserPassports(context.user.id);
```

## Example: REST from Mobile App
```http
GET /user/123/passports
```

## References
- [Cloudflare Workers RPC](https://developers.cloudflare.com/workers/runtime-apis/bindings/service-bindings/rpc/)
- [Hono Docs](https://hono.dev/) 