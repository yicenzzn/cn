# 地域及可用区

### 地域

地域（Region）是指物理数据中心所在的地域位置，京东云支持四个地域，分别是华北-北京、华南-广州、华东-上海、华东-宿迁。
同一个地域共享计算、网络、存储等资源，不同地域间资源完全隔离，保证各个地域间业务的稳定性和地域间的容错性。

### 可用区

可用区（Availability Zone）是单一地域内分别位于不同地点的数据中心集群，具有独立的网络、供电、散热和实体安全保障，并且通过云服务商的内部低延迟、高带宽网络相互连接。应用和服务的多可用区部署是实现业务高可用的重要方式。

 中心可用区：Availability Zone简称AZ。单个地域下可以包含多个AZ，不同AZ之间实现资源隔离，保障资源的高可用性。同地域下的AZ通常采用低延迟与高带宽的线路进行互联。AZ代表是中心可用区。
 
 边缘可用区：Tethered Edge Zone简称EZ。京东云外联边缘可用区是由京东云设置并管理的中小型边缘数据中心。京东云在华南-广州地域支持边缘可用区，支持在边缘可用区使用部分资源。

|地域|地域ID|可用区|
|----|-----|------|
|华北-北京| cn-north-1|标准可用区|
|华东-上海|cn-east-2|标准可用区</br>边缘可用区|
|华南-广州|cn-south-1|标准可用区|
|华东-宿迁|cn-east-1|标准可用区|

### 资源说明

中心可用区和边缘可用区支持的产品略有不同。

中心可用区：全量产品；

边缘可用区：子网、公网IP、ACL、安全组、路由表、本地存储云主机、虚机镜像和SSH密钥等，暂不支持NAT网关、LB、BGW、VPN和原生容器等产品。

## 相关参考

- [VPC产品概述](Product-Overview.md)
- [配置VPC](../Operation-Guide/VPC-Configuration.md)
- [使用限制](Restrictions.md)
- [常见问题](../FAQ/FAQ.md)

