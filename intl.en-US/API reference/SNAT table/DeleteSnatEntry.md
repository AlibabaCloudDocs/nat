# DeleteSnatEntry

Deletes a specified Source Network Address Translation \(SNAT\) entry.

## Description

DeleteSnatEntry is an asynchronous operation. After you make a request, the ID of the request is returned but the specified SNAT entry is not deleted. The system deletes the SNAT entry in the background. You can call the DescribeNatGateways operation to query the state of the SNAT entry:

-   **Deleting**: specifies that the system is deleting the SNAT entry. You can only query the state of the SNAT entry, but cannot perform other operations.
-   If no SNAT entry is returned in the response, the SNAT entry is deleted.

**Note:** If a SNAT table contains SNAT entries in the **Pending** state, you cannot delete any SNAT entries in the SNAT table.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Vpc&api=DeleteSnatEntry&type=RPC&version=2016-04-28)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DeleteSnatEntry|The operation that you want to perform. Set the value to **DeleteSnatEntry**. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the NAT gateway is deployed. You can call the [DescribeRegions](~~36063~~) operation to query region IDs. |
|SnatEntryId|String|Yes|snat-bp1vcgcf8tm0plqcg\*\*\*\*|The ID of the SNAT entry. |
|SnatTableId|String|Yes|stb-bp190wu8io1vgev80\*\*\*\*|The ID of the SNAT table to which the SNAT entry belongs. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|47B80B6A-759A-479C-A565-76D04BDA29F3|The ID of the request. |

## Examples

Sample requests

```
https://vpc.aliyuncs.com/?Action=DeleteSnatEntry
&RegionId=cn-hangzhou
&SnatEntryId=snat-bp1vcgcf8tm0plqcg****
&SnatTableId=stb-bp190wu8io1vgev80****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DeleteSnatEntryResponse>
      <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
</DeleteSnatEntryResponse>
```

`JSON` format

```
{ 
    "RequestId": "0ED8D006-F706-4D23-88ED-E11ED28DCAC0"
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The error message returned because the specified region ID does not exist. Check whether the region ID is valid.|
|400|IncorretSnatEntryStatus|Some Snat entry status blocked this operation..|The error message returned because you are unauthorized to perform the specified operation. The error message returned because one or more SNAT entries in the SNAT table are in the Pending or Modifying state.|
|404|InvalidSnatEntryId.NotFound|Specified Snat entry ID does not exist|The error message returned because the specified SNAT entry does not exist. Check whether the SNAT entry is valid.|
|404|InvalidSnatTableId.NotFound|Specified SNAT table does not exist.|The error message returned because the specified SNAT table does not exist. Check whether the parameter is valid.|
|404|InvalidSnatEntryId.NotFound|Specified SNAT entry does not exist.|The error message returned because the specified SNAT entry does not exist. Check whether the SNAT entry is valid.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Vpc).

