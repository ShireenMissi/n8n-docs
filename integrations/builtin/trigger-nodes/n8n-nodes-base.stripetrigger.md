---
title: Stripe Trigger
description: Documentation for the Stripe Trigger node in n8n, a workflow automation platform. Includes details of operations and configuration, and links to examples and credentials information.
contentType: integration
---

# Stripe Trigger

Use the Stripe Trigger node to respond to events in Stripe and integrate Stripe with other applications. n8n has built-in support for a wide range of Stripe features, including receiving notifications about payments, customers, subscriptions, and more.

On this page, you'll find a list of events the Stripe Trigger node can respond to and links to more resources.

/// note | Credentials
Refer to [Stripe credentials](/integrations/builtin/credentials/stripe/) for guidance on setting up authentication.
///

## Events

The Stripe Trigger node can respond to the following events:

* **Account Updated**: Triggered when account information is updated
* **Charge Failed**: Triggered when a charge attempt fails
* **Charge Succeeded**: Triggered when a charge succeeds
* **Customer Created**: Triggered when a new customer is created
* **Customer Deleted**: Triggered when a customer is deleted
* **Customer Source Created**: Triggered when a customer adds a payment source
* **Customer Source Deleted**: Triggered when a customer removes a payment source
* **Customer Source Updated**: Triggered when a customer updates a payment source
* **Customer Subscription Created**: Triggered when a customer subscription is created
* **Customer Subscription Deleted**: Triggered when a customer subscription is deleted
* **Customer Subscription Updated**: Triggered when a customer subscription is updated
* **Customer Updated**: Triggered when customer information is updated
* **Invoice Created**: Triggered when an invoice is created
* **Invoice Payment Failed**: Triggered when an invoice payment fails
* **Invoice Payment Succeeded**: Triggered when an invoice payment succeeds
* **Payment Intent Succeeded**: Triggered when a payment intent succeeds
* **Payment Method Attached**: Triggered when a payment method is attached
* **All Events**: Triggered on any Stripe event

## Webhook signature verification

**Important security feature**: The Stripe Trigger node validates webhook signatures to ensure the authenticity of incoming webhook events. This prevents spoofed or tampered webhook requests from being processed.

### How it works

* The node automatically validates the `Stripe-Signature` header using HMAC-SHA256 algorithm
* Signature verification requires the webhook secret from your Stripe dashboard
* Webhooks with invalid or missing signatures are rejected
* This follows Stripe's recommended security best practices for webhook handling

### Configuration requirements

1. **Obtain your webhook secret**: Navigate to the Stripe dashboard → Developers → Webhooks section
2. **Configure credentials**: Add the webhook secret (starts with `whsec_`) to your [Stripe credentials](/integrations/builtin/credentials/stripe/)
3. **Automatic verification**: Once configured, signature verification happens automatically for all incoming webhooks

/// warning | Required configuration
Existing Stripe webhook configurations must have the webhook secret properly configured in credentials. Webhooks without valid signatures will no longer be processed.
///

## Node parameters

### Events

Select which Stripe events should trigger your workflow. You can choose specific events or select **All Events** to trigger on any Stripe event.

## Templates and examples

<!-- see https://www.notion.so/n8n/Pull-in-templates-for-the-integrations-pages-37c716837b804d30a33b47475f6e3780 -->
[[ templatesWidget(title, 'stripe-trigger') ]]

## Related resources

Refer to [Stripe's documentation](https://stripe.com/docs/webhooks){:target=_blank .external-link} for more information about webhooks and events.

--8<-- "_snippets/integrations/builtin/trigger-nodes/ssl-support.md"
