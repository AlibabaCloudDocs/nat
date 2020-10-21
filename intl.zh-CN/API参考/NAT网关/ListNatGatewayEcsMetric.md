# ListNatGatewayEcsMetric

调用ListNatGatewayEcsMetric接口查看NAT网关的流量监控数据。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=ListNatGatewayEcsMetric&type=RPC&version=2016-04-28)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListNatGatewayEcsMetric|要执行的操作，取值：**ListNatGatewayEcsMetric**。 |
|NatGatewayId|String|是|ngw-2vc53wynunp35lw1y\*\*\*\*|要查看流量监控数据的NAT网关ID。

 **说明：** 只支持单个NAT网关实例查询。 |
|RegionId|String|是|cn-chengdu|NAT网关实例所属的地域，您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。 |
|TimePoint|Long|是|1602653760|要查看流量监控数据的时间戳，分钟级。

 例如您要查看2020-07-13 17:22:00至2020-07-13 17:23:00的流量监控数据，您要传2020-07-13 17:22:00的时间戳。 |
|DryRun|Boolean|否|false|是否只预检此次请求，取值：

 **true**：发送检查请求，不会查看流量监控数据。检查项包括AccessKey是否有效、RAM用户的授权情况和是否填写了必需参数。如果检查不通过，则返回对应错误。如果检查通过，会返回错误码`DryRunOperation`。

 **false**（默认值）：发送正常请求，通过检查后返回2XX HTTP状态码并查看流量监控数据。 |
|OrderKey|String|否|ActiveSessionNum|流量监控数据的排序字段，默认按照ActiveSessionNum排序。 |
|OrderType|String|否|desc|流量监控数据的排序规则，取值：

 -   **desc**（默认值）：降序。
-   **asc**：升序。 |
|PrivateIpAddress|String|否|192.168.0.12|要查看流量监控数据的ECS实例的IP地址。 |
|NextToken|String|否|caeba0bbb2be03f84eb48b699f0a4883|查询凭证（Token），取值为上一次API调用返回的NextToken参数值。如果没有下一个查询，请不传。 |
|MaxResults|String|否|20|分页大小，取值范围：**10**~**20**，默认为**20**。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|MaxResults|Integer|1|分页大小。 |
|MetricDataList|Array of MetricData| |流量监控数据列表。 |
|ActiveSessionNum|Long|6|分钟并发连接数，单位为个。 |
|NatGatewayId|String|ngw-2vc53wynunp35lw1y\*\*\*\*|要查看流量监控数据的NAT网关ID。 |
|NewSessionRate|Long|0|新建连续速率，单位为个/秒。 |
|PrivateIpAddress|String|192.168.0.12|要查看流量监控数据的ECS实例的IP地址。 |
|RxBps|Long|125|出方向流量，单位为bps。 |
|RxPps|Long|2|出方向包，单位为个/秒。 |
|Timestamp|Long|1602653760|要查看流量监控数据的时间戳，分钟级。 |
|TxBps|Long|125|入方向流量，单位为bps。 |
|TxPps|Long|2|入方向包，单位为个/秒。 |
|NextToken|String|caeba0bbb2be03f84eb48b699f0a4883|下一个查询开始Token，NextToken为空说明没有下一个。 |
|RequestId|String|0ED8D006-F706-4D23-88ED-E11ED28DCAC0|请求ID。 |

## 示例

请求示例

```
https://vpc.aliyuncs.com/?Action=ListNatGatewayEcsMetric
&NatGatewayId=ngw-2vc53wynunp35lw1y****
&RegionId=cn-chengdu
&TimePoint=1602653760
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<ListNatGatewayEcsMetricResponse>
  <RequestId>F3C9E92A-0BAA-4444-ABD9-4E41BADBBD3E</RequestId>
  <NextToken></NextToken>
  <MetricDataList>
        <PrivateIpAddress>192.168.0.48</PrivateIpAddress>
        <RxBps>1178</RxBps>
        <TxBps>45593</TxBps>
        <RxPps>2</RxPps>
        <TxPps>4</TxPps>
        <ActiveSessionNum>6</ActiveSessionNum>
        <NewSessionRate>0</NewSessionRate>
        <NatGatewayId>ngw-2vc53wynunp35lw1y****</NatGatewayId>
        <Timestamp>1602653760</Timestamp>
  </MetricDataList>
  <MaxResults>1</MaxResults>
</ListNatGatewayEcsMetricResponse>
```

`JSON` 格式

```
{
  "RequestId": "F3C9E92A-0BAA-4444-ABD9-4E41BADBBD3E",
  "NextToken": "",
  "MetricDataList": [
    {
      "PrivateIpAddress": "192.168.0.48",
      "RxBps": 1178,
      "TxBps": 45593,
      "RxPps": 2,
      "TxPps": 4,
      "ActiveSessionNum": 6,
      "NewSessionRate": 0,
      "NatGatewayId": "ngw-2vc53wynunp35lw1y****",
      "Timestamp": 1602653760
    }
  ],
  "MaxResults": 1
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Vpc)查看更多错误码。

