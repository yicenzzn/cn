# 使用限制

本文将详细介绍公网IP相关的使用限制，具体分为以下几个方面：
- [创建公网IP](restrictions#user-content-1)
- [绑定资源](restrictions#user-content-2)
- [调整带宽](restrictions#user-content-3)
- [删除公网IP](restrictions#user-content-5)

### 创建公网IP
<div id="user-content-1"></div>

- 为避免业务正常运转，创建后付费计费类型的公网IP，账户余额需不少于50元，预付费无余额门槛限制；
- 目前每个京东云账户支持各个地域（region）最多申请10个弹性公网IP，如需更多配额请[提交工单](https://ticket.jdcloud.com/applyorder/form?cateId=1135&questionId=1155)申请；
- 申请弹性公网IP时设置的带宽为出方向带宽，即从京东云公网IP出去访问Internet的带宽上限，购买带宽上限为10Mbps以内的公网IP，出方向带宽为实际购买的带宽上限，入方向带宽均为10Mbps。购买带宽上限超过10Mbps的公网IP，出入方向带宽上限一致，均为实际购买的带宽上限；


### 绑定资源
<div id="user-content-2"></div>

- 弹性公网IP仅可与同地域资源（如合作云主机）进行绑定。
- 弹性公网IP同时只能与一个云资源绑定；
- 单个弹性公网IP可以在一天之内进行多次绑定/解绑操作。如果需要为已绑定弹性公网IP的资源更换IP，必须先将资源与当前的IP解绑，之后再进行新IP的绑定。

### 调整带宽
<div id="user-content-3"></div>

- 合作弹性公网IP均支持调整带宽上限。其中包年包月计费模式下的弹性公网IP，提升带宽时，到期时间不变，需支付带宽差价，不支持降低带宽。


### 删除公网IP
<div id="user-content-5"></div>

- 不支持删除处于绑定状态的合作弹性公网IP，如需删除IP，需先解绑资源；
- 不支持删除包年包月的资源。

## 相关参考
- [创建公网IP](../Operation-Guide/Create-Elastic-IP.md)
- [修改带宽](../Operation-Guide/Modify-Elastic-IP.md)
- [删除公网IP](../Operation-Guide/Delete-Elastic-IP.md)
- [绑定资源](../Operation-Guide/Associate-Elastic-IP.md)
