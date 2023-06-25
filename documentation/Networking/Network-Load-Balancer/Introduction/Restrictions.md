# 限制说明

您可以快速创建并使用网络负载均衡 NLB，但使用中有部分约束条件需要注意。


| 资源	| 限制	| 例外申请方式 |
| :- | :- | :- |
|单地域下负载均衡实例	|5个	|工单|
|一个负载均衡下的监听器	|20个	|工单|
|一个负载均衡下的后端服务	|20个	|工单|
|一个负载均衡下的虚拟服务器组	|20个|	工单|
|一个虚拟服务器组内的实例	|100个|	工单|

- 当您的访问请求经由 NLB 进行转发时，请勿将访问发起端同时作为 NLB 的后端服务器，否则可能引起流量异常。

## 相关参考

- [产品概述](../Introduction/Product-Overview.md)
- [价格总览](../Pricing/Price-Overview.md)
- [创建实例](../Getting-Started/Create-Instance.md)
- [创建虚拟服务器组](../Operation-Guide/TargetGroup-Management.md)
- [配置侦听策略](../Operation-Guide/Listener-Management.md)
- [管理后端服务与查看服务实例健康状态](../Operation-Guide/Backend-Management.md)
- [查看监控信息](../Operation-Guide/Monitoring.md)
