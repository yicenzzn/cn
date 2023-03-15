# 京东云高可用业务架构建设

- [一、应用场景](#一、应用场景)
- [二、环境准备](#二、环境准备)
  - [2.1 环境架构](#2.1 环境架构)
  - [2.2 环境介绍](#2.2 环境介绍)
  - [2.3 产品列表](#2.3 产品列表)

- [三、操作步骤](#三、操作步骤)
  - [3.1 基础环境准备](#3.1 基础环境准备)
  - [3.2 业务侧wordpress配置](#3.2 业务侧wordpress配置)
  - [3.3 实例模板及高可用组、LB配置](#3.3 实例模板及高可用组、LB配置)

- [四、验证测试](#四、验证测试)

## 一、应用场景

本文以 2022 年一个实际项目为基础，来演示在京东云上构建高可用业务的整个过程。公有云及私有云客户可通过使用京东云的弹性 IAAS、PAAS 服务，创建高可用、高弹性、高可扩展、高安全的云上业务环境，提升业务 SLA, 提升运维自动化水平，降低资源成本及运维成本。有业务迁移上云需求，希望构建云上高可用业务架构的客户或对云上高可用架构规划有兴趣的读者可以一看。

客户业务为典型的 web 应用，在京东云上创建一个通过公网 IP/ 域名访问的高可用的 web 网站，包含通用应用的标准框架，包括访问接入层、APP 层、缓存层、数据库层。整体业务架构设计提供可用区 (AZ) 级别的高可用等级。

**本文演示场景包括**单 AZ 出现故障导致的主机故障、数据库故障、缓存故障场景下，业务能够提供持续访问能力。并保障数据的完整性和一致性，同时，能够在无人干预的条件下，实现业务的弹性扩展，保障业务高并发的场景下有良好的响应时间。

**说明：**本文的架构为演示架构，并未严格遵循生产环境的业务性能及安全的整体规划步骤及要求，在生产环境中，至少应该对主机及 CFS 的存储性能进行压测，确保能够满足实际业务需求，同时，通过域名访问的 web 服务，建议使用 WAF 等安全防护产品，保障业务的入口安全。

## 二、环境准备

### 2.1 环境架构

![图片](../../../../image/Best-Practice/Service-Construction/640.jpeg)

### 2.2 环境介绍

业务架构以某单位的业务需求为基础，模拟其业务生产环境，规划京东云上的业务整体架构，其中，NAT网关、负载均衡、堡垒机均创建在公网访问子网，其余主机及数据库等，创建在内部子网内。

其中应用主机使用高可用组创建， LB后端直接挂载高可用组。

使用高可用组的目标是实现业务高峰期故障时，计算资源能自动加入负载均衡后端，自动化扩展业务处 理能力。减少运维干预成本。

### 2.3 产品列表

| 项目       | 规格                          | 数量 | 说明                                                         |      |
| ---------- | ----------------------------- | ---- | ------------------------------------------------------------ | ---- |
| 云主机     | 2C8G 50G系统盘                | 2~3  | 为保障验证效果，主机能临时绑定公网IP (生产环境无需绑定) 100.126.38.2 (公) 10.0.1.16 100.126.38.3 (公)    10.0.1.13 10.0.1.16 演示过程中会有新主机生成 |      |
| 高可用组   | 使用应用主机模板              | 1    | 配置弹性伸缩，配置告警条件，在业务压力大导致CPU触发阈值后，自动扩容主机，提升负载能力 |      |
| 云数据库   | 2C8G 50GSSD 存储 MySQL  5.7   | 1    | mysql -1-a0b7e160c1xxxx.jdcloud.com                          |      |
| 云Redis    | 4G                            | 1    | redis-1kn4b5zwgzc5-xxxn-1.jdcloud.com                        |      |
| 弹性公网IP | 4个，主机及LB各一个           | 4    | 5M带宽                                                       |      |
| LB         | 1个，配1个公网IP 作为业务入口 | 1    | LB绑定公网IP，配置轮询模式。例如， Vip： 10.0.1.27 公网 IP： 100.126.35.4 |      |
| CFS        | 1个                           | 1    | 共享存储作为业务应用数据存储目录挂载于高可用组主机特定目录下：例如，mount -t nfs -o vers=3 -o  noresvport  10.0.0.200:/cfs /wp |      |

## 三、操作步骤

### 3.1 基础环境准备

业务以一个典型的wordpress的网站为例，业务容器化部署于云主机上，高可用依赖京东云的云主机高可用组，主机安装docker，并配置docker服务自动启动。

```bash
#创建应用数据目录 配置目录权限、安装docker等
 mkdir -p /wp
 chmod 777 /wp
 yum install docker vim -y
 systemctl enable docker
 systemctl start docker
 #挂载CFS文件作为应用数据目录
 yum install nfs-utils -y
 systemctl enable rpcbind    
 systemctl start rpcbind
 mount -t nfs -o vers=3 -o noresvport 10.0.0.200:/cfs /wp
#配置启动自动挂载CFS及启动服务，通过rc.local实现：
#[root@wpha0 wp]# cat /etc/rc.local
#!/bin/bash
# THIS FILE IS ADDED FOR COMPATIBILITY PURPOSES
#
# It is highly advisable to create own systemd services or udev rules
# to run scripts during boot instead of using this file.
#
# In contrast to previous versions due to parallel execution during boot
# this script will NOT be run after all other services.
#
# Please note that you must run 'chmod +x /etc/rc.d/rc.local' to ensure
# that this script will be executed during boot.
touch /var/lock/subsys/local
mount -t nfs -o vers=3 -o noresvport 10.0.0.200:/cfs /wp
#（说明，生产环境可在/etc/fstab挂载）
bash /root/start.sh
start.sh见以下代码
[root@wpha0 wp]# cat /root/start.sh
docker stop wordpress
sleep 3
docker rm wordpress
sleep 3
docker run -d --name=wordpress --restart=unless-stopped -p 443:443 -p 80:80 -v /wp:/var/www/html wordpress
#[root@wpha0 wp]#
#启动脚本编辑完成后，并写入rc.local后，rc.local调整成可执行，以实现启动主机运行脚本， rc.local实现了主机启动后自动挂载CFS到指定目录，然后，通过start.sh自动清除旧数据，重新拉起wordpress服务。
chmod +x /etc/rc.d/rc.local
#拉取应用所需镜像
 docker pull wordpress
#拉取镜像后，运行服务。
docker run -d --name=wordpress --restart=unless-stopped -p 443:443
```

注意，这个场景下，主要调整了几个位置：

1. 挂载CFS为wordpress的工作目录，这样，调整页面内容以及拉起新主机后，网站内容都保持一致。相关自动挂载方式为在`/etc/rc.local`加入挂载命令，同时`chmod +x /etc/rc.d/rc.local` 把这个文件加一下可执行权限。
2. 需要把wp目录的权限改为777 （或docker内部的 33 tape等，不过不同版本可能有区别，改成777相对稳妥）， 否则挂载后，docker内部的wordpress无法获取目录读写权限。
3. NFS挂载需要安装nfs插件`yum install nfs-utils -y` 并启动rpc服务`systemctl enable rpcbind`    `systemctl start rpcbind`

WP目录为777 权限

![图片](../../../../image/Best-Practice/Service-Construction/640-1677584869153-3.jpeg)

到这里基础主机环境准备完成。

下一步，进行wordpress应用的配置，实现高可用可视化的演示效果。

### 3.2 业务侧wordpress配置

web应用使用wordpress部署。通过docker部署，并实现高可用组主机自动伸缩自动化拉起。

```bash
# 通过docker拉取wordpress 
docker pull wordpress

# 拉取镜像后
docker run -d --name=wordpress --restart=unless-stopped -p 443:443 -p 80:80 -v /wp:/var/www/html wordpress
# 其中/wp 是挂载的CFS，作为多个应用主机共同挂载，作为wordpress的应用的应用文件目录。
# 启动wordpress容器，并挂载CFS目录为WP的应用目录。
# 以上部署在前面已经完成。

# 前置准备工作-负载均衡：
# 配置一个带公网IP的负载均衡，并配置监听器，监听器后端暂时配置一个已经拉起了docker的这台主机 

# 前置准备工作-数据库：
# 在配置网站前，需要首先在云控制台的RDS那里为wordpress创建一个账户：wordpress，并设置密码，建立一个库：wordpress（因为后续演示方案有调整，我又创建了一个新库wordpressbackup，实际正常来讲一个库就可以了），并授权wordpress库给wordpress用户。

# 前置准备工作-redis：
# 在控制台购买一个redis，记录redis的URL，为后续配置redis 缓存做准备。

# 这样，基本的应用环境就绪了。
```

通过浏览器访问负载均衡(注意访问LB，不直接访问主机)的IP的80端口，即可进入wordpress的配置 页面， wordpress的配置，主要是数据库的地址以及数据库前缀的配置，输入正确的数据库的host 地址及密码即可，其余保持默认，其他依据官网手册指导保持默认配置即可。

配置完成后，wordpress会自动为网站创建相关的表，并提示配置wordpress的admin以及管理密码。

安装完成后，可以登录数据库查看创建的表，后续MySQL高可用演示时，也可以登录到数据库做些常规 操作，不受高可用切换影响。

到此，基本的应用就安装完成了。

![image-20230228194928397](../../../../image/Best-Practice/Service-Construction/image-20230228194928397.png)

配置redis动态缓存加速：

redis的角色，在这个案例里边，在wordpress里 redis 作为一个动态加速缓存使用，对加速网站访问， 减轻数据库压力起到一定作用。

下载wordpress的redis插件，redis-cache。

下载后通过wordpress的管理页面-plugin --addnew 直接上传，然后依据插件操作手册安装配置即可。

![图片](../../../../image/Best-Practice/Service-Construction/640-1677584987647-6.jpeg)

安装redis-cache以后，会在/wp/wp-content/plugins 目录下生成一个 redis-cache目录。需要同时在/wp/wp- content 下生成一个 object-cache.php文件，正常来讲，需要调整一个参数host改成redis的域名即可。如果配置了密码，就需要调整这个以及redis-cache目录下的配置文件把密码配置进去，这个因为是 演示环境，redis设置 了免密，生产环境一定要设置密码。

![image-20230228195027819](../../../../image/Best-Practice/Service-Construction/image-20230228195027819.png)

安装配置完成后，在管理界面的setting里会有redis的配置选项，这个和版本有关系，有些版本可能会让在这里做参数配置。直接改文件参数效果是一样的。

![图片](../../../../image/Best-Practice/Service-Construction/640-1677585046678-9.jpeg)

mysql及redis管理及相关登录方式介绍：

```bash
# MySQL的登录，没有安装client，使用了一个mysql的docker
# 相关命令：
docker run --name mysql -p 3306:3306 --restart=unless-stopped -v /root/dbackup/:/db -e MYSQL_ROOT_PASSWORD=123456 -d mysql:5.7
# 进入mysql的docker中：
docker exec -it mysql bash
# 连接wordpress使用的数据库：
mysql -h mysql-xxxea04fc4c52.jdcloud.com -u wordpress -p
use wordpressbackup;
show tables;
select id from wpbackup_posts;

# --中间因为做了多次演练和数据库切换，中间做了wordpress数据库导出和导入操作
# mysql 数据库导出（均在mysql的docker容器中执行命令）：
mysqldump  -h  mysql-xxxa04fc4c52.jdcloud.com -uwordpress -p --databases wordpressbackup >/db/wordpressbackup-0322.sql
# 数据导入：
# 进入数据库，
use wordpressbackup;
source /db/wordpressbackup-0322.sql;

# ----redis验证
# redis验证，同样是没有安装client，通过docker里的命令行去连接：
docker run -d --name redis --memory=1G -p 7379:6379   redis
docker exec -it redis bash   

# redis-cli -h redis-j49rpxxx.jdcloud.com

# 登入后，查看信息：
KEYS *
```

wordpress配置主页显示hostname及来源IP

让wordpress获取hostname 并在页面展示+获取访客地址，以增强演示效果，明确看到访问的实际主 机位置。

为了让访问者看到访问的IP是哪个（证实高可用组的自动扩容及业务的自动拉起），需要在所使用的 theme 目录的function里加入相关代码。

```bash
]# vim /wp/wp-content/themes/twentytwentytwo/function.php
```

在里边加入以下代码，一个是`show_ip`函数，一个是`show_hostname`函数。

```php
function get_the_user_ip() {
    if ( ! empty( $_SERVER["HTTP_CLIENT_IP"] ) ) {
        //check ip from share internet
        $ip = $_SERVER["HTTP_CLIENT_IP"];
    } elseif ( ! empty( $_SERVER["HTTP_X_FORWARDED_FOR"] ) ) {
        //to check ip is pass from proxy
        $ip = $_SERVER["HTTP_X_FORWARDED_FOR"];
    } else {
        $ip = $_SERVER["REMOTE_ADDR"];
    }
    return apply_filters( "wpb_get_ip", $ip );
}
add_shortcode("show_ip", "get_the_user_ip");

function get_hostname()
{
    $hostname = gethostname();
    echo "$hostname\n";
    return apply_filters( "hostname", $hostname );
}

add_shortcode("show_hostname", "get_hostname");
```

然后，在wordpress的site里加入短代码实现：

![图片](../../../../image/Best-Practice/Service-Construction/640-1677585177394-12.jpeg)

保存后，看到页面可以显示相关的IP及hostname信息了。

![image-20230228195451732](../../../../image/Best-Practice/Service-Construction/image-20230228195451732.png)

到这里，wordpress的应用环境配置完成。

下一步配置业务的高可用环境，实现跨AZ的高可用组及主机自动弹性伸缩。

### 3.3 实例模板及高可用组、LB配置

单台主机配置完成后，重启能自动拉起应用，进行确认后， 将现有主机打一个镜像。作为高可用组的实例模板。后续LB后端的高可用组通过这个模板创建主机。

其余包括数据库配置、网站数据、redis缓存配置等，均实现了服务及数据的分离，因此，在后期进行动态弹性扩容时，使用这个模板的高可用组，可以直接拉起服务，实现动态弹性伸缩。

**实例模板：**

![image-20230228195546923](../../../../image/Best-Practice/Service-Construction/image-20230228195546923.png)

![image-20230228195639284](../../../../image/Best-Practice/Service-Construction/image-20230228195639284.png)

**高可用组：**

高可用组使用制作好了wordpress的应用主机的镜像。做到高可用组自动弹性伸缩出新主机--新主机自动 拉起wordpress应用--新主机自动挂载到LB接收业务流量的模式。

![image-20230228195714850](../../../../image/Best-Practice/Service-Construction/image-20230228195714850.png)

![img](../../../../image/Best-Practice/Service-Construction/640-1677585451906-19.jpeg)

![image-20230228195809283](../../../../image/Best-Practice/Service-Construction/image-20230228195809283.png)

**LB配置：**

LB监听器选择后端服务为高可用组，并配置健康检查。

![图片](../../../../image/Best-Practice/Service-Construction/640-1677585514679-22.jpeg)

![image-20230228195913051](../../../../image/Best-Practice/Service-Construction/image-20230228195913051.png)

高可用组挂载到LB后端以后，应用环境已经搭建完成。

可以访问LB入口，访问到网站，并且会轮询到不同服务器，同时，访问单台服务器的外网IP也可以访问网站业务：

LB访问截图(2张，分别访问到了两个主机)

![image-20230228195937300](../../../../image/Best-Practice/Service-Construction/image-20230228195937300.png)

![image-20230228200003209](../../../../image/Best-Practice/Service-Construction/image-20230228200003209.png)

单台主机访问截图（直接访问单台主机IP，刷新后不会轮询主机）：

![image-20230228200022190](../../../../image/Best-Practice/Service-Construction/image-20230228200022190.png)

演示环境就绪。

下一步，进行破坏性演练，检验高可用环境的效果。

## 四、验证测试

高可用演示脚本：

| 验证项目 | 详细描述                                                     | 预期结果                                                     |      |
| -------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ---- |
| 云主机   | 模拟主机故障- 通过底层命令/控制台关闭可用区A的应用云主机     | 站点访问正常，可以新增、删除、修改post                       |      |
| 高可用组 | 高可用组配置弹性伸缩，设置最小最 大实例个数，并配置伸缩触发的阈值 (告警配置内配置) | 通过stress命令模拟高并发场景，高可用组通 过弹性伸缩特性创建新主机并挂载到LB后，实现多主机接收流量 |      |
| RDS      | 模拟RDS实例故障- 通过底层命令关闭 RDS的主实例                | - 主从切换，业务不受影响                                     |      |
| RDS      | 主从切换从控制台可以看到切换过程                             | 切换过程完成后，  RDS状态为运行中                            |      |
| Redis    | 模拟Redis实例故障- 通过底层命令关闭Redis的主实例             | - 主从切换，业务不受影响（本文未截图）                       |      |
| Redis    | redis在模拟故障过程中，业务持续访问                          | 从redis返回的数据不受切换影响（本文未截图）                  |      |

高可用组信息，目前LB后端挂载的为高可用组：

测试页面信息（所有IP均为非真实IP）：

业务入口(LB)：http://100.126.35.4/

高可用组单台主机访问入口目前为：

http://100.126.38.13/

http://100.126.38.16

主机的高可用及自动伸缩：

演示所需的一些脚本：

一个是模拟生产环境，对业务主入口的LB持续访问，这个在测试过程中，一直可以访问到，不会中断。

```bash
#!/bin/bash
#for ((i=1;i<=10;i++))
for i in {1..15000}
do
    curl 100.126.35.4
    echo $i
    echo $(date +%T)
    sleep 3
done
```

一个是模拟单机环境，对业主机入口的持续访问，这个在测试过程中，当针对单机关机时，访问会卡住。

```bash
#!/bin/bash
#for ((i=1;i<=10;i++))
for i in {1..15000}
do
    curl 100.126.38.16
    echo $i
    echo $(date +%T)
    sleep 3
done
```

演示过程中，高可用组自动伸缩功能，能正常扩容出新的主机并提供业务访问。

高可用组的自动伸缩，通过 stress模拟压力

```bash
# 安装stress后，直接运行（主机为2C）：
stress --CPU 2

# 通过top命令可以看到CPU被打满。
# 过2分钟（高可用组伸缩策略配置的时间），高可用组会自动扩展一台主机，
# 并作为高可用组的一台主机自动挂载到LB的后端，可在LB及主机界面看到自动扩容的主机。
```

![image-20230228200141615](../../../../image/Best-Practice/Service-Construction/image-20230228200141615.png)

在控制台将一台高可用组内主机关机，然后可见LB后端服务健康检查发现挂载的高可用组一台服务器异常，高可用组如配置最小的主机数量，则高可用组也自动扩出一台主机，继续提供服务。在此期间，流量会转发给后端正常主机，健康检查异常的主机不再接收流量，业务访问持续正常。

![image-20230228200246749](../../../../image/Best-Practice/Service-Construction/image-20230228200246749.png)

![image-20230228200319766](../../../../image/Best-Practice/Service-Construction/image-20230228200319766.png)

PAAS服务的高可用：

本演示以MySQL及redis在底层直接杀docker，然后业务访问不中断，控制台上会出现主从切换现象在这个过程中对业务的访问不会中断。

底层进行RDS主备切换（kill掉RDS主库），业务访问同样不会中断，提供截图可以看到主从切换过程。

![image-20230228200451677](../../../../image/Best-Practice/Service-Construction/image-20230228200451677.png)

![image-20230228200615500](../../../../image/Best-Practice/Service-Construction/image-20230228200615500.png)

本文实际部署环境为京东为客户搭建的私有云环境（JDSTACK），公有云与私有云为相同技术栈，搭建及验证过程相似。限于篇幅，redis验证部分及主机可访问性脚本结果未截图，感兴趣的读者可自行在云上通过本文指引过程搭建验证。