# RocketMQ-Client
this is a dot net client and a windows server for rocketmq（rocket mq的c#客户端和windows服务端）

alibaba-rocketmq-4.2是rocket-mq windows服务器软件
<br>
client-ikvm-4.2为rocket-mq c#客户端dll
<br>
<br>
//启动推送型消费者
<br>
ChainwayPullConsumer consumer = new ChainwayPullConsumer();
<br>
consumer.setNamesrvAddr(nameAddress);
<br>
consumer.subscribe(t, "*");
<br>
consumer.setConsumeFromWhere(ConsumeFromWhere.CONSUME_FROM_FIRST_OFFSET);
<br>
consumer.setConsumerGroup(group);
<br>
//设置消费者端口，官方没有该功能。适用端口有安全限制的服务器
<br>
if (port > 0) consumer.setClientPort(port);
<br>
<br>
<br>
//启动生产者
<br>
ChainwayProducer producer = new ChainwayProducer(group);
<br>
producer.setNamesrvAddr(nameAddress);
<br>
//设置生产者端口，官方没有该功能。适用端口有安全限制的服务器
<br>
if (port > 0) producer.setClientPort(port)
<br>

