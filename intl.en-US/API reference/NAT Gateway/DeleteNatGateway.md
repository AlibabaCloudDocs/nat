# DeleteNatGateway

Deletes a specified NAT gateway.

## Description

DeleteNatGateway is an asynchronous operation. After you make a request, the ID of the request is returned but the specified NAT gateway is not deleted. The system deletes the NAT gateway in the background. You can call the [DescribeNatGateways](~~36054~~) operation to query the state of the NAT gateway. Note the following states:

-   **Deleting**: indicates that the system is deleting the NAT gateway. You can only query the state of the NAT gateway, but cannot perform other operations.
-   If no NAT gateway is returned in the response, the NAT gateway is deleted.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Vpc&api=DeleteNatGateway&type=RPC&version=2016-04-28)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DeleteNatGateway|The operation that you want to perform. Set the value to **DeleteNatGateway**. |
|NatGatewayId|String|Yes|ngw-bp1uewa15k4iy5770\*\*\*\*|The ID of the NAT gateway. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the NAT gateway is deployed. You can call the [DescribeRegions](~~36063~~) operation to query region IDs. |
|Force|Boolean|No|false|Specifies whether to forcibly delete the NAT gateway. Valid values:

 -   **true**: forcibly deletes the NAT gateway. When you set the value to **true**:
    -   The system automatically deletes Source Network Address Translation \(SNAT\) entries for the NAT gateway.
    -   The system automatically deletes Destination Network Address Translation \(DNAT\) entries for the NAT gateway.
    -   The system automatically disassociates the elastic IP address \(EIP\) from the NAT gateway.
    -   The system automatically deletes the routes that use the NAT gateway as the next hop.
    -   The system automatically disassociates the NAT service plans from the NAT gateway.
-   **false**: does not forcibly delete the NAT gateway. When you set the value to **false**:
    -   You must manually disassociate the NAT service plans from the NAT gateway.
    -   You must manually delete the SNAT entries for the NAT gateway.
    -   You must manually delete the DNAT entries for the NAT gateway.
    -   You must manually disassociate the EIP from the NAT gateway. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|4EC47282-1B74-4534-BD0E-403F3EE64CAF|The ID of the request. |

## Examples

Sample requests

```
https://vpc.aliyuncs.com/?Action=DeleteNatGateway
&NatGatewayId=ngw-bp1uewa15k4iy5770****
&RegionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DeleteNatGatewayResponse>
      <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
</DeleteNatGatewayResponse>
```

`JSON` format

```
{ 
    "RequestId": "0ED8D006-F706-4D23-88ED-E11ED28DCAC0"
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The error message returned because the specified region ID does not exist. Check whether the region ID is valid.|
|404|InvalidNatGatewayId.NotFound|The specified NatGatewayId does not exist in our records.|The error message returned because the specified NAT gateway ID does not exist. Check whether the value of the NatGatewayId parameter is valid.|
|400|DependencyViolation.BandwidthPackages|There are BandwidthPackages on specified NatGateway not deleted.|The error message returned because one or more NAT service plans are associated with the NAT gateway. Disassociate all NAT service plans from the NAT gateway and try again.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Vpc).

