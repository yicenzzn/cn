# 登录Linux实例
在购买并启动了Linux类型的实例后，您可以选择登录实例进行相关管理。根据您本地的操作系统，可以使用不同的登录方式，具体内容可参考下表：
<table>
   <tr>
      <td> 本地操作系统类型 </td>
      <td> 登录方式  </td>
   </tr>
   <tr>
      <td> Wndows </td>
      <td> VNC 登录<br>通过远程登录软件使用密码登录  </td>
   </tr>
   <tr>     
      <td> Linux / Mac OS</td>
      <td>VNC 登录<br>使用密码登录   </td>
   </tr>
</table>

## 登录准备
创建实例并获取账号和对应密码：

* 管理员账号：root
* 密码：京东云实例可以通过两种方式获取密码
  *  在创建实例时，选择**自动生成**，则系统将以短信及邮件方式发送默认密码，您可以在登录实例时，使用默认密码进行验证。
  *  选择**自定义**，则在密码设置文本框中输入自定义密码，如果忘记密码，可以通过[重置密码](../Operation-Guide/Instance/Reset-Password.md)功能重新设置密码，此功能只有“运行”状态实例可用。

## 使用VNC登录Linux实例
VNC登录是京东云为用户提供的一种通过 Web 浏览器远程连接实例的方式。在没有安装远程登陆客户端或者客户端远程登陆无法使用的情况下，用户可以通过 VNC 登陆连接到实例，观察实例状态，并且可通过实例用户进行基本的实例管理操作。
VNC登陆的场景至少包括以下几种：

* 查看实例的启动进度
* 无法通过远程登录软件或密钥登录时，通过 VNC 登陆来登录实例。

1. 在实例列表的操作列，点击**远程连接**即可通过 VNC 连接至Linux实例。


![sdsd](../../../../image/vmx/Getting-Start-Linux-Connect-console.png)  

2. 点击VNC之后进入到登录页面
* 默认用户名：root        
* 密码：为您创建实例时设置的实例密码 

<div align="center">
<img src="https://img1.jcloudcs.com/cn/image/vm/Getting-Start-Linux-Connect-vnc.png" width="700">
</div>

请注意：

* 同一浏览器下，同一时间只支持使用VNC登录一台实例。
* 要正常使用VNC登录，建议使用高版本浏览器，如：Chrome及Firefox等浏览器。
* 暂不支持文件上传下载。

## 本地为Windows，通过远程登录软件使用密码登录
您可选择多种远程登录软件登陆京东云Linux实例。本例以 CentOS 7.1 64位系统，Xshell远程登录软件为示范，可按照如下步骤完成登录。

1. 下载并安装远程登录软件
    可使用此地址下载：http://iaas-cns-download.s3.cn-north-1.jcloudcs.com/xshell5_5.0.1332.exe 或自行下载Xshell软件。
    下载后双击xshell5_5.0.1332.exe进行安装。

2. 安装完成，打开Xshell，并点击新建，根据要求输入相应参数

	* 名称：自定义设置
	* 协议：SSH
	* 主机：实例所绑定的公网IP，可在实例列表查询
	* 端口号：22!
	[](https://img1.jcloudcs.com/cn/image/vm/Getting-Start-Linux-Connect-linux-xshell.png)

3. 选择用户身份认证
	* 密码登录
		* 方法：选择Password
		* 用户名：默认用户名为root<br>
		<div align="center">
		<img src="https://img1.jcloudcs.com/cn/image/vm/Getting-Start-Linux-Connect-linux-xshell1.png" width="700">
		</div>
		* 点击确定，连接实例，如下图：<br>
		<div align="center">
		<img src="https://img1.jcloudcs.com/cn/image/vm/Getting-Start-Linux-Connect-linux-xshell2.png" width="700">
		</div>

## 本地为Linux/Mac OS，使用密码登录Linux实例
Linux用户请直接运行以下命令，Mac OS用户请打开系统自带的终端（Terminal）后运行以下命令，随后输入该实例root用户的密码，输入正确即可连接实例。

```Shell
ssh root@<实例的公网IP地址>
```

## 相关参考

[重置密码](../Operation-Guide/Instance/Reset-Password.md)



  [1]: ./images/Getting-Start-Linux-Connect-console.png "Getting-Start-Linux-Connect-console.png"
  [2]: ./images/Getting-Start-Linux-Connect-vnc.png "Getting-Start-Linux-Connect-vnc.png"
  [3]: ./images/Getting-Start-Linux-Connect-linux-xshell.png "Getting-Start-Linux-Connect-linux-xshell.png"
  [4]: ./images/Getting-Start-Linux-Connect-linux-xshell1.png "Getting-Start-Linux-Connect-linux-xshell1.png"
  [5]: ./images/Getting-Start-Linux-Connect-linux-xshell2.png "Getting-Start-Linux-Connect-linux-xshell2.png"
  [6]: ./images/Getting-Start-Linux-Connect-linux-xshell3.png "Getting-Start-Linux-Connect-linux-xshell3.png"
  [7]: ./images/Getting-Start-Linux-Connect-linux-xshell4.png "Getting-Start-Linux-Connect-linux-xshell4.png"
  [8]: ./images/Getting-Start-Linux-Connect-linux-xshell5.png "Getting-Start-Linux-Connect-linux-xshell5.png"
