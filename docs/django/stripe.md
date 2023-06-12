---
layout: default
title: Stripe Payment
parent: Django
---
# Stripe Payment System

## Listen to Stripe events locally
When developing the app locally, is may be necessary to have a local instance of the webhook listener. This can be achieved by using the [Stripe CLI](https://stripe.com/docs/stripe-cli) and issuing the following commands:

```bash
stripe login
```
```bash
# remember the trailing / or this wont work!
stripe listen --forward-to localhost:8000/webhook/
```
Issuing triggers can be done as followed:
```bash
stripe trigger payment_intent.succeeded
```

## Endpoints 

### `config/`
Returns the Stripe public key
```json
{"publicKey": <STRIPE_PUBLISHABLE_KEY>}
```

### `customer-portal/`
Redirects user to Stripe customer portal to handle subscription - only if user is signed in and, has or have had, a subscription. 

* If user is not signed in, it redirects to homepage
* If user does not have or have not had a subscription, it redirects to profile page

### `create-checkout-session/`
Returns a checkout session id and returns as json:
```json
{"sessionId": <SESSIONID>}
```
If an error occurs, it will also be returned as json:
```json
{"error": <error>}
```

### `webhook/`