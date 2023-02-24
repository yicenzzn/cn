# 裸金属实例概述

裸金属实例是基于京东云新一代自研虚拟化技术架构**京刚**推出的云主机实例类型，同时兼顾物理机性能及虚拟机灵活性。与上一代虚拟化技术架构相比，新一代虚拟化技术架构不再有任何虚拟化开销，提供物理级别的资源隔离，支持嵌套虚拟化，您的业务可直接访问裸金属实例上的计算资源，保障您的业务安全。
 
## 产品特点
*  极致性能：具备与物理机无差别的极致性能，提供网络和存储的硬件加速能力，将原有虚拟化网络和存储协议栈负载从物理宿主机上卸载至特定硬件上，无额外虚拟化损耗，并且支持嵌套虚拟化
*  安全隔离：提供硬件级别隔离，资源独占，无需与其他云上用户争抢宿主机资源
*  分钟级交付：无需提前采购及人工介入，分钟级交付一台裸金属实例，保证及时响应业务扩容需求
*  无缝集成云产品：完全兼容VPC、云硬盘、云数据库、云监控等云产品，提供完整的云上解决方案
*  一致性管理体验：支持控制台及SDK/OpenAPI/CLI操作，与普通实例体验一致

## 与普通实例及物理服务器对比
<table>
   <tr>
      <td colspan="2">功能</td>
      <td >普通实例</td>
      <td >裸金属实例</td>
      <td >物理服务器</td>
	</tr>
	<tr>
      <td rowspan="2">计算/内存</td>
      <td >无性能损失</td>
      <td >N</td>
      <td >Y</td>
      <td >Y</td>
	</tr>
	<tr>
      <td >无资源争抢</td>
      <td >N</td>
      <td >Y</td>
      <td >Y</td>
   	</tr>
  	<tr>
      <td rowspan="3">存储</td>
      <td >云盘系统盘/数据盘</td>
      <td >Y</td>
      <td >Y</td>
      <td >N</td>
	</tr>
	<tr>
      <td >云盘快照及恢复</td>
      <td >Y</td>
      <td >Y</td>
      <td >N</td>
   	</tr>
	<tr>
      <td >整机镜像</td>
      <td >Y</td>
      <td >Y</td>
      <td >N</td>
   	</tr>
  	<tr>
      <td rowspan="3">网络</td>
      <td >VPC互通</td>
      <td >Y</td>
      <td >Y</td>
      <td >N</td>
	</tr>
	<tr>
      <td >安全组</td>
      <td >Y</td>
      <td >Y</td>
      <td >N</td>
   	</tr>
	<tr>
      <td >ACL</td>
      <td >Y</td>
      <td >Y</td>
      <td >N</td>
   	</tr>
  	<tr>
      <td rowspan="5">运维管理</td>
      <td >SDK/OpenAPI/CLI</td>
      <td >Y</td>
      <td >Y</td>
      <td >N</td>
	</tr>
  	<tr>
      <td >控制台</td>
      <td >Y</td>
      <td >Y</td>
      <td >N</td>
	</tr>
	<tr>
      <td >VNC</td>
      <td >Y</td>
      <td >N</td>
      <td >N</td>
	</tr>
	<tr>
      <td >远程连接</td>
      <td >Y</td>
      <td >Y</td>
      <td >Y</td>
	</tr>
	<tr>
      <td >分钟级交付</td>
      <td >Y</td>
      <td >Y</td>
      <td >Y</td>
	</tr>
  	<tr>
      <td >虚拟化</td>
      <td >嵌套虚拟化</td>
      <td >N</td>
      <td >Y</td>
      <td >Y</td>
	</tr>
</table>


## 使用限制

* 	仅支持京东云在华北-北京地域2020年1月2日及之后提供的以下官方镜像：CentOS 7.2、CentOS 7.4及CentOS 7.6，以及基于上述官方镜像创建的实例而制作的私有镜像，若您需要将已有私有镜像转换为支持创建裸金属实例的镜像，请参考 [创建裸金属实例](Create-BM-Instance.md)
*  	仅支持云硬盘作系统盘
* 	部分规格不支持配置多网卡，仅支持单网卡（主网卡），详见 [实例规格类型](https://docs.jdcloud.com/cn/virtual-machines/instance-type-family)
*  	部分规格不支持热插拔云硬盘，需要关机挂载/卸载云硬盘
*  	不支持挂载加密盘及多点挂载盘
*	不支持调整配置
* 	不支持控制台VNC访问，可以通过远程登录服务WebTerminal实现控制台登录

