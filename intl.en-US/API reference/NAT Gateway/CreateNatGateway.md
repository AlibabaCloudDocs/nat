# CreateNatGateway

Creates a Network Address Translation \(NAT\) gateway.

## API description

When you call this operation, note the following limits:

-   If the route table of the Virtual Private Cloud \(VPC\) network contains a route entry with a destination CIDR block of 0.0.0.0/0, you cannot create a standard NAT gateway in the VPC network. You must delete the route entry before you create a standard NAT gateway in the VPC network. The preceding limit does not apply when you create an enhanced NAT gateway in the VPC network.
-   You cannot deploy a user-created Source Network Address Translation \(SNAT\) gateway and a NAT gateway in the same VPC network. A user-created SNAT gateway refers to an Elastic Compute Service \(ECS\) instance that is used as a SNAT gateway.
-   After you create a NAT gateway, a route entry is automatically added to the route table of the VPC network. The destination CIDR block of the route entry is 0.0.0.0/0 and the next hop is the NAT gateway. This ensures that traffic is routed to the NAT gateway.
-   When you create an enhanced NAT gateway, the system automatically creates the service linked role \(SLR\) AliyunServiceRoleForNatgw for the NAT gateway. Then, the system attaches the permission policy AliyunServiceRolePolicyForNatgw to the role. This allows the NAT gateway to access other resources on Alibaba Cloud. For more information, see [Service linked roles for NAT Gateway](~~174251~~).

**Note:** When you create a standard NAT gateway, the system does not automatically create the SLR AliyunServiceRoleForNatgw for the NAT gateway.


## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Vpc&api=CreateNatGateway&type=RPC&version=2016-04-28)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Required|CreateNatGateway|The operation that you want to perform. Set the value to **CreateNatGateway**. |
|RegionId|String|Required|cn-hangzhou|The ID of the region where the NAT gateway is deployed.

 You can call the [DescribeRegions](~~36063~~) operation to query region IDs. |
|VpcId|String|Required|vpc-bp1di7uewzmtvfuq8\*\*\*\*|The ID of the VPC network for which you want to create the NAT gateway. |
|Name|String|No|fortest|The name of the NAT gateway.

 The name must be 2 to 128 characters in length, and can contain digits, periods \(.\), underscores \(\_\), and hyphens \(-\). It must start with a letter or Chinese character and cannot start with `http://` or `https://`.

 If you do not specify this parameter, the ID of the gateway is used as the gateway name. |
|Description|String|No|testnat|The description of the NAT gateway.

 It must be 2 to 256 characters in length, and cannot start with `http://` or `https://`. |
|ClientToken|String|No|shefffxxddjehfh123|The client token that is used to guarantee the idempotence of the request. You can use the client to generate a value that is unique among different requests. **ClientToken** can contain only ASCII characters and cannot exceed 64 characters in length. |
|Spec|String|No|Small|The size of the NAT gateway. Valid values:

 -   **Small**: small. This is the default value.
-   **Middle**: middle.
-   **Large**: large.
-   **XLarge.1**: super large. |
|BandwidthPackage.N.IpCount|Integer|No|5|The number of public IP addresses in the NAT bandwidth plan. Valid values: 1 to 50.

 N indicates the sequence number of the NAT bandwidth plan. Valid values: 1 to 4.

 This parameter can only be specified for NAT bandwidth plans that were purchased before January 26, 2018. If you do not have a NAT bandwidth plan that was purchased before January 26, 2018 under your account, bind an elastic IP address. |
|BandwidthPackage.N.Bandwidth|Integer|No|5|The bandwidth value of NAT bandwidth plan N. Valid values: 5 to 5,000.

 This parameter can only be specified for NAT bandwidth plans that were purchased before January 26, 2018. If you do not have a NAT bandwidth plan that was purchased before January 26, 2018 under your account, bind an elastic IP address. |
|BandwidthPackage.N.Zone|String|No|cn-hangzhou-b|The zone to which NAT service plan N is allocated. If you do not specify this parameter, the bandwidth plan is randomly allocated to a zone.

 Even if the IP addresses of the NAT bandwidth plan and the ECS instance belong to different zones, the ECS instance can still connect to the NAT gateway. However, you can reduce the network latency by allocating the NAT bandwidth plan to the zone where your ECS instance is deployed.

 This parameter can only be specified for NAT bandwidth plans that were purchased before January 26, 2018. If you do not have a NAT bandwidth plan that was purchased before January 26, 2018 under your account, bind an elastic IP address. |
|BandwidthPackage.N.ISP|String|No|BGP|By default, the type of Internet Service Provider \(ISP\) line of NAT bandwidth plan N is BGP \(Multi-ISP\).

 This parameter can only be specified for NAT bandwidth plans that were purchased before January 26, 2018. If you do not have a NAT bandwidth plan that was purchased before January 26, 2018 under your account, bind an elastic IP address. |
|InstanceChargeType|String|No|PostPaid|The billing method. Set the value to **PostPaid** \(pay-as-you-go\). The default value is **PostPaid**. For more information, see [Pay-as-you-go](~~88658~~). |
|PricingCycle|String|No|Month|The billing cycle of subscription NAT gateways. You do not need to specify this parameter. |
|Duration|String|No|1|The subscription duration. You do not need to specify this parameter. |
|AutoPay|Boolean|No|false|Specifies whether to enable automatic payment. You do not need to specify this parameter. |
|VSwitchId|String|No|vsw-bp1e3se98n9fq8hle\*\*\*\*|The ID of the VSwitch to which the NAT gateway is attached.

 You can specify this parameter only when **NatType** is set to **Enhanced**. |
