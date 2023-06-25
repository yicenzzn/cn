# 合作云硬盘扩容概述

<br>

## 概述

合作云硬盘是京东云和合作伙伴共同推出为云主机提供的可扩展的存储设备，创建云硬盘后用户可对云硬盘升级容量，以增加存储空间，同时保留云硬盘上原有的数据。云硬盘执行升级容量操作之后，还需要在云主机上扩展云硬盘的文件系统以识别新增存储空间。

云硬盘扩容有多种场景，以下列出了云硬盘做数据盘时，常见的几种云硬盘扩容场景及相关文档链接，请您根据具体场景选择合适的扩容方式：



- 扩容 有分区的Windows或Linux 实例的数据盘，请参考[扩容文件系统（有分区）](https://docs.jdcloud.com/cn/cloud-disk-service/expand-file-system-multi-partition)。



- 扩容 Linux 实例未做分区的数据盘，请参考[扩容文件系统（Linux无分区）](https://docs.jdcloud.com/cn/cloud-disk-service/expand-file-system-linux)。


## 扩容限制

新款云硬盘分为第二代通用型SSD、性能型SSD和增强型SSD云盘。新款云硬盘允许扩容的上限相同，均为32000GB。详情参考下表：

<table class="confluenceTable"><tbody><tr class="firstRow"><th style="text-align: left; color: rgb(0, 0, 0); padding-top: 7px; padding-bottom: 7px; vertical-align: top; border-top-color: rgb(221, 221, 221); white-space: pre-wrap; background-color: rgb(240, 240, 240);" class="confluenceTh"><span style="color: rgb(0, 0, 0); font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">云硬盘类别</span></th><th style="text-align: left; color: rgb(0, 0, 0); padding-top: 7px; padding-bottom: 7px; vertical-align: top; border-top-color: rgb(221, 221, 221); white-space: pre-wrap; background-color: rgb(240, 240, 240);" class="confluenceTh"><span style="color: rgb(0, 0, 0); font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">扩容前容量</span></th><th style="text-align: left; color: rgb(0, 0, 0); padding-top: 7px; padding-bottom: 7px; vertical-align: top; border-top-color: rgb(221, 221, 221); white-space: pre-wrap; background-color: rgb(240, 240, 240);" class="confluenceTh"><span style="color: rgb(0, 0, 0); font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">扩容后容量上限</span></th></tr><tr><td style="padding-top: 7px; padding-bottom: 7px; vertical-align: top; white-space: pre-wrap;" class="confluenceTd"><span style="color: rgb(0, 0, 0); font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">增强型SSD云盘</span></td><td style="padding-top: 7px; padding-bottom: 7px; vertical-align: top; white-space: pre-wrap;" class="confluenceTd"><span style="color: rgb(0, 0, 0); font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">&lt; 4000GB</span></td><td style="padding-top: 7px; padding-bottom: 7px; vertical-align: top; white-space: pre-wrap;" class="confluenceTd"><span style="color: rgb(0, 0, 0); font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">32000GB</span></td></tr><tr><td style="padding-top: 7px; padding-bottom: 7px; vertical-align: top; white-space: pre-wrap;" class="confluenceTd"><span style="color: rgb(0, 0, 0); font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">第二代通用型SSD云盘</span></td><td style="padding-top: 7px; padding-bottom: 7px; vertical-align: top; white-space: pre-wrap;" class="confluenceTd"><span style="color: rgb(0, 0, 0); font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">&lt; 4000GB</span></td><td style="padding-top: 7px; padding-bottom: 7px; vertical-align: top; white-space: pre-wrap;" class="confluenceTd"><span style="color: rgb(0, 0, 0); font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">32000GB</span></td></tr><tr><td style="padding-top: 7px; padding-bottom: 7px; vertical-align: top; white-space: pre-wrap;" class="confluenceTd"><span style="color: rgb(0, 0, 0); font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">性能型SSD云盘</span></td><td style="padding-top: 7px; padding-bottom: 7px; vertical-align: top; white-space: pre-wrap;" class="confluenceTd"><span style="color: rgb(0, 0, 0); font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">&lt; 4000GB</span></td><td style="padding-top: 7px; padding-bottom: 7px; vertical-align: top; white-space: pre-wrap;" class="confluenceTd"><span style="color: rgb(0, 0, 0); font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">32000GB</span></td></tr></tbody></table>



​	

​	




​	
​	
