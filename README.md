# RocketMQ-Client
<p>this is a dot net client and a windows server for rocketmq（rocket mq的c#客户端和windows服务端）</p>

<p>alibaba-rocketmq-4.2是rocket-mq windows服务器软件</p>
<p>client-ikvm-4.2为rocket-mq c#客户端dll</p>

### 启动推送型消费者
```
<p>DefaultMQPushConsumer consumer = new DefaultMQPushConsumer();</p>
<p>consumer.setNamesrvAddr(nameAddress);</p>
<p>consumer.subscribe(t, "*");</p>
<p>consumer.setConsumeFromWhere(ConsumeFromWhere.CONSUME_FROM_FIRST_OFFSET);</p>
<p>consumer.setConsumerGroup(group);</p>
```

### 设置消费者端口，官方没有该功能。适用端口有安全限制的服务器

`<p>if (port > 0) { consumer.setClientPort(port); }</p>`

### 注册推送事件

`<p>consumer.registerMessageListener(new ChainwayMessageListener());</p>`

### 启动消费者
```
<p>consumer.start();</p>
<p>public class ChainwayMessageListener : MessageListenerConcurrently</p>
<p>{</p>
    <p>public ConsumeConcurrentlyStatus consumeMessage(List l, ConsumeConcurrentlyContext ccc)</p>
    <p>{</p>
    <p>//业务代码</p>
    <p>}</p>
<p>}</p>
```

### 启动生产者
```
<p>DefaultMQProducer producer = new DefaultMQProducer(group);</p>
<p>producer.setNamesrvAddr(nameAddress);</p>
```
### 设置生产者端口，官方没有该功能。适用端口有安全限制的服务器
`<p>if (port > 0) producer.setClientPort(port)</p>`
### 启动生产者
`<p>producer.start();</p>`
### 建议使用jdk1.8
### 建议使用已经封装过的ChainwayMQ
https://github.com/franknew/DataSync