|NatType|String|No|Normal|The type of the NAT gateway. Valid values:

 -   **Normal**: standard NAT gateway.
-   **Enhanced**: enhanced NAT gateway. For more information about enhanced NAT gateways, see [Release notes for Enhanced NAT Gateway](~~163610~~).

 **Note:** The default type of the NAT gateway created in the China \(Zhangjiakou-Beijing Winter Olympics\), China \(Hohhot\), China \(Chengdu\), China \(Heyuan\), UK \(London\), Germany \(Frankfurt\), Malaysia \(Kuala Lumpur\), and India \(Mumbai\) regions is **Enhanced**. |
|InternetChargeType|String|No|PayBySpec|The metering method of the NAT gateway. Valid values: **PayBySpec** \(pay by specification\). |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|NatGatewayId|String|ngw-112za33e4\*\*\*\*|The ID of the created NAT gateway. |
|ForwardTableIds|List|ftb-11tc6xgmv\*\*\*\*|The list of route entries. |
|BandwidthPackageIds|List|bwp-11odxu2k7\*\*\*\*|The list of NAT bandwidth plans. |
|RequestId|String|2315DEB7-5E92-423A-91F7-4C1EC9AD97C3|The request ID. |
|SnatTableIds|List|stb-SnatTableIds\*\*\*\*|The ID of the SNAT table. |

## Examples

Sample request

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
    <BandwidthPackageIds>
  </BandwidthPackageIds>
    <RequestId>7C01CA72-73FD-4056-B16A-42E392D47625</RequestId>
    <SnatTableIds>
          <SnatTableId>stb-wz9aq9mec6f843j45****</SnatTableId>
    </SnatTableIds>
    <ForwardTableIds>
          <ForwardTableId>ftb-wz9sl3znmxhy605f8****</ForwardTableId>
    </ForwardTableIds>
    <NatGatewayId>ngw-wz95lh0c2wj9b6r1z****</NatGatewayId>
</CreateNatGatewayResponse>
```

`JSON` format

```
{
	"BandwidthPackageIds": {
		"BandwidthPackageId": []
	},
	"RequestId": "7C01CA72-73FD-4056-B16A-42E392D47625",
	"SnatTableIds": {
		"SnatTableId": [
			"stb-wz9aq9mec6f843j45****"
		]
	},
	"ForwardTableIds": {
		"ForwardTableId": [
			"ftb-wz9sl3znmxhy605f8****"
		]
	},
	"NatGatewayId": "ngw-wz95lh0c2wj9b6r1z****"
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|InvalidVPCStatus|vpc incorrect status.|The error message returned because the operation is not supported when the VPC network is in the current state. Check whether the status of the VPC network is valid.|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The error message returned because the specified region ID does not exist.|
|400|InvalidNatGatewayName.MalFormed|NatGateway name is not valid.|The error message returned because the specified gateway name is invalid.|
|400|InvalidNatGatewayDescription.MalFormed|NatGateway description is not valid.|The error message returned because the specified gateway description is invalid.|
|400|MissingParameter.BandwidthPackage|only support one BandwidthPackage be created with NatGateway.|The error message returned because no EIP bandwidth plan is specified.|
|404|InvalidVpcId.NotFound|Specified value of VpcId is not found in our record.|The error message returned because the specified VPC network does not exist. Check whether the specified VPC network ID is valid.|
|400|MissingParameter|Miss mandatory parameter.|The error message returned because the required parameters are missing. Check whether you have set all the required parameters before you call this operation.|
|404|InvalidZoneId.NotFound|Specified value of ZoneId is not exists.|The error message returned because the specified zone ID does not exist.|
|404|InvalidZoneId.NotFound|Can not find ZoneId for allocated ip.|The error message returned because the zone of the specified IP address is invalid.|
|400|QuotaExceeded.BandwidthPackageIps|The specified ipCount exceeded quota.|The error message returned because the number of IP addresses exceeds the quota. Submit a ticket to increase the quota.|
|400|InvalidParameter.Name.Malformed|The specified Name is not valid.|The error message returned because the specified name is invalid. Enter the name in the correct format.|
|400|InvalidParameter.Description.Malformed|The specified Description is not valid.|The error message returned because the specified description is invalid.|
|400|ZONE\_NO\_AVAILABLE\_IP|The Zone have no available ip.|The error message returned because no IP addresses are available in the zone.|
|400|InvalidParameter.BandwidthPackage.n.ISP.ValueNotSupport|The specified ISP of BandwidthPackage is not valid.|The error message returned because the specified ISP of the EIP bandwidth plan is invalid.|
|400|InvalidNatGatewayId.NotFound|The NatGatewayId not exist.|The error message returned because the specified NAT gateway ID does not exist. Check whether the value of the NatGatewayId parameter is valid.|
|400|VswitchStatusError|The VSwitch is creating .|The error message returned because the operation is not supported when the system is creating the VSwitch.|
|400|VpcStatusError|The Vpc is creating .|The error message returned because the operation is not supported when the system is creating the VPC network.|
|400|InvalidParameter.Spec.ValueNotSupported|The specified Spec is not valid.|The error message returned because the specified specification is invalid.|
|400|Forbidden.CheckEntryRuleQuota|Route entry quota rule check error.|The error message returned because an error occurred when the system was checking the quota of route entries.|
|400|NoPermission.CreateServiceLinkedRole|You are not authorized to create service linked role|The error message returned because you do not have permissions to create a SLR.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Vpc).

