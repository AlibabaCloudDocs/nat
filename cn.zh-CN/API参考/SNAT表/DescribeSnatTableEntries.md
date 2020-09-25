# DescribeSnatTableEntries

调用DescribeSnatTableEntries接口查询已创建的SNAT条目。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DescribeSnatTableEntries&type=RPC&version=2016-04-28)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeSnatTableEntries|要执行的操作。取值：**DescribeSnatTableEntries**。 |
|RegionId|String|是|cn-hangzhou|NAT网关所在的地域。您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。 |
|SnatTableId|String|是|stb-8vbczigrhop8x5u3t\*\*\*\*|SNAT表ID。 |
|SnatEntryId|String|否|snat-8vbae8uqh7rjpk7d2\*\*\*\*|SNAT条目ID。 |
|SourceVSwitchId|String|否|vsw-3xbjkhjshjdf\*\*\*\*|通过SNAT功能进行公网访问的交换机ID。 |
|SourceCIDR|String|否|116.xx.xx.28/33|SNAT条目的源网段。 |
|SnatIp|String|否|116.xx.xx.28|SNAT条目的公网IP。 |
|SnatEntryName|String|否|SnatEntry-1|SNAT条目的名称。

 长度为2~128个字符，必须以字母或中文开头，但不能以`http://`或`https://`开头。 |
|PageNumber|Integer|否|1|列表的页码，默认值为1。 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为50，默认值为10。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|SnatTableEntries|Array of SnatTableEntry| |SNAT列表的详细信息。 |
|SnatTableEntry| | | |
|SnatEntryId|String|snat-kmd6nv8fy\*\*\*\*|SNAT条目的ID。 |
|SnatEntryName|String|SnatEntry-1|SNAT条目的名称。 |
|SnatIp|String|116.xx.xx.28|SNAT条目的公网IP。 |
|SnatTableId|String|stb-gz3r3odawdgffde\*\*\*\*|SNAT条目所属的SNAT表ID。 |
|SourceCIDR|String|116.xx.xx.28/33|SNAT条目的源网段。 |
|SourceVSwitchId|String|vsw-3xbdsffvfgdfds\*\*\*\*|通过SNAT功能进行公网访问的交换机ID。 |
|Status|String|Pending|SNAT条目状态：

 -   **Pending**：配置中，可能是创建中和修改中。
-   **Available**：可用。
-   **Deleting**：删除中。 |
|TotalCount|Integer|1|列表条目数。 |
|PageNumber|Integer|1|当前页码。 |
|PageSize|Integer|5|每页包含的条目数。 |
|RequestId|String|6D7E89B1-1C5B-412B-8585-4908E222EED5|请求ID。 |

## 示例

请求示例

```
https://vpc.aliyuncs.com/?Action=DescribeSnatTableEntries
&RegionId=cn-hangzhou
&SnatTableId=stb-8vbczigrhop8x5u3t****
&<公共请求参数>
```

正常返回示例

`XML` 格式

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

`JSON` 格式

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

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|
|404|InvalidSnatTableId.NotFound|Specified SNAT table does not exist.|指定的 SNAT 表不存在，请您检查输入参数是否正确。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

