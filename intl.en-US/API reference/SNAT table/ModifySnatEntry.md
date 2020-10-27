# ModifySnatEntry

Modifies a specified Source Network Address Translation \(SNAT\) entry.

## Description

ModifySnatEntry is an asynchronous operation. After you make a request, the ID of the request is returned but the specified SNAT entry is not modified. The system modifies the entry in the background. You can call the [DescribeNatGateways](~~36054~~) operation to query the state of the SNAT entry:

-   **Pending**: indicates that the system is modifying the SNAT entry. You can only query the state of the SNAT entry, but cannot perform other operations.
-   **Available**: indicates that the DNAT entry is modified.

**Note:** **Pending**: indicates that you cannot modify the SNAT entry in the SNAT table.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Vpc&api=ModifySnatEntry&type=RPC&version=2016-04-28)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ModifySnatEntry|The operation that you want to perform. Set the value to **ModifySnatEntry**. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the NAT gateway is deployed. You can call the [DescribeRegions](~~36063~~) operation to query region IDs. |
|SnatEntryId|String|Yes|snat-bp1vcgcf8tm0plqcg\*\*\*\*|The ID of the SNAT entry. |
|SnatTableId|String|Yes|stb-8vbczigrhop8x5u3t\*\*\*\*|The ID of the SNAT table to which the SNAT entry belongs. |
|SnatIp|String|No|47.xx.xx.98|The public IP address in the SNAT entry. If multiple IP addresses are specified, separate them with commas \(,\).

**Note:** If you specify multiple public IP addresses to create a SNAT address pool, make sure that you have added all public IP addresses to the same EIP bandwidth plan. |
|SnatEntryName|String|No|SnatEntry-1|The name of the SNAT entry.

The description must be 2 to 128 characters in length, and start with a letter or Chinese character. It cannot start with `http://` or `https://`. |
|ClientToken|String|No|02fb3da4-130e-11e9-8e44-001\*\*\*\*|The client token that is used to ensure the idempotence of the request. You can use the client to generate a token, but you must make sure that it is unique among different requests. Only ASCII characters are allowed. It can contain up to 64 ASCII characters. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|2315DEB7-5E92-423A-91F7-4C1EC9AD97C3|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=ModifySnatEntry
&RegionId=cn-hangzhou
&SnatEntryId=snat-bp1vcgcf8tm0plqcg****
&SnatTableId=stb-8vbczigrhop8x5u3t****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ModifySnatEntryResponse>
      <RequestId>2315DEB7-5E92-423A-91F7-4C1EC9AD97C3</RequestId>
</ModifySnatEntryResponse>
```

`JSON` format

```
{
  "RequestId": "2315DEB7-5E92-423A-91F7-4C1EC9AD97C3"
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The error message returned because the specified region ID does not exist. Check whether the region ID is valid.|
|404|InvalidSnatTableId.NotFound|Specified SNAT table does not exist.|The error message returned because the specified SNAT table does not exist. Verify the parameter and try again.|
|400|InvalidSnatIp.Malformed|The specified SnatIp is not a valid IP address.|The error message returned because the specified public IP address is invalid.|
|404|InvalidSnatEntryId.NotFound|Specified SNAT entry does not exist.|The error message returned because the specified SNAT entry does not exist. Check whether the SNAT entry is valid.|
|400|Forbidden.SourceVSwitchId.Duplicated|The specified SourceCIDRis duplicated.|The error message returned because the SNAT entry is already configured for the specified VSwitch.|
|404|InvalidSnatIp.NotFound|Specified SnatIp does not found on the NAT Gateway|The error message returned because the specified public IP address does not exist in the NAT gateway.|
|400|Forbidden.IpUsedInForwardTable|The specified SnatIp already used in forward table|The error message returned because the specified public IP address is already used by a DNAT entry. Select another IP address or delete the DNAT rule that uses the public IP address.|
|400|InvalidParameter.Name.Malformed|The specified Name is not valid.|The error message returned because the specified name is invalid.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Vpc).

