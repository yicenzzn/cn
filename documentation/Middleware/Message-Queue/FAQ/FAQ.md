# 常见问题

## 功能类
**Q：消息队列 JCQ 支持外网访问吗？**

A：华北-北京地域支持HTTPS的方式公网访问。

**Q：目前消息队列 JCQ 支持哪些协议？**

A：京东云消息队列 JCQ支持HTTP、HTTPS、TCP协议。

**Q：JCQ 消息能服务器保存多长时间？**

A：存储的消息最多保存 3 天，超过 3 天未消费的消息会被删除。

**Q：每个用户Topic支持的最大TPS限额是多少？**

A：目前每个Topic支持的TPS最大限额为5000，如不能满足您的业务需求，请联系客服。

**Q：常见返回错误码**

A：使用http/https方式拉取消息，[常见错误码](../Operation-Guide/API-Reference/Call-Method/Response-Result.md)。

## 使用问题

**Q：用户拉取不到消息怎么办？**

A：请从以下问题中排查：

1. topic中没有消息，或者发送方没有发送消息。

2. 如果用户消费时带了tag，则会开启tag过滤规则，过滤没有此tag的消息。消费时代码里不要带tag，或者填写正确的tag，请参考[消费分类](../Best-Practice/Message-Classification.md).

3. 如果用户以重启进程方式拉取，每次拉取一条消息，都会拉同一个partition，若此partition无消息则会一直拉不到。建议将拉取逻辑放到循环里，在进程内循环拉取。循环拉取过程中，会出现一会儿能拉到数据，一会儿拉不到，属于正常情况。

**Q：用户订阅不上消息怎么办？**

A：用户未授予合适的权限导致，需要参考[主主授权](https://docs.jdcloud.com/cn/message-queue/main-main-authorization)对被授权用户进行授权。

**Q：拉消息，返回{"code":500,"message":"FAILED","status":"FAILED"}怎么办？**

A：原因是拉请求并发到达，只有一个拉取成功，另外一个由于没有待拉取的消息返回的错误，可以通过修改Broker的返回值解决。

**Q：报错Topic不存在，是什么原因？**

A:1.确认AK/SK填写正确。AK/SK 请从控制台”账户管理“--”AccessKey管理“获取；

  2.确认代码中填写的是Topic名称，而不是Topic id。Topic名称请从控制台”消息队列JCQ“--对应Topic名称--“Topic”详情--“基本信息”获取；
  
  3.确认代码中填写的接入点（访问信息）正确，接入点请从控制台”消息队列JCQ“--对应Topic名称--“Topic”详情--“访问信息”获取。
  
**Q：消费日志中报错 subscription not exist ，订阅不存在，是什么原因？**

A：1.Topic下没有此订阅；

   2.订阅的创建者是子账号A，但是代码中使用的AK/SK，不是该子账号的AK/SK；   建议消费请使用使用与创建订阅相同账号的AK/SK。

**Q：使用sync方法单条/批量发送消息，但日志中出现ASYNC_REQUEST，是什么原因？**

A：日志中ASYNC_REQUEST发送的是trace topic消息轨迹，trace topic是采用异步发送的。


**Q：SDK报错连接超时``` 
exception:[com.jcloud.jcq.communication.exception.CommunicationException: ChannelFuture has been completed, but the channel localAddress: , remoteAddress: is still not active!]```**


A：该报错是因为网络不通，通常有如下几种原因:

1. 没有在和topic同地域的云VPC环境下连接jcq；

2. 在同地域云VPC环境下，但是云主机的安全组、子网关联的ACL没有放行相应网段。

**Q：SDK报错```
The heart beat service for the channel localAddress: 10.0.0.3:44452, remoteAddress: 100.72.13.171:2888 has already been shutdown```**

A：该报错是客户端重新拉取路由，属于正常情况。

**Q：报错订阅不存在**

A：消费日志中报错`subscription not exist`，通常有以下两种原因:

1. topic下没有此订阅

2. 订阅的创建者是子账号A，但是代码中使用的ak/sk，不是该子账号的ak/sk
    建议是哪个账号创建的订阅，就用哪个账号的ak/sk来进行消费。

**Q：如何判断消费签名是否正确**

A：使用工具[签名算法](../Operation-Guide/API-Reference/Call-Method/Signature-Algorithm.md)。该工具会返回签名计算过程中排序后的key、signSource和最终的签名。



**Q: 如何判断消息是否进入Topic**

A：请参考以下场景：

1. 联系消息发送方，确认消息是否成功发送，消息成功发送会返回messageId，每一条消息都有独立的messageId，可以和消息发送方进行确认。

2. 如果是开普勒、云交易、宙斯的用户，可以根据订单号，查询消息是否进入topic，步骤如下：

   (1) 登录京东云控制台，消息队列JCQ - 消息查询。如果用的是云鼎，请登录云鼎控制台

   (2) 选择地域、topic、**Business ID**，**Business ID为订单号**，点击查询。如果查询不到消息，请联系下业务方确认消息是否正常发送。
 

3. 只能查询到消息生命周期3天以内的消息，3天之前的消息，请联系业务方进行确认。

4. 消息查询更详细使用方式参考：[查询消息](../Operation-Guide/Message-Management/Query-Message.md)


