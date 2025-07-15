# Architecture Overview

This document describes the high-level architecture of the TravelPassport platform.

## System Diagram

```mermaid
<!-- ARCHITECTURE_DIAGRAM_PLACEHOLDER -->
flowchart TD
  subgraph Cloudflare
    A["travelpassport-web (Remix Worker)"]
    B["api-worker (Hono, Drizzle, D1, RPC)"]
    C["D1 Database"]
  end
  D["Mobile App (React Native)"]
  E["Public REST API (Hono)"]
  F["Clerk"]
  G["Stripe"]

  A -- "RPC" --> B
  B -- "SQL" --> C
  D -- "HTTPS" --> E
  E -- "REST" --> B
  A -- "Auth" --> F
  D -- "Auth" --> F
  A -- "Payments" --> G
  D -- "Payments" --> G
```

## Components

- **travelpassport-web (Remix Worker):** The web frontend, deployed on Cloudflare Workers, communicates with the API worker via RPC for all business logic and data needs.
- **api-worker (Hono, Drizzle, D1, RPC):** The backend API, responsible for all database operations, business logic, and exposing both REST (for mobile) and RPC (for web) interfaces.
- **D1 Database:** Cloudflare's serverless SQL database, managed via Drizzle ORM.
- **Mobile App (React Native):** The mobile client, communicates with the API worker via public REST endpoints.
- **Clerk:** Authentication provider for both web and mobile clients.
- **Stripe:** Payment provider for order and fulfillment workflows.

## Data Flow
- The web app uses RPC to call business logic in the API worker.
- The mobile app uses REST endpoints exposed by the API worker.
- All database operations are handled by the API worker using Drizzle ORM and D1.
- Authentication is managed by Clerk for both web and mobile.
- Payments are processed via Stripe, with order status tracked in D1. 