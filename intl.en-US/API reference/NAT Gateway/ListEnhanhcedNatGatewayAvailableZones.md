# ListEnhanhcedNatGatewayAvailableZones

Queries the zones that support enhanced NAT gateways in a specified region.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Vpc&api=ListEnhanhcedNatGatewayAvailableZones&type=RPC&version=2016-04-28)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ListEnhanhcedNatGatewayAvailableZones|The operation that you want to perform. Set the value to **ListEnhanhcedNatGatewayAvailableZones**. |
|RegionId|String|Yes|cn-qingdao|The ID of the region that you want to query. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|0ED8D006-F706-4D23-88ED-E11ED28DCAC0|The ID of the request. |
|Zones|Array of Zone| |The list of zones. |
|LocalName|String|China \(Qingdao\) Zone A|The name of the zone. |
|ZoneId|String|cn-qingdao-a|The ID of the zone. |

## Examples

Sample requests

```
http(s)://vpc.aliyuncs.com/? Action=ListEnhanhcedNatGatewayAvailableZones
&RegionId=cn-qingdao
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ListEnhanhcedNatGatewayAvailableZonesResponse>
  <RequestId>9AD606B4-5DE0-4868-AF98-EEC00C14304C</RequestId>
  <Zones>
        <ZoneId>cn-hangzhou-h</ZoneId>
        <LocalName>China (Hangzhou) Zone H</LocalName>
  </Zones>
  <Zones>
        <ZoneId>cn-hangzhou-i</ZoneId>
        <LocalName>China (Hangzhou) Zone I</LocalName>
  </Zones>
</ListEnhanhcedNatGatewayAvailableZonesResponse>
```

`JSON` format

```
{
	"RequestId": "9AD606B4-5DE0-4868-AF98-EEC00C14304C",
	"Zones": [
		{
			"ZoneId": "cn-hangzhou-h",
			"LocalName":"China (Hangzhou) Zone H"
		},
		{
			"ZoneId": "cn-hangzhou-i",
			"LocalName":"China (Hangzhou) Zone I"
		}
	]
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The error message returned because the specified region ID does not exist. Check whether the region ID is valid.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Vpc).

