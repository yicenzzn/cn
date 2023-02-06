# **什么情况下需要进行域名归属校验？**

1.	域名首次接入时，例如：a.example.com；该域名接入后，同级域名及次级域名如b.example.com视为已有权限域名，默认可接入，无需校验，若加速配置不同需单独配置。但上级域名如example.com接入仍需校验。

2.	同级泛域名接入时，需校验，次级泛域名，不支持接入。例如：a.example.com已接入时，*.example.com接入时仍需校验；*.a.example.com属于次级泛域名，不支持接入，反之如此。

3.	当前域名或子域名已在其他账号下接入时，需在相应账号下删除后再添加，泛域名遵循同一规则。注：同级精确域名可以在不同账号下添加，但需要进行归属权校验。

# **方法一：DNS解析验证**

1. 在添加域名时，如果该域名需校验，在域名下方会提示需验证域名归属权。

2. 验证方法中，默认为 DNS 解析验证。

   使用 DNS 解析验证的方式，需要您前往该域名的解析服务商，在主域名下添加一个主机记录值为 _cdnautover 的 TXT 记录。

   `注意`

   无论您需要新增的域名为 c.b.a.example.com、\*.example.com 或 test.example.com，多级域名下主机记录值仍应添加在主域名下，例如：添加的域名是 c.b.a.example.com，需要新增一条解析记录为 _cdnautover.example.com即可。

   ![DNS解析验证](https://github.com/jdcloudcom/cn/blob/cdn_20220222_api/image/CDN/DNS解析验证.png)

   # **DNS 解析添加方法参考：**

   如果您的解析服务商在京东云 DNSPod 上，可进入[DNS解析控制台](https://www.jdcloud.com/cn/products/jd-cloud-dns)，找到该域名并单击解析，添加一条记录类型为 TXT 的 DNS 记录，主机记录填写为_cdnautover，记录类型选择为 TXT，记录值填写为京东云 CDN 提供的记录值，其余选项按照默认参数填写即可。可参考:[DNS解析操作说明](https://docs.jdcloud.com/cn/jd-cloud-dns/domain-record-add)。

3. 添加完解析记录后，等待 TXT 记录值生效，生效后，您可点击下方的验证按钮，即可完成域名归属校验；如果验证失败，请确认当前 TXT 记录值在域名解析服务商内是否已生效或是否填写了正确的 TXT 记录值。

# **方法二：文件验证**

1.	在添加域名时，如果该域名需校验，在域名下方会提示需验证域名归属权；

2.	在验证方法内，选择文件验证的方式；

![文件验证](https://github.com/jdcloudcom/cn/blob/cdn_20220222_api/image/CDN/文件验证.png)

3.	单击下载文件 verification.html；

4.	将该文件上传至您主域名的服务器（例如您的 CVM、COS、阿里 ECS、阿里 OSS 等）根目录下，例如：当前添加的域名为 test.example.com，您需要将该文件上传至 example.com 的根目录下；

5.	确保可通过 http://example.com/verification.html 访问至该文件后，即可单击验证按钮进行验证。如果文件内的记录值与我们提供的记录值是一致的，即可验证通过；如果验证失败，请确保上述文件链接可访问，并且您上传的文件为正确文件，可通过访问文件的链接与所下载的文件进行比对是否一致。

   `注意`

   选择中国境外或全球加速服务需特别注意：

   在完成上述归属权校验后，可点击下一步，并需要添加境外 TXT 记录，校验生效通过后方可成功激活，域名境外激活状态会在域名详情页展示。

   1）境外TXT记录值在客户控制台/运营后台-域名管理-资源信息-基本信息中可查（仅中国境外/全球加速域名有，若无值则境外加速域名未创建添加成功。同时在将境内加速修改为境外或全球加速时也需要添加境外 TXT 记录。

   2）激活中国境外或全球加速域名，必须要加 “verify” 这个前缀，例如域名是 www.jd.com， 则进行 DNS 解析时的主机记录为 “verify.www.jd.com”。
   
  ![境外加速域名归属验证1](https://github.com/jdcloudcom/cn/blob/cdn_20220222_api/image/CDN/境外加速域名归属验证1.png)
  
  ![境外加速域名归属验证2](https://github.com/jdcloudcom/cn/blob/cdn_20220222_api/image/CDN/境外加速域名归属验证2.png) 
  
