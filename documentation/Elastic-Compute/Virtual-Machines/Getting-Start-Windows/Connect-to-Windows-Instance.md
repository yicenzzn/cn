# 登录Windows实例
在购买并启动了Windows类型的实例后，您可以选择登录实例进行相关管理。根据您本地的操作系统和实例是否可被 Internet 访问，不同情况下可以使用不同的登录方式，具体内容可参考下表：

<table>
   <tr>
      <td> 本地操作系统类型 </td>
      <td> Linux实例绑定公网IP  </td>
      <td> Linux实例没有绑定公网IP </td>
   </tr>
   <tr>
      <td> Wndows </td>
      <td> VNC 登录<br>WebTerminal 登录<br>远程桌面连接  </td>
      <td rowspan="3"> VNC登录 </td>
   </tr>
   <tr>     
      <td> Linux </td>
      <td>VNC 登录<br>WebTerminal 登录<br>rdesktop登录   </td>
   </tr>
   <tr>  
      <td> Mac OS    </td>
      <td> VNC 登录<br>WebTerminal 登录<br>Remote Desktop登录 </td>
   </tr>
</table>

## 登录准备
创建实例并获取账号和对应密码

* 管理员账号：Administrator
* 密码：京东云实例可以通过两种方式获取密码
  *  在创建实例时，选择**暂不设置**，则系统将以短信及邮件方式发送默认密码，您可以在登录实例时，使用默认密码进行验证。
  *  选择**立即设置**，则在密码设置文本框中输入自定义密码，如果忘记密码，可以通过[重置密码](../Operation-Guide/Instance/Reset-Password.md)功能重新设置密码，此功能只有“运行”状态实例可用。

## 使用 WebTerminal 登录Windows实例
WebTerminal是京东云提供的基于SSH/RDP协议的Web远程终端工具，安全组开放SSH/RDP对应端口后，可直接在Web上远程登录云主机实例。支持命令复制粘贴、多用户登录、多会话、可视化查看系统文件资源等功能。

由于WebTerminal服务会使用内部地址对客户端发起的SSH请求进行转发，因此需要预先确认实例绑定的安全组和网络ACL（如有）在入方向允许的规则中包含服务使用的地址网段。不同连接方式和不同地域下所需添加的网段如下：（如入方向源IP未限定具体IP地址或网段，则无需再额外配置）
* 内网连接：不区分地域，地址为 **100.64.0.0/10**
* 公网连接：
  * 华北-北京：**114.67.239.0/24**
  * 华南-广州：**114.67.202.0/24**
  * 华东-上海：**114.67.126.0/24**
  * 华东-宿迁：**116.198.205.0/24**


1. 在实例列表的操作列，点击 **远程连接** ，在登录方式选择中选择 **WebTerminal登录**。
2. 
<div align="center">
<img src="https://img1.jcloudcs.com/cn/image/vm/webterminal.png" width="700">
</div>

2. 在登录弹窗中，根据实际情况完成选择或填写
* 实例：可切换当前地域下的实例，仅显示请求时状态为 **运行中** 的实例。
* 连接方式：绑定弹性公网IP情况下可选通过公网或内外连接，如未绑定弹性公网IP将默认使用内外连接。
* 端口：填写RDP端口。默认3389，如自行修改了RDP端口请酌情填写。
* 用户名：默认为administrator，如在实例内创建了其他用户可按登录需求填写。
* 认证方式：仅支持密码。
* 会话名称：默认为administrator@<实例ID>，可自行修改为方便识别的会话名称。

<div align="center">
<img src="https://img1.jcloudcs.com/cn/image/vm/webterminal-windows.jpg" width="450">
</div>

3. 登录成功后，可在Web端管理实例。由于RDP协议不支持多会话，因此Windows实例的会话不支持复制，同时，由于可直接通过文件夹查看系统内文件，左侧边栏的“系统文件目录”功能在Windows会话窗口下不支持。


<div align="center">
<img src="https://img1.jcloudcs.com/cn/image/vm/webterminal-windows1.png" width="700">
</div>

>请注意：
>* 边缘可用区实例不支持通过内网IP登录，须绑定弹性公网IP后通过公网登录

## 使用VNC登录实例
VNC登录是京东云为用户提供的一种通过 Web 浏览器远程连接实例的方式。在没有安装远程登陆客户端或者客户端远程登陆无法使用的情况下，用户可以通过 VNC 登陆连接到实例，观察实例状态，并且可通过实例用户进行基本的实例管理操作。
VNC登陆的场景至少包括以下几种：
* 查看实例的启动进度
* 无法通过客户端 SSH 或 mstsc 登录时，通过 VNC 登陆来登录实例

1. 在实例列表的操作列，点击【远程连接】即可通过 VNC 连接至 Windows 实例。
<div align="center">
<img src="https://img1.jcloudcs.com/cn/image/vm/Getting-Start-Linux-Connect-console.png">
</div>

2. 通过在左上角点击 `Ctrl+Alt+Del` 命令进入系统登录界面：
* 默认用户名：administrator        
* 密码：为您创建实例时设置的实例密码 
<div align="center">
<img src="https://img1.jcloudcs.com/cn/image/vm/Getting-Start-Linux-Connect-Windows-VNC.png">
</div>

请注意：

* 同一浏览器下，同一时间只支持使用VNC登录一台实例。
* 要正常使用VNC登录，建议使用高版本浏览器，如：Chrome及Firefox等等。
* 暂不支持文件上传下载。

