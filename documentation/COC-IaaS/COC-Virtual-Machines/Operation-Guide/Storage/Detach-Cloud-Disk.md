# 卸载云硬盘
## 前提条件
* 卸载系统盘，实例须处于**已停止**状态；
* 卸载数据盘，实例须处于**运行中**或**已停止**状态。

## 操作影响
* 磁盘成功卸载后，Tab页内云硬盘挂载状态将变更为**卸载中**，卸载云盘需要一定时间，还请您耐心等候并刷新页面，卸载成功后挂载状态将变更为“已卸载”，此状态将保留15分钟，处于该状态的云硬盘不占用实例已挂载盘数量，且不影响已卸载磁盘被卸载实例的任何操作和使用。

## 操作步骤

1. 访问[云主机控制台](https://cns-console.jdcloud.com/host/compute/list)，即进入实例列表页面。或访问[京东云控制台](https://console.jdcloud.com)点击顶部导航栏**弹性计算-云主机**进入实例列表页。
2. 选择地域后在实例列表中选择需要卸载云硬盘的实例，点击ID/名称进入详情页。
3. 点击**磁盘Tab**，找到需要卸载云硬盘，点击**卸载**按钮。
![](https://img1.jcloudcs.com/cn/image/vm/detachclouddisk.png)
4. 在弹出的二次确认弹窗中，点击确认。

此外您还可以从云硬盘控制台进行卸载操作，详细步骤请参见[云硬盘侧卸载](http://docs.jdcloud.com/cloud-disk-service/detach-cloud-disk)。


## 相关参考

[云硬盘侧卸载](http://docs.jdcloud.com/cn/cloud-disk-service/detach-cloud-disk)
