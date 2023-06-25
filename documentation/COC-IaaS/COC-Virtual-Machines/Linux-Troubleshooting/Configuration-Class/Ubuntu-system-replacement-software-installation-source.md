# ubuntu系统更换软件安装源

使用官方镜像的Ubuntu云主机默认使用京东云内部软件安装源，如需更换为国内清华源，请按照以下步骤操作：

1、备份原有源文件：`cp /etc/apt/sources.list /etc/apt/sources.list.backup`

2、执行：`vi /etc/apt/sources.list`

编辑源文件，将内容替换为需要更换的源，使用清华源可参考[清华源官网](https://mirrors.tuna.tsinghua.edu.cn/help/ubuntu/)编辑源文件，编辑后保存。

3、执行`apt-get update`命令使源文件生效，安装软件验证是否正常

注意如果源文件的条目使用https链接，在执行`apt-get update`时有可能会卡在working[0%]无法继续。此时需要将源文件中每条下载链接的https修改为http，如图所示：

![](../../../../../image/Elastic-Compute/Virtual-Machine/Linux/ubuntu-change-yum-01.png)
将所有https修改为http

![](../../../../../image/Elastic-Compute/Virtual-Machine/Linux/ubuntu-change-yum-02.png)
修改完毕后保存文件再次尝试更新源。

如需更换回京东云内部源，执行`cp /etc/apt/sources.list.backup /etc/apt/sources.list`将源文件替换回原有备份文件后执行`apt-get upadate`即可。
