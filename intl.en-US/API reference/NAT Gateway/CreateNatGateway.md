# CreateNatGateway

Creates a NAT gateway.

## Description

When you call this operation, take note of the following information:

-   When you create an enhanced NAT gateway, the system automatically creates the service linked role \(SLR\) AliyunServiceRoleForNatgw for the NAT gateway. Then, the system attaches the permission policy AliyunServiceRolePolicyForNatgw to the role. This allows the NAT gateway to access other resources on Alibaba Cloud. For more information, see [Service linked role for NAT Gateway](~~174251~~).

**Note:** When you create a standard NAT gateway, the system does not automatically create the SLR AliyunServiceRoleForNatgw for the NAT gateway.

-   CreateNatGateway is an asynchronous operation. After you make a request, a NAT gateway ID is returned but the specified NAT gateway is not created. The system creates the NAT gateway in the background. You can call the [DescribeNatGateways](~~36054~~) operation to query the state of the NAT gateway:
    -   **Creating**: indicates that the system is creating the NAT gateway. You can only query the state of the NAT gateway, but cannot perform other operations.
    -   **Available**: indicates that the NAT gateway is created.

**Note:** It takes one to three minutes to create a NAT gateway.

-   After you create a NAT gateway, a route entry is automatically added to the route table of the virtual private cloud \(VPC\). The destination CIDR block of the route entry is 0.0.0.0/0 and the next hop is the NAT gateway. This ensures that traffic is routed to the NAT gateway.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Vpc&api=CreateNatGateway&type=RPC&version=2016-04-28)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateNatGateway|The operation that you want to perform. Set the value to **CreateNatGateway**. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the NAT gateway is deployed.

 You can call the [DescribeRegions](~~36063~~) operation to query region IDs. |
|VpcId|String|Yes|vpc-bp1di7uewzmtvfuq8\*\*\*\*|The ID of the VPC to which the NAT gateway belongs. When you specify a VPC, take note of the following limits:

 To create a standard NAT gateway, make sure that the route table of the VPC does not contain a route entry with the destination CIDR block set to 0.0.0.0/0. If such a custom route entry exists, delete it. If you create an enhanced NAT gateway, this limit does not apply. |
|Name|String|No|fortest|The name of the NAT gateway.

 The name must be 2 to 128 characters in length, and can contain digits, periods \(.\), underscores \(\_\), and hyphens \(-\). It must start with a letter and cannot start with `http://` or `https://`.

 If you do not set this parameter, the ID of the gateway is used as the gateway name. |
|Description|String|No|testnat|The description of the NAT gateway.

 It must be 2 to 256 characters in length, and cannot start with `http://` or `https://`. |
|ClientToken|String|No|shefffxxddjehfh123|The client token that is used to ensure the idempotence of the request. You can use the client to generate a value that is unique among different requests. **ClientToken** can contain only ASCII characters and cannot exceed 64 characters in length. |
|Spec|String|No|Small|The size of the NAT gateway. Valid values:

 -   **Small**: small. This is the default value.
-   **Middle**: middle.
-   **Large**: large.
-   **XLarge.1**: super large-1. |
|InstanceChargeType|String|No|PostPaid|The billing method of the NAT gateway. Set the value to **PostPaid** \(Pay-as-you-go\). The default value is **PostPaid**. For more information, see [Pay-as-you-go](~~88658~~). |
|PricingCycle|String|No|Month|The billing cycle of subscription NAT gateways. You do not need to specify this parameter. |
|Duration|String|No|1|The subscription duration. You do not need to specify this parameter. |
|AutoPay|Boolean|No|false|Specifies whether to enable automatic payment. You do not need to specify this parameter. |
|VSwitchId|String|No|vsw-bp1e3se98n9fq8hle\*\*\*\*|The ID of the VSwitch to which the NAT gateway is attached.

 When you create an enhanced NAT gateway, you must specify a VSwitch for the gateway. Then, the system assigns an unused IP address from the VSwitch to the gateway.

 -   To create an enhanced NAT gateway attached to an existing VSwitch, make sure that the zone to which the VSwitch belongs supports enhanced NAT gateways. In addition, the VSwitch must have unused public IP addresses.
-   If you do not have a VSwitch in the VPC, create a VSwitch in the zone that supports enhanced NAT gateways. Then, specify the VSwitch for the enhanced NAT gateway.

 You can call the [ListEnhanhcedNatGatewayAvailableZones](~~182292~~) operation to query zones that support enhanced NAT gateways. You can call the [DescribeVSwitches](~~35748~~) operation to query the number of available public IP addresses in the VSwitch. |
