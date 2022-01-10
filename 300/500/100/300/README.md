# 300 - How to Set Up a Webhook Tutorial

Based on "How to Set Up a Webhook Tutorial" at https://hookdeck.com/guides/webhooks/setting-up-webhook-tutorial

There are three important questions that stand out when learning a new technology: the **what**, the **why** and the **how**. In a [previous article](../100/README.md), we took a thorough look at ```what``` webhooks are and ```why``` you need them. In this tutorial, we are taking a look at the ```how```.

Before we get started, let me share some helpful tips about reading documentation I have discovered over the years working with webhooks. I have had my fair share of frustration trying to find the appropriate information from webhook documentation from different providers.

## 100 - Tips on reading documentation for webhooks

Going through technical documentation is not perceived to be a fun-filled exercise for most developers, and documentation from webhook providers is not an exception.

| Tip | Explanation |
| --- | --- |
| Look for the Developers section | Webhooks are part of the programmatic interface of the webhook provider, thus you would most likely find documentation for webhooks in this section of the provider's website. |
| Use the search bar | Most documentation have search functionality, which you can use to quickly find the information you need with the right keywords, for example **"webhook events."** |
| Check for event types | Events are the main point of interest when it comes to webhooks. Knowing the event types will help you understand the events you can subscribe to. For example an e-commerce site can allow subscriptions for events, such as an item being added to the cart, the purchase of an item, etc. |
| Find information on [webhook security](https://hookdeck.com/guides/webhooks/webhook-security-vulnerabilities-guide) | Webhook requests are regular HTTP requests and are thus prone to all the security threats that HTTP requests face. You want to check information on the security of the provider's webhooks, for example IP/domain whitelisting, authentication tokens, API keys, etc. |
| Rate limits and retries | Just like regular HTTP requests, a webhook request can fail and you also need to consider scalability on the side of the API receiving the requests. Thus, information on the maximum number of concurrent requests and if the value can be configured is important. You also want to find out if failed requests are automatically retried by the provider, if not, you might need to set up your own system to achieve that. |

## 200 - Tutorial: How to set up Stripe webhooks








== WE ARE HERE ==
