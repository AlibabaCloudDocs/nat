# ListEnhanhcedNatGatewayAvailableZones

调用ListEnhanhcedNatGatewayAvailableZones接口查询增强型NAT网关的资源可用区。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=ListEnhanhcedNatGatewayAvailableZones&type=RPC&version=2016-04-28)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListEnhanhcedNatGatewayAvailableZones|要执行的操作，取值：**ListEnhanhcedNatGatewayAvailableZones**。 |
|RegionId|String|是|cn-qingdao|要查询的地域ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|0ED8D006-F706-4D23-88ED-E11ED28DCAC0|请求ID。 |
|Zones|Array of Zone| |可用区集合。 |
|LocalName|String|华北1 可用区 A|可用区名称。 |
|ZoneId|String|cn-qingdao-a|可用区ID。 |

## 示例

请求示例

```
http(s)://vpc.aliyuncs.com/?Action=ListEnhanhcedNatGatewayAvailableZones
&RegionId=cn-qingdao
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<ListEnhanhcedNatGatewayAvailableZonesResponse>
  <RequestId>9AD606B4-5DE0-4868-AF98-EEC00C14304C</RequestId>
  <Zones>
        <ZoneId>cn-hangzhou-h</ZoneId>
        <LocalName>华东 1 可用区 H</LocalName>
  </Zones>
  <Zones>
        <ZoneId>cn-hangzhou-i</ZoneId>
        <LocalName>华东 1 可用区 I</LocalName>
  </Zones>
</ListEnhanhcedNatGatewayAvailableZonesResponse>
```

`JSON` 格式

```
{
	"RequestId": "9AD606B4-5DE0-4868-AF98-EEC00C14304C",
	"Zones": [
		{
			"ZoneId": "cn-hangzhou-h",
			"LocalName": "华东 1 可用区 H"
		},
		{
			"ZoneId": "cn-hangzhou-i",
			"LocalName": "华东 1 可用区 I"
		}
	]
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Vpc)查看更多错误码。

