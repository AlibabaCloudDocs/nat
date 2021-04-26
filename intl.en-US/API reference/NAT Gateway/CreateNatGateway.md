# CreateNatGateway

Creates an enhanced NAT gateway.

## Description

When you call this operation, take note of the following information:

-   When you first create an enhanced NAT gateway, the system automatically creates the service-linked role AliyunServiceRoleForNatgw for the NAT gateway. Then, the system attaches the permission policy AliyunServiceRolePolicyForNatgw to the role. This allows the NAT gateway to access other resources on Alibaba Cloud. For more information, see [Service-linked roles](~~174251~~).
-   CreateNatGateway is an asynchronous operation. After you make a request, a NAT gateway ID is returned but the specified NAT gateway is not created. The system creates the NAT gateway in the background. You can call the [DescribeNatGateways](~~36054~~) operation to query the state of the NAT gateway. Take note of the following states:
    -   **Creating** indicates that the system is creating the NAT gateway. You can only query the state of the NAT gateway, but cannot perform other operations.
    -   **Available** indicates that the NAT gateway is created.

**Note:** The time required to create a NAT gateway is approximately 3 to 5 minutes.

-   After you create a NAT gateway, a route entry is automatically added to the route table of the virtual private cloud \(VPC\). The destination CIDR block of the route entry is 0.0.0.0/0 and the next hop is the NAT gateway. This ensures that traffic is routed to the NAT gateway.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Vpc&api=CreateNatGateway&type=RPC&version=2016-04-28)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateNatGateway|The operation that you want to perform. Set the value to **CreateNatGateway**. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the NAT gateway is deployed.

 You can call the [DescribeRegions](~~36063~~) operation to query region IDs. |
|VpcId|String|Yes|vpc-bp1di7uewzmtvfuq8\*\*\*\*|The ID of the VPC where the NAT gateway is deployed. |
|VSwitchId|String|Yes|vsw-bp1e3se98n9fq8hle\*\*\*\*|The ID of the vSwitch to which the NAT gateway is attached.

 When you create an enhanced NAT gateway, you must specify a vSwitch for the NAT gateway. Then, the system assigns an idle private IP address from the vSwitch to the NAT gateway.

 -   To create an enhanced NAT gateway that is attached to an existing vSwitch, make sure that the zone to which the vSwitch belongs supports enhanced NAT gateways. In addition, the vSwitch must have idle IP addresses.
-   If you do not have a vSwitch in the VPC, create a vSwitch in the zone that supports enhanced NAT gateways. Then, specify the vSwitch for the enhanced NAT gateway.

 You can call the [ListEnhanhcedNatGatewayAvailableZones](~~182292~~) operation to query zones that support enhanced NAT gateways. You can call the [DescribeVSwitches](~~35748~~) operation to query the number of available IP addresses in the vSwitch. |
|NatType|String|Yes|Enhanced|The type of NAT gateway. Set the value to **Enhanced** \(enhanced NAT gateway\). For more information, see [Release notes of enhanced NAT gateways](~~163610~~). |
|Name|String|No|fortest|The name of the NAT gateway.

 The name must be 2 to 128 characters in length, and can contain digits, periods \(.\), underscores \(\_\), and hyphens \(-\). The name must start with a letter and cannot start with `http://` or `https://`.

 If you do not set this parameter, the ID of the NAT gateway is used as the name of the NAT gateway. |
|Description|String|No|testnat|The description of the NAT gateway.

 The description must be 2 to 256 characters in length, and cannot start with `http://` or `https://`. |
|ClientToken|String|No|shefffxxddjehfh123|The client token that is used to ensure the idempotence of the request You can use the client to generate the value, but you must ensure that it is unique among different requests. The **ClientToken** parameter can contain only ASCII characters and cannot exceed 64 characters in length. |
|Spec|String|No|Small|The size of the NAT gateway. Valid values:

 -   **Small**: a small-sized NAT gateway. This is the default value.
-   **Middle**: a medium-sized NAT gateway.
-   **Large**: a large-sized NAT gateway. |
|InstanceChargeType|String|No|PostPaid|
 The billing method of the NAT gateway. Set the value to **PostPaid** \(pay-as-you-go\). The default value is **PostPaid**. For more information, see [Pay-as-you-go](~~88658~~). |
|PricingCycle|String|No|Month|-   
 The billing cycle of subscription NAT gateways. You do not need to set this parameter. |
|Duration|String|No|1|
 The duration of the subscription. You do not need to set this parameter. |
|AutoPay|Boolean|No|false|
 Specifies whether to enable automatic payment. You do not need to set this parameter. |
|InternetChargeType|String|No|PayBySpec|The metering method of the NAT gateway. Set the value to **PayByLcu**: pay-by-CU. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|NatGatewayId|String|ngw-112za33e4\*\*\*\*|The ID of the created NAT gateway. |
|ForwardTableIds|List|ftb-11tc6xgmv\*\*\*\*|The list of DNAT entries. |
|RequestId|String|2315DEB7-5E92-423A-91F7-4C1EC9AD97C3|The ID of the request. |
|SnatTableIds|List|stb-SnatTableIds\*\*\*\*|The list of SNAT entries. |

