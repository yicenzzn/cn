# 自定义域名服务

## 常见概念
绑定自定义域名，您需要了解以下概念：

* 用户域名、自定义域名、自有域名：您在域名服务商处购买的域名。
* OSS 访问域名或 Bucket 域名：OSS 为您的 Bucket 分配的的访问域名。

### 您可以将自定义的域名访问绑定在属于自己的Bucket上面，即CNAME。在您开通CNAME功能后，OSS将自动处理对该域名的访问请求。 

*并且按照中国《互联网管理条例》的要求，用户如需开通这项功能，必须提供工信部备案号，域名持有者身份证等有效资料，经由京东云审批通过后才可以使用。*

## 应用场景

例如，当用户需要将网站中的文件迁移到OSS，并且不想修改网页的代码，即保持网站的链接不变，CNAME功能特别适合这种场景。
例如用户A的网站域名为www.example.com ，网站文件为abc.html，网站链接为：http://www.example.com/abc.html 。

流程如下：

 1.在OSS上创建一个Bucket，命名为example，并上传abc.html网站文件到该存储空间中。
 
 2.OSS控制台，将www.example.com 这个自定义的域名绑定在已创建存储空间上。
 
 3.在域名服务器上，添加CNAME规则，将www.example.com 映射成存储空间域名。
 
 4.http://www.example.com/abc.html 请求到达OSS后，OSS会找到www.example.com 和存储空间域名（example.s3.cn-north-1.jdcloud-oss.com）的映射，转换变成访问桶的abc.html文件。即对http://www.example.com/abc.html 的访问，经过OSS处理后，实际上访问的是http://example.s3.cn-north-1.jdcloud-oss.com/abc.html 。
 
## 自定义域名优势

* 当用户需要将网站中的文件迁移到OSS，并且不想修改网页的代码，即保持网站的链接不变。
* 避免业务中可能涉及的跨域或者安全问题。 
 
## 控制台：自定义域名 
在OSS Bucket上传对象后，可获取对象的地址，包含两个部分：OSS域名地址+对象文件名，OSS 访问域名格式如下：

```
<BucketName>.<Endpoint>
```

[外网域名- endpoint ](../../API-Reference-S3-Compatible/Regions-And-Endpoints.md)

自定义域名绑定成功后，OSS中存储文件的访问地址可使用自定义域名。例如，您的存储空间example位于华北-北京，对象文件名称为test.jpg，绑定的自定义域名为hello-world.com，则该对象访问地址为：

* 未绑定之前：example.s3.cn-north-1.jdcloud-oss.com /test.jpg
* 绑定成功后：hello-world.com/test.jpg
  您可以通过控制台将自定义域名绑定到OSS外网域名上实现自定义域名访问存储空间下的文件。

## 绑定域名操作步骤
1.登入控制台->对象存储->空间管理->进入某个Bucket->空间设置，点击“自定义域名”。

2.单击添加域名按钮，打开绑定用户域名页面，如下图所示：

![图片](https://github.com/jdcloudcom/cn/blob/edit/image/Object-Storage-Service/OSS-094.jpg)
 
3.绑定域名

 *  在用户域名框中，输入要绑定的域名名称。
 *  如果需要CDN加速，通过单击自定义域名tab 页的提示文案，前往京东云CDN控制台开通CDN加速。
 
4.单击提交。

**说明**
 
*  一个域名只能绑定相同地域中一个Bucket，每个Bucket最多绑定20个域名。
*  您绑定的域名需在工信部备案，否则域名访问将会受到影响。
*  建议您将自定义的域名访问绑定在属于自己的Bucket上面。域名绑定成功后，为了使用域名正常访问OSS，还需要需要用户到域名解析商处添加CNAME记录指向OSS访问域名。
*  如果您的用户域名需要通过HTTPS的方式访问OSS服务，必须购买相应的数字证书。并通过工单提交您的证书，并通过京东云OSS托管您的证书，详见[自定义域名支持HTTPS访问 OSS 服务](../../Best-Practices/Custom-Domain-Name-Guidance.md)。
*  如果您输入的域名已经被其他用户恶意绑定，系统将提示域名被绑定。您可以单击提交工单的方式，按照OSS的验证方案，完成验证域名所有权，如果通过域名所有权验证，即可绑定域名，同时解除此域名与之前存储空间的绑定关系。
*  目前仅支持使用自定义域名下载文件，如您需上传文件或对Bucket进行各种操作请使用京东云OSS访问域名。


## 域名解析操作步骤（以京东云云解析为例）

登录京东云云解析DNS 控制台进入域名解析列表页面。
单击目标域名或右侧的解析按钮进入域名解析页面。
单击添加解析后，打开添加解析页面。
在记录类型下拉列表中，选择CNAME；在记录值框中，填写对应的存储空间外网域名（即Bucket域名，如BucketName.s3.cn-north-1.jdcloud-oss.com）。
单击确认，域名解析完成。
具体参考[京东云云解析DNS-添加解析记录](https://docs.jdcloud.com/cn/jd-cloud-dns/domain-record-add)
