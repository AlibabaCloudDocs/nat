# DeleteForwardEntry

Deletes a specified DNAT entry.

## Description

DeleteForwardEntry is an asynchronous operation. After you make a request, the ID of the request is returned but the specified DNAT entry is not deleted. The system deletes the entry in the background. You can call the [DescribeNatGateways](~~36054~~) operation to query the DNAT entry in the DNAT table:

-   **Deleting**: indicates that the system is deleting the DNAT entry. You can only query the state of the DNAT entry, but cannot perform other operations.
-   If no DNAT entry is returned in the response, the DNAT entry is deleted.

**Note:** If a DNAT table contains DNAT entries in the **Pending** state, you cannot delete DNAT entries in the DNAT table.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Vpc&api=DeleteForwardEntry&type=RPC&version=2016-04-28)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DeleteForwardEntry|The operation that you want to perform. Set the value to **DeleteForwardEntry**. |
|ForwardEntryId|String|Yes|fwd-8vbn3bc8roygjp0gy\*\*\*\*|The ID of the DNAT entry to be deleted. |
|ForwardTableId|String|Yes|ftb-8vbx8xu2lqj9qb334\*\*\*\*|The ID of the DNAT table to which the DNAT entry belongs. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the NAT gateway is deployed. You can call the [DescribeRegions](~~36063~~) operation to query region IDs. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|0ED8D006-F706-4D23-88ED-E11ED28DCAC0|The ID of the request. |

## Examples

Sample requests

```
https://vpc.aliyuncs.com/?Action=DeleteForwardEntry
&ForwardEntryId=fwd-8vbn3bc8roygjp0gy****
&ForwardTableId=ftb-8vbx8xu2lqj9qb334****
&RegionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DeleteForwardEntryResponse>
      <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
</DeleteForwardEntryResponse>
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
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The error message returned because the specified region ID does not exist. Check whether the service is available in the region.|
|400|IncorretForwardEntryStatus|Some Forward entry status blocked this operation..|The error message returned because you are unauthorized to perform the specified operation. The error message returned because one or more DNAT entries in the DNAT table are in the Pending or Modifying state.|
|404|InvalidForwardEntryId.NotFound|Specified forward entry ID does not exist|The error message returned because the specified DNAT entry does not exist.|
|404|InvalidForwardTableId.NotFound|Specified forward table does not exist.|The error message returned because the specified DNAT table does not exist. Verify the parameter and try again.|
|400|IncorretForwardEntryStatus|The Specified forwardEntry is not exist|The error message returned because the specified DNAT entry does not exist.|
|400|MissingParameter|Missing mandatory parameter|The error message returned because the required parameters are not set. Check whether you have set all of the required parameters before you call this operation.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Vpc).

