# springboot-rabbitmq

Core Concepts :
RabbitMQ is a widely used open-source message broker software that facilitates communication between different components of a software system. It's based on the Advanced Message Queuing Protocol (AMQP), which is a standardized messaging protocol designed to enable communication between various software applications.

1. Producer - is an application that sends messages to RabbitMQ exchanges. These messages could be any type of data, such as orders, events, notifications, etc.

2. Exchange - basically, it acts as intermediary between the producer and a queue. Exchanges receive messages from producers and then decide how to route them to one or more queues based on the message's routing key and the exchange's routing rules. There are different types of exchanges, such as direct, topic, fanout, and headers, which determine the routing behavior.

3. Routing Key/Bindings - define the relationship between exchanges and queues. They specify which queues should receive messages from which exchanges based on the message's routing key and exchange type. The routing key is like an address for the message.

4. Queues - are message buffers that store messages until consumers retrieve and process them. Messages in a queue are ordered and can be processed in a first-in, first-out (FIFO) manner. The messages are put into a queue by a producer and read from it by a consumer. Once a message is read, it is consumed and removed from the queue. A message can thus only be processed exactly once.

5. Consumers - are applications or components that subscribe to queues and retrieve messages from them. They process the messages according to the logic implemented in the consumer code.

Overall, RabbitMQ provides a way for decoupled components of a system to communicate asynchronously and reliably. It enables different parts of a distributed application to communicate without needing to know the details of each other's implementation, leading to improved system scalability, flexibility, and robustness.

Workflow:

[Producer] --> [Exchange] --> [Queue] --> [Consumer]
                  ^           |
                  |           v
          [Binding Rules]   [Acknowledgments]

1. The producer generates a message and sends it to an exchange.
2. The exchange receives the message and uses binding rules to determine which queue(s) the message should be routed to.
3. The message is stored in the queue until a consumer retrieves it.
4. The consumer fetches the message from the queue and processes it.
5. After successful processing, the consumer sends an acknowledgment back to the RabbitMQ broker.
6. If the consumer crashes or fails to acknowledge, RabbitMQ can re-queue the message for delivery to another consumer.
7. The message may persist on disk if configured for durability.

          
