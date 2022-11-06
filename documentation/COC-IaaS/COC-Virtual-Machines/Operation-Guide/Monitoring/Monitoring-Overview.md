# 监控与报警概述
实例监控与报警为您提供实时实例监控管理服务，支持不同监控维度，在实例成功创建后即开始采集数据，以图表方式直观展现，方便您掌握实例资源使用情况、运行状态等信息，同时您可设置不同的报警规则，当触发该类条件后则触发报警通知，使您轻松定位故障。

## 监控指标
京东云为您提供云主机实例的CPU、内存、磁盘、网络等类型的监控指标。具有较高的通用性，能满足您平时对监控数据的需求，上报的指标种类不支持调整，可在云主机详情页或云监控-资源监控-云主机 下查看监控数据；

### 基础指标 
<table>
	<thead>
    <tr>
	<th>指标类型</th>
	<th>指标英文名</th>
        <th>指标中文名</th>
      	<th>单位</th>
      	<th>说明</th>
        <th>上报维度</th>
    </tr>
    <tr>
        <td rowspan="1">CPU</td>
        <td>vm.cpu.util</td>
	<td>CPU使用率</td>
	<td> % </td>
        <td> 非空闲vCPU所占的百分比</td>
        <td> 实例 </td>   
    </tr>
    <tr>
        <td rowspan="4">磁盘</td>
        <td>vm.disk.bytes.read</td>
	<td>磁盘读吞吐量（Host）<sup>*</sup></td>
	<td> Bps </td>
        <td> 全部磁盘每秒读取的字节数</td>
        <td> 实例 </td>   
    </tr>
    <tr>
        <td>vm.disk.bytes.write</td>
	<td>磁盘写吞吐量（Host）<sup>*</sup></td>
	<td> Bps </td>
        <td> 全部磁盘每秒写入的字节数</td>
        <td> 实例 </td>   
    </tr>	
    <tr>
        <td> vm.disk.dev.io.read</td>
        <td> 磁盘读IOPS </td>
        <td> Count/s</td> 
        <td> 磁盘每秒读请求数量</td>
    </tr> 
    <tr>
        <td> vm.disk.dev.io.write</td>
        <td> 磁盘写IOPS </td>
        <td>Count/s</td> 
        <td>磁盘每秒写请求数量</td>
    </tr>
    <tr>
        <td rowspan="4">网络</td>
        <td>vm.network.bytes.incoming </td>
        <td>网络入带宽（Host）<sup>*</sup></td>
        <td>bps</td> 
        <td>全部网卡每秒接收的比特数</td>
        <td>实例</td>
    </tr>
    <tr>
        <td>vm.network.bytes.outgoing</td>
        <td> 网络出带宽（Host）<sup>*</sup></td>
        <td>bps</td> 
        <td>全部网卡每秒接收的比特数</td>
        <td>实例</td>
    </tr>
    <tr>
        <td>vm.network.dev.packets.in </td>
        <td> 网络入包量</td>
        <td>pps</td> 
        <td> 网卡每秒入包量</td>
    </tr>
    <tr>
        <td>vm.network.dev.packets.out </td>
        <td> 网络出包量 </td>
        <td>pps</td> 
        <td>网卡每秒出包量</td>
    </tr>
    <tr>
</table> 
  
 ## 监控数据说明
* 名称中有“（Host）”字样的指标为云主机所在宿主机采集并上报，其余指标均为系统组件采集上报；
* 所有网络监控指标均不区分内外网，即为内网+外网的整体数据；
* 监控数据采集周期为10s，最小展示间隔为1min；
* 不同指标的默认聚合方式不同，可在监控图中查看各指标的聚合方式；
* 统计周期默认支持1小时、6小时、12小时、1天、3天、7天及14天，此外还支持您设置统计周期，最短为1分钟，最长为一个月。不同统计周期监控值会做对应聚合，例如6小时统计周期情况下，监控图上间隔5分钟显示一个监控值，该监控值为对应统计周期内采集值的聚合，当前仅支持以默认聚合方式查询；
* 监控数据最长保存30天，用户在控制台可以查看30天的监控数据。

## 监控指标单位
单位是监控指标的基本度量，下方为云监控所支持的指标单位：
<table>
	<thead>
    <tr>
	<th>单位</th>
	<th>说明</th>
    </tr>
	</thead>
	<body>
    <tr>
	<td>%</td>
	<td>百分比</td>
    </tr>
    <tr>
	<td>Bytes</td>
	<td>字节数，用于表示数据的大小。1Byte = 8bit</td>
    </tr>
    <tr>
	<td>Bps</td>
	<td>每秒字节数（bytes per second）</td>
    </tr>
    <tr>
	<td>bps</td>
	<td>每秒比特数（bits per second）</td>
    </tr>
    <tr>
	<td>pps</td>
	<td>每秒包数（packets per second）</td>
    </tr>
    <tr>
	<td>Count</td>
	<td>次数</td>
    </tr>
    <tr>
	<td>Count/s</td>
	<td>每秒操作的次数（counts per second）</td>
    </tr>
    <tr>
	</body>
</table>


  
## 相关参考
[官方镜像系统组件](https://docs.jdcloud.com/cn/virtual-machines/default-agent-in-public-image)

[获取实例监控数据](https://docs.jdcloud.com/cn/virtual-machines/get-monitor-data)

[云监控-自定义监控](https://docs.jdcloud.com/cn/monitoring/custom-monitoring-overview)

 
   
