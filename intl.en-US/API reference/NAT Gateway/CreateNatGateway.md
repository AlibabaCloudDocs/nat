# CreateNatGateway

Creates an enhanced NAT gateway.

## Description

When you call this operation, take note of the following information:

-   When you first create an enhanced NAT gateway, the system automatically creates the service-linked role \(SLR\) AliyunServiceRoleForNatgw for the NAT gateway. Then, the system attaches the permission policy AliyunServiceRolePolicyForNatgw to the role. This allows the NAT gateway to access other resources on Alibaba Cloud. For more information, see [Service-linked roles](~~174251~~).
-   CreateNatGateway is an asynchronous operation. After you make a request, a NAT gateway ID is returned but the specified NAT gateway is not created. The system creates the NAT gateway in the background. You can call the [DescribeNatGateways](~~36054~~) operation to query the state of the NAT gateway:
    -   **Creating**: indicates that the system is creating the NAT gateway. You can only query the state of the NAT gateway, but cannot perform other operations.
    -   **Available**: indicates that the NAT gateway is created.

**Note:** It takes 1 to 3 minutes to create a NAT gateway.

-   After you create a NAT gateway, a route entry is automatically added to the route table of the virtual private cloud \(VPC\). The destination CIDR block of the route entry is 0.0.0.0/0 and the next hop is the NAT gateway. This ensures that traffic is routed to the NAT gateway.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Vpc&api=CreateNatGateway&type=RPC&version=2016-04-28)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateNatGateway|The operation that you want to perform. Set the value to **CreateNatGateway**. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the NAT gateway is deployed.

 You can call the [DescribeRegions](~~36063~~) operation to query region IDs. |
|VpcId|String|Yes|vpc-bp1di7uewzmtvfuq8\*\*\*\*|The ID of the VPC to which the NAT gateway belongs. |
|VSwitchId|String|Yes|vsw-bp1e3se98n9fq8hle\*\*\*\*|The ID of the vSwitch to which the NAT gateway is attached.

 When you create an enhanced NAT gateway, you must specify a vSwitch for the NAT gateway. Then, the system assigns an idle private IP address from the vSwitch to the NAT gateway.

 -   To create an enhanced NAT gateway that is attached to an existing vSwitch, make sure that the zone to which the vSwitch belongs supports enhanced NAT gateways. In addition, the vSwitch must have idle IP addresses.
-   If you do not have a vSwitch in the VPC, create a vSwitch in the zone that supports enhanced NAT gateways. Then, specify the vSwitch for the enhanced NAT gateway.

 You can call the [ListEnhanhcedNatGatewayAvailableZones](~~182292~~) operation to query zones that support enhanced NAT gateways. You can call the [DescribeVSwitches](~~35748~~) operation to query the number of available IP addresses in the vSwitch. |
|NatType|String|Yes|Enhanced|The type of the NAT gateway. Set the value to **Enhanced** \(enhanced NAT gateway\). For more information about enhanced NAT gateways, see [Release notes for enhanced NAT gateways](~~163610~~). |
|Name|String|No|fortest|The name of the NAT gateway.

 The name must be 2 to 128 characters in length, and can contain digits, periods \(.\), underscores \(\_\), and hyphens \(-\). The name must start with a letter and cannot start with `http://` or `https://`.

 If you do not set this parameter, the ID of the NAT gateway is used as the name of the NAT gateway. |
|Description|String|No|testnat|The description of the NAT gateway.

 The description must be 2 to 256 characters in length, and cannot start with `http://` or `https://`. |
|ClientToken|String|No|shefffxxddjehfh123|The client token that is used to ensure the idempotence of the request. You can use the client to generate a value that is unique among different requests. **ClientToken** can contain only ASCII characters and cannot exceed 64 characters in length. |
|Spec|String|No|Small|The size of the NAT gateway. Valid values:

 -   **Small**: a small-sized NAT gateway. This is the default value.
-   **Middle**: a medium-sized NAT gateway.
-   **Large**: a large-sized NAT gateway.
-   **XLarge.1**: a super large-sized NAT gateway. |
|InstanceChargeType|String|No|PostPaid|NAT网关的付费模式，取值：

**PostPaid**（默认值）：按量付费。

 **PrePaid**：包年包月。

 包年包月和按量付费的详细信息，请参见[包年包月](~~88657~~)和[按量付费](~~88658~~)。

 The billing method of the NAT gateway. Set the value to **PostPaid** \(pay-as-you-go\). The default value is **PostPaid**. For more information, see [Pay-as-you-go](~~88658~~).

 The billing method of the NAT gateway. Set the value to **PostPaid** \(pay-as-you-go\). The default value is **PostPaid**. For more information, see [Pay-as-you-go](~~88658~~). |
|PricingCycle|String|No|Month|包年包月的计费周期，取值：

**Month**（默认值）：按月付费。

 **Year**：按年付费。

 当**InstanceChargeType**参数的值为**PrePaid**时，该参数必选；当**InstanceChargeType**参数的值为**PostPaid**时，该参数可不填。

 The billing cycle of subscription NAT gateways. You do not need to set this parameter.

 The billing cycle of subscription NAT gateways. You do not need to set this parameter. |
|Duration|String|No|1|购买时长。

当**PricingCycle**取值**Month**时，**Period**取值范围为**1~9**。

 当**PricingCycle**取值**Year**时，**Period**取值范围为**1~3**。

 如果**InstanceChargeType**参数的值为**PrePaid**时，该参数必选。

 The duration of the subscription. You do not need to set this parameter.

 The duration of the subscription. You do not need to set this parameter. |
