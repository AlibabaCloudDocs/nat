# ConvertBandwidthPackage

调用ConvertBandwidthPackage将NAT带宽包转换为共享带宽。

## API描述

NAT带宽包转换为共享带宽前，请先了解：

-   转换操作，不会产生额外费用。
-   转换过程中，NAT网关原有SNAT条目和DNAT条目不受影响，也不会对正在运行的业务产生影响，但还是建议您在业务低峰期进行转换操作。
-   转换后，NAT带宽包中的公网IP将转换为EIP。共享带宽的带宽峰值、计费方式与原有NAT带宽包保持一致。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=ConvertBandwidthPackage&type=RPC&version=2016-04-28)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ConvertBandwidthPackage|要执行的操作，取值：**ConvertBandwidthPackage**。 |
|BandwidthPackageId|String|是|bwp-bp1xea10o8qxw4f\*\*\*\*|NAT带宽包的ID。 |
|RegionId|String|是|cn-hangzhou|NAT网关所在的地域。您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。 |
|ClientToken|String|否|123e4567-e89b-12d3-a456-426655440000|保证请求幂等性。从您的客户端生成一个参数值，确保不同请求间该参数值唯一。**ClientToken**只支持ASCII字符，且不能超过64个字符。详细信息，请参见[如何保证幂等性](~~36569~~)。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ConvertInstanceId|String|cbwp-s6lmotmkkf567b\*\*\*\*|转换后的共享带宽实例ID。 |
|RequestId|String|0C2EE7A8-74D4-4081-8236-CEBDE3BBCF50|请求ID。 |

## 示例

请求示例

```

http(s)://[Endpoint]/?Action=ConvertBandwidthPackage
&BandwidthPackageId=bwp-bp1xea10o8qxw4f****
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

```
<ConvertBandwidthPackageResponse>
	  <RequestId>0C2EE7A8-74D4-4081-8236-CEBDE3BBCF50</RequestId>
	  <ConvertInstanceId>cbwp-s6lmotmkkf567b****</ConvertInstanceId>
</ConvertBandwidthPackageResponse>
```

`JSON` 格式

```
{
	"RequestId":"0C2EE7A8-74D4-4081-8236-CEBDE3BBCF50",
	"ConvertInstanceId":"cbwp-s6lmotmkkf567b****"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|500|InternalError|The request processing has failed due to some unknown error.|请求处理由于某些未知错误失败。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

