
- Many producers can send messages that go to one queue, and many consumers can try to receive data from one queue.
-  A worker process running in the background will pop the tasks and eventually execute the job.
- When you run many workers the tasks will be shared between them.
 - By default, RabbitMQ will send each message to the next consumer, in sequence.
 - On average every consumer will get the same number of messages. This way of distributing messages is called round-robin
But we don't want to lose any tasks. If a worker dies, we'd like the task to be delivered to another worker.


In order to make sure a message is never lost, RabbitMQ supports message acknowledgments. An ack(nowledgement) is sent back by the consumer to tell RabbitMQ that a particular message had been received, processed and that RabbitMQ is free to delete it.
if any thing bad happens to the message RabbitMQ will re queue the message .
a default timeout is 30min . 

```python
docker run -d --hostname my-rabbit --name rabbitmq -p 5672:5672 -p 15672:15672 rabbitmq:3-management


# 5672 : backend communication
# 15672 : for rabbitmq dashboard (http://localhost:15672)
# Username: `guest`, Password: `guest`

```

we are going to use pika python client 

```python
pip install pika 
```



# Sending Steps 

1. establish connection with rabbitMQ

```python
import pika

parameter = pika.ConnectionParameter('localhost')
connection = pika.BlockingConnection(parameter)

channel = connection.channel()
```

2. declare queue

```python
channel.queue_declare(queue = "hello" )
```

3.  
In RabbitMQ a message can never be sent directly to the queue, it always needs to go through an exchange.
use a default exchange identified by an empty string. This exchange is special ‒ it allows us to specify exactly to which queue the message should go. The queue name needs to be specified in the `routing_key` parameter:

```python
channel.basic_publish(exchange='',  routing_key='hello',  body='Hello World!')
```

4. close connection
```python
connection.close()
```


# Receiving Steps

1. make connection
2. make queue
3. receveing message from queue works by subscribing a `callback` function to a queue. Whenever we receive a message, this `callback` function is called by the Pika library. 

```python
# function to consume
def callback(ch, method, properties, body):  
print(f" [x] Received {body}")

channel.basic_consume(queue='hello', auto_ack=True, on_message_callback=callback )

channel.start_consuming()

```


we can start more than 


# Exchange

define :  it receives messages from producers and on the other side it pushes them to queues

- A _producer_ is a user application that sends messages.
- A _queue_ is a buffer that stores messages.
- A _consumer_ is a user application that receives messages.

producer never sends any messages directly to a queue
Instead, the producer can only send messages to an _exchange_.

what to do with message is defined by exchange type .
