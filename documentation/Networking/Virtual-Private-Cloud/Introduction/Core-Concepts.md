## 专业术语

|   **英文**    |   **中文**   | **说明**                                                     |
| :----------- | :---------- | ----------------------------------------------------------- |
|      VPC      |   虚拟网络   | 京东公有云上自定义的逻辑隔离的网络空间，与您在数据中心搭建的传统网络类似，此私有网络空间由用户完全掌控，支持自定义网段划分、路由策略等。用户可以在VPC内创建和管理多种云产品，如云主机、负载均衡等，同时可配置网络内的资源连接Internet。另外，您可以通过专线/VPN接入，打通您的IDC内网和京东云网络，实现应用的混合云部署，以及将应用平滑地迁移至云上。 |
|    Subnet     |     子网     | 子网是所属VPC IP地址范围内的 IP 地址块。目前私有网络中的部分云资源部署在子网内，如云主机、负载均衡。子网base在VPC下，在创建 VPC后，您可以在VPC下添加子网。相同VPC下子网的IP地址块不可以重叠，不同VPC下子网的IP地址块可以重叠。子网支持两种类型：标准子网和边缘子网。 |
|    Standard Subnet     |     标准子网     | 子网类型，标准子网不与边缘可用区绑定，目前在标准子网只能创建资源到中心可用区。 |
|    Edge Subnet     |     边缘子网     | 子网类型，边缘子网只会与一个独立边缘可用区绑定，边缘子网只能创建资源到绑定的独立边缘可用区。 |
|      RTB      |    路由表    | 路由表是一系列路由规则的集合，用于控制私有网络中子网的流量流出方向。京东云共有两种类型的路由表：默认路由表和自定义路由表。随私有网络创建时自动创建的路由表为默认路由表，用户主动创建的路由表为自定义路由表。每个子网都必须关联一张路由表且只能关联一张路由表，每张路由表可以关联多个子网。 |
|      ACL      | 访问控制列表 | 子网级别无状态的可选安全层，用于控制进出子网的数据流，可以精确到协议和端口粒度，可用作防火墙来控制进出一个或多个子网的流量。没有网络ACL的保护或者没有配置访问控制策略，会导致子网中的服务器所有网络端口更容易在互联网上遭受攻击甚至导致被入侵。网络ACL可用于对跨子网的东西向访问流量或者进出互联网的南北向访问流量进行过滤。具有相同网络流量控制的子网可以关联同一个网络 ACL，通过设置出站和入站允许规则，对进出子网的流量进行精确控制。 |
|  Elastic IP   |  弹性公网IP  | 弹性公网IP是可以独立申请的公网IP地址，支持与云主机、负载均衡、NFV实例等资源进行动态绑定和解绑，弹性公网IP支持两种类型：标准公网IP和边缘公网IP。 |
|  Standard Elastic IP   |  标准公网IP  | 标准弹性公网IP在地域中心可用区发布，可以绑定中心可用区的资源。 |
|  Edge Elastic IP   |  边缘公网IP  | 边缘弹性公网IP，IP地址在边缘可用区发布，最终客户可以就近接入，满足客户高带宽、低时延的要求。 |
| NFV Instance  |   NFV实例    | NFV为Network Function Virtualization的缩写。NFV实例是采用软件技术与虚拟化技术所实现的具备传统网络功能的虚拟网络设备。例如：以镜像方式创建的VPN网关、NAT网关虚机实例等。 |
|      BGP      | 边界网关协议 | BGP为Border Gateway Protocol的缩写。网络运营商之间通过BGP协议互相宣告IP地址段，BGP IP可以实现单IP多线路，达到不同运营商用户可以高速访问的效果。 |
|    Region     |     地域     | 不同的地域即不同的地理区域。目前京东云有四个地域，分别为华北-北京、华南-广州、华东-宿迁、华东-上海。 |
| Availability Zone |    可用区    | Availability Zone简称AZ。单个地域下可以包含多个AZ，不同AZ之间实现资源隔离，保障资源的高可用性。同地域下的AZ通常采用低延迟与高带宽的线路进行互联。AZ代表是中心可用区。 |
| Tethered Edge Zone |    边缘可用区    | Tethered Edge Zone简称EZ。京东云外联边缘可用区是由京东云设置并管理的中小型边缘数据中心。 |
| Tethered Independent Edge Zone |    独立边缘可用区    | Tethered Independent Edge Zone为外联独立边缘可用区，通过VPN与中心可用区互联，外联独立边缘可用区的计算资源与公有云中心区域的计算资源管理通道打通，数据通道隔离。 |
| Tethered Express Edge Zone |    高速边缘可用区    | Tethered Express Edge Zone为外联高速边缘可用区，通过专线与中心可用区互联，外联高速边缘可用区的计算资源与公有云中心区域的计算资源管理通道和数据通道都互通。 |
|  VPN Gateway  |   VPN网关    | VPN为Virtual Private Network的缩写。VPN网关是基于互联网，通过加密隧道技术将企业数据中心与云上VPC进行安全互联的产品。 |
|  NAT Gateway  |   NAT网关    | NAT为Network Address Translator的缩写。NAT网关可以为用户提供企业级VPC公网接入服务。 |
| Load Balancer |   负载均衡   | 负载均衡可以对多台云主机进行流量分发，提升应用系统的对外服务能力，消除单点故障。 |
|      BGW      |   边界网关   | 数据中心南北向网关对接专线通道，提供客户业务的虚拟网络通道。 |
|   Instance    |     实例     | 特指云主机、容器资源。                                       |

## 相关参考
- [VPC](Features/VPC-Features.md)
- [产品优势](Benefits.md)
- [创建VPC](../Operation-Guide/VPC-Configuration.md)
- [地域及可用区](Region-Az.md)
