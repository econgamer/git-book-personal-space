---
description: 19/08/2020
---

# RabbitMQ - Publish/Subscribe

The core idea in the messaging model in RabbitMQ is that the producer never sends any messages directly to a queue. Actually, quite often the producer doesn't even know if a message will be delivered to any queue at all.

Instead, the producer can only send messages to an _exchange_. An exchange is a very simple thing. On one side it receives messages from producers and the other side it pushes them to queues. The exchange must know exactly what to do with a message it receives. Should it be appended to a particular queue? Should it be appended to many queues? Or should it get discarded. The rules for that are defined by the _exchange type_.

Source Code:



**Temporary queue \(Declared two exclusive queue in this tutorial\)**:

```python
result = channel.queue_declare(queue='', exclusive=True)
```

**Remember to bind it to the exchange after declaration:**

```bash
channel.queue_bind(exchange='logs',
                   queue=result.method.queue)
```

### Cheat Sheet

```bash
$ sudo rabbitmqctl list_exchanges
```

```bash
$ rabbitmqctl list_bindings
```

![Result](../.gitbook/assets/result%20%284%29.png)

