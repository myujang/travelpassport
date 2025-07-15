# Payments & Fulfillment

## Overview
Payments are processed via Stripe. Orders and fulfillment are tracked in the D1 database.

## Stripe Integration
- Web and mobile clients use Stripe Checkout or Payment Intents.
- Payment confirmation triggers order creation in D1.

## Order Status Workflow
1. User places order and pays via Stripe.
2. API worker receives Stripe webhook and updates order status in D1.
3. Fulfillment workflow is triggered (manual or automated).
4. Order status is updated as shipped/delivered in D1.

## References
- [Stripe Docs](https://stripe.com/docs) 