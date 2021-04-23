# CreateForwardEntry

Adds a Destination Network Address Translation \(DNAT\) entry to a DNAT table.

## Description

Each DNAT entry consists of the following elements:**ExternalIp**, **ExternalPort**, **protocol**, **InternalIp**, and **InternalPort**. After you add a DNAT entry, the NAT gateway forwards packets that are received on **ExternalIp: ExternalPort** to **InternalIp: InternalPort**. The NAT gateway also returns responses by using the same route.

When you call this operation, take note of the following limits:

-   CreateForwardEntry is an asynchronous operation. After you make a request, a DNAT entry ID is returned but the specified DNAT entry is not added. The system adds the entry in the background. You can call the [DescribeForwardTableEntries](~~36053~~) operation to query the state of the DNAT entry.
    -   When the DNAT entry is in the **Pending** state, the system is adding the DNAT entry. You can only query the state of the DNAT entry, and cannot perform other operations.
    -   When the DNAT entry is in the **Available** state, the DNAT entry is added.
-   All combinations of **ExternalIp**, **ExternalPort**, and**Protocol** used in DNAT entries must be unique. You cannot distribute requests to more than one Elastic Compute Service \(ECS\) instance if these requests are originated from the same source IP address, received on the same port, and use the same protocol.
-   The combinations of **Protocol**, **InternalIp**, and **InternalPort** used in DNAT entries must be unique.
-   If one or more DNAT entries in the DNAT table are in the **Pending** or **Modifying** state, you cannot add DNAT entries to the DNAT table.
-   You can add up to 100 DNAT entries to a DNAT table.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Vpc&api=CreateForwardEntry&type=RPC&version=2016-04-28)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateForwardEntry|The operation that you want to perform. Set the value to **CreateForwardEntry**. |
|ExternalIp|String|Yes|116.XX.XX.28|The public IP address used by the ECS instance to access the Internet. The public IP address must meet the following requirements:

 -   If you purchased a NAT bandwidth plan before November 3, 2017, the **ExternalIp** parameter must be a public IP address that is associated with the NAT bandwidth plan.
-   If you did not purchase a NAT bandwidth plan before November 3, 2017, the **ExternalIp** must be an elastic IP address \(EIP\) that is associated with the NAT gateway. |
|ExternalPort|String|Yes|8080|The public port used for port forwarding. Valid values: **1** to **65535**. |
|ForwardTableId|String|Yes|ftb-bp1mbjubq34hlcqpa\*\*\*\*|The ID of the DNAT table. |
|InternalIp|String|Yes|192.XX.XX.1|The private IP address that is mapped to the public IP address in the DNAT entry. The private IP address must meet the following requirements:

 -   It must belong to the CIDR block of the virtual private cloud \(VPC\) where the NAT gateway is deployed.
-   The DNAT entry takes effect only when it is used by an ECS instance that is not associated with an EIP. If the private IP address specified by the **InternalIp** parameter is allocated to a non-ECS resource, such as a high-availability virtual IP address \(HAVIP\), Server Load Balancer \(SLB\) instance, or ApsaraDB RDS instance, the DNAT entry does not take effect. Therefore, inbound traffic cannot be forwarded to the private IP address. |
|InternalPort|String|Yes|80|The internal port to which requests are forwarded. Valid values: **1** to **65535**. |
|IpProtocol|String|Yes|TCP|The protocol type. Valid values:

 -   **TCP**: forwards TCP packets.
-   **UDP**: forwards UDP packets.
-   **Any**: forwards packets of all protocols. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the NAT gateway is created. You can call the [DescribeRegions](~~36063~~) operation to query the most recent region list. |
|ForwardEntryName|String|No|ForwardEntry-1|The name of the DNAT entry.

 The name must be 2 to 128 characters in length. It must start with a letter but cannot start with `http://` or `https://`. |
|ClientToken|String|No|0c593ea1-3bea-11e9-b96b-88e9fe6\*\*\*\*|The client token that is used to ensure the idempotence of the request. You can use the client to generate the value, but you must ensure that it is unique among different requests. **ClientToken** can contain only ASCII characters and cannot exceed 64 characters in length. |
|PortBreak|Boolean|No|false|Specify whether to remove limits on the port range. Valid values:

 -   **true**: removes limits on the port range.
