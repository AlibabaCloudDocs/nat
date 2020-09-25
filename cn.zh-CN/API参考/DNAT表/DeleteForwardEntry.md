# DeleteForwardEntry

调用DeleteForwardEntry接口删除指定的DNAT条目。

## API描述

DeleteForwardEntry接口属于异步接口，即系统会先返回一个请求ID，但DNAT条目并未删除完成，系统后台的删除任务仍在进行。您可以调用[DescribeNatGateways](~~36054~~)查询DNAT条目的状态：

-   当DNAT条目处于**Deleting**状态时，表示DNAT条目正在删除中，在该状态下，您只能执行查询操作，不能执行其他操作。
-   当返回的DNAT条目列表为空时，表示DNAT条目删除完成。

**说明：** 如果DNAT表中有DNAT条目的状态为**Pending**时，无法删除该DNAT表中的DNAT条目。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DeleteForwardEntry&type=RPC&version=2016-04-28)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteForwardEntry|要执行的操作，取值：**DeleteForwardEntry**。 |
|ForwardEntryId|String|是|fwd-8vbn3bc8roygjp0gy\*\*\*\*|要删除的DNAT条目ID。 |
|ForwardTableId|String|是|ftb-8vbx8xu2lqj9qb334\*\*\*\*|DNAT条目所属的DNAT列表ID。 |
|RegionId|String|是|cn-hangzhou|NAT网关所在的地域。您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|0ED8D006-F706-4D23-88ED-E11ED28DCAC0|请求ID。 |

## 示例

请求示例

```
https://vpc.aliyuncs.com/?Action=DeleteForwardEntry
&ForwardEntryId=fwd-8vbn3bc8roygjp0gy****
&ForwardTableId=ftb-8vbx8xu2lqj9qb334****
&RegionId=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DeleteForwardEntryResponse>
      <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
</DeleteForwardEntryResponse>
```

`JSON` 格式

```
{ 
    "RequestId": "0ED8D006-F706-4D23-88ED-E11ED28DCAC0"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|
|400|IncorretForwardEntryStatus|Some Forward entry status blocked this operation..|无法执行该操作。DNAT表中有DNAT条目的状态处于Pending或Modifying状态。|
|404|InvalidForwardEntryId.NotFound|Specified forward entry ID does not exist|该DNAT条目不存在。|
|404|InvalidForwardTableId.NotFound|Specified forward table does not exist.|指定的 DNAT 表不存在，请您检查输入参数是否正确。|
|400|IncorretForwardEntryStatus|The Specified forwardEntry is not exist|该DNAT条目不存在。|
|400|MissingParameter|Missing mandatory parameter|缺少必要参数，请您检查必填参数是否都已填后再进行操作。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

