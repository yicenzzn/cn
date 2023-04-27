# Windows通过远程桌面上传文件

## 应用场景

本文档介绍Windows系统下如何通过远程桌面上传文件。

## 注意事项

该方法不适用于上传大文件。

## 操作步骤

1.点击运行，输入命令：***mstsc***，打开远程桌面连接对话框。

![](../../../../../image/Elastic-Compute/Virtual-Machine/Windows/Windows通过远程桌面上传文件00.png)

2.点击【显示选项】，弹出“远程桌面连接”对话框。

![](../../../../../image/Elastic-Compute/Virtual-Machine/Windows/Windows通过远程桌面上传文件01.png)

3.选择页签“本地资源”，点击【详细信息】按钮。

![](../../../../../image/Elastic-Compute/Virtual-Machine/Windows/Windows通过远程桌面上传文件02.png)

4.在驱动器模块，选择要上传到Windows云主机的文件所在的本地硬盘。
![](../../../../../image/Elastic-Compute/Virtual-Machine/Windows/Windows通过远程桌面上传文件03.png)

5.配置完成后，登录到Windows云主机，选择【开始】-【计算机】即可以看到挂载到云主机的本地硬盘。
![](../../../../../image/Elastic-Compute/Virtual-Machine/Windows/Windows通过远程桌面上传文件04.png)

6.将本地硬盘中的代码文件拷贝到Windows云主机上，即完成了文件上传操作。

