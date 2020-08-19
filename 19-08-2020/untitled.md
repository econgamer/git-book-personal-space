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



