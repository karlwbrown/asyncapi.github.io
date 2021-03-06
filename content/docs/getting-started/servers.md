---
title: "Servers"
date: 2019-04-03T10:56:52+01:00
menu:
  docs:
    parent: 'getting-started'
weight: 110
---

In the previous lesson, we learned how to create the definition of a simple [Hello World application](/docs/getting-started/hello-world), so let's take it from there.

In this article, we will learn how to add "servers" to our AsyncAPI document. Adding and defining servers is useful because it specifies where and how to connect. The connection facilitates where to send and receive messages.


{{<code lang="yaml" lines="5-8">}}
asyncapi: 2.0.0
info:
  title: Hello world publisher application
  version: '0.1.0'
servers:
  production:
    url: broker.mycompany.com
    protocol: amqp
    protocolVersion: "0.9.1"
    description: This is "My Company" broker.
channels:
  hello:
    publish:
      message:
        payload:
          type: string
          pattern: '^hello .+$'
{{</code>}}

We added a new section called "servers" in our AsyncAPI document.

You might have noticed that the example mentions "amqp". This protocol is very common and was popularized by RabbitMQ (among others). You can use any protocol. For example, the most common are `mqtt` (widely adopted by the Internet of Things and mobile apps), `kafka` (popular for its streaming solution), `ws` (WebSockets are frequently used in browsers), and `http` (used in HTTP streaming APIs.)

{{%remember%}}
The "servers" section defines where your application should connect to start sending and receiving messages. 

1. If you are using a {{<link "https://fmvilas.com/event-driven-architectures-asyncapi/">}}broker-centric architecture{{</link>}} such as Kafka or RabbitMQ, usually you specify the URL of the broker. 
2. If you have the classic client-server model such as for REST APIs, then your server should be the URL of the server.
{{%/remember%}}

## Conclusion

Now we know where to connect to start publishing "hello {name}" messages.

On the next chapter, you'll learn how to add security requirements to a server.

{{%next-chapter url="/docs/getting-started/security"%}}
