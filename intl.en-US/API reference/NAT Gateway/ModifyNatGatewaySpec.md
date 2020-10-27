# ModifyNatGatewaySpec

Changes the size of a NAT gateway.

## Description

ModifyNatGatewaySpec is an asynchronous operation. After you make a request, the ID of the request is returned but the specified NAT gateway is not modified. The system modifies the NAT gateway in the background. You can call the [DescribeNatGateways](~~36054~~) operation to query the state of the NAT gateway:

-   **Modifying**: indicates that the system is modifying the NAT gateway. You can only query the state of the NAT gateway, but cannot perform other operations.
-   **Available**: indicates that the NAT gateway is modified.

NAT gateways are available in different sizes. The size of a NAT gateway determines the Source Network Address Translation \(SNAT\) performance of the gateway, such as the maximum number of connections and the number of new connections per second. However, the data throughput is not affected. The following table describes the correlations between different sizes of NAT gateways and SNAT performance metrics.

|Size

|Maximum number of connections

|Number of new connections per second |
|------|-------------------------------|--------------------------------------|
|Small

|10,000

|1,000 |
|Middle

|50,000

|5,000 |
|Large

|200,000

|10,000 |
|Super Large-1

|1,000,000

|50,000 |

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Vpc&api=ModifyNatGatewaySpec&type=RPC&version=2016-04-28)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ModifyNatGatewaySpec|The operation that you want to perform. Valid value to **ModifyNatGatewaySpec**. |
|NatGatewayId|String|Yes|ngw-bp1uewa15k4iy5770\*\*\*\*|The ID of the NAT gateway. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the NAT gateway is deployed. |
|Spec|String|Yes|Small|The size of the NAT gateway. Valid values:

 -   Small: a small-sized NAT gateway.
-   Middle: a middle-sized NAT gateway.
-   Large: a large-sized NAT gateway.
-   XLarge.1: a super large-sized NAT gateway. |
|ClientToken|String|No|SHA234js121223xxxxx|The client token that is used to ensure the idempotence of the request. You can use the client to generate a value that is unique among different requests. **ClientToken** can contain only ASCII characters and cannot exceed 64 characters in length. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|DBD4E4A2-786E-4BD2-8EB6-107FFC2B5B7D|The ID of the request. |

## Examples

Sample requests

```
https://vpc.aliyuncs.com/?Action=ModifyNatGatewaySpec
&NatGatewayId=ngw-bp1uewa15k4iy5770****
&RegionId=cn-hangzhou
&Spec=Small
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ModifyNatGatewaySpecResponse>
      <RequestId>DBD4E4A2-786E-4BD2-8EB6-107FFC2B5B7D</RequestId>
</ModifyNatGatewaySpecResponse>
```

`JSON` format

```
{
    "RequestId":"DBD4E4A2-786E-4BD2-8EB6-107FFC2B5B7D"
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The error message returned because the specified region ID does not exist. Check whether the region ID is valid.|
|404|InvalidNatGatewayId.NotFound|The specified NatGatewayId does not exist in our records.|The error message returned because the specified NAT gateway ID does not exist. Check whether the value of the NatGatewayId parameter is valid.|
|400|NATGW\_MODIFY\_SPEC\_SAME|The specified Spec is same with now.|The error message returned because the specified gateway size is the same as the current one.|
|400|InvalidParameter.Spec.ValueNotSupported|The specified Spec is not valid.|The error message returned because the specified gateway size is invalid.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Vpc).

