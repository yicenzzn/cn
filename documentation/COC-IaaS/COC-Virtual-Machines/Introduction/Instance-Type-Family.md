# 实例规格类型

实例是京东云为您业务提供计算服务的最小单位，不同实例通过其规格类型及具体规格来标识相应的计算、内存、存储及网络能力。同时，您创建实例时指定的实例类型决定了实例的硬件配置，您可基于需要部署运行的应用类型及规模选择适当的实例规格类型及具体规格。

以下为当前京东云在售的实例规格类型信息，不同地域可售卖实例类型及规格不完全相同，请以实例创建页面所显示为准。具体在售实例规格类型根据不同应用场景可以分为：

#### x86规格
* 通用型：[通用标准型](Instance-Type-Family#user-content-1)
* 计算优化型：[计算优化标准型](Instance-Type-Family#user-content-2)
* 内存优化型：[内存优化标准型](Instance-Type-Family#user-content-3)、[内存优化增强型](Instance-Type-Family#user-content-4)
* 突发性能型：[突发性能型](Instance-Type-Family#user-content-5)
* 高频计算型：[高频计算通用型](Instance-Type-Family#user-content-6)、[高频计算计算型](Instance-Type-Family#user-content-7)
* 存储优化型：[存储优化IO型](Instance-Type-Family#user-content-8)、[存储优化大数据型](Instance-Type-Family#user-content-9)
## x86规格：
## 通用型
通用型当前提供通用共享型及通用标准型，为您提供均衡的计算及内存资源，可满足大部分业务场景下的需求。其中通用标准型中每一个vCPU都对应一个处理器的超线程核，其vCPU与内存比为1:4。

### 通用标准型

<div id="user-content-1"></div>

**规格类型特点:**

* vCPU与内存比为1:4（g.n1.xlarge_m规格除外）
* 处理器：
	* 第三代：2.6 GHz主频的Intel Xeon Platinum 8338C（Icelake）处理器 或 2.6 GHz主频的Intel Xeon Gold 6267（Cascade Lake）处理器  
	* 第二代：
	  * 2.6 GHz主频的Intel Xeon Gold 6267（Cascade Lake）处理器 或 2.4 GHz主频的Intel Xeon Gold 6148（Skylake）处理器
	  * 2.6 GHz主频的AMD EPYC ROME 处理器
* 支持以下类型云硬盘：
	* 第二代通用型SSD云盘
	* 性能型SSD云盘
	* 增强型SSD云盘
* 镜像使用限制：
	* 3代及以上Intel系列
* 适用场景：
	* 各种类型和规模的企业级应用
	* 中小型数据系统、缓存、搜索集群
	* 数据分析和计算
	* 计算集群、依赖内存的数据处理

**实例规格**

第三代

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|g.n3.medium|1|4|2|1
|g.n3.large|2|8|2|2
|g.n3.xlarge|4|16|4|4
|g.n3.2xlarge|8|32|4|4
|g.n3.3xlarge|12|48|8|4
|g.n3.4xlarge|16|64|8|4
|g.n3.6xlarge|24|96|8|4
|g.n3.8xlarge|32|128|8|4
|g.n3.12xlarge|48|192|8|4
|g.n3.16xlarge|64|256|8|4

第二代

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|g.n2.medium|1|4|2|1
|g.n2.large|2|8|2|2
|g.n2.xlarge|4|16|4|4
|g.n2.2xlarge|8|32|4|4
|g.n2.4xlarge|16|64|8|4


### 计算优化标准型
计算优化标准型可满足每一个vCPU都对应一个Intel Xeon处理器的超线程核，为您提供高性能的计算资源。

<div id="user-content-2"></div>

**规格类型特点：**

* vCPU与内存比约为1:2
* 处理器：
	* 第四代：2.6 GHz主频的Intel Xeon Platinum 8338C（Icelake）处理器，基于京刚架构将虚拟化和管理开销卸载至自研专用硬件，大幅提升存储网络性能
	* 第三代：2.6 GHz主频的Intel Xeon Platinum 8338C（Icelake）处理器 或 2.6 GHz主频的Intel Xeon Gold 6267（Cascade Lake）处理器
	* 第二代：
	  * 2.6 GHz主频的Intel Xeon Gold 6267（Cascade Lake）处理器 或 2.4 GHz主频的Intel Xeon Gold 6148 （Skylake）处理器
	  * 2.6 GHz主频的AMD EPYC ROME 处理器
	* 第一代：2.1 GHz主频的Intel Xeon E5-2683 v4（Broadwell）处理器
* 支持以下类型云硬盘：
	* 第二代通用型SSD云盘
	* 性能型SSD云盘
	* 增强型SSD云盘
* 适用场景：
	* 批处理工作负载
	* Web前端服务器
	* 大型多人在线游戏（MMO）前端
	* 数据分析、批量计算、视频编码
	* 高性能科学和工程应用

**实例规格**

第三代

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|c.n3.medium|1|2|2|2
|c.n3.large|2|4|2|2
|c.n3.xlarge|4|8|4|4
|c.n3.2xlarge|8|16|4|4
|c.n3.3xlarge|12|24|8|4
|c.n3.4xlarge|16|32|8|4
|c.n3.6xlarge|24|48|8|4
|c.n3.8xlarge|32|64|8|4
|c.n3.12xlarge|48|96|8|4
|c.n3.16xlarge|64|128|8|4

第二代

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|c.n2.large|2|4|2|2
|c.n2.xlarge|4|8|4|4
|c.n2.2xlarge|8|16|4|4
|c.n2.4xlarge|16|32|8|4
|c.n2.8xlarge|32|64|8|4
|c.n2.16xlarge|64|128|8|4
|c.n2.18xlarge	|72|144|8|4

## 内存优化型
内存优化型当前提供内存优化标准型和内存优化增强型，适用于存在大量内存操作、查找和计算的应用。每一个vCPU都对应一个Intel Xeon处理器的超线程核。

### 内存优化标准型

<div id="user-content-3"></div>

**规格类型特点：**

* vCPU与内存比约为1:8
* 处理器:
	* 第三代：2.6 GHz主频的Intel Xeon Platinum 8338C（Icelake）处理器 或 2.6 GHz主频的Intel Xeon Gold 6267（Cascade Lake）处理器 
	* 第二代：
	  * 2.6 GHz主频的Intel Xeon Gold 6267（Cascade Lake）处理器 或 2.4 GHz主频的Intel Xeon Gold 6148 （Skylake）处理器
	  * 2.6 GHz主频的AMD EPYC ROME 处理器
* 支持以下类型云硬盘：
	* 第二代通用型SSD云盘
	* 性能型SSD云盘
	* 增强型SSD云盘
* 镜像使用限制：
	* 3代及以上Intel系列
* 适用场景：
	* 高性能数据库、内存数据库
	* 数据分析与挖掘、分布式内存缓存
	* Hadoop、Spark群集以及其他企业大内存需求应用

**实例规格**

第三代

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|m.n3.large|2|16|2|2
|m.n3.xlarge|4|32|4|4
|m.n3.2xlarge|8|64|4|4
|m.n3.3xlarge|12|96|8|4
|m.n3.4xlarge|16|128|8|4
|m.n3.6xlarge|24|192|8|4
|m.n3.8xlarge|32|256|8|4

第二代

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|m.n2.large|2|16|2|2
|m.n2.xlarge|4|32|4|4
|m.n2.2xlarge|8|64|4|4
|m.n2.3xlarge|12|96|8|4
|m.n2.4xlarge|16|128|8|4
|m.n2.6xlarge|24|192|8|4
|m.n2.8xlarge|32|256|8|4
|m.n2.15xlarge|60|512|8|4


### 内存优化增强型

<div id="user-content-4"></div>

**规格类型特点：**

* vCPU与内存比约为1:12
* 处理器：
	* 2.6 GHz主频的Intel Xeon Gold（Icelake）处理器
* 支持以下类型云硬盘：
	* 第二代通用型SSD云盘
	* 性能型SSD云盘
	* 增强型SSD云盘
* 系统盘使用限制：
	* 仅支持云硬盘系统盘
* 适用场景：
	* 高性能数据库、内存数据库，如Redis
	* 数据分析与挖掘、分布式内存缓存
	* Hadoop、Spark群集以及其他企业大内存需求应用

**实例规格**

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
|:---|:---|:---|:---|:---
|m.e2.7xlarge|28|348|4|4
|m.e2.14xlarge|56|696|4|4
|m.e2.26xlarge|104|1466|4|4
|m.e2.52xlarge|208|2932|8|4



## 突发性能型

突发性能型实例是一种通过积分机制约束CPU使用率的实例规格，适用于平时CPU使用率较低，偶发使用率突增的入门级或轻量级计算场景。突发型实例提供了在一定时间区间内动态分配计算力的能力，闲时积累忙时消耗，相对于普通实例规格，更为经济。[突发性能型规格介绍](https://docs.jdcloud.com/virtual-machines/Burst-Instance-Overview)

<div id="user-content-5"></div>

**规格类型特点：**

* 基于规格和基准性能提供算力，允许一定时间范围内算力的累积，通过积分体现实例算力的消耗和积累情况。
* 处理器：
    * 第二代：2.6 GHz主频的Intel Xeon Gold 6267（Cascade Lake）处理器  
* 支持以下类型云硬盘：
	* 第二代通用型SSD云盘
	* 性能型SSD云盘
	* 增强型SSD云盘
* 系统盘使用限制：
    * 仅支持云硬盘系统盘
* 适用场景：
    * 微服务、轻负载应用
    * 代码库、Web服务、开发测试环境

**实例规格**

第二代

实例规格|vCPU（核）|内存（GB）|基准性能 |网卡数|单网卡队列数 |每小时可获积分 | 积分余额上限
|:---|:---|:---|:--- |:---|:---|:---|:---
|t.e2.large|2|2|20% |2|1 | 24 |576
|t.c2.small|1|2|10% |2|1 | 6 |144
|t.c2.large|2|4|20% |2|1 | 24 |576
|t.g2.large|2|8|30% |2|1 | 36|864
|t.e2.xlarge|4|4|30% |2|1 | 72 |1728
|t.e2.2xlarge|8|8|30% |2|1 | 144| 3456
|t.e2.4xlarge|16|16|15% |2|1 | 144 |3456
|t.c2.xlarge|4|8|30% |2|1 | 72 |1728
|t.g2.xlarge|4|16|40% |2|1| 96 | 2304
|t.c2.2xlarge|8|16|30% |2|1 | 144| 3456
|t.c2.4xlarge|16|32|15% |2|1 | 144| 3456
|t.g2.2xlarge|8|32|40% |2|1| 192|4608


## 高频计算型

高频计算型当前提供高频计算通用型，为您提供高性能的计算资源。每一个vCPU都对应一个Intel Xeon处理器的超线程核。

### 高频计算通用型

<div id="user-content-6"></div>

**规格类型特点：**

* vCPU与内存比为1:4
* 计算性能稳定，处理器主频高
* 处理器：
	* 第二代：3.2 GHz主频的Intel Xeon Gold 6146（Skylake）处理器
	* 第一代：3.2 GHz主频的Intel Xeon E5-2667 v4（Broadwell）处理器
* 支持以下类型云硬盘：
	* 第二代通用型SSD云盘
	* 性能型SSD云盘
	* 增强型SSD云盘
* 适用场景：
	* 高性能Web前端服务器
	* 高性能科学和工程应用
	* MMO游戏、视频编码

**实例规格**

第三代：

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|h.g3.large|2|8|2|2
|h.g3.xlarge|4|16|4|4
|h.g3.2xlarge|8|32|4|4
|h.g3.3xlarge|12|48|4|4
|h.g3.4xlarge|16|64|8|4
|h.g3.6xlarge|24|96|8|4
|h.g3.8xlarge|32|128|8|4
|h.g3.12xlarge|48|192|8|4
|h.g3.16xlarge|64|256|8|4
|h.g3.metal|88|384|8|4

第二代：

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|h.g2.large|2|8|2|2
|h.g2.xlarge|4|16|4|4
|h.g2.2xlarge|8|32|4|4
|h.g2.3xlarge|12|48|4|4
|h.g2.4xlarge|16|64|8|4
|h.g2.6xlarge|24|96|8|4
|h.g2.8xlarge|32|128|8|4

### 高频计算计算型

<div id="user-content-7"></div>

**规格类型特点：**

* vCPU与内存比为1:4
* 计算性能稳定，处理器主频高
* 处理器：
	* 第二代：3.2 GHz主频的Intel Xeon Gold 6146（Skylake）处理器
	* 第一代：3.2 GHz主频的Intel Xeon E5-2667 v4（Broadwell）处理器
* 支持以下类型云硬盘：
	* 第二代通用型SSD云盘
	* 性能型SSD云盘
	* 增强型SSD云盘
* 适用场景：
	* 高性能Web前端服务器
	* 高性能科学和工程应用
	* MMO游戏、视频编码
	
**实例规格**

第三代：

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|h.c3.large|2|4|2|2
|h.c3.xlarge|4|8|4|4
|h.c3.2xlarge|8|16|4|4
|h.c3.3xlarge|12|24|4|4
|h.c3.4xlarge|16|32|8|4
|h.c3.6xlarge|24|48|8|4
|h.c3.8xlarge|32|64|8|4
|h.c3.12xlarge|48|96|8|4
|h.c3.16xlarge|64|128|8|4

第二代： 

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|h.c2.large|2|4|2|2
|h.c2.xlarge|4|8|4|4
|h.c2.2xlarge|8|16|4|4
|h.c2.3xlarge|12|24|4|4
|h.c2.4xlarge|16|32|8|4
|h.c2.6xlarge|24|48|8|4
|h.c2.8xlarge|32|64|8|4
|h.c2.15xlarge|60|128|8|4

## 存储优化型

存储优化型当前提供存储优化IO型及存储优化大数据型，为您提供高性能的本地存储资源。每一个vCPU都对应一个Intel Xeon处理器的超线程核。

### 存储优化IO型

<div id="user-content-8"></div>

**规格类型特点：**

* vCPU与内存比为1:4
* 提供低时延高IO的本地存储
* 处理器：
	* 第三代：第三代：2.6 GHz主频的Intel Xeon Platinum 8338C（Icelake）处理器 或 2.6 GHz主频的Intel Xeon Gold 6267（Cascade Lake）处理器
	* 第二代：2.4 GHz主频的Intel Xeon Gold 6148（Skylake）处理器
	
* 支持本地数据盘（临时存储），并支持以下类型云硬盘。请注意 **本地数据盘为临时存储盘，有丢失数据的风险（比如发生迁移或宿主机宕机等情况），不适用于应用层没有数据冗余架构的使用场景， 建议您使用云硬盘存储重要数据。** 
	* 第二代通用型SSD云盘
	* 性能型SSD云盘
	* 增强型SSD云盘
* 适用场景：
	* 高性能关系数据库
	* NoSQL数据库
	* ElasticSearch等场景

**实例规格**


第三代：

实例规格|vCPU（核）|内存（GiB）|本地数据盘（临时存储 GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---|:---
|s.i3.large|2|8|2 x 50 NVMe SSD|4|4
|s.i3.xlarge|4|16|2 x 100 NVMe SSD|4|4
|s.i3.2xlarge|8|32|2 x 200 NVMe SSD|4|4
|s.i3.4xlarge|16|64|2 x 400 NVMe SSD|8|4
|s.i3.8xlarge|32|128|2 x 800 NVMe SSD|8|4


第二代：

实例规格|vCPU（核）|内存（GiB）|本地数据盘（临时存储 GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---|:---
|s.i2.2xlarge|8|64|1 x 1600 NVMe SSD|4|4
|s.i2.4xlarge|16|128|2 x 1600 NVMe SSD|8|4
|s.i2.8xlarge|32|256|4 x 1600 NVMe SSD|8|4
|s.i2.12xlarge|48|384|6 x 1600 NVMe SSD|8|4
|s.i3.15xlarge|60|512|7 x 1600 NVMe SSD|8|4
|s.i3.16xlarge|64|512|8 x 1600 NVMe SSD|8|4

### 存储优化大数据型

<div id="user-content-9"></div>

**规格类型特点：**

* vCPU与内存比约为1:4
* 提供低时延高容量及高吞吐的本地存储
* 处理器：
	* 第二代：2.1 GHz主频的Intel Xeon Silver 4116（Skylake）处理器
	* 第一代：2.2 GHz主频的Intel Xeon E5-2650 v4（Broadwell）处理器
* 支持本地数据盘（临时存储），并支持以下类型云硬盘。请注意 **本地数据盘为临时存储盘，有丢失数据的风险（比如发生迁移或宿主机宕机等情况），不适用于应用层没有数据冗余架构的使用场景， 建议您使用云硬盘存储重要数据。** 
	* 第二代通用型SSD云盘
	* 性能型SSD云盘
	* 增强型SSD云盘
* 适用场景：
	* Hadoop MapReduce、HDFS、Hive、HBase
	* 其他海量数据存储区及计算的业务场景

**实例规格**

第二代：

实例规格|vCPU（核）|内存（GiB）|本地数据盘（临时存储 GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---|:---
|s.d2.xlarge|4|32|2 x 1675 NVMe SSD|4|4
|s.d2.2xlarge|8|64|4 x 1675 NVMe SSD|4|4
|s.d2.4xlarge|16|128|8 x 1675 NVMe SSD|8|4
|s.d2.6xlarge|24|192|12 x 1675 NVMe SSD|8|4
|s.d2.8xlarge|32|256|16 x 1675 NVMe SSD|8|4
|s.d2.12xlarge|48|384|24 x 1675 NVMe SSD|8|4

第一代：

实例规格|vCPU（核）|内存（GiB）|本地数据盘（临时存储 GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---|:---
|s.d2.xlarge|4|32|2 x 1675 SAS HDD|4|4
|s.d2.2xlarge|8|64|4 x 1675 SAS HDD|4|4
|s.d2.4xlarge|16|128|8 x 1675 SAS HDD|8|4
|s.d2.6xlarge|24|192|12 x 1675 SAS HDD|8|4
|s.d2.8xlarge|32|256|16 x 1675 SAS HDD|8|4
|s.d2.12xlarge|48|384|24 x 1675 SAS HDD|8|4


请注意：

* 标 * 规格表示不支持以该规格新建云主机，且不支持您将当前云主机调整至该规格，但不影响您现有该规格云主机的使用；
* 可购买规格还请以控制台为准；
* 在购买实例后，您可根据业务规模变更情况对实例进行配置修改，详细请参见[调整配置](../Operation-Guide/Instance/Resize-Instance.md)。

## 相关参考

[调整配置](../Operation-Guide/Instance/Resize-Instance.md)
