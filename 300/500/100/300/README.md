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

Now that we have a good amount of webhook knowledge, let's put that knowledge into action with an exercise using [Stripe](https://stripe.com/). We are going to sign up for a Stripe account and register for Stripe webhooks in order to receive webhook requests on a demo Node.js server.

If you want to learn more about Stripe webhooks before we get started, you can read their docs at [Developer Tools → Webhooks](https://stripe.com/docs/webhooks). Here, you can find information on

1. [Working with different programming languages](https://stripe.com/docs/webhooks/build)
2. [Stripe verification](https://stripe.com/docs/webhooks/signatures) signatures for authentication
3. Stripe webhook integration [best practices](https://stripe.com/docs/webhooks/best-practices)
4. [Sample integrations](https://stripe.com/docs/webhooks/integration-builder)

### 100 - Create a Stripe account

Head over to the [Stripe registration page](https://dashboard.stripe.com/register) to set up a new account. You will be required to verify your email address after you register.

Created:

- User email: wvanheemstra@icloud.com
- Password: *****

### 200 - Clone a Node.js API

Once you have your Stripe account set up, the next step is to clone the demo Node.js API. The API we will be using is available on [Hookdeck's GitHub repo](https://github.com/hookdeck/nodejs-webhook-server-example). Clone this repository by running the following command:

```
$ git clone https://github.com/hookdeck/nodejs-webhook-server-example.git
```

**NOTE**: If you are blocked from cloning from GitHub (perhaps becasue you are behind a corporate firewall), you can also ```download``` and unzip the repository directly from the web page at https://github.com/hookdeck/nodejs-webhook-server-example.

Or find the same repository files here at https://github.com/vanHeemstraSystems/hookdeck-headstart/tree/main/containers/app/hookdeck

This will make the project available at the location on your file system where you ran the command.

Navigate to the root of the project and install the required dependencies by running the following commands:

```
$ cd nodejs-webhook-server-example
$ npm install
```

When the installation completes, you can then run the Node.js server with the following command:

```
$ npm start
```

This will boot up the API application and print a message to the screen indicating that the API is now running and listening for connections on ```port 1337```.

The endpoint to be used for the webhook requests is ```/stripe-webhooks-endpoint``` and can be found in the ```routes.js``` file as shown below:

```
router.post("/stripe-webhooks-endpoint", bodyParser.raw({type: 'application/json'}), function(req, res) {
 console.log(req.body);
 res.send("Stripe Successfully received Webhook request");
});
```
routes.js

This endpoint receives the webhook requests, prints the request body to the console, and returns a message.

### 300 - Get a webhook URL

== WE ARE HERE ==