|AutoPay|Boolean|No|false|是否自动付费，取值：

**false**：不开启自动付费，生成订单后需要到订单中心完成支付。

 **true**：开启自动付费，自动支付订单。

 当**InstanceChargeType**参数的值为**PrePaid**时，该参数必选；当**InstanceChargeType**参数的值为**PostPaid**时，该参数不填。

 Specifies whether to enable automatic payment. You do not need to set this parameter.

 Specifies whether to enable automatic payment. You do not need to set this parameter. |
|InternetChargeType|String|No|PayBySpec|The metering method for the NAT gateway. Valid values:

 -   **PayBySpec**: pay by specification.
-   **PayByLcu**: pay by LCU. |

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
      <RequestId>5AF873FB-6669-4AD5-A4DA-478D535C8F0D</RequestId>
      <SnatTableIds>
            <SnatTableId>stb-bp1evej8rk6ww1djl****</SnatTableId>
      </SnatTableIds>
      <ForwardTableIds>
            <ForwardTableId>ftb-bp1d09hosgndxs154****</ForwardTableId>
      </ForwardTableIds>
      <NatGatewayId>ngw-bp1m842e0dz1t5cos****</NatGatewayId>
</CreateNatGatewayResponse>
```

`JSON` format

```
{
	"RequestId": "5AF873FB-6669-4AD5-A4DA-478D535C8F0D",
	"SnatTableIds": {
		"SnatTableId": [
			"stb-bp1evej8rk6ww1djl****"
		]
	},
	"ForwardTableIds": {
		"ForwardTableId": [
			"ftb-bp1d09hosgndxs154****"
		]
	},
	"NatGatewayId": "ngw-bp1m842e0dz1t5cos****"
}
```

## Error codes

|HttpCode|Error codes|Error message|Description|
|--------|-----------|-------------|-----------|
|400|InvalidVPCStatus|vpc incorrect status.|The error message returned because the operation is not supported when the VPC is in the current state. Check whether the state of the VPC is valid.|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The error message returned because the specified region ID is invalid. Check whether the service is available in the specified region.|
|400|InvalidNatGatewayName.MalFormed|NatGateway name is not valid.|The error message returned because the specified gateway name is invalid.|
|400|InvalidNatGatewayDescription.MalFormed|NatGateway description is not valid.|The error message returned because the specified gateway description is invalid.|
|400|MissingParameter.BandwidthPackage|only support one BandwidthPackage be created with NatGateway.|The error message returned because no EIP bandwidth plan is specified.|
|404|InvalidVpcId.NotFound|Specified value of VpcId is not found in our record.|The error message returned because the specified VPC does not exist. Check whether the specified VPC ID is valid.|
|400|MissingParameter|Miss mandatory parameter.|The error message returned because the required parameters values are missing. Check whether you have set all the required parameters before you call this operation.|
|404|InvalidZoneId.NotFound|Specified value of ZoneId is not exists.|The error message returned because the specified zone ID does not exist.|
|404|InvalidZoneId.NotFound|Can not find ZoneId for allocated ip.|The error message returned because the zone of the specified IP address is invalid.|
|400|QuotaExceeded.BandwidthPackageIps|The specified ipCount exceeded quota.|The error message returned because the number of IP addresses exceeds the quota. Submit a ticket to increase the quota.|
|400|InvalidParameter.Name.Malformed|The specified Name is not valid.|The error message returned because the specified name is invalid.|
|400|InvalidParameter.Description.Malformed|The specified Description is not valid.|The error message returned because the specified description is invalid.|
|400|ZONE\_NO\_AVAILABLE\_IP|The Zone have no available ip.|The error message returned because no IP addresses are available in the zone.|
|400|InvalidParameter.BandwidthPackage.n.ISP.ValueNotSupport|The specified ISP of BandwidthPackage is not valid.|The error message returned because the specified Internet Service Provider \(ISP\) of the NAT service plan is invalid.|
|400|InvalidNatGatewayId.NotFound|The NatGatewayId not exist.|The error message returned because the specified NAT gateway ID does not exist. Check whether the value of the NatGatewayId parameter is valid.|
|400|VswitchStatusError|The VSwitch is creating .|The error message returned because the operation is not supported when the system is creating the vSwitch.|
|400|VpcStatusError|The Vpc is creating .|The error message returned because the operation is not supported when the system is creating the VPC.|
|400|InvalidParameter.Spec.ValueNotSupported|The specified Spec is not valid.|The error message returned because the specified specification is invalid.|
|400|Forbidden.CheckEntryRuleQuota|Route entry quota rule check error.|The error message returned because an error occurred when the system was checking the quota of route entries.|
|400|NoPermission.CreateServiceLinkedRole|You are not authorized to create service linked role|The error message returned because you do not have permissions to create an SLR.|
|400|OperationFailed.VswNotBelongToVpc|Operation failed because the specified VSwitch is not bound to the same VPC with NAT gateway.|The error message returned because the specified vSwitch and NAT gateway are not deployed in the same VPC.|
|400|OperationFailed.EnhancedUserIsUnAuthorized|Operation failed because the user is not authorized to create an enhanced NAT gateway.|The error message returned because the user is not authorized to create enhanced NAT gateways.|
|400|OperationUnsupported.PrePaidPyByLcu|The operation failed because the subscription NAT gateway does not support the pay-by-LCU billing method.|The error message returned because subscription NAT gateways do not support the pay-by-LCU metering method.|
|400|OperationFailed.NormalInventoryNotEnough|Operation failed because the inventory of standard NAT gateway is insufficient.|The error message returned because the quota of standard NAT gateway is insufficient.|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Vpc).

