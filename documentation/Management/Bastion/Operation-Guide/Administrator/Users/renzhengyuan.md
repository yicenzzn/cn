# 认证源管理

支持OAuth2.0、AD/LDAP第三方应用认证机制，做到防止运维人员身份冒用和复用，控制账号密码泄露风险。

通过【用户】-【认证源管理】查看创建的认证源，认证源列表展示认证源名称、认证类型、用户数、操作。

![](/image/Bastion/rzyyy.png)

### 新建认证源

管理员可以在 【用户】-【认证源管理】点击左上角创建认证源。

**OAuth2.0**：填写认证源名称、认证源类型、认证服务端点、令牌服务端点、用户信息端点、客户端/应用ID、客户端密码，完成创建。

![](/image/Bastion/rzy1.png)

说明：

|    字段    |   说明  | 
| :--------: | :--------:|
| 认证服务端点  | 用于请求并打开OAuth服务认证页面 |
| 令牌服务端点  | 用于获取OAuth服务令牌 |
| 用户信息端点  | 用于获取OAuth服务用户信息 |
| 客户端/应用ID  | 用于请求时互信 |
| 客户端密码  | 用于请求时互信 |
| redirectUri  | 用于OAuth服务器回传结果 |
| redirectUriRelay  | 用于ssh登录认证时，OAuth服务器回传结果 |

**AD/LDAP**：填写认证源名称、认证源类型、服务器地址、Base DN、部门过滤、用户过滤、管理员账号、管理员密码，选择用户名、手机号、Email，完成创建。

![](/image/Bastion/rzy222.png)

说明：

- **服务器地址**:配置LDAP服务器地址，用于请求LDAP服务器；端口默认明文传输，勾选“开启SSL”则加密传输。

- **Base DN**：LDAP目录树的最顶部就是根，也就是所谓的 "Base DN"，如 "dc=xksec,dc=com, ou=JDCLOUD "。见下图示意。

![](/image/Bastion/basedn.png) 

- **部门过滤**：部门过滤属性，例如：(|(objectclass=group)(objectclass=groupofnames)(objectclass=organizationalUnit))
- **用户过滤**:  用户过滤属性，例如 ：(|(objectclass=user)(objectclass=person)(objectclass=inetOrgPerson))
- **管理员账号**: LDAP服务器管理员账号
- **管理员密码**: LDAP服务器管理员密码
- **选择用户名**: 选择用户属性
- **手机号**：选择手机号属性
- **Email**：选择Email属性

### AD/LDAP用户导入

1.通过京东云堡垒机【用户】-【认证源】，完成AD/LDAP创建。选择已建好的认证源列选择“导入用户”，如下图：

![](/image/Bastion/rzydryh.png) 

2.选择AD/LDAP服务已创建的用户进行导入。（已导入的用户不展示）

![](/image/Bastion/rzyxzyh.png) 

3.导入成功，在【用户】-【用户管理】列表展示导入的用户信息。

![](/image/Bastion/rzycgdryh.png) 

### OAuth2.0认证源创建示例

- 以**京东云**认证认证源配置：

通过登录京东云控制台，【用户池】-【应用管理】完成应用创建，创建过程中的回调地址填写堡垒机认证源创建时的redirectUri和redirectUriRelay；密码验证方式、令牌等配置参考下图。

![](/image/Bastion/rzyyhcyygl.png) 

- 以某平台OAuth认证配置说明：

1.首先需要在某平台创建一个OAuth2.0认证；

![](/image/Bastion/rzy2.png)

2.登录京东云控制台，登录堡垒机创建“认证源”，复制京东云堡垒机创建页面的redirectUri、redirectUriRelay配置到某平台OAuth内。（作用：用于双方认证互信）

![](/image/Bastion/rzy3.png)

3.将某平台的认证服务端点、令牌服务端点、用户信息端点、客户端/应用ID、客户端密码配置到京东云“认证源”完成第三方认证配置。

![](/image/Bastion/rzy4.png)

### 认证源登录操作说明

认证源完成创建后，在【用户管理】新建用户的第三方认证源类型支持选择已创建的认证源配置。

![](/image/Bastion/rzy5.png)

成功配置认证源后，则在登录堡垒机时，在堡垒机登录页面的“登录”按钮下方显示“第三方认证”入口。

![](/image/Bastion/rzy7.png)

点击“第三方认证登录”按钮，跳转第三方登录页面。

![](/image/Bastion/rzy8.png)

输入用户名后，点击“登录”按钮，跳转第三方登录页面（如下图）；成功输入第三方认证的账号和密码，则成功登录并跳转堡垒机控制台页面。

![](/image/Bastion/rzy9.png)

### SSH认证源登录说明

当运维人员使用SSH通过认证源方式登录时；

1.在SSH登录时输入password位置**直接回车**，之后会显示(如下图)一个URL地址。

![](/image/Bastion/rzy10.png)

2.复制上图URL，通过浏览器打开（如下图），复制凭证.

![](/image/Bastion/rzy11.png)

3.将复制的凭证输入SSH页面完成登录。

![](/image/Bastion/rzy12.png)
