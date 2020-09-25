# DescribeForwardTableEntries

调用DescribeForwardTableEntries接口查询已创建的DNAT条目。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DescribeForwardTableEntries&type=RPC&version=2016-04-28)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeForwardTableEntries|要执行的操作，取值：**DescribeForwardTableEntries**。 |
|ForwardTableId|String|是|ftb-bp1mbjubq34hlcqpa\*\*\*\*|DNAT列表的ID。 |
|RegionId|String|是|cn-hangzhou|NAT网关所在的地域。您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。 |
|ForwardEntryId|String|否|fwd-8vbn3bc8roygjp0gy\*\*\*\*|DNAT条目ID。 |
|ExternalIp|String|否|116.xx.xx.28|DNAT条目中提供公网访问的公网IP地址。 |
|ExternalPort|String|否|8080|进行端口转发的外部端口，取值范围：1~65535。 |
|InternalIp|String|否|192.xx.xx.123|通过DNAT条目进行公网通信的ECS实例的私网IP地址。 |
|InternalPort|String|否|80|进行端口转发的内部端口，取值范围：1~65535。 |
|IpProtocol|String|否|TCP|协议类型，取值：

 -   **TCP**：转发TCP协议的报文。
-   **UDP**：转发UDP协议的报文。
-   **Any**：转发所有协议的报文。 |
|ForwardEntryName|String|否|ForwardEntry-1|DNAT条目的名称。

 长度为2~128个字符，必须以字母或中文开头，但不能以`http://`或`https://`开头。 |
|PageNumber|Integer|否|1|列表的页码，默认值为1。 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为50，默认值为10。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ForwardTableEntries|Array of ForwardTableEntry| |DNAT列表的详细信息。 |
|ForwardTableEntry| | | |
|ExternalIp|String|139.xxx.xx.79|DNAT条目中提供公网访问的公网IP地址。 |
|ExternalPort|String|80|进行端口转发的外部端口。 |
|ForwardEntryId|String|fwd-119smw5tk\*\*\*\*|DNAT条目的ID。 |
|ForwardEntryName|String|ForwardEntry-1|DNAT条目的名称。 |
|ForwardTableId|String|ftb-11tc6xgmv\*\*\*\*|DNAT条目所属DNAT表的ID。 |
|InternalIp|String|192.168.1.xx|通过DNAT条目进行公网通信的ECS实例的私网IP地址。 |
|InternalPort|String|25|进行端口转发的内部端口。 |
|IpProtocol|String|TCP|协议类型：

 -   **TCP**：转发TCP协议的报文。
-   **UDP**：转发UDP协议的报文。
-   **Any**：转发所有协议的报文。 |
|Status|String|Available|DNAT条目的状态：

 -   **Pending**：配置中，可能是创建中和修改中。
-   **Available**：可用。
-   **Deleting**：删除中。 |
|TotalCount|Integer|5|列表条目数。 |
|PageNumber|Integer|1|当前页码。 |
|PageSize|Integer|10|每页包含的条目数。 |
|RequestId|String|A6C4A8B1-7561-4509-949C-20DEB40D71E6|请求ID。 |

## 示例

请求示例

```
https://vpc.aliyuncs.com/?Action=DescribeForwardTableEntries
&ForwardTableId=ftb-bp1mbjubq34hlcqpa****
&RegionId=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML` 格式

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

`JSON` 格式

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

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|
|400|IncorretForwardEntryStatus|Some Forward entry status blocked this operation..|无法执行该操作。DNAT表中有DNAT条目的状态处于Pending或Modifying状态。|
|404|InvalidForwardTableId.NotFound|Specified forwardTableId does not exist|指定的 DNAT 表不存在，请您检查输入参数是否正确。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

