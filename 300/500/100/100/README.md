# 100 - What Are Webhooks And How They Work

Based on "What Are Webhooks And How They Work" at https://hookdeck.com/guides/webhooks/what-are-webhooks-how-they-work

In today's highly connected online world, nothing can function optimally in isolation. Achieving a task (almost) always involves the participation of more than one entity. E-commerce apps need to communicate with payment systems, payment systems need to communicate with banking systems, banking systems need to communicate with customer accounts...do you see the pattern?

The ability of independent online systems to communicate with one another and share data is the core of what makes online services valuable today. In this post, we will look at webhooks. A webhook is one of the many ways to facilitate communication between online services and by the end of this post, you will fully understand what webhooks are, how they work, and when to use them.

## 100 - What is a webhook?

A webhook is an HTTP request, triggered by an event in a source system and sent to a destination system, often with a payload of data. Webhooks are automated, in other words they are automatically sent out when their event is fired in the source system.

This provides a way for one system (the source) to "speak" (HTTP request) to another system (the destination) when an event occurs, and share information (request payload) about the event that occurred.

![image](https://user-images.githubusercontent.com/12828104/148640616-63ca1e74-36d3-4172-b0f9-b45772756a8e.png)

Webhooks

## 200 - What are webhooks used for?

Based on the definition above, I am sure you're already getting an idea of what webhooks are used for. Simply put, webhooks are used to communicate the occurrence of an event in one system to another system, and they often share data about the event. However, an example is always easier to illustrate so let's look at a case of webhooks in action.

Let's say you subscribe to a streaming service. The streaming service wants to send you an email at the beginning of each month when it charges your credit card.

The streaming service can subscribe to the banking service (the source) to send a webhook when a credit card is charged (event trigger) to their emailing service (the destination). When the event is processed, it will send you a notification each time your card is charged.

The banking system webhooks will include information about the charge (event data), which the emailing service uses to construct a suitable message for you, the customer.

## 300 - How webhooks work

### 100 - Webhook request process

For a system to send webhooks, the system has to be able to support the process. You can build your system to send webhooks by triggering HTTP requests for different types of events.

Webhooks are most common in [SaaS](https://en.wikipedia.org/wiki/Software_as_a_service) platforms like [GitHub](https://docs.github.com/en/developers/webhooks-and-events/webhooks/about-webhooks), [Shopify](https://shopify.dev/api/admin/rest/reference/events/webhook), [Stripe](https://stripe.com/docs/webhooks), [Twilio](https://www.twilio.com/docs/usage/webhooks), and [Slack](https://slack.com/intl/en-ca/help/articles/115005265063-Incoming-webhooks-for-Slack) because they support different types of events based on the activities that happen within them.

To receive webhook requests, you have to register for one or more of the events (also known as topics) for which the platform offers a webhook. A webhook request will be sent to a destination endpoint (URL). It can be your application, register the URL as the ***Webhook URL*** for that event.

Once the webhook registration for an event is complete, you will receive webhook requests at the destination URL you provided each time the event occurs.

### 200 - Consuming a webhook

Now that you have registered for webhook requests, you have to be prepared to receive them.

- Webhooks are regular HTTP requests and should be handled as such. (webhook providers always have documentation for implementation details.)
- Webhooks payloads are in serialized form-encoded JSON or XML formats.
- Webhooks are a one-way communication system but it is best practice to return a 200 or 302 status code to let the source application know that you have received it.
- It is also advised to make the [webhook request operation at your end idempotent](https://hookdeck.com/guides/webhooks/implement-webhook-idempotency), as some source applications can send the same webhook request more than once. In this type of scenario, you want to ensure that your response to a webhook request is not duplicated as this might lead to a [compromised system](https://hookdeck.com/guides/webhooks/how-solve-webhook-data-integrity-issues).
- A single webhook request can also be distributed to multiple destinations that require the information, in a process known as [fanning out](https://hookdeck.com/guides/product/post/how-fan-out-webhooks-different-services). This allows source systems to speak to more applications and better distribute information across the web.

### 300 - POST or GET Webhooks

You might get webhooks requests as GET or POST requests, dependent on the webhooks provider. GET webhook requests are simple and have their payload appended to the webhook URL as a query string. POST webhook requests have their payload in the request body and might also contain properties like authentication tokens.

## 400 - Conclusion

Information rules the web, and getting information in real-time makes online services highly efficient and responsive to customer needs. Webhooks offers a non-complex way to make sharing information in real-time amongst online platforms possible.
