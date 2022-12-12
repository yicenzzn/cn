# 实例规格类型

实例是京东云为您业务提供计算服务的最小单位，不同实例通过其规格类型及具体规格来标识相应的计算、内存、存储及网络能力。同时，您创建实例时指定的实例类型决定了实例的硬件配置，您可基于需要部署运行的应用类型及规模选择适当的实例规格类型及具体规格。

以下为当前京东云在售的实例规格类型信息，不同地域可售卖实例类型及规格不完全相同。目前原生容器实例和原生容器Pod所有地域均支持创建二代和三代实例规格类型的资源，原生容器实例在华北-北京支持一代实例规格类型。具体在售实例规格类型根据不同应用场景可以分为：

#### x86规格
* 通用型：[通用标准型](instance-type-family#user-content-2)
* 计算优化型：[计算优化标准型](instance-type-family#user-content-3)
* 内存优化型：[内存优化标准型](instance-type-family#user-content-4)
* 高频计算型：[高频计算通用型](instance-type-family#user-content-5)

## x86规格：
## 通用型
通用型当前提供通用共享型及通用标准型，为您提供均衡的计算及内存资源，可满足大部分业务场景下的需求。其中通用标准型中每一个vCPU都对应一个处理器的超线程核，其vCPU与内存比为1:4。

### 通用共享型

<div id="user-content-1"></div>

通用共享型实例采用非绑定CPU调度模式，每个vCPU会被分配到任何空闲的超线程核上，不同实例的vCPU可以互相争抢物理CPU资源。通用共享型实例拥有高性价比的优点，但由于需要对资源进行争抢，在性能上可能会受到不同程度的影响。


**规格类型特点：**

* vCPU与内存比为1:1、1:2或1:4，提供多种处理器内存配比。
* 处理器：
        
* 第一代：2.1 GHz主频的Intel Xeon E5-2683 v4（Broadwell）处理器
* 支持以下类型云硬盘：
	* 通用型SSD云盘
	* 性能型SSD云盘
	* 容量型HDD云盘
* 适用场景：
	* 访问量较小的个人网站初级阶段
	* 微服务
	* 测试环境

**实例规格**

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数

第一代

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|g.s1.micro|1|1|2|1
|g.s1.small|1|2|2|1

### 通用标准型

<div id="user-content-2"></div>

**规格类型特点:**

* vCPU与内存比为1:4（g.n1.xlarge_m规格除外）
* 处理器：
	* 第三代：2.6 GHz主频的Intel Xeon Platinum 8338C（Icelake）处理器 或 2.6 GHz主频的Intel Xeon Gold 6267（Cascade Lake）处理器  
	* 第二代：
	  * 2.6 GHz主频的Intel Xeon Gold 6267（Cascade Lake）处理器 或 2.4 GHz主频的Intel Xeon Gold 6148（Skylake）处理器
	  * 2.6 GHz主频的AMD EPYC ROME 处理器
	* 第一代：2.1 GHz主频的Intel Xeon E5-2683 v4（Broadwell）处理器
* 支持以下类型云硬盘：
	* 通用型SSD云盘
	* 性能型SSD云盘
	* 容量型HDD云盘
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
|g.n3.18xlarge|72|288|8|4

第二代

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|g.n2.medium|1|4|2|1
|g.n2.large|2|8|2|2
|g.n2.xlarge|4|16|4|4
|g.n2.2xlarge|8|32|4|4
|g.n2.4xlarge|16|64|8|4
|g.n2.8xlarge|32|128|8|4
|g.n2.16xlarge|64|256|8|4
|g.n2.18xlarge|72|288|8|4

<div id="user-content-13"></div>

第一代

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|g.n1.medium|1|4|2|1 
|g.n1.large|2|8|2|2 
|g.n1.xlarge_m|4|12|4|4
|g.n1.xlarge|4|16|4|4
|g.n1.2xlarge|8|32|4|4
|g.n1.4xlarge|16|64|8|4
|g.n1.8xlarge|32|128|8|4 

## 计算优化型
计算优化型当前提供计算优化标准型，计算优化标准型可满足每一个vCPU都对应一个Intel Xeon处理器的超线程核，为您提供高性能的计算资源。

### 计算优化标准型

<div id="user-content-3"></div>

**规格类型特点：**

* vCPU与内存比约为1:2
* 处理器：
	* 第三代：2.6 GHz主频的Intel Xeon Platinum 8338C（Icelake）处理器 或 2.6 GHz主频的Intel Xeon Gold 6267（Cascade Lake）处理器
	* 第二代：
	  * 2.6 GHz主频的Intel Xeon Gold 6267（Cascade Lake）处理器 或 2.4 GHz主频的Intel Xeon Gold 6148 （Skylake）处理器
	  * 2.6 GHz主频的AMD EPYC ROME 处理器
	* 第一代：2.1 GHz主频的Intel Xeon E5-2683 v4（Broadwell）处理器
* 支持以下类型云硬盘：
	* 通用型SSD云盘
	* 性能型SSD云盘
	* 容量型HDD云盘
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
|c.n3.large|2|4|2|2
|c.n3.xlarge|4|8|4|4
|c.n3.2xlarge|8|16|4|4
|c.n3.3xlarge|12|24|8|4
|c.n3.4xlarge|16|32|8|4
|c.n3.6xlarge|24|48|8|4
|c.n3.8xlarge|32|64|8|4
|c.n3.12xlarge|48|96|8|4
|c.n3.16xlarge|64|128|8|4
|c.n3.22xlarge|88|176|8|4

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

第一代

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|c.n1.large|2|4|2|2
|c.n1.xlarge_m|4|4|4|4
|c.n1.xlarge|4|8|4|4
|c.n1.2xlarge_s|8|8|4|4
|c.n1.2xlarge_m|8|12|4|4
|c.n1.2xlarge|8|16|4|4	
|c.n1.4xlarge_m|16|16|8|4
|c.n1.4xlarge|16|32|8|4	
|c.n1.8xlarge|32|64|8|4


## 内存优化型
内存优化型当前提供内存优化标准型，适用于存在大量内存操作、查找和计算的应用。每一个vCPU都对应一个Intel Xeon处理器的超线程核。

<div id="user-content-4"></div>

### 内存优化标准型

**规格类型特点：**

* vCPU与内存比约为1:8
* 处理器：
	* 第三代：2.6 GHz主频的Intel Xeon Platinum 8338C（Icelake）处理器 或 2.6 GHz主频的Intel Xeon Gold 6267（Cascade Lake）处理器 
	* 第二代：
	  * 2.6 GHz主频的Intel Xeon Gold 6267（Cascade Lake）处理器 或 2.4 GHz主频的Intel Xeon Gold 6148 （Skylake）处理器
	  * 2.6 GHz主频的AMD EPYC ROME 处理器
	* 第一代：2.1 GHz主频的Intel Xeon E5-2683 v4（Broadwell）处理器
* 支持以下类型云硬盘：
	* 通用型SSD云盘
	* 性能型SSD云盘
	* 容量型HDD云盘
* 镜像使用限制：
	* 3代及以上Intel系列，AMD系列仅支持云盘系统盘镜像
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
|m.n3.16xlarge|64|512|8|4

第二代

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|m.n2.large|2|16|2|2
|m.n2.xlarge|4|32|4|4
|m.n2.2xlarge|8|64|4|4
|m.n2.4xlarge|16|128|8|4
|m.n2.8xlarge|32|256|8|4
|m.n2.16xlarge|64|512|8|4
|m.n2.18xlarge|72|576|8|4

第一代

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|m.n1.small| 1 | 8 | 2|1
|m.n1.medium|2	|12|2|2
|m.n1.large|2|16|2|2 
|m.n1.xlarge|4|32|4|4 
|m.n1.2xlarge|8|64|4|4  
|m.n1.4xlarge|16|128|8|4 

<div id="user-content-17"></div>

### 高频计算通用型

**规格类型特点：**

* vCPU与内存比为1:4
* 计算性能稳定，处理器主频高
* 处理器：
	* 第二代：3.2 GHz主频的Intel Xeon Gold 6146（Skylake）处理器
	* 第一代：3.2 GHz主频的Intel Xeon E5-2667 v4（Broadwell）处理器
* 支持以下类型云硬盘：
	* 通用型SSD云盘
	* 性能型SSD云盘
	* 容量型HDD云盘
* 适用场景：
	* 高性能Web前端服务器
	* 高性能科学和工程应用
	* MMO游戏、视频编码

**实例规格**

第二代：

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|h.g2.large|2|8|2|2
|h.g2.xlarge|4|16|4|4
|h.g2.2xlarge|8|32|4|4
|h.g2.4xlarge|16|64|8|4
|h.g2.8xlarge|32|128|8|4

第一代：

实例规格|vCPU（核）|内存（GiB）|网卡数|单网卡队列数
:---|:---|:---|:---|:---
|h.g1.large|2|8|2|2
|h.g1.xlarge|4|16|4|4
|h.g1.2xlarge|8|32|4|4
|h.g1.4xlarge|16|64|8|4
|h.g1.6xlarge|24|96|8|4
