# ModifyNatGatewaySpec

Upgrades a subscription NAT gateway.

## Description

**Note:**

-   You cannot call this operation to downgrade a NAT gateway. You can downgrade a NAT gateway only in the console.
-   When you call this operation to upgrade a subscription NAT gateway, an order is generated. After you complete the payment in the order center, the NAT gateway is upgraded.

ModifyNatGatewaySpec is an asynchronous operation. After you make a request, the ID of the request is returned but the specified NAT gateway is not modified. The system modifies the NAT gateway in the background. You can call the [DescribeNatGateways](~~36054~~) operation to query the state of a NAT gateway.

-   **Modifying**: indicates that the system is modifying the NAT gateway. You can only query the state of the NAT gateway, but cannot perform other operations.
-   **Available**: indicates that the NAT gateway is modified.

NAT gateways offer different specifications. The specification of a NAT gateway determines its SNAT performance, such as the maximum number of connections and the number of new connections per second. However, the specification does not affect the data throughput. The following table describes the correlations between different specifications of NAT gateways and SNAT performance metrics.

|Specification

|Number of maximum connections

|Number of new connections per second |
|---------------|-------------------------------|--------------------------------------|
|Small

|10,000

|1,000 |
|Middle

|50,000

|5,000 |
|Large

|200,000

|10,000 |

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Vpc&api=ModifyNatGatewaySpec&type=RPC&version=2016-04-28)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ModifyNatGatewaySpec|The operation that you want to perform. Set the value to **ModifyNatGatewaySpec**. |
|NatGatewayId|String|Yes|ngw-bp1uewa15k4iy5770\*\*\*\*|The ID of the NAT gateway. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the NAT gateway is deployed. You can call the [DescribeRegions](~~36063~~) operation to query the most recent region list. |
|Spec|String|Yes|Middle|The specification of the NAT gateway. Valid values:

 -   **Small**: small
-   **Middle**: middle
-   **Large**: large |
|AutoPay|Boolean|No|false|Specifies whether to enable automatic payment. Valid values:

 -   **true**: enables automatic payment.
-   **false**: disables automatic payment. This is the default value. |
|ClientToken|String|No|123e4567-e89b-12d3-a456-426655\*\*\*\*|The client token that is used to ensure the idempotence of the request. You can use the client to generate the value, but you must make sure that it is unique among different requests. **ClientToken** can contain only ASCII characters. It must be 1 to 64 characters in length. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|DBD4E4A2-786E-4BD2-8EB6-107FFC2B5B7D|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=ModifyNatGatewaySpec
&NatGatewayId=ngw-bp1uewa15k4iy5770****
&RegionId=cn-hangzhou
&Spec=Middle
&<Common request parameters>
```

Sample success response

`XML` format

```
<ModifyNatGatewaySpecResponse>
  <RequestId>DBD4E4A2-786E-4BD2-8EB6-107FFC2B5B7D</RequestId>
</ModifyNatGatewaySpecResponse>
```

`JSON` format

```
{
    "RequestId": "DBD4E4A2-786E-4BD2-8EB6-107FFC2B5B7D"
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The error message returned because the specified region ID does not exist.|
|404|InvalidNatGatewayId.NotFound|The specified NatGatewayId does not exist in our records.|The error message returned because the specified NAT gateway ID does not exist. Check whether the NAT gateway ID is valid.|
|400|NATGW\_MODIFY\_SPEC\_SAME|The specified Spec is same with now.|The error message returned because the specified gateway specification is the same as the current gateway specification.|
|400|InvalidParameter.Spec.ValueNotSupported|The specified Spec is not valid.|The error message returned because the specified gateway specification is invalid.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Vpc).

