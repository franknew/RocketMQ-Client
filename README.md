# RocketMQ-Client
this is a dot net client and a windows server for rocketmq（rocket mq的c#客户端和windows服务端）

alibaba-rocketmq-4.2是rocket-mq windows服务器软件
<br>
client-ikvm-4.2为rocket-mq c#客户端dll
### 启动推送型消费者
DefaultMQPushConsumer consumer = new DefaultMQPushConsumer();
<br>
consumer.setNamesrvAddr(nameAddress);
<br>
consumer.subscribe(t, "*");
<br>
consumer.setConsumeFromWhere(ConsumeFromWhere.CONSUME_FROM_FIRST_OFFSET);
<br>
consumer.setConsumerGroup(group);
### 设置消费者端口，官方没有该功能。适用端口有安全限制的服务器
if (port > 0) consumer.setClientPort(port);
### 注册推送事件
consumer.registerMessageListener(new ChainwayMessageListener());
### 启动消费者
consumer.start();
<br>
public class ChainwayMessageListener : MessageListenerConcurrently
<br>
{
<br>

    public ConsumeConcurrentlyStatus consumeMessage(List l, ConsumeConcurrentlyContext ccc)
<br>
    {
### 业务代码
    }
<br>
}
### 启动生产者
DefaultMQProducer producer = new DefaultMQProducer(group);
<br>
producer.setNamesrvAddr(nameAddress);
### 设置生产者端口，官方没有该功能。适用端口有安全限制的服务器
if (port > 0) producer.setClientPort(port)
### 启动生产者
producer.start();
### 建议使用jdk1.8
### 建议使用已经封装过的ChainwayMQ
https://github.com/franknew/DataSync

