# CreateForwardEntry

使用CreateForwardEntry在DNAT列表中添加DNAT条目。

## API描述

每条DNAT条目由五部分组成，包括**ExternalIp**、**ExternalPort**、**protocol**、**InternalIp**和**InternalPort**。添加DNAT条目后，NAT网关会将**ExternalIp:ExternalPort**上收到的指定协议的报文转发给**InternalIp:InternalPort**，并将回复消息原路返回。

调用本接口添加DNAT条目时，请注意：

-   CreateForwardEntry接口属于异步接口，即系统会先返回一个DNAT条目ID，但该DNAT条目并未添加完成，系统后台的添加任务仍在进行。您可以调用[DescribeForwardTableEntries](~~36053~~)查询DNAT条目的状态：
    -   当DNAT条目处于**Pending**状态时，表示DNAT条目正在添加中，在该状态下，您只能执行查询操作，不能执行其他操作。
    -   当DNAT条目处于**Available**状态时，表示DNAT条目添加完成。
-   所有DNAT条目的**ExternalIp**、**ExternalPort**和**Protocol**三个字段组成的组合必须互不重复，即不允许将同一个源IP、同一个端口、同一个协议的消息转发到多个目标ECS实例。
-   所有DNAT条目的**Protocol**、**InternalIp**和**InternalPort**三个字段组成的组合也必须互不重复。
-   当DNAT表中有DNAT条目的状态处于**Pending**或**Modifying**状态时，无法添加DNAT条目。
-   一个DNAT表最多可添加100条DNAT条目。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=CreateForwardEntry&type=RPC&version=2016-04-28)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateForwardEntry|要执行的操作，取值：**CreateForwardEntry**。 |
|ExternalIp|String|是|116.XX.XX.28|提供公网访问的公网IP地址，该公网IP需满足以下条件：

 -   对于2017年11月03日之前账户下存在NAT带宽包的用户，**ExternalIp**必须是该NAT网关的NAT带宽包中的公网IP地址。
-   对于2017年11月03日之前账户下不存在NAT带宽包的用户，**ExternalIp**必须是绑定了该NAT网关的弹性公网IP。 |
|ExternalPort|String|是|8080|需要进行端口转发的外部端口，取值范围：**1**~**65535**。 |
|ForwardTableId|String|是|ftb-bp1mbjubq34hlcqpa\*\*\*\*|DNAT列表的ID。 |
|InternalIp|String|是|192.XX.XX.1|需要进行公网通信的ECS实例的私网IP地址，该私网IP地址需满足以下条件：

 -   必须属于NAT网关所在的VPC的网段。
-   必须被一个ECS实例使用且该实例没有绑定EIP时，DNAT条目才生效。如果该**InternalIp**被HAVIP、SLB或RDS等非ECS资源使用，DNAT条目无效，公网流量无法转发到该IP上。 |
|InternalPort|String|是|80|需要进行端口转发的内部端口，取值范围：**1**~**65535**。 |
|IpProtocol|String|是|TCP|协议类型，取值：

 -   **TCP**：转发TCP协议的报文。
-   **UDP**：转发UDP协议的报文。
-   **Any**：转发所有协议的报文。 |
|RegionId|String|是|cn-hangzhou|NAT网关所在的地域ID。您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。 |
|ForwardEntryName|String|否|ForwardEntry-1|DNAT规则的名称。

 长度为2~128个字符，必须以大小写字母或中文开头，但不能以`http://`或`https://`开头。 |
|ClientToken|String|否|0c593ea1-3bea-11e9-b96b-88e9fe6\*\*\*\*|保证请求幂等性。从您的客户端生成一个参数值，确保不同请求间该参数值唯一。**ClientToken**只支持ASCII字符，且不能超过64个字符。 |
|PortBreak|Boolean|否|false|是否开启端口突破，取值：

 -   **true**：开启端口突破。
-   **false**（默认值）：不开启端口突破。

 **说明：** 当DNAT条目和SNAT条目使用同一个公网IP地址时，如果您想配置大于1024的端口号，您需要指定**PortBreak**为**true**。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ForwardEntryId|String|fwd-119smw5tkasdf\*\*\*\*|DNAT条目的ID。 |
|RequestId|String|A4AEE536-A97A-40EB-9EBE-53A6948A6928|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=CreateForwardEntry
&ExternalIp=116.XX.XX.28
&ExternalPort=8080
&ForwardTableId=ftb-bp1mbjubq34hlcqpa****
&InternalIp=192.XX.XX.1
&InternalPort=80
&IpProtocol=TCP
&RegionId=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<CreateForwardEntryResponse>
  <RequestId>A4AEE536-A97A-40EB-9EBE-53A6948A6928</RequestId>
  <ForwardEntryId>fwd-119smw5tkasdf****</ForwardEntryId>
</CreateForwardEntryResponse>
```

`JSON`格式

```
{
    "RequestId": "A4AEE536-A97A-40EB-9EBE-53A6948A6928",
    "ForwardEntryId": "fwd-119smw5tkasdf****"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的regionid不存在。|
|400|InvalidExternalIp.Malformed|The specified ExternalIp is not a valid IP address.|该公网IP不合法。|
|400|InvalidInternalIp.Malformed|The specified InternalIp is not a valid IP address.|该目标私网IP不合法。|
|400|InvalidExternalPort.Malformed|The specified ExternalPort is not a valid port.|该公网端口不合法。|
|400|InvalidInternalPort.Malformed|The specified InternalPort is not a valid port.|该私网端口不合法。|
|400|Forbidden.DestnationIpOutOfVpcCIDR|The specified Internal Ip is Out of VPC CIDR.|该私网IP不在VPC的网段范围内，请您填写在VPC的网段范围内的私网IP。|
|400|InvalidProtocal.ValueNotSupported|The specified IpProtocol does not support.|该协议类型不支持。|
|400|IncorretForwardEntryStatus|Some Forward entry status blocked this operation..|无法执行该操作。DNAT表中有DNAT条目的状态处于Pending或Modifying状态。|
|404|InvalidForwardTableId.NotFound|Specified forward table does not exist.|指定的 DNAT 表不存在，请您检查输入参数是否正确。|
|404|InvalidExternalIp.NotFound|Specified External Ip address does not found on the VRouter|该公网IP不存在。|
|400|Forbidden.ExternalIp.UsedInSnatTable|The specified ExternalIp is already used in SnatTable|该公网IP已经被SNAT使用，请更换其他公网IP或将当前公网IP的SNAT规则删除。|
|400|Forbindden|The specified Instance already bind eip|该实例已经绑定了 EIP，请将 ECS 实例与 EIP 解绑后再添加该端口转发规则。|
|400|Forbidden.InternalIpOutOfVpcCIDR|The specified Internal Ip is Out of VPC CIDR.|该私网IP不在VPC的网段范围内。|
|400|Invalid.natgwNotExist|The specified natgateway not exist.|该NAT网关不存在。|
|400|InvalidIp.NotInNatgw|The specified Ip not belong to natgateway.|该 IP 地址不属于该 NAT 网关。|
|400|MissingParameter|Missing mandatory parameter|缺少必要参数，请您检查必填参数是否都已填后再进行操作。|
|500|InternalError|The request processing has failed due to some unknown error.|请求处理由于某些未知错误失败。|
|400|InvalidParameter.Name.Malformed|The specified Name is not valid.|该名称不合法，请您按照正确的格式书写名称。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Vpc)查看更多错误码。

