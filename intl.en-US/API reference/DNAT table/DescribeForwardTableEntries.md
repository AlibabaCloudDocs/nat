# DescribeForwardTableEntries

Queries Destination Network Address Translation \(DNAT\) entries in a DNAT table.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Vpc&api=DescribeForwardTableEntries&type=RPC&version=2016-04-28)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeForwardTableEntries|The operation that you want to perform. Set the value to **DescribeForwardTableEntries**. |
|ForwardTableId|String|Yes|ftb-bp1mbjubq34hlcqpa\*\*\*\*|The ID of the DNAT table. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the NAT gateway is deployed. You can call the [DescribeRegions](~~36063~~) operation to query region IDs. |
|ForwardEntryId|String|No|fwd-8vbn3bc8roygjp0gy\*\*\*\*|The ID of the DNAT entry. |
|ExternalIp|String|No|116.xx.xx.28|The public IP address used in the DNAT entry. The public IP address is used by the Elastic Compute Service \(ECS\) instance to receive requests from the Internet. |
|ExternalPort|String|No|8080|The external port in the DNAT entry. The external port is used by the Elastic Compute Service \(ECS\) instance to receive requests from the Internet. Valid values: 1 to 65535. |
|InternalIp|String|No|192.xx.xx.123|The private IP address of the ECS instance in the DNAT entry. |
|InternalPort|String|No|80|The internal port that is mapped to the external port in the DNAT entry. Valid values: 1 to 65535. |
|IpProtocol|String|No|TCP|The forwarding protocol. Valid values:

 -   **TCP**: forwards TCP packets.
-   **UDP**: forwards UDP packets.
-   **Any**: forwards packets of all protocols. |
|ForwardEntryName|String|No|ForwardEntry-1|The name of the DNAT entry.

 The description must be 2 to 128 characters in length, and start with a letter. It cannot start with `http://` or `https://`. |
|PageNumber|Integer|No|1|The number of the page to return. Default value: 1. |
|PageSize|Integer|No|10|The number of entries to return on each page. Valid values: 1 to 50. Default value: 10. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|ForwardTableEntries|Array of ForwardTableEntry| |The details of the DNAT entry. |
|ForwardTableEntry| | | |
|ExternalIp|String|139.xxx.xx.79|The public IP address in the DNAT entry. The public IP address is used by the ECS instance to receive requests from the Internet. |
|ExternalPort|String|80|The external port in the DNAT entry. The external port is used by the ECS instance to receive requests from the Internet. |
|ForwardEntryId|String|fwd-119smw5tk\*\*\*\*|The ID of the DNAT entry. |
|ForwardEntryName|String|ForwardEntry-1|The name of the DNAT entry. |
|ForwardTableId|String|ftb-11tc6xgmv\*\*\*\*|The ID of the DNAT table to which the DNAT entry belongs. |
|InternalIp|String|192.168.1.xx|The private IP address that is mapped to the public IP address in the DNAT entry. |
|InternalPort|String|25|The internal port that is mapped to the external port in the DNAT entry. |
|IpProtocol|String|TCP|The type of the protocol. Valid values:

 -   **TCP**: forwards TCP packets.
-   **UDP**: forwards UDP packets.
-   **Any**: forwards packets of all protocols. |
|Status|String|Available|The state of the DNAT entry:

 -   **Pending**: indicates that the DNAT entry is being created or modified.
-   **Available**: indicates that the DNAT entry is available for use.
-   **Deleting**: indicates that the DNAT entry is being deleted. |
|TotalCount|Integer|5|The total number of entries returned. |
|PageNumber|Integer|1|The page number of the returned page. |
|PageSize|Integer|10|The number of entries returned per page. |
|RequestId|String|A6C4A8B1-7561-4509-949C-20DEB40D71E6|The ID of the request. |

## Examples

Sample requests

```
https://vpc.aliyuncs.com/?Action=DescribeForwardTableEntries
&ForwardTableId=ftb-bp1mbjubq34hlcqpa****
&RegionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeForwardTableEntriesResponse>	
  <PageNumber>1</PageNumber>
  <TotalCount>1</TotalCount>
  <PageSize>10</PageSize>
  <RequestId>D15864E1-6068-4CF9-AC3D-653D2143E269</RequestId>
  <ForwardTableEntries>
        <ForwardTableEntry>
              <Status>Available</Status>
              <IpProtocol>TCP</IpProtocol>
              <ForwardEntryId>fwd-bp1yjpsk36ojv9rrz****</ForwardEntryId>
              <ExternalIp>47.96.xx.184</ExternalIp>
              <ForwardTableId>ftb-bp1pnianh59fsh09b****</ForwardTableId>
              <ExternalPort>80</ExternalPort>
              <InternalPort>25</InternalPort>
              <InternalIp>192.168.xx.39</InternalIp>
              <ForwardEntryName>vmeixme</ForwardEntryName>
        </ForwardTableEntry>
  </ForwardTableEntries>
</DescribeForwardTableEntriesResponse>
```

`JSON` format

```
{
	"PageNumber": 1,
	"TotalCount": 1,
	"PageSize": 10,
	"RequestId": "D15864E1-6068-4CF9-AC3D-653D2143E269",
	"ForwardTableEntries": {
		"ForwardTableEntry": [
			{
				"Status": "Available",
				"IpProtocol": "TCP",
				"ForwardEntryId": "fwd-bp1yjpsk36ojv9rrz****",
				"ExternalIp": "47.96.xx.184",
				"ForwardTableId": "ftb-bp1pnianh59fsh09b****",
				"ExternalPort": "80",
				"InternalPort": "25",
				"InternalIp": "192.168.xx.39",
				"ForwardEntryName": "vmeixme"
			}
		]
	}
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The error message returned because the specified region ID does not exist. Check whether the region ID is valid.|
|400|IncorretForwardEntryStatus|Some Forward entry status blocked this operation..|The error message returned because you are not authorized to perform the specified operation. One or more DNAT entries in the DNAT table are in the Pending or Modifying state.|
|404|InvalidForwardTableId.NotFound|Specified forwardTableId does not exist|The error message returned because the specified DNAT entry does not exist. Verify the parameter and try again.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Vpc).

