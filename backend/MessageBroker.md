# RabbitMQ

## Installation





## Intro

四个核心概念：

- Producing：发送消息
- Queue：暂存消息的“信箱”
- Comsuming：接受消息
- Exchange：有点类似路由器？Producer会把所有的消息交给Exchange，由它决定如何处理消息：给哪个队列或者给哪些队列，又或者是直接丢弃

一个简单的架构图如下：

![image-example](https://www.rabbitmq.com/img/tutorials/python-three-overall.png)

其中Exchange有四种工作模式：

- direct
- topic
- headers
- fanout 

## Work queues

一个比较简单的模型，建立一个队列，它能够把任务(消息)分发给多个worker，分别执行

![image-20231118134216798](https://lbw-img-lbw.oss-cn-beijing.aliyuncs.com/img/202311181342570.png)

默认的情况下，queue会把消息按顺序平均的分配给每一个worker

### 消息确认机制

在worker执行任务时，可能出现各种各样的错误：worker意外终止、worker失去了与Broker的连接......出现这些情况我们都可以认为是任务没有正常执行完毕，我们希望这种没有正常执行的任务能够重做，就需要一个**确认机制**来让Broker知道一个任务是否完成

默认情况下，worker完成任务后需要向Broker确认，确认后Broker就可以将此任务标记为完成之后删除；rabbitmq的默认超时时间是30min，若超时则会把这个任务重新加到队列中



### 消息持久性

消息确认能解决当worker出问题时，仍然保证任务能够被正常执行；但是当Broker出错时，怎么保证所有的任务不会丢失呢？这里用到消息的持久机制

开启消息的持久化非常简单，在生命channel的时候把durable参数置为True即可：
```python
channel.queue_declare(queue='task_queue', durable=True)
```



## Publish/Subscribe

把一个消息同时发送给多个worker

实现非常简单，把Exchange设置为fanout模式即可，这个模式会把消息转发给所有队列，实现消息的广播

对于Producer：

1. 声明channel：

   ```python
   channel.exchange_declare(exchange='logs', exchange_type='fanout')
   ```

2. publish消息：

   ```python
   channel.basic_publish(exchange='logs', routing_key='', body=message)
   ```

对于Consumer：

1. 声明channel

2. ==绑定==channel：

   ```python
   channel.queue_bind(exchange='logs', queue=queue_name)
   ```

3. subscribe消息：

   ```python
   channel.basic_consume(
       queue=queue_name, on_message_callback=callback, auto_ack=True)
   
   channel.start_consuming()
   ```



## Routing

有选择的接收消息：不像P/S那样广播，而是类似组播



















