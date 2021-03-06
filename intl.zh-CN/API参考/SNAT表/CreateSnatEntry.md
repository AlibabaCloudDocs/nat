# CreateSnatEntry

调用CreateSnatEntry接口在SNAT列表中添加SNAT条目。

## API描述

调用本接口添加SNAT条目时，请注意：

-   CreateSnatEntry接口属于异步接口，即系统会先返回一个SNAT条目ID，但该SNAT条目并未添加完成，系统后台的添加任务仍在进行。您可以调用[DescribeSnatTableEntries](~~42677~~)查询SNAT条目的状态：
    -   当SNAT条目处于**Pending**状态时，表示SNAT条目正在添加中，在该状态下，您只能执行查询操作，不能执行其他操作。
    -   当SNAT条目处于**Available**状态时，表示SNAT条目添加完成。
-   SNAT条目中指定的交换机和ECS实例必须在NAT网关所属的VPC内。
-   每个交换机和ECS实例只能属于一个SNAT条目。
-   如果交换机中存在HAVIP实例，则无法添加SNAT条目。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=CreateSnatEntry&type=RPC&version=2016-04-28)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateSnatEntry|要执行的操作，取值：**CreateSnatEntry**。 |
|RegionId|String|是|cn-hangzhou|NAT网关所在的地域ID。 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。 |
|SnatIp|String|是|47.XX.XX.98|公网IP地址，多个IP之间用半角逗号（,）隔开。

 **说明：** 指定多个公网IP配置SNAT IP地址池时，需确保每个公网IP都加入到同一个共享带宽中。 |
|SnatTableId|String|是|stb-bp190wu8io1vgev\*\*\*\*|SNAT表ID。 |
|SourceVSwitchId|String|否|vsw-bp1nhx2s9ui5o\*\*\*\*|需要公网访问的交换机的ID。 |
|SourceCIDR|String|否|10.1.1.0/24|交换机或ECS实例的网段。

 -   交换机粒度：指定交换机的网段（如192.168.1.0/24），当交换机下的ECS实例发起互联网访问请求时，NAT网关会为其提供SNAT服务（代理上网服务）。
    -   如果**SnatIp**仅指定了一个公网IP，ECS实例使用指定的公网IP访问互联网。
    -   如果**SnatIp**指定了多个公网IP，ECS实例随机使用**SnatIp**中的公网IP访问互联网。
-   ECS粒度：指定ECS实例的地址（如192.168.1.1/32），当ECS实例发起互联网访问请求时，NAT网关会为其提供SNAT服务（代理上网服务）。
    -   如果**SnatIp**仅指定了一个公网IP，ECS实例使用指定的公网IP访问互联网。
    -   如果**SnatIp**指定了多个公网IP，ECS实例随机使用**SnatIp**中的公网IP访问互联网。

 此参数和**SourceVSwtichId**参数互斥，不能同时出现。如果指定了**SourceVSwitchId**，则不能指定**SourceCIDR**参数。如果指定了**SourceCIDR**参数，则不能指定**SourceVSwitchId**参数。 |
|SnatEntryName|String|否|SnatEntry-1|SNAT条目的名称。

 长度为2~128个字符，必须以大小写字母或中文开头，但不能以`http://`或`https://`开头。 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44\*\*\*\*|保证请求幂等性。从您的客户端生成一个参数值，确保不同请求间该参数值唯一。**ClientToken**只支持ASCII字符，且不能超过64个字符。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|SnatEntryId|String|snat-kmd6nv8fy\*\*\*\*|SNAT条目ID。 |
|RequestId|String|2315DEB7-5E92-423A-91F7-4C1EC9AD97C3|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=CreateSnatEntry
&RegionId=cn-hangzhou
&SnatIp=47.XX.XX.98
&SnatTableId=stb-bp190wu8io1vgev****
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<CreateSnatEntryResponse>
      <RequestId>2315DEB7-5E92-423A-91F7-4C1EC9AD97C3</RequestId>
      <SnatEntryId>snat-119smw5tkx****</SnatEntryId>
</CreateSnatEntryResponse>
```

`JSON`格式

```
{
    "SnatEntryId": "snat-kmd6nv8fyx****",
    "RequestId": "2315DEB7-5E92-423A-91F7-4C1EC9AD97C3"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的regionid不存在。|
|404|InvalidSnatTableId.NotFound|Specified SNAT table does not exist.|指定的 SNAT 表不存在，请您检查输入参数是否正确。|
|400|Forbidden.SourceVSwitchId.IncludeHaVip|There is some HaVips under specified VSwitch|该交换机下有关联的HAVIP。|
|400|InvalidSnatIp.Malformed|The specified SnatIp is not a valid IP address.|该公网IP不合法。|
|400|SNAT\_IP\_POOL\_COUNT\_TOO\_MANY|The Snat pool ip too many.|SNAT IP池的IP达到配额。|
|400|Forbidden.SnatEntryCountLimited|SNAT entry in the specified SNAT table reach it?s limit.|SNAT条目数量已达到配额。|
|400|NOT\_ALLOW\_USE\_SOURCECIDR|The User not in nat\_scope\_unlimited white list. Cannot use SourceCidr param.|内网IP超出VPC网段范围。|
|404|InvalidVSwitchId.NotFound|The specified virtual switch does not exists.|该交换机不存在，请您检查输入的交换机是否正确。|
|400|INVALID\_PARAMETER|The parameter invalid.|参数不合法。|
|400|Forbidden.SourceVSwitchId.Duplicated|The specified SourceCIDRis duplicated.|该交换机已配置了 SNAT 规则，请您不要重复设置。|
|404|InvalidSnatIp.NotFound|Specified SnatIp does not found on the NAT Gateway|该公网IP不在NAT网关中。|
|400|Forbidden.IpUsedInForwardTable|The specified SnatIp already used in forward table|该公网IP已经被DNAT使用，请更换其他公网IP地址或将当前公网IP的DNAT规则删除。|
|400|Forbindden|The specified Instance already bind eip|该实例已经绑定了 EIP，请将 ECS 实例与 EIP 解绑后再添加该端口转发规则。|
|400|OperationUnsupported.CidrConflict|The specified CIDR block conflicts with an existing SNAT entry.|您指定的CIDR的网段与已有的SNAT条目冲突。|
|400|InvalidParameter.Name.Malformed|The specified Name is not valid.|该名称不合法，请您按照正确的格式书写名称。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Vpc)查看更多错误码。

