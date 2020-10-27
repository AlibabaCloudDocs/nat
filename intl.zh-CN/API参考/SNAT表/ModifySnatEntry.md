# ModifySnatEntry

调用ModifySnatEntry接口修改指定的SNAT条目。

## API描述

ModifySnatEntry接口属于异步接口，即系统会先返回一个请求ID，但SNAT条目并未修改完成，系统后台的修改任务仍在进行。您可以调用[DescribeNatGateways](~~36054~~)查询SNAT条目的状态：

-   当SNAT条目处于**Pending**状态时，表示SNAT条目正在修改中，在该状态下，您只能执行查询操作，不能执行其他操作。
-   当SNAT条目处于**Available**状态时，表示SNAT条目修改完成。

**说明：** 如果SNAT表中有SNAT条目的状态为**Pending**时，无法修改该SNAT表中的SNAT条目。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=ModifySnatEntry&type=RPC&version=2016-04-28)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifySnatEntry|要执行的操作，取值：**ModifySnatEntry**。 |
|RegionId|String|是|cn-hangzhou|NAT网关所在的地域。您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。 |
|SnatEntryId|String|是|snat-bp1vcgcf8tm0plqcg\*\*\*\*|要修改的SNAT条目的ID。 |
|SnatTableId|String|是|stb-8vbczigrhop8x5u3t\*\*\*\*|SNAT条目所在的SNAT表的ID。 |
|SnatIp|String|否|47.xx.xx.98|SNAT条目中的公网IP地址。多个IP之间用逗号（,）隔开。

 **说明：** 指定多个公网IP配置SNAT IP地址池时，需确保每个公网IP都加入到同一个共享带宽中。 |
|SnatEntryName|String|否|SnatEntry-1|SNAT条目的名称。

 长度为2~128个字符，必须以字母或中文开头，但不能以`http://`或`https://`开头。 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44-001\*\*\*\*|保证请求幂等性。从您的客户端生成一个参数值，确保不同请求间该参数值唯一。ClientToken只支持ASCII字符，且不能超过64个字符。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|2315DEB7-5E92-423A-91F7-4C1EC9AD97C3|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ModifySnatEntry
&RegionId=cn-hangzhou
&SnatEntryId=snat-bp1vcgcf8tm0plqcg****
&SnatTableId=stb-8vbczigrhop8x5u3t****
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<ModifySnatEntryResponse>
	  <RequestId>2315DEB7-5E92-423A-91F7-4C1EC9AD97C3</RequestId>
</ModifySnatEntryResponse>
```

`JSON` 格式

```
{
  "RequestId": "2315DEB7-5E92-423A-91F7-4C1EC9AD97C3"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|
|404|InvalidSnatTableId.NotFound|Specified SNAT table does not exist.|指定的 SNAT 表不存在，请您检查输入参数是否正确。|
|400|InvalidSnatIp.Malformed|The specified SnatIp is not a valid IP address.|该公网IP不合法。|
|404|InvalidSnatEntryId.NotFound|Specified SNAT entry does not exist.|指定的 SNAT 条目不存在，请您检查填写的 SNAT 条目是否正确。|
|400|Forbidden.SourceVSwitchId.Duplicated|The specified SourceCIDRis duplicated.|该交换机已配置了 SNAT 规则，请您不要重复设置。|
|404|InvalidSnatIp.NotFound|Specified SnatIp does not found on the NAT Gateway|该公网IP不在NAT网关中。|
|400|Forbidden.IpUsedInForwardTable|The specified SnatIp already used in forward table|该公网IP已经被DNAT使用，请更换其他公网IP地址或将当前公网IP的DNAT规则删除。|
|400|InvalidParameter.Name.Malformed|The specified Name is not valid.|该名称不合法，请您按照正确的格式书写名称。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Vpc)查看更多错误码。