## 本地为Windows，使用远程桌面登录Windows实例
使用MSTSC 远程桌面连接Window实例，须先确保实例绑定公网IP，并且安全组和网络ACL规则中允许通过此类访问。可在京东云控制台创建Windows系统实例，获得公网IP：XXX.XXX.XXX.XXX
1. 点击电脑**开始**按钮，找到“运行”<br>
<div align="center">
<img src="https://img1.jcloudcs.com/cn/image/vm/Getting-Start-Linux-Connect-Windows-menu.png" width="700">
</div>
2. 在运行中输入`mstsc`命令，点击确定，即可打开远程桌面连接对话框。<br>
<div align="center">
<img src="https://img1.jcloudcs.com/cn/image/vm/Getting-Start-Linux-Connect-Windows-mstsc.png" width="700">
</div>

3. 根据创建实例时绑定的公网IP，连接实例，输入用户名：Administrator，勾选**允许我保存凭据**。

<div align="center">
<img src="https://img1.jcloudcs.com/cn/image/vm/Getting-Start-Linux-Connect-Windows-mstsc1.png" width="700">
</div>

4. 点击**连接**后，输入密码，连接到实例。<br>

<div align="center">
<img src="https://img1.jcloudcs.com/cn/image/vm/Getting-Start-Linux-Connect-Windows-mstsc2.png" width="700">
</div>

5. 勾选**不再询问我是否连接到此计算机**，点击**是**。<br>

<div align="center">
<img src="https://img1.jcloudcs.com/cn/image/vm/Getting-Start-Linux-Connect-Windows-mstsc3.png" width="700">
</div>

6. 成功连接到您在京东云创建的Windows实例。<br>

<div align="center">
<img src="https://img1.jcloudcs.com/cn/image/vm/Getting-Start-Linux-Connect-Windows-mstsc4.png" width="700">
</div>

7. 如果登录失败，请确认公网IP地址是否输入正确，并查看实例关联[安全组](https://docs.jdcloud.com/cn/virtual-private-cloud/security-group-features)及所在子网的[网络ACL](http://docs.jdcloud.com/cn/virtual-private-cloud/network-acl-features)配置，确认实例是否允许3389端口的入流量。


## 本地为Linux，使用rdesktop登录Windows实例
本地系统为Linux，需要远程登录Window实例时，需要安装相应的远程桌面连接程序，通常使用rdesktop客户端。

登录之前请您查看实例所在[安全组](http://docs.jdcloud.com/cn/virtual-private-cloud/security-group-features)及所在子网的[网络ACL](http://docs.jdcloud.com/cn/virtual-private-cloud/network-acl-features)
配置，确保实例3389端口已开放。在安装了rdesktop之后，运行以下命令登录实例：

```Shell
rdesktop -u administrator -p <实例登录密码> <实例公网IP地址>
```

## 本地为MAC，使用远程桌面登录Windows实例
以微软官方提供的Remote Desktop为例，示意本地为MAC OS如何远程登录Windows实例。Remote Desktop可以前往[HockeyApp](https://appcenter.ms/)下载，下载前请确认当前系统版本是否支持。

1. 运行Microsoft Remote Desktop，点击**Add Desktop**。

<div align="center">
<img src="https://img1.jcloudcs.com/cn/image/vm/Getting-Start-Windows-Connect-Windows-mac1.png" width="700">
</div>

2. 在弹出的窗口中输入windows实例的公网IP地址,点击**Add**添加保存。

<div align="center">
<img src="https://img1.jcloudcs.com/cn/image/vm/Getting-Start-Windows-Connect-Windows-mac2.png" width="700">
</div>

3. 完成添加后，在“saved Desktop”中通过公网IP地址找到该实例，点击图标，输入用户名和密码，Windows实例的默认用户名是 administrator。随后点击**Done**即可连接实例。

<div align="center">
<img src="https://img1.jcloudcs.com/cn/image/vm/Getting-Start-Windows-Connect-Windows-mac3.png" width="700">
</div>
<div align="center">
<img src="https://img1.jcloudcs.com/cn/image/vm/Getting-Start-Windows-Connect-Windows-mac4.png" width="700">
</div>

4. 首次连接后，再次连接时可以直接找到并选中希望连接的实例图标，点击窗口设置图标里的**Connect**完成登录信息输入后进行连接。


## 相关参考 

[重置密码](../Operation-Guide/Instance/Reset-Password.md)

[安全组](http://docs.jdcloud.com/cn/virtual-private-cloud/security-group-features)

[网络ACL](http://docs.jdcloud.com/cn/virtual-private-cloud/network-acl-features)


  [1]: ./images/Getting-Start-Linux-Connect-console.png "Getting-Start-Linux-Connect-console.png"
  [2]: ./images/Getting-Start-Linux-Connect-Windows-VNC.png "Getting-Start-Linux-Connect-Windows-VNC.png"
  [3]: ./images/Getting-Start-Linux-Connect-Windows-menu.png "Getting-Start-Linux-Connect-Windows-menu.png"
  [4]: ./images/Getting-Start-Linux-Connect-Windows-mstsc.png "Getting-Start-Linux-Connect-Windows-mstsc.png"
  [5]: ./images/Getting-Start-Linux-Connect-Windows-mstsc1.png "Getting-Start-Linux-Connect-Windows-mstsc1.png"
  [6]: ./images/Getting-Start-Linux-Connect-Windows-mstsc2.png "Getting-Start-Linux-Connect-Windows-mstsc2.png"
  [7]: ./images/Getting-Start-Linux-Connect-Windows-mstsc3.png "Getting-Start-Linux-Connect-Windows-mstsc3.png"

  [8]: ./images/Getting-Start-Linux-Connect-Windows-mstsc4.png "Getting-Start-Linux-Connect-Windows-mstsc4.png"