## Examples

Sample requests

```
https://vpc.aliyuncs.com/?Action=CreateNatGateway
&RegionId=cn-hangzhou
&VpcId= vpc-bp1di7uewzmtvfuq8****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<CreateNatGatewayResponse>
  <RequestId>2315DEB7-5E92-423A-91F7-4C1EC9AD97C3</RequestId>
  <SnatTableIds>
        <SnatTableId>stb-SnatTableIds****</SnatTableId>
  </SnatTableIds>
  <ForwardTableIds>
        <ForwardTableId>ftb-11tc6xgmv****</ForwardTableId>
  </ForwardTableIds>
  <NatGatewayId>ngw-112za33e4****</NatGatewayId>
</CreateNatGatewayResponse>
```

`JSON` format

```
{
    "RequestId": "2315DEB7-5E92-423A-91F7-4C1EC9AD97C3",
    "SnatTableIds": {
        "SnatTableId": "stb-SnatTableIds****"
    },
    "ForwardTableIds": {
        "ForwardTableId": "ftb-11tc6xgmv****"
    },
    "NatGatewayId": "ngw-112za33e4****"
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|InvalidVPCStatus|vpc incorrect status.|The error message returned because the operation is not supported when the VPC is in the current state. Check whether the state of the VPC is valid.|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The error message returned because the specified region ID does not exist.|
|400|InvalidNatGatewayName.MalFormed|NatGateway name is not valid.|The error message returned because the specified gateway name is invalid.|
|400|InvalidNatGatewayDescription.MalFormed|NatGateway description is not valid.|The error message returned because the specified gateway description is invalid.|
|400|MissingParameter.BandwidthPackage|only support one BandwidthPackage be created with NatGateway.|The error message returned because no EIP bandwidth plan is specified.|
|404|InvalidVpcId.NotFound|Specified value of VpcId is not found in our record.|The error message returned because the specified VPC does not exist. Check whether the specified VPC ID is valid.|
|400|MissingParameter|Miss mandatory parameter.|The error message returned because one or more required parameters are not set. Check whether you have set all the required parameters before you call this operation.|
|404|InvalidZoneId.NotFound|Specified value of ZoneId is not exists.|The error message returned because the specified zone does not exist.|
|404|InvalidZoneId.NotFound|Can not find ZoneId for allocated ip.|The error message returned because the zone of the specified IP address is invalid.|
|400|QuotaExceeded.BandwidthPackageIps|The specified ipCount exceeded quota.|The error message returned because the number of IP addresses exceeds the quota. Submit a ticket to increase the quota.|
|400|InvalidParameter.Name.Malformed|The specified Name is not valid.|The error message returned because the specified name is invalid.|
|400|InvalidParameter.Description.Malformed|The specified Description is not valid.|The error message returned because the specified description is invalid.|
|400|ZONE\_NO\_AVAILABLE\_IP|The Zone have no available ip.|The error message returned because no IP addresses are available in the zone.|
|400|InvalidParameter.BandwidthPackage.n.ISP.ValueNotSupport|The specified ISP of BandwidthPackage is not valid.|The error message returned because the specified Internet Service Provider \(ISP\) of the EIP bandwidth plan is invalid.|
|400|InvalidNatGatewayId.NotFound|The NatGatewayId not exist.|The error message returned because the specified NAT gateway ID does not exist. Check whether the value of the NatGatewayId parameter is valid.|
|400|VswitchStatusError|The VSwitch is creating .|The error message returned because the operation is not supported when the system is creating the vSwitch.|
|400|VpcStatusError|The Vpc is creating .|The error message returned because the operation is not supported when the system is creating the VPC.|
|400|InvalidParameter.Spec.ValueNotSupported|The specified Spec is not valid.|The error message returned because the specified specification is invalid.|
|400|Forbidden.CheckEntryRuleQuota|Route entry quota rule check error.|The error message returned because an error occurred when the system was checking the quota of route entries.|
|400|NoPermission.CreateServiceLinkedRole|You are not authorized to create service linked role|The error message returned because you are unauthorized to create a service-linked role.|
|400|OperationFailed.VswNotBelongToVpc|Operation failed because the specified VSwitch is not bound to the same VPC with NAT gateway.|The error message returned because the specified vSwitch and NAT gateway are not deployed in the same VPC.|
|400|OperationFailed.EnhancedUserIsUnAuthorized|Operation failed because the user is not authorized to create an enhanced NAT gateway.|The error message returned because you are unauthorized to create enhanced NAT gateways.|
|400|OperationUnsupported.PrePaidPyByLcu|The operation failed because the subscription NAT gateway does not support the pay-by-LCU billing method.|The error message returned because subscription NAT gateways do not support the pay-by-CU metering method.|
|400|OperationFailed.NormalInventoryNotEnough|Operation failed because the inventory of standard NAT gateway is insufficient.|The error message returned because the quota of standard NAT gateways is insufficient.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Vpc).

