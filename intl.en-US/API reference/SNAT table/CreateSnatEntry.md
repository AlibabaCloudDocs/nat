# CreateSnatEntry

Adds a Source Network Address Translation \(SNAT\) entry to a SNAT table.

## Description

When you call this operation, take note of the following information:

-   CreateSnatEntry is an asynchronous operation. After you make a request, a SNAT entry ID is returned but the specified SNAT entry is not added. The system adds the entry in the background. You can call the [DescribeNatGateways](~~36054~~) operation to query the SNAT entry:
    -   **Pending**: indicates that the system is adding the SNAT entry. You can only query the state of the SNAT entry, but cannot perform other operations.
    -   **Available**: indicates that the SNAT entry is added.
-   The VSwitch and the Elastic Compute Service \(ECS\) instance specified in the SNAT entry must be in the virtual private cloud \(VPC\) where the NAT gateway is deployed.
-   Each VSwitch or ECS instance can be specified in only one SNAT entry.
-   If a highly available VIP \(HAVIP\) instance exists in the VSwitch, you cannot create SNAT entries.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Vpc&api=CreateSnatEntry&type=RPC&version=2016-04-28)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateSnatEntry|The operation that you want to perform. Set the value to **CreateSnatEntry**. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the NAT gateway is deployed. You can call the [DescribeRegions](~~36063~~) operation to query region IDs. |
|SnatIp|String|Yes|47.xx.xx.98|The public IP addresses. Separate multiple IP addresses with commas \(,\).

 **Note:** If you select multiple elastic IP addresses \(EIPs\) to create a SNAT address pool, make sure that you have added all EIPs to the same EIP bandwidth plan. |
|SnatTableId|String|Yes|stb-bp190wu8io1vgev\*\*\*\*|The ID of the SNAT table. |
|SourceVSwitchId|String|No|vsw-bp1nhx2s9ui5o\*\*\*\*|The ID of VSwitch that needs to access the Internet. |
|SourceCIDR|String|No|10.1.1.0/24|The CIDR block of the VSwitch or the IP address of the ECS instance.

 -   VSwitch granularity: specifies the CIDR block of the VSwitch, for example, 192.168.1.0/24. When an ECS instance attached to the VSwitch requires Internet access, the NAT gateway provides the SNAT service \(Internet proxy service\) for the ECS instance. If you specify only one public IP address in the **SnatIp** parameter, the ECS instance uses the specified public IP address to access the Internet. If you specify multiple public IP addresses in the **SnatIp** parameter, the ECS instance randomly selects a public IP address from **SnatIp** to access the Internet.
-   ECS granularity: specifies the IP address of the ECS instance, for example, 192.168.1.1/32. When the ECS instance requires Internet access, the NAT gateway provides the SNAT service \(Internet proxy service\) for the ECS instance. If you specify only one public IP address in the **SnatIp** parameter, the ECS instance uses the specified public IP address to access the Internet. If you specify multiple public IP addresses in the **SnatIp** parameter, the ECS instance randomly selects a public IP address from **SnatIp** to access the Internet.

 This parameter and the **SourceVSwtichId** parameter are mutually exclusive. If the **SourceVSwitchId** parameter is specified, you cannot set the **SourceCIDR** parameter in the same request. If the **SourceCIDR** parameter is specified, you cannot set the **SourceVSwitchId** parameter in the same request. |
|SnatEntryName|String|No|SnatEntry-1|The name of the SNAT entry.

 The description must be 2 to 128 characters in length, and start with a letter. It cannot start with `http://` or `https://`. |
|ClientToken|String|No|02fb3da4-130e-11e9-8e44-001sdfg|The client token that is used to ensure the idempotence of the request. You can use the client to generate a value that is unique among different requests. **ClientToken** can contain only ASCII characters and cannot exceed 64 characters in length. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|SnatEntryId|String|snat-kmd6nv8fy\*\*\*\*|The ID of the SNAT entry. |
|RequestId|String|2315DEB7-5E92-423A-91F7-4C1EC9AD97C3|The ID of the request. |

## Examples

Sample requests

```
https://vpc.aliyuncs.com/?Action=CreateSnatEntry
&RegionId=cn-hangzhou
&SnatIp=47.xx.xx.98
&SnatTableId=stb-bp190wu8io1vgevx****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<CreateSnatEntryResponse>
      <RequestId>2315DEB7-5E92-423A-91F7-4C1EC9AD97C3</RequestId>
      <SnatEntryId>snat-119smw5tkx****</SnatEntryId>
</CreateSnatEntryResponse>
```

`JSON` format

```
{
    "SnatEntryId": "snat-kmd6nv8fyx****",
    "RequestId": "2315DEB7-5E92-423A-91F7-4C1EC9AD97C3"
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The error message returned because the specified region ID does not exist. Check whether the region ID is valid.|
|404|InvalidSnatTableId.NotFound|Specified SNAT table does not exist.|The error message returned because the specified SNAT table does not exist. Check whether the parameter is valid.|
|400|Forbidden.SourceVSwitchId.IncludeHaVip|There is some HaVips under specified VSwitch|The error message returned because one or more HAVIPs belong to the specified VSwitch.|
|400|InvalidSnatIp.Malformed|The specified SnatIp is not a valid IP address.|The error message returned because the specified IP address is invalid.|
|400|SNAT\_IP\_POOL\_COUNT\_TOO\_MANY|The Snat pool ip too many.|The error message returned because the number of IP addresses in the SNAT IP address pool reaches the quota limit.|
|400|Forbidden.SnatEntryCountLimited|SNAT entry in the specified SNAT table reach it? s limit.|The error message returned because the number of SNAT entries reaches the quota limit.|
|400|NOT\_ALLOW\_USE\_SOURCECIDR|The User not in nat\_scope\_unlimited white list. Cannot use SourceCidr param.|The error message returned because the specified private IP address is not within the CIDR block of the VPC.|
|404|InvalidVSwitchId.NotFound|The specified virtual switch does not exists.|The error message returned because the specified VSwitch does not exist. Check whether the specified parameter is valid.|
|400|INVALID\_PARAMETER|The parameter invalid.|The error message returned because the specified parameter is invalid.|
|400|Forbidden.SourceVSwitchId.Duplicated|The specified SourceCIDRis duplicated.|The error message returned because the SNAT entry is already configured for the specified VSwitch.|
|404|InvalidSnatIp.NotFound|Specified SnatIp does not found on the NAT Gateway|The error message returned because the specified public IP address does not exist on the NAT gateway.|
|400|Forbidden.IpUsedInForwardTable|The specified SnatIp already used in forward table|The error message returned because the specified public IP address is used by a Destination Network Address Translation \(DNAT\) entry. Select a different IP address or delete the DNAT rule that uses the public IP address.|
|400|Forbindden|The specified Instance already bind eip|The error message returned because the ECS instance is assigned an EIP. Disassociate the EIP from the ECS instance, and then create forwarding rules.|
|400|OperationUnsupported.CidrConflict|The specified CIDR block conflicts with an existing SNAT entry.|The error message returned because the specified CIDR block conflicts with the existing SNAT entries.|
|400|InvalidParameter.Name.Malformed|The specified Name is not valid.|The error message returned because the specified name is invalid.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Vpc).

