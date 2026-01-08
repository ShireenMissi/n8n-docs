---
title: Stripe credentials
description: Documentation for Stripe credentials. Use these credentials to authenticate Stripe in n8n, a workflow automation platform.
---

# Stripe credentials

You can use these credentials to authenticate the following nodes:

- [Stripe](/integrations/builtin/app-nodes/n8n-nodes-base.stripe/)
- [Stripe Trigger](/integrations/builtin/trigger-nodes/n8n-nodes-base.stripetrigger/)

## Prerequisites

* Create a [Stripe](https://stripe.com/){:target="_blank" .external-link} account.
* For webhook functionality, ensure you have created a webhook endpoint in your Stripe dashboard.

## Supported authentication methods

- API Key

## Related resources

Refer to [Stripe's API documentation](https://stripe.com/docs/api){:target="_blank" .external-link} for more information about the service.

## Using API Key

To configure this credential, you'll need:

- A **Secret Key**: Your Stripe API secret key
- A **Webhook Secret** (optional, but required for Stripe Trigger node): Your webhook signing secret for signature verification

### Getting your API credentials

1. Open your [Stripe Dashboard](https://dashboard.stripe.com/){:target="_blank" .external-link}
2. Navigate to **Developers** → **API keys**
3. Copy your **Secret key** (starts with `sk_`)
   - For testing, use the test mode secret key (starts with `sk_test_`)
   - For production, use the live mode secret key (starts with `sk_live_`)
4. In n8n, enter this key in the **Secret Key** field

### Getting your webhook secret

The webhook secret is required for the [Stripe Trigger](/integrations/builtin/trigger-nodes/n8n-nodes-base.stripetrigger/) node to validate webhook signatures and ensure webhook authenticity.

1. In your [Stripe Dashboard](https://dashboard.stripe.com/){:target="_blank" .external-link}, navigate to **Developers** → **Webhooks**
2. Click on an existing webhook endpoint or create a new one
3. In the webhook details page, locate the **Signing secret** section
4. Click **Reveal** to show the webhook secret (starts with `whsec_`)
5. Copy the webhook secret
6. In n8n, enter this secret in the **Webhook Secret** field

/// note | Security best practice
The webhook secret validates the authenticity of webhook events from Stripe. Keep this secret confidential and configure it in your credentials to enable signature verification in the Stripe Trigger node.
///

/// warning | Webhook signature verification
As of the latest version, the Stripe Trigger node requires valid webhook signatures. Webhooks without properly configured webhook secrets and valid signatures will be rejected to prevent spoofed or tampered webhook events.
///

## Test mode vs. Live mode

Stripe provides separate API keys for test mode and live mode:

- **Test mode**: Use test mode keys (prefix `sk_test_`) for development and testing. Test mode uses simulated payment methods and doesn't process real transactions.
- **Live mode**: Use live mode keys (prefix `sk_live_`) for production. Live mode processes real payments and transactions.

Make sure to use the appropriate webhook secret that corresponds to your API key mode (test or live).
