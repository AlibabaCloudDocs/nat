# DeleteNatGateway

Deletes a NAT gateway.

## Description

DeleteNatGateway is an asynchronous operation. After you make a request, the ID of the request is returned but the specified NAT gateway is not deleted. The system deletes the NAT gateway in the background. You can call the [DescribeNatGateways](~~36054~~) operation to query the state of a NAT gateway:

-   **Deleting**: indicates that the system is deleting the NAT gateway. You can only query the state of the NAT gateway, but cannot perform other operations.
-   If no NAT gateway is returned in the response, the NAT gateway is deleted.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Vpc&api=DeleteNatGateway&type=RPC&version=2016-04-28)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DeleteNatGateway|The operation that you want to perform. Set the value to **DeleteNatGateway**. |
|NatGatewayId|String|Yes|ngw-bp1uewa15k4iy5770\*\*\*\*|The ID of the NAT gateway to be deleted. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the NAT gateway is deployed. You can call the [DescribeRegions](~~36063~~) operation to query the most recent region list. |
|Force|Boolean|No|false|Specifies whether to forcibly delete the NAT gateway. Valid values:

 -   **true**: forcibly deletes the NAT gateway. If you set the value to **true**:
    -   If the NAT gateway has SNAT entries, the system automatically deletes them.
    -   If the NAT gateway has DNAT entries, the system automatically deletes them.
    -   If the NAT gateway is associated with an elastic IP address \(EIP\), the system automatically disassociates it from the NAT gateway.
    -   If you have added routes whose next hop is the NAT gateway, the system automatically deletes them.
    -   If the NAT gateway is associated with a NAT bandwidth plan, the system automatically disassociates the NAT bandwidth plan.
-   **false**: does not forcibly delete the NAT gateway. If you set the value to **false**:
    -   If the NAT gateway is associated with a NAT bandwidth plan, disassociate the NAT bandwidth plan first.
    -   If the NAT gateway has SNAT entries, delete them first.
    -   If the NAT gateway has DNAT entries, delete them first.
    -   If the NAT gateway is associated with an EIP, disassociate the EIP from the NAT gateway first. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|0ED8D006-F706-4D23-88ED-E11ED28DCAC0|The ID of the request. |

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
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The error message returned because the specified region ID does not exist.|
|404|InvalidNatGatewayId.NotFound|The specified NatGatewayId does not exist in our records.|The error message returned because the specified NAT gateway ID does not exist. Check whether the NAT gateway ID is valid.|
|400|DependencyViolation.BandwidthPackages|There are BandwidthPackages on specified NatGateway not deleted.|The error message returned because one or more NAT bandwidth plans are associated with the NAT gateway. Disassociate all NAT bandwidth plans from the NAT gateway and try again.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Vpc).

