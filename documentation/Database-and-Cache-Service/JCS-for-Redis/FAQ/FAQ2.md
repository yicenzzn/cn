# 账号与安全

**Q：当把实例从密码访问改为免密访问模式后，使用原用户名密码访问为何会报错？**

A：可在“参数配置”中，修改@no-auth-ignore 参数值为 yes。当重新改回为密码访问后，再将该参数值恢复为默认值no。

**Q：redis由免密设置为密码认证后，对客户端的影响？**

A：修改密码的过程会对客户端产生影响，建议尽量在业务低峰期操作。与redis建立的旧链接不受影响，与redis建立的新连接会受到影响。

**Q：如何平滑修改密码**

A：如果您需要进行平滑修改密码，建议可参考如下步骤进行：

Step1：在实例详情页的“参数配置”tab页中，修改@no-auth-ignore 参数值为 yes。

Step2：将服务端实例修改为“免密访问”模式。

Step3：在client客户端，上线新的密码。

Step4：将服务端实例开启密码访问，并修改为新密码。

Step5：恢复@no-auth-ignore 参数值为默认值no。

**Q：创建完Redis后，默认的白名单就会设置为0.0.0.0/0，这个有什么策略可以控制嘛？**

A：0.0.0.0/0 是默认值，表示这个vpc内所有的地址都可以连接这个集群，可以调用设置白名单接口修改这个值。请参考以下API：

| 接口 | 说明  |  
|:--   |:-- |
| [describeIpWhiteList](http://docs.jdcloud.com/cn/jcs-for-redis/api/describeipwhitelist?content=API)    |  表示获取Redis实例的IP白名单（只有白名单内的IP、网络才能访问该实例）  |
| [modifyIpWhiteList](https://docs.jdcloud.com/cn/jcs-for-redis/api/modifyipwhitelist?content=API)    |  修改Redis实例的IP白名单  |


