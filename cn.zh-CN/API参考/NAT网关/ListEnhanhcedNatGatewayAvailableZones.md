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
      <RequestId>6FEA0CF3-D3B9-43E5-A304-D217037876A8</RequestId>
      <Zones>
            <Zone>
                  <ZoneId>cn-qingdao-a</ZoneId>
                  <LocalName>华北 1 可用区 A</LocalName>
            </Zone>
            <Zone>
                  <ZoneId>cn-qingdao-b</ZoneId>
                  <LocalName>华北 1 可用区 B</LocalName>
            </Zone>
      </Zones>
</ListEnhanhcedNatGatewayAvailableZonesResponse>
```

`JSON` 格式

```
{
	"RequestId":"6FEA0CF3-D3B9-43E5-A304-D217037876A8",
	"Zones":{
		"Zone":[		
			{
				"ZoneId":"cn-qingdao-a",
				"LocalName":"华北 1 可用区 A"
			},
			{
				"ZoneId":"cn-qingdao-b",
				"LocalName":"华北 1 可用区 B"
			}
              ]
            }
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