-   **false** \(default\): sets limits on the port range.

 **Note:** An SNAT entry and a DNAT entry may use the same public IP address. If you want to specify a port number greater than 1024, set **Portbreak** to **true**. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|ForwardEntryId|String|fwd-119smw5tkasdf\*\*\*\*|The ID of the DNAT entry. |
|RequestId|String|A4AEE536-A97A-40EB-9EBE-53A6948A6928|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=CreateForwardEntry
&ExternalIp=116.XX.XX.28
&ExternalPort=8080
&ForwardTableId=ftb-bp1mbjubq34hlcqpa****
&InternalIp=192.XX.XX.1
&InternalPort=80
&IpProtocol=TCP
&RegionId=cn-hangzhou
&<Common Request Parameters>
```

Sample success responses

`XML` format

```
<CreateForwardEntryResponse>
  <RequestId>A4AEE536-A97A-40EB-9EBE-53A6948A6928</RequestId>
  <ForwardEntryId>fwd-119smw5tkasdf****</ForwardEntryId>
</CreateForwardEntryResponse>
```

`JSON` format

```
{
    "RequestId": "A4AEE536-A97A-40EB-9EBE-53A6948A6928",
    "ForwardEntryId": "fwd-119smw5tkasdf****"
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The error message returned because the specified region ID does not exist.|
|400|InvalidExternalIp.Malformed|The specified ExternalIp is not a valid IP address.|The error message returned because the specified IP address is invalid.|
|400|InvalidInternalIp.Malformed|The specified InternalIp is not a valid IP address.|The error message returned because the specified private IP address is invalid.|
|400|InvalidExternalPort.Malformed|The specified ExternalPort is not a valid port.|The error message returned because the specified public port is invalid.|
|400|InvalidInternalPort.Malformed|The specified InternalPort is not a valid port.|The error message returned because the specified private port is invalid.|
|400|Forbidden.DestnationIpOutOfVpcCIDR|The specified Internal Ip is Out of VPC CIDR.|The error message returned because the specified private IP address does not fall within the CIDR block of the VPC. Enter a private IP address that falls within the CIDR block of the VPC.|
|400|InvalidProtocal.ValueNotSupported|The specified IpProtocol does not support.|The error message returned because the specified protocol type is not supported.|
|400|IncorretForwardEntryStatus|Some Forward entry status blocked this operation..|The error message returned because the operation cannot be performed. The error message returned because one or more DNAT entries in the DNAT table are in the Pending or Modifying state.|
|404|InvalidForwardTableId.NotFound|Specified forward table does not exist.|The error message returned because the specified DNAT table does not exist. Check the parameter value and try again.|
|404|InvalidExternalIp.NotFound|Specified External Ip address does not found on the VRouter|The error message returned because the specified public IP address does not exist.|
|400|Forbidden.ExternalIp.UsedInSnatTable|The specified ExternalIp is already used in SnatTable|The error message returned because the specified public IP address is already used by an SNAT entry. Select a different IP address or delete the SNAT entry.|
|400|Forbindden|The specified Instance already bind eip|The error message returned because the ECS instance is associated with an EIP. Disassociate the EIP from the ECS instance before you create forwarding rules.|
|400|Forbidden.InternalIpOutOfVpcCIDR|The specified Internal Ip is Out of VPC CIDR.|The error message returned because the private IP address does not fall within the CIDR block of the VPC.|
|400|Invalid.natgwNotExist|The specified natgateway not exist.|The error message returned because the specified NAT gateway does not exist.|
|400|InvalidIp.NotInNatgw|The specified Ip not belong to natgateway.|The error message returned because the specified IP address is not associated with the NAT gateway.|
|400|MissingParameter|Missing mandatory parameter|The error message returned because one or more required parameters are not set. Check whether you have set all required parameters.|
|500|InternalError|The request processing has failed due to some unknown error.|The error message returned because an unknown error occurred.|
|400|InvalidParameter.Name.Malformed|The specified Name is not valid.|The error message returned because the specified name is invalid.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Vpc).

