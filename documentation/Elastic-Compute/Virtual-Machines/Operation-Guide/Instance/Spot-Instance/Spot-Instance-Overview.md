# 抢占式实例产品说明

抢占式实例指的是云主机的一种计费模式，特点是系统会随时自动回收这些实例，但相对于按配置计费实例价格有一定的折扣。

抢占式实例的使用和按配置计费的云主机实例基本一致。

抢占式实例目前正在邀测阶段，且暂不支持华东-宿迁地域

## 当前价格与系统回收策略

* **价格**：当前阶段抢占式实例将以同规格按配置计费实例的固定折扣价出售，不同区域不同规格的折扣不同，最低1折。（如果按配置计费的规格原价变动，抢占式实例的折扣后金额也会随之变动）
* **折扣范围**：仅涉及云主机 CPU 和内存部分，其他部分如系统盘、数据盘、带宽、收费镜像等云主机关联收费项均不受抢占式实例的折扣影响。
* **系统中断机制**：当市场供需关系变化及库存不足时，系统会从已分配的抢占式实例里随机回收，实例将会被释放（如果云硬盘和弹性公网IP购买时勾选了随实例释放，这些资源也将会一并释放）。中断前将会提前5分钟进行通知，可通过[实例元数据](https://docs.jdcloud.com/cn/virtual-machines/instance-metadata)进行感知。 

## 抢占式实例和按配置计费的的区别

| **共同点**                                                                                        | **区别**                                                     |
| ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| 均为后付费模式，不需要提前支付费用。<br/>可随时开通/删除云主机，按实例的实际使用量付费。<br/>计费时间粒度精确到秒，每小时整点进行一次结算。<br/>当前抢占式实例与包年包月/按配置云主机共用配额。 | **价格**：抢占式实例最低价格是同规格按配置计费模式的1折。<br/>**优惠限制**：抢占式实例价格不予其他任何优惠、折扣叠加，且不适用实例抵扣券；<br/>**中断机制**：按配置计费的生命周期由用户控制，抢占式实例会被系统中断。<br/>**使用限制**：<br/>不支持续费，即转换为包年/包月实例或按配置实例；<br/>不支持添加购物车、停机不计费功能；<br/>不支持重置系统、调整配置；调整高可用组时，不支持选择强制均衡；<br/>不支持制定宿主机创建、在高可用组内创建； |

## 不适用场景

因系统中断机制，您并不能完全掌握实例的生命周期，建议避免在抢占式实例上运行对稳定性要求较高的业务，例如：

* 不能中断的任务
* 数据库服务等有状态应用
* 未采用负载均衡的在线服务
* 大于10小时的长时间计算作业
* 分布式架构里的核心主控制节点

## 适用场景

* 图像渲染
* 实时分析
* 大数据分析
* 科学计算
* 测试业务

## 最佳实践建议

* 避免在抢占式实例上运行不能中断的任务，而运行对错误容忍度高和使用灵活的应用；
* 把需要比较长时间的大型工作任务拆分成大量小的、异步的短时间工作任务，减少被中断的可能性；
* 在晚上或周末这种非高峰时段运行大型抢占式虚拟机集群；
* 通过负载均衡在保证在线和网站服务的稳定性；
* 通过实例元数据感知即将中断的实例，主动做好备份和迁移； 


## 常见问题

**实例为什么会被系统中断？**

抢占式实例的特点就是售价相对低，但当市场供需关系变化及库存不足时，系统会从已分配的抢占式实例里随机回收，实例数据不会保留。

**能否进行续费、转包年包月和按配置计费方式？**

不支持。

**如何感知实例将要被中断？**

通过实例元数据可提前5分钟感知即将中断的实例，主动做好备份和迁移

**抢占式实例如何统计计费时长？**

从您创建抢占式实例开始，到该实例被释放的时刻结束（用户主动删除或系统中断），精度精确到秒。

**怎么查看竞价实例消费明细？**

与按配置计费类型实例一样，抢占式实例属于后付费服务。

**抢占式的配额限制和包年包月或者按配置计费共用吗？**

共用。
