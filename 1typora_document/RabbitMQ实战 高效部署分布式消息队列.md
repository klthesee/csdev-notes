RabbitMQ实战 高效部署分布式消息队列

# rabbitTemplate

1.convertAndSend（String routingKey, Object message, MessagePostProcessor messagePostProcessor）

2.

# 章2：理解消息通信

1.只有一个tcp连接，这个tcp连接没有连接线程数的限制。来了一个线程是在现有的tcp连接上建立一个信道。

2.消息路由必须有3部分：交换器、队列、绑定。
											 ![image-20201110091204452](G:\_document\1typora_document\RabbitMQ实战 高效部署分布式消息队列.assets\image-20201110091204452.png)

3.basic.consume命令：消费者会自动回去队列的下一条消息。
  basic.get命令：消费者获取一条消息后，需要手动获取下一条。

4.交换器：消息想要到达队列，需要通过路由器。路由器根据路由键，将消息路由到队列。

5.交换器有4种：direct、fanout、topic、headers
direct：直接发给一个队列
fanout：广播给所有队列
topic：多播，按照规则进行路由
headers

6.生产者发消息：basic_publish($msg,'','路由键')
第一个参数：消息内容。第二个参数：空字符串，表示默认交换器（交换器名）。第三个参数：定义交换器时声明的路由键。

7.topic的不同之处：消费者可以绑定规则到交换器(第三个参数不同)
queue_bind('msg-inbox-logs','logs-exchange','*.msg-inbox')
第一个参数：队列名字。第二个参数：交换器名字。第三个参数：定义规则路由键（可以找到多个路由键）。

