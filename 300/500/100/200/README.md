# 200 - When to Use Webhooks? Compared with WebSocket, Pub/Sub, and Polling.

Based on "When to Use Webhooks? Compared with WebSocket, Pub/Sub, and Polling." at https://hookdeck.com/guides/webhooks/when-to-use-webhooks

One of the simplest ways online applications share data is through the use of webhooks, a one-way communication format for moving data from one application to another. However, webhooks aren't the only method for data transfer between networked applications. As an engineer, it is very important to use the right tool for the right problem, or you could risk trivializing or overengineering the solution.

In this article, we will start by looking at how webhooks work. Then, I will compare the process with other data sharing techniques used by modern architectures in order to pair each technique with the scenarios where you should use them.

After the comparisons comes the answer to the question that might be heaviest on your mind: When should I be using webhooks?

## 100 - How webhooks work

Webhook communication is achieved by sending an HTTP request from a source application to a destination application. When an event takes place in the source application, an HTTP request which might contain data relating to the event is triggered. This HTTP request is sent to the destination application's endpoint (often referred to as the webhook URL.)

Webhook requests can be sent using the POST or GET request methods. This depends on the webhook provider's preferences — the information on how to consume the requests is always available on the provider's documentation.

Now that we have a good understanding of how [webhooks](https://hookdeck.com/guides/webhooks/what-are-webhooks-how-they-work) work, let's dive in to some comparisons.

## 200 - Webhooks or WebSockets

### 100 - How WebSockets work

WebSockets are used to facilitate two-way real-time communication between two networked systems. WebSockets achieve this by keeping a socket open on both the client and the server for the duration of the conversation.

This opens a duplex communication stream enabling both the client and server to pass information between one another with no significant latency added.

![image](https://user-images.githubusercontent.com/12828104/148641001-7e96bd60-6e63-44cf-b753-495ae900b9a1.png)

WebSockets

### 200 - Differences between webhooks and WebSockets

Webhooks are used for one-way communication from a source application to a destination application, while WebSockets facilitate two-way communication between server and client.

Webhooks are mostly used by two servers to pass information, while WebSockets are used primarily for server-to-client (mostly web browsers) communication.

Also, webhooks close the socket connection on the receiving application once a response has been sent back, while WebSockets keep the connection open for as long as required and not just for a single transfer of information.

In terms of communication protocols, WebSocket uses its own custom ```WS``` protocol while webhooks use regular ```HTTP```.

### 300 - When to use WebSockets

Use WebSockets when you want two-way communication between two networked systems, for example when building a chat application. WebSockets are also very useful for data visualization dashboards or maps that need to reflect real-time data values.

## 300 - Webhooks or pub/sub

### 100 - How pub/sub works

[Pub/sub](https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern), which is short for publish/subscribe, is a communication system for distributing messages between a set of publishers (message producers) and subscribers (message consumers). A pub/sub system buffers messages from producers and routes them to subscribers through the use of dedicated channels known as topics. Publishers publish messages to topics and subscribers express interest by subscribing to the topics.

Once a message is published to a specific topic, the message is cloned and sent to all the subscribers subscribed to it.

== IMAGE HERE, MISSING ==

pub/sub

### 200 - Differences between webhooks and pub/sub

In a pub/sub system, message sources are decoupled from message consumers while in webhooks, the message producer is fully aware of the location of the consumer through the webhook URL.

Webhooks are a direct form of communication between the producer and consumer while pub/sub is a middle-man framework that routes messages from publishers to subscribers. The communication setup in a webhook is one-to-one, i.e. one producer to one consumer, while in a pub/sub system you can have many producers sending messages to multiple consumers.

### 300 - When to use pub/sub

Use a pub/sub system when you have multiple consumers interested in the same message or more than one message producer.

Also, use a pub/sub system when you want to asynchronously process messages. Webhooks are synchronous.

An example of a situation where a pub/sub system is appropriate is in an e-commerce site. When a customer makes a purchase, you need to mail an invoice to the customer, send information to the delivery department, and enter the sale record in your CRM. Let's imagine that a mailing service, delivery service, and records service handle these responsibilities respectively.

That is three systems interested in the same message. You can publish this message to a pub/sub system, which will then route it to these three subscribed services.

## 400 - Webhooks or polling

### 100 - How polling works

Polling involves periodically making requests to a system to check for new events or data. If new data is found, a response is returned with the new data in its payload. If no new data is available, nothing is returned.

Polling is used to query systems for new information and can be set up as an automated cron job that runs at certain intervals.

To capture the difference between these two approaches with a relatable example, polling is like going to the post office to check if you have new mail. Using webhooks is basically having mail delivered to your house every time you have new mail simply by giving the postman your house address.



WE ARE HERE

