# 扩容云硬盘

随着您业务数据增长，若当前云硬盘容量不能满足需要，您可对其进行扩容操作。

## 前提条件及限制

* 云硬盘当前支持两种扩容模式：
  * 普通扩容：云硬盘须处于**可用**状态，如挂载至实例须先操作卸载；
  * 热扩容: 云主机详情页支持云盘热扩容，云盘须处于**可用**或**已挂载**状态，无须操作卸载即可操作扩容；
* 扩容不会影响原有数据，但稳妥起见，建议您在扩容前对数据盘制作快照以做数据备份。

## 操作影响
* 系统盘：如您使用京东云提供的官方镜像创建云主机，且镜像内默认安装的核心系统组件运行正常，扩容系统盘并且重启云主机/组件后，系统会自动进行文件系统扩容。如果您的云主机安装的操作系统版本为CentOS 7以上，可以通过以下命令行重启组件。
    ```
    service jcs-entry restart
    service jcs-agent-core restart
    ```
> 请注意：操作系统为CentOS 6.X版本的云主机仅支持通过重启云主机进行自动扩容。
* 数据盘：由于数据盘上的所有分区均为用户自行设置，因此云硬盘扩容后系统不会对文件系统进行扩容，请参考[扩容文件系统](http://docs.jdcloud.com/cloud-disk-service/cloud-disk-expansion-overview) 完成后续操作。



## 操作步骤

详细操作步骤请参考[云硬盘扩容](http://docs.jdcloud.com/cn/cloud-disk-service/disk-expand)。

## 相关参考

[扩容文件系统](http://docs.jdcloud.com/cn/cloud-disk-service/cloud-disk-expansion-overview)

[云硬盘扩容](http://docs.jdcloud.com/cn/cloud-disk-service/disk-expand)
