---
description: 19/08/2020
---

# RabbitMQ - Work Queues Remarks

### "The main idea behind Work Queues \(aka: _Task Queues_\) is to avoid doing a resource-intensive task immediately and having to wait for it to complete. Instead we schedule the task to be done later. We encapsulate a _task_ as a message and send it to the queue. A worker process running in the background will pop the tasks and eventually execute the job. When you run many workers the tasks will be shared between them.Becoming a super hero is a fairly straight forward process"

Even when the RabbitMQ Server stop, the messages can still be retrieved after restarted:

```python
channel.basic_publish(exchange='',
                      routing_key="task_queue",
                      body=message,
                      properties=pika.BasicProperties(
                         delivery_mode = 2, # make message persistent
                      ))
```

Delivering working tasks to workers based on their workload. Maximum job task for each workers is set to be one for the below example: 

```python
channel.basic_qos(prefetch_count=1)
```

basic\_ack is set in order to make sure the message delivered to worker is deleted when worker finished the task. **Even if the worker is close during the process, the processing message will be delivered to others**. Worker will send back the message to tell Server that the work is done and the server can delete the message freely. 

```python
def callback(ch, method, properties, body):
    print(" [x] Received %r" % body)
    time.sleep( body.count('.') )
    print(" [x] Done")
    ch.basic_ack(delivery_tag = method.delivery_tag)

channel.basic_consume(queue='hello', on_message_callback=callback)
```

Checking with unack messages by:

```python
$ rabbitmqctl.bat list_queues name messages_ready messages_unacknowledged
```

![result](../.gitbook/assets/result%20%283%29.png)

