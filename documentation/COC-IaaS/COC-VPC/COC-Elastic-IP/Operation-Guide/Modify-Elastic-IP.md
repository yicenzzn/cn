# 修改弹性公网IP带宽

京东云支持合作弹性公网IP实时进行升配与降配操作，本文将详细介绍如何修改公网IP的带宽上限。

## 操作场景

- 根据业务需要实时调整公网IP带宽上限，如当前带宽上限不能满足业务需求，提升带宽上限，如当前业务量降低，可降低公网IP的带宽上限。

## 前提条件及限制

- 确保您已经创建一个合作弹性公网IP；
- 包年包月计费类型，升配需要补带宽差价，不支持降配；

## 操作步骤

步骤1：登录京东云控制台，进入控制台导航页面；

步骤2：在控制台左侧导航栏，选择网络-【合作私有网络】-【合作弹性公网IP】，进入弹性公网IP列表页；

步骤3：在弹性公网IP列表页，定位到需要调整带宽的弹性公网IP，在操作列点击【更多】选择【修改带宽】按键，进入修改带宽弹窗；

> 注：弹性公网IP详情页右上角快捷操作菜单同时提供绑定资源按键，功能与列表页按键保持一致。

步骤4：在修改带宽弹窗，调整滑块或输入带宽值，指定需要修改的带宽；

> 注：带宽上限值仅支持带宽范围内的正整数，带宽范围为当前带宽值~200Mbps。


步骤5：在修改带宽弹窗，点击【确定】按键，进入订单确认页；


步骤6：在订单确认页，点击立即开通，完成支付并返回弹性公网IP列表页，查看带宽修改情况。

## 相关参考

- [使用限制](../Introduction/Restrictions.md)
- [创建公网IP](Create-Elastic-IP.md)
- [常见问题](../FAQ/FAQ.md)
