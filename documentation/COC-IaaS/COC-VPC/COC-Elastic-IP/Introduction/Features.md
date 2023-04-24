# 产品功能

在您使用弹性公网IP产品之前，建议您先阅读合作弹性公网IP相关的[核心概念](Core-Concepts.md)，这里详细介绍了弹性公网IP的创建、资源绑定、资源解绑以及修改带宽等功能。
### 公网服务
  - 为绑定的云资源提供公网访问和被公网访问的能力
### 灵活绑定/解绑
  - 可根据业务需要实时与云主机、负载均衡等云资源绑定或解绑，相关操作请参考[绑定弹性公网IP](../Operation-Guide/Associate-Elastic-IP.md)或[解绑弹性公网IP](../Operation-Guide/Elastic-IP-Management/Disassociate-Elastic-IP.md)
  - 支持云资源实时更换公网IP，在多活容灾场景下，能快速屏蔽故障，例：当云主机出现故障时，可将其绑定的公网IP解绑，然后与备用机绑定，快速恢复业务运转
  
### 资源管理
  - 支持单独购买，在不创建云资源的情况下可单独购买公网IP，相关操作请参考[创建弹性公网IP](../Operation-Guide/Create-Elastic-IP.md)
 
  - 支持单独释放，从云资源解绑后，支持单独删除公网IP，解绑公网IP请参考[解绑弹性公网IP](../Operation-Guide/Disassociate-Elastic-IP.md)，释放公网IP请参考[删除弹性公网IP](../Operation-Guide/Delete-Elastic-IP.md)
  - 支持单独持有，在删除与公网IP绑定的云资源时可以单独保留公网IP。
  - 支持调整带宽，实时生效，具体请参考[修改弹性公网IP带宽](../Operation-Guide/Modify-Elastic-IP.md)

## 相关参考
- [核心概念](Core-Concepts.md)
- [绑定弹性公网IP](../Operation-Guide/Associate-Elastic-IP.md)
- [解绑弹性公网IP](../Operation-Guide/Disassociate-Elastic-IP.md)