|NatType|String|No|Enhanced|The type of the NAT gateway. Valid values:

 -   **Normal**: a standard NAT gateway.
-   **Enhanced**: an enhanced NAT gateway. For more information about enhanced NAT gateways, see [Release notes for Enhanced NAT Gateway](~~163610~~).

 **Note:** Enhanced NAT gateways are available in all regions except Australia \(Sydney\). |
|InternetChargeType|String|No|PayBySpec|The billing method for the NAT gateway. Valid values:

 -   **PayBySpec**: billed on a pay-by-specification basis.
-   **PayByLcu**: billed on a pay-by-LCU basis.

 **Note:** If you create a NAT gateway in the China \(Chengdu\), Malaysia \(Kuala Lumpur\), India \(Mumbai\), Indonesia \(Jakarta\), Germany \(Frankfurt\) or UK \(London\) region, you can set the value of **InternetChargeType** to **PayByLcu** only when you set the value of **NatType** to **Enhanced**. |

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

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|InvalidVPCStatus|vpc incorrect status.|The error message returned because the operation is not supported when the VPC is in the current state. Check whether the state of the VPC is valid.|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The error message returned because the specified region ID does not exist. Check whether the region ID is valid.|
|400|InvalidNatGatewayName.MalFormed|NatGateway name is not valid.|The error message returned because the specified gateway name is invalid.|
|400|InvalidNatGatewayDescription.MalFormed|NatGateway description is not valid.|The error message returned because the specified gateway description is invalid.|
|400|MissingParameter.BandwidthPackage|only support one BandwidthPackage be created with NatGateway.|The error message returned because no EIP bandwidth plan is specified.|
|404|InvalidVpcId.NotFound|Specified value of VpcId is not found in our record.|The error message returned because the specified VPC does not exist. Check whether the specified VPC ID is valid.|
|400|MissingParameter|Miss mandatory parameter.|The error message returned because the required parameters are missing. Check whether you have set all the required parameters before you call this operation.|
|404|InvalidZoneId.NotFound|Specified value of ZoneId is not exists.|The error message returned because the specified zone ID does not exist.|
|404|InvalidZoneId.NotFound|Can not find ZoneId for allocated ip.|The error message returned because the zone of the specified IP address is invalid.|
|400|QuotaExceeded.BandwidthPackageIps|The specified ipCount exceeded quota.|The error message returned because the number of IP addresses exceeds the quota. Submit a ticket to increase the quota.|
|400|InvalidParameter.Name.Malformed|The specified Name is not valid.|The error message returned because the specified name is invalid.|
|400|InvalidParameter.Description.Malformed|The specified Description is not valid.|The error message returned because the specified description is invalid.|
|400|ZONE\_NO\_AVAILABLE\_IP|The Zone have no available ip.|The error message returned because no IP addresses are available in the zone.|
|400|InvalidParameter.BandwidthPackage.n.ISP.ValueNotSupport|The specified ISP of BandwidthPackage is not valid.|The error message returned because the specified Internet service provider \(ISP\) of the EIP bandwidth plan is invalid.|
|400|InvalidNatGatewayId.NotFound|The NatGatewayId not exist.|The error message returned because the specified NAT gateway ID does not exist. Check whether the value of the NatGatewayId parameter is valid.|
|400|VswitchStatusError|The VSwitch is creating .|The error message returned because the operation is not supported when the system is creating the VSwitch.|
|400|VpcStatusError|The Vpc is creating .|The error message returned because the operation is not supported when the system is creating the VPC.|
|400|InvalidParameter.Spec.ValueNotSupported|The specified Spec is not valid.|The error message returned because the specified specification is invalid.|
|400|Forbidden.CheckEntryRuleQuota|Route entry quota rule check error.|The error message returned because an error occurred when the system was checking the quota of route entries.|
|400|NoPermission.CreateServiceLinkedRole|You are not authorized to create service linked role|The error message returned because you do not have permissions to create an SLR.|
|400|OperationFailed.VswNotBelongToVpc|Operation failed because the specified VSwitch is not bound to the same VPC with NAT gateway.|The error message returned because the specified VSwitch and NAT gateway are not deployed in the same VPC.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Vpc).

