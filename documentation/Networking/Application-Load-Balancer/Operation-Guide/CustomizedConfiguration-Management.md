# 个性化配置管理

[原理介绍](CustomizedConfiguration-Management#principle-introduction)

[添加个性化配置](CustomizedConfiguration-Management#add-CostomizedConfiguration)

[管理个性化配置](CustomizedConfiguration-Management#manage-CostomizedConfiguration)

## 原理介绍
<div id="principle-introduction"></div>
通过将个性化配置与应用负载均衡绑定来让应用负载均衡使用个性化配置中设置的配置项，进而满足您个性化的业务需求。目前个性化配置仅支持绑定应用负载均衡。

个性化配置是一系列配置项的集合，目前支持的配置项有：共享Session Ticket。个性化配置允许您修改每一条配置项的内容，确认修改后马上生效。一个个性化配置中有默认的配置项，默认配置项只允许修改，不允许删除。目前的默认配置项有：共享Session Ticket。

#### 共享Session Ticket

##### Session Ticket

在介绍共享Session Ticket配置项前，我们简单介绍一下 Session Ticket 入门。使用 Session Ticket 提供了一种快速恢复 TLS 会话的方式。

在 TLS 握手过程中，服务器端将会话状态通过一个仅该服务器端持有的密钥进行加密，并将加密后的会话状态等信息发送给客户端。这些加密后的信息被称之为 Session Ticket。当客户端再次请求访问相同的服务器端时，它可以在 TLS 握手时发送此 Session Ticket，当服务器端利用密钥识别出此 Session Ticket 之后即可恢复 TLS 会话，无需再进行完整的 TLS 握手。

使用 Session Ticket 可以大幅减少进行 TLS 握手的时间，快速恢复客户端与服务器端的 TLS 会话，从而提高服务效率。同时服务器端在发送完 Session Ticket 后可以删除掉与客户端的会话状态，释放掉这部分缓存，从而提高服务性能。

关于 Session Ticket 的更多信息，可阅读[[RFC 5077]](https://www.rfc-editor.org/rfc/rfc5077).

##### 共享Session Ticket 配置项

您在某个个性化配置里开启了共享Session Ticket 的配置项后，该个性化配置会为您生成一个用于加密 Session Ticket 的密钥。您可以将一个个性化配置与多个应用负载均衡绑定，此时所有应用负载均衡内所有的 HTTPS 监听器和 TLS 监听器均会使用该密钥与客户端通信，从而大幅降低时延并提高性能。

## 添加个性化配置
<div id="add-CostomizedConfiguration"></div>

1. 通过网络-负载均衡-个性化配置进入个性化配置列表页。

2. 点击**创建**，打开个性化配置创建弹窗，填写个性化配置名称和描述。

3. 创建完毕后，进入该个性化配置详情页，在配置信息处点击**编辑**，为个性化配置设置配置项。
    - 共享Session Ticket：
      - 该配置项为默认配置项，不可删除，默认为关闭；
      - 将开关打开，则该个性化配置会创建一个密钥；将打开的开关关闭，则该个性化配置会删除之前创建的密钥。
    
    **注意**：新添加的个性化配置绑定负载均衡后才会生效，具体请见[管理个性化配置](CustomizedConfiguration-management#manage-CostomizedConfiguration)。
    

## 管理个性化配置
<div id="manage-CostomizedConfiguration"></div>

1. 查看个性化配置：在个性化配置列表页点击个性化配置ID进入个性化配置详情页，可查看个性化配置的详细信息。
1. 编辑个性化配置：在详情页可以修改个性化配置名称；点击详情页的**编辑**，可设置个性化配置的配置项。
1. 删除个性化配置：点击个性化配置列表-操作栏下的**删除**或个性化配置详情-操作栏下的**删除**，可删除个性化配置。已经绑定负载均衡的个性化配置不允许删除，需要先解除所有的绑定后再删除
1. 绑定/解绑负载均衡：在个性化配置详情页的“绑定资源”Tab，通过点击**绑定**，可以将个性化配置与负载均衡进行绑定，目前仅支持绑定应用负载均衡；通过点击**解绑**，可以进行单条解绑，也可以通过勾选复选框进行批量解绑。
