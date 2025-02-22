
# 安全加速SCDN 应用防火墙

**应用防火墙说明**

安全加速SCDN 的应用防火墙功能，可检查 Web 流量以识别攻击行为。它能够根据您指定的规则集，自动过滤非法流量。应用规则集阻止、挑战恶意请求流量。也可以阻止垃圾评论、跨站脚本攻击和SQL注入等。

WAF的作用是检查对您网站的HTTP请求，通过检查GET和POST请求，应用规则来帮助过滤掉访问中的非法流量。如果安全加速确定了可疑用户行为，则WAF将通过页面“挑战”此访问者，
此页面需要访问者成功提交验证码才可以继续进行操作。如果挑战失败，则该操作将会被拦截。这意味着SCDN 将阻止被识别的非法流量到达源站服务器。

* 可通过应用需要安全策略的严格程度，设置OWASP 核心规则集防护等级，高、中、低。该规则集涵盖了OWASP Top10的典型漏洞。

* 可设置页面规则，为站点的某些URL绕过防火墙规则，用来排除避免受到WAF的影响。

注：确定适合站点安全等级的因素很多。比如，如果您的企业业务包括大型文件上传，则将及安全级别降低更为合适。因为从安全防御角度，上传大文件是一种常见的攻击方式，将会触发防火墙拦截。

安全加速SCDN包含如下三种规则集，用于增加您的应用和站点的安全性。


**托管规则集**

安全加速托管规则集，提供了对网站常见攻击类型的规则组。包括：

* Flash：当站点使用Flash框架时，可以开启此规则集进行保护。
* Miscellaneous：该规则集用于防护某些已经披露的Web应用程序恶意攻击或者恶意漏洞.
* Specials：该规则集包含了一些特殊攻击类型的规则。
* Whmcs：当源站使用Whmcs管理软件时，可以开启此规则集进行保护。
* WordPress：当源站使用WordPress时，可以开启此规则集进行保护。

**OWASP 核心规则集**

* 核心规则集主要覆盖OWASP Top10的攻击行为。可通过防护规则等级设置，支持级别为：高、中、低、关闭。
* 每个防护等级对应不同分数，SCDN根据用户请求触发的规则为每个请求打分。
* 请求的分数评估完成后，会将最终分数与为配置的防护规则等级进行比较，如果分数超过了规则等级，请求将会被相应的动作进行处理。

目前OWASP 核心规则集提供了三种处理动作，包括：

  * 阻止：用户请求被阻断并drop。

  * 验证码：用户会收到验证码挑战页面。

  * 允许：用户请求被允许通过并在日志中记录。


**防火墙规则**

防火墙规则用于用户自定义防护策略，它可根据用户实际业务需要进行灵活配置，可防护在两种SCDN预定义规则集之外的攻击。

防火墙规则包含自定义防火墙规则与速率限制功能。其中自定义规则具备两个核心功能，

* 规则匹配：

  定义在SCDN运行的自定义规则过滤流量，通过规则表达式构成，多条之间为且的关系。

  支持作为过滤条件的字段类型包括：Cookie、主机名、IP地址、地域、refer、请求方法、URI、HTTP版本、UA等

* 操作动作：

  定义匹配规则时安全加速执行的动作。可进行处理的动作包括：
  
  阻止:用户请求被阻断并drop。
  
  JS挑战:对请求发起JavaScript代码执行的挑战，验证其请求的真实性。
  
  验证码：用户会收到验证码挑战页面。
  
  允许:用户请求被允许通过并在日志中记录。
  
  绕过：绕过某些安全功能。



