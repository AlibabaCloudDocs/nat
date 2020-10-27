# DescribeSnatTableEntries

Queries Source Network Address Translation \(SNAT\) entries in a SNAT table.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Vpc&api=DescribeSnatTableEntries&type=RPC&version=2016-04-28)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeSnatTableEntries|The operation that you want to perform. Set the value to **DescribeSnatTableEntries**. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the NAT gateway is deployed. You can call the [DescribeRegions](~~36063~~) operation to query region IDs. |
|SnatTableId|String|Yes|stb-8vbczigrhop8x5u3t\*\*\*\*|The ID of the SNAT table. |
|SnatEntryId|String|No|snat-8vbae8uqh7rjpk7d2\*\*\*\*|The ID of the SNAT entry.|
|SourceVSwitchId|String|No|vsw-3xbjkhjshjdf\*\*\*\*|The ID of the VSwitch that accesses the Internet through SNAT. |
|SourceCIDR|String|No|116.xx.xx.28/33|The source CIDR block of the SNAT entry. |
|SnatIp|String|No|116.xx.xx.28|The public IP address in the SNAT entry. |
|SnatEntryName|String|No|SnatEntry-1|The name of the SNAT entry.

The description must be 2 to 128 characters in length, and start with a letter. It cannot start with `http://` or `https://`. |
|PageNumber|Integer|No|1|The number of the page to return. Default value: 1. |
|PageSize|Integer|No|10|The number of entries to return on each page. Valid values: 1 to 50. Default value: 10. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|SnatTableEntries|Array of SnatTableEntry| |The detailed information about the SNAT entry. |
|SnatTableEntry| | | |
|SnatEntryId|String|snat-kmd6nv8fy\*\*\*\*|The ID of the SNAT entry. |
|SnatEntryName|String|SnatEntry-1|The name of the SNAT entry. |
|SnatIp|String|116.xx.xx.28|The public IP address in the SNAT entry. |
|SnatTableId|String|stb-gz3r3odawdgffde\*\*\*\*|The ID of the SNAT table to which the SNAT entry belongs. |
|SourceCIDR|String|116.xx.xx.28/33|The source CIDR block of the SNAT entry. |
|SourceVSwitchId|String|vsw-3xbdsffvfgdfds\*\*\*\*|The ID of the VSwitch that accesses the Internet through SNAT. |
|Status|String|Pending|The state of the SNAT entry. Valid values:

-   **Pending**: indicates that the SNAT entry is being created or modified.
-   **Available**: indicates that the SNAT entry is available.
-   **Deleting**: indicates that the SNAT entry is being deleted. |
|TotalCount|Integer|1|The total number of SNAT entries. |
|PageNumber|Integer|1|The number of the returned page. |
|PageSize|Integer|5|The number of entries returned per page. |
|RequestId|String|6D7E89B1-1C5B-412B-8585-4908E222EED5|The ID of the request. |

## Examples

Sample requests

```
https://vpc.aliyuncs.com/?Action=DescribeSnatTableEntries
&RegionId=cn-hangzhou
&SnatTableId=stb-8vbczigrhop8x5u3t****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeSnatTableEntriesResponse>    
  <PageNumber>1</PageNumber>
  <PageSize>10</PageSize>
  <RequestId>6D7E89B1-1C5B-412B-8585-4908E222EED5</RequestId>
  <SnatTableEntries>
        <SnatTableEntry>
              <SnatEntryId>snat-kmd6nv8fy****</SnatEntryId>
              <SnatIp>139.xx.xx.40</SnatIp>
              <SnatTableId>stb-gz3r3odaw****</SnatTableId>
              <SourceCIDR>192.168.1.0/24</SourceCIDR>
              <SourceVSwitchId>vsw-yrv0hffhghd****</SourceVSwitchId>
              <Status>Available</Status>
        </SnatTableEntry>
        <SnatTableEntry>
              <SnatEntryId>snat-bs5bezbme****</SnatEntryId>
              <SnatIp>139.xx.xx.40</SnatIp>
              <SnatTableId>stb-gz3r3odaw****</SnatTableId>
              <SourceCIDR>192.168.3.0/24</SourceCIDR>
              <SourceVSwitchId>vsw-3xbvdgdfeg****</SourceVSwitchId>
              <Status>Available</Status>
        </SnatTableEntry>
  </SnatTableEntries>
</DescribeSnatTableEntriesResponse>
```

`JSON` format

```
{
    "PageNumber": 1, 
    "PageSize": 10, 
    "RequestId": "6D7E89B1-1C5B-412B-8585-4908E222EED5", 
    "SnatTableEntries": {
        "SnatTableEntry": [
            {
                "SnatEntryId": "snat-kmd6nv8fy****", 
                "SnatIp": "139.xx.xx.40", 
                "SnatTableId": "stb-gz3r3odaw****", 
                "SourceCIDR": "192.168.1.0/24", 
                "SourceVSwitchId": "vsw-yrv0hffhghd****", 
                "Status": "Available"
            }, 
            {
                "SnatEntryId": "snat-bs5bezbme****", 
                "SnatIp": "139.xx.xx.40", 
                "SnatTableId": "stb-gz3r3odaw****", 
                "SourceCIDR": "192.168.3.0/24", 
                "SourceVSwitchId": "vsw-3xbvdgdfeg****", 
                "Status": "Available"
            }
        ]
    }
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The error message returned because the specified region ID does not exist. Check whether the region ID is valid.|
|404|InvalidSnatTableId.NotFound|Specified SNAT table does not exist.|The error message returned because the specified SNAT table does not exist. Check whether the parameter is valid.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Vpc).

