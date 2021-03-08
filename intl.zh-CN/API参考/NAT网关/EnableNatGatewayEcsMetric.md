# EnableNatGatewayEcsMetric

调用EnableNatGatewayEcsMetric接口开启ECS流量监控。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=EnableNatGatewayEcsMetric&type=RPC&version=2016-04-28)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|EnableNatGatewayEcsMetric|要执行的操作，取值：**EnableNatGatewayEcsMetric**。 |
|NatGatewayId|String|是|ngw-2vc53wynunp35lw1y\*\*\*\*|要开启ECS流量监控功能的NAT网关ID。 |
|RegionId|String|是|cn-chengdu|NAT网关所属的地域，您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。 |
|DryRun|Boolean|否|false|是否只预检此次请求，取值：

 **true**：发送检查请求，不会开启ECS流量监控。检查项包括AccessKey是否有效、RAM用户的授权情况和是否填写了必需参数。如果检查不通过，则返回对应错误。如果检查通过，会返回错误码`DryRunOperation`。

 **false**（默认值）：发送正常请求，通过检查后返回2XX HTTP状态码并开启ECS流量监控。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|0ED8D006-F706-4D23-88ED-E11ED28DCAC0|请求ID。 |

## 示例

请求示例

```
https://vpc.aliyuncs.com/?Action=EnableNatGatewayEcsMetric
&NatGatewayId=ngw-2vc53wynunp35lw1y****
&RegionId=cn-chengdu
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<EnableNatGatewayEcsMetricResponse>
      <RequestId>5AF873FB-6669-4AD5-A4DA-478D535C8F0D</RequestId>
</EnableNatGatewayEcsMetricResponse>
```

`JSON` 格式

```
{
	"RequestId": "5AF873FB-6669-4AD5-A4DA-478D535C8F0D"

}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Vpc)查看更多错误码。

