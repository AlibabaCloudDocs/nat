# CreateSnatEntry

Adds a Source Network Address Translation \(SNAT\) entry to an SNAT table.

## Description

When you call this operation, take note of the following limits:

-   CreateSnatEntry is an asynchronous operation. After you make a request, an SNAT entry ID is returned but the specified SNAT entry is not added. The system adds the entry in the background. You can call the [DescribeSnatTableEntries](~~42677~~) operation to query the state of the SNAT entry.
    -   When the SNAT entry is in the **Pending** state, the system is adding the SNAT entry. You can only query the state of the SNAT entry, and cannot perform other operations.
    -   When the SNAT entry is in the **Available** state, the SNAT entry is added.
-   The vSwitch and the Elastic Compute Service \(ECS\) instance specified in the SNAT entry must belong to the virtual private cloud \(VPC\) where the NAT gateway is deployed.
-   Each vSwitch or ECS instance can be specified in only one SNAT entry.
-   If a high-availability virtual IP address \(HAVIP\) exists in the vSwitch, you cannot create SNAT entries.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Vpc&api=CreateSnatEntry&type=RPC&version=2016-04-28)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateSnatEntry|The operation that you want to perform. Set the value to **CreateSnatEntry**. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the NAT gateway is created. You can call the [DescribeRegions](~~36063~~) operation to query the most recent region list. |
|SnatIp|String|Yes|47.XX.XX.98|Public IP addresses. Separate multiple IP addresses with commas \(,\).

 **Note:** If you select multiple elastic IP addresses \(EIPs\) to create an SNAT address pool, make sure that you have associated all EIPs with the same EIP bandwidth plan. |
|SnatTableId|String|Yes|stb-bp190wu8io1vgev\*\*\*\*|The ID of the SNAT table. |
|SourceVSwitchId|String|No|vsw-bp1nhx2s9ui5o\*\*\*\*|The ID of the vSwitch that is required to access the Internet. |
|SourceCIDR|String|No|10.1.1.0/24|The CIDR block of the vSwitch or the IP address of the ECS instance.

 -   You can specify the CIDR block of a vSwitch. When the ECS instances that belong to the vSwitch send requests to the Internet, the NAT gateway provides SNAT services.
    -   If**SnatIp** is set to a public IP address, the ECS instances use the public IP address to access the Internet.
    -   If**SnatIp** is set to multiple public IP addresses, the ECS instances randomly use the IP addresses specified by the **SnatIp** parameter to access the Internet.
-   You can also specify the IP address of an ECS instance. When the ECS instance sends requests to the Internet, the NAT gateway provides SNAT services.
    -   If**SnatIp** is set to a public IP address, the ECS instance uses the public IP address to access the Internet.
    -   If**SnatIp** is set to multiple public IP addresses, the ECS instance randomly uses the IP addresses specified by the **SnatIp** parameter to access the Internet.

 This parameter and the **SourceVSwtichId** parameter cannot be set at the same time. If the **SourceVSwitchId** parameter is set, you cannot set the **SourceCIDR** parameter. If the **SourceCIDR** parameter is set, you cannot set the **SourceVSwitchId** parameter. |
|SnatEntryName|String|No|SnatEntry-1|The name of the SNAT entry.

 The name must be 2 to 128 characters in length, and must start with a letter. It cannot start with `http://` or `https://`. |
|ClientToken|String|No|02fb3da4-130e-11e9-8e44\*\*\*\*|The client token that is used to ensure the idempotence of the request. You can use the client to generate the value, but you must ensure that it is unique among different requests. **ClientToken** can contain only ASCII characters and cannot exceed 64 characters in length. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|SnatEntryId|String|snat-kmd6nv8fy\*\*\*\*|The ID of the SNAT entry. |
|RequestId|String|2315DEB7-5E92-423A-91F7-4C1EC9AD97C3|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=CreateSnatEntry
&RegionId=cn-hangzhou
&SnatIp=47.XX.XX.98
&SnatTableId=stb-bp190wu8io1vgev****
&<Common Request Parameters>
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
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The error message returned because the specified region ID does not exist.|
|404|InvalidSnatTableId.NotFound|Specified SNAT table does not exist.|The error message returned because the specified SNAT table does not exist. Check whether the ID of the SNAT table is valid.|
|400|Forbidden.SourceVSwitchId.IncludeHaVip|There is some HaVips under specified VSwitch|The error message returned because one or more HAVIPs belong to the specified vSwitch.|
|400|InvalidSnatIp.Malformed|The specified SnatIp is not a valid IP address.|The error message returned because the specified IP address is invalid.|
|400|SNAT\_IP\_POOL\_COUNT\_TOO\_MANY|The Snat pool ip too many.|The error message returned because the number of IP addresses in the SNAT IP address pool has reached the upper limit.|
|400|Forbidden.SnatEntryCountLimited|SNAT entry in the specified SNAT table reach it?s limit.|The error message returned because the number of SNAT entries has reached the upper limit.|
|400|NOT\_ALLOW\_USE\_SOURCECIDR|The User not in nat\_scope\_unlimited white list. Cannot use SourceCidr param.|The error message returned because the specified private IP address does not fall within the CIDR block of the VPC.|
|404|InvalidVSwitchId.NotFound|The specified virtual switch does not exists.|The error message returned because the specified vSwitch does not exist. Check whether the specified vSwitch ID is valid.|
|400|INVALID\_PARAMETER|The parameter invalid.|The error message returned because the specified parameter is invalid.|
|400|Forbidden.SourceVSwitchId.Duplicated|The specified SourceCIDRis duplicated.|The error message returned because an SNAT entry is already created for the specified vSwitch.|
|404|InvalidSnatIp.NotFound|Specified SnatIp does not found on the NAT Gateway|The error message returned because the specified public IP address is not found on the NAT gateway.|
|400|Forbidden.IpUsedInForwardTable|The specified SnatIp already used in forward table|The error message returned because the specified public IP address is already used by a DNAT entry. Select another public IP address or delete the DNAT entry.|
|400|Forbindden|The specified Instance already bind eip|The error message returned because the ECS instance is associated with an EIP. Disassociate the EIP from the ECS instance before you create forwarding rules.|
|400|OperationUnsupported.CidrConflict|The specified CIDR block conflicts with an existing SNAT entry.|The error message returned because the specified CIDR block conflicts with those in existing SNAT entries.|
|400|InvalidParameter.Name.Malformed|The specified Name is not valid.|The error message returned because the specified name is invalid.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Vpc).

