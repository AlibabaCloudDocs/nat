# EnableNatGatewayEcsMetric

Enables the traffic monitoring feature for NAT gateways.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Vpc&api=EnableNatGatewayEcsMetric&type=RPC&version=2016-04-28)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|EnableNatGatewayEcsMetric|The operation that you want to perform. Set the value to **EnableNatGatewayEcsMetric**. |
|NatGatewayId|String|Yes|ngw-2vc53wynunp35lw1y\*\*\*\*|The ID of the NAT gateway for which you want to enable the traffic monitoring feature. |
|RegionId|String|Yes|cn-chengdu|The ID of the region where the NAT gateway is deployed. You can call the [DescribeRegions](~~36063~~) operation to query region IDs. |
|DryRun|Boolean|No|false|Specifies whether to precheck only this request. Valid values:

 **true**: The validity of the request is checked but the traffic monitoring feature is not enabled. The system checks whether your AccessKey pair is valid, whether the Resource Access Management \(RAM\) user is authorized, and whether the required parameters are specified. If the request fails the precheck, the corresponding error code is returned. If the request passes the precheck, the `DryRunOperation` error code is returned.

 **false** \(default\): The validity of the request is checked. If the request passes the precheck, a 2XX HTTP status code is returned and the traffic monitoring feature is enabled. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|0ED8D006-F706-4D23-88ED-E11ED28DCAC0|The ID of the request. |

## Examples

Sample requests

```
https://vpc.aliyuncs.com/?Action=EnableNatGatewayEcsMetric
&NatGatewayId=ngw-2vc53wynunp35lw1y****
&RegionId=cn-chengdu
&<Common request parameters>
```

Sample success responses

`XML` format

```
<EnableNatGatewayEcsMetricResponse>
      <RequestId>5AF873FB-6669-4AD5-A4DA-478D535C8F0D</RequestId>
</EnableNatGatewayEcsMetricResponse>
```

`JSON` format

```
{
	"RequestId": "5AF873FB-6669-4AD5-A4DA-478D535C8F0D"

}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Vpc).

