# 地域及可用区
京东云合作云主机机房分布在全球多个位置，这些位置称为地域。每个地域（region）都是一个独立的地理区域，每个地域都是完全独立的。

京东云支持您在不同地域部署云业务，同时为了避免单地域部署可能带来的单点风险，建议在部署方案设计阶段考虑多地域多可用区部署。实例创建后，不支持更换地域或更换可用区。

可用区（Availability Zone）是电力及网络之间互相独立的物理区域，相同可用区内的实例之间较之同地域不同可用区内实例之间的网络延时更小。同地域内不同可用区之间提供内网互通环境，可用区之间可做到故障隔离。

* 若您的业务要求有较高容灾能力，建议将实例部署在同一地域不同可用区内；
* 若您的业务要求有较低网络时延，建议将实例部署在同一可用区内。


## 京东云合作地域及可用区分布
<table>
	<thead>
	<tr>
		<th colspan="2">地域名称及编码</th>
      	<th>可用区名称及编码</th>
      	<th>所在城市</th>
   	</tr>
		</thead>
	<tbody>
   	<tr>
      	<td rowspan="10">亚太地域</td>
      	<td rowspan="3">中国-香港-11<br>cn-hongkong-11</td>
     	<td> 可用区A<br>cn-hongkong-11a</td>
	   	<td> 香港</td>
   </tr>
		
   <tr>
     	<td> 可用区B<br>cn-hongkong-11b</td>
	   	<td> 香港</td>
   </tr>
   <tr>
     	<td> 可用区C<br>cn-hongkong-11c</td>
	   	<td> 香港</td>
   </tr>
   <tr>
     	<td rowspan="4">亚太-新加坡-11<br>ap-singapore-11</td>
     	<td>可用区A<br>ap-singapore-11a</td>
	   	<td>新加坡</td>
   </tr>
   <tr>
     	<td> 可用区B<br>ap-singapore-11b</td>
	   	<td> 新加坡</td>
   </tr>
   <tr>
     	<td> 可用区C<br>ap-singapore-11c</td>
	   	<td> 新加坡</td>
   </tr>
   <tr>
     	<td> 可用区D<br>ap-singapore-11d</td>
	   	<td> 新加坡</td>
   </tr>
   </tr>
    	<tr>
     	<td rowspan="3">亚太-曼谷<br>ap-thailand-11</td>
     	<td>可用区A<br>ap-thailand-11a</td>
	   	<td>曼谷</td>
   </tr>
      </tr>
    	<tr>
     	<td>可用区B<br>ap-thailand-11b</td>
	   	<td>曼谷</td>
   </tr>
       	<tr>
     	<td>可用区C<br>ap-thailand-11c</td>
	   	<td>曼谷</td>
   </tr>
   </tbody>
</table>

> 实际可使用可用区请以控制台显示为准。

