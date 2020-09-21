# CreateNatGateway

调用CreateNatGateway接口创建一个NAT网关。

## API描述

在调用本接口创建NAT网关时，请注意：

-   创建普通型NAT网关前，如果VPC的路由表中已经存在一条目标网段为0.0.0.0/0的路由条目，则不支持为该VPC创建NAT网关。如需创建，请先删除该路由条目。如果您创建的是增强型NAT网关，则无此限制。
-   不支持NAT网关与自建SNAT网关（使用一台ECS作为SNAT网关）在VPC中并存。
-   NAT网关创建后，系统会在VPC的路由表中自动添加一条目标网段为0.0.0.0/0，下一跳为NAT网关的路由条目，用于将流量路由到NAT网关。
-   首次创建增强型NAT网关时，系统会自动创建一个名称为AliyunServiceRoleForNatgw的服务关联角色，并且为该角色添加名称为AliyunServiceRolePolicyForNatgw的权限策略，授予NAT网关拥有访问其他云资源的权限。详细信息，请参见[服务关联角色](~~174251~~)。

**说明：** 如果您要创建的NAT网关类型为普通型NAT网关，系统不会自动创建名称为AliyunServiceRoleForNatgw的服务关联角色，也能成功创建NAT网关。


## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=CreateNatGateway&type=RPC&version=2016-04-28)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateNatGateway|要执行的操作，取值：**CreateNatGateway**。 |
|RegionId|String|是|cn-hangzhou|NAT网关所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。 |
|VpcId|String|是|vpc-bp1di7uewzmtvfuq8\*\*\*\*|需要创建NAT网关的VPC的ID。 |
|Name|String|否|fortest|NAT网关的名称。

 名称在2~128个字符之间，必须以英文字母或中文开头，不能以`http://`和`https://`开头，可包含数字、点号（.）、下划线（\_）或短横线（-）。

 如果没有指定该参数，默认使用网关ID作为名称。 |
|Description|String|否|testnat|NAT网关的描述。

 描述在2~256个字符之间，不能以`http://`和`https://`开头。 |
|ClientToken|String|否|shefffxxddjehfh123|保证请求幂等性。从您的客户端生成一个参数值，确保不同请求间该参数值唯一。**ClientToken**只支持ASCII字符，且不能超过64个字符。 |
|Spec|String|否|Small|NAT网关的规格，取值：

 -   **Small**（默认值）：小型。
-   **Middle**：中型。
-   **Large**：大型。
-   **XLarge.1**：超大型。 |
|BandwidthPackage.N.IpCount|Integer|否|5|NAT带宽包中的公网IP数量，取值范围：1~50。

 N是第几个NAT带宽包，取值范围：1~4。

 本参数仅支持在2017年11月3日之前账号下存在NAT带宽包的用户指定。2017年11月3日之前账号下不存在NAT带宽包的用户，请绑定EIP。 |
|BandwidthPackage.N.Bandwidth|Integer|否|5|第N个NAT带宽包的带宽值，取值范围：5~5000。

 本参数仅支持在2017年11月3日之前账号下存在NAT带宽包的用户指定。2017年11月3日之前账号下不存在NAT带宽包的用户，请绑定EIP。 |
|BandwidthPackage.N.Zone|String|否|cn-hangzhou-b|第N个NAT带宽包的可用区。不指定该参数时，系统将随机分配一个可用区。

 NAT带宽包的IP与后端ECS不处于同一个可用区，并不影响其连通性；但是位于相同可用区时，可减小延迟。

 本参数仅支持在2017年11月3日之前账号下存在NAT带宽包的用户指定。2017年11月3日之前账号下不存在NAT带宽包的用户，请绑定EIP。 |
|BandwidthPackage.N.ISP|String|否|BGP|第N个NAT带宽包中的线路ISP类型，默认为BGP（多线）。

 本参数仅支持在2017年11月3日之前账号下存在NAT带宽包的用户指定。2017年11月3日之前账号下不存在NAT带宽包的用户，请绑定EIP。 |
|InstanceChargeType|String|否|PostPaid|计费方式，取值：

 **PrePaid**：包年包月。

 **PostPaid**（默认值）：按量计费。

 包年包月和按量计费的详细信息，请参见[包年包月](~~88657~~)和[按量计费](~~88658~~)。 |
|PricingCycle|String|否|Month|包年包月的计费周期，取值：

 **Month**（默认值）：按月付费。

 **Year**：按年付费。

 当**InstanceChargeType**参数的值为**PrePaid**时，该参数必选；当**InstanceChargeType**参数的值为**PostPaid**时，该参数可不填。 |
|Duration|String|否|1|购买时长。

 当**PricingCycle**取值**Month**时，**Period**取值范围为**1~9**。

 当**PricingCycle**取值**Year**时，**Period**取值范围为**1~3**。

 如果**InstanceChargeType**参数的值为**PrePaid**时，该参数必选。 |
|AutoPay|Boolean|否|false|是否自动付费，取值：

 **false**：不开启自动付费，生成订单后需要到订单中心完成支付。

 **true**：开启自动付费，自动支付订单。

 当**InstanceChargeType**参数的值为**PrePaid**时，该参数必选；当**InstanceChargeType**参数的值为**PostPaid**时，该参数不填。 |
|VSwitchId|String|否|vsw-bp1e3se98n9fq8hle\*\*\*\*|NAT网关所属的交换机的ID。

 仅**NatType**取值为**Enhanced**时，才支持配置此参数。 |
|NatType|String|否|Normal|NAT网关的类型，取值：

 -   **Normal**：普通型NAT网关。
-   **Enhanced**：增强型NAT网关。增强型NAT网关详情，请参见[增强型NAT网关发布公告](~~163610~~)。

 **说明：** 目前，在华北3（张家口）、华北5（呼和浩特）、西南1（成都）、华南2（河源）、英国（伦敦）、德国（法兰克福）、马来西亚（吉隆坡）和印度（孟买）地域创建NAT网关，NAT网关类型默认为**Enhanced**。 |
|InternetChargeType|String|否|PayBySpec|NAT网关的计量方式，取值：**PayBySpec**（按固定规格计费）。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|NatGatewayId|String|ngw-112za33e4\*\*\*\*|创建的NAT网关的实例ID。 |
|ForwardTableIds|List|ftb-11tc6xgmv\*\*\*\*|转发条目列表。 |
|BandwidthPackageIds|List|bwp-11odxu2k7\*\*\*\*|NAT带宽包列表。 |
|RequestId|String|2315DEB7-5E92-423A-91F7-4C1EC9AD97C3|请求ID。 |
|SnatTableIds|List|stb-SnatTableIds\*\*\*\*|SNAT表的ID。 |

## 示例

请求示例

```
https://vpc.aliyuncs.com/?Action=CreateNatGateway
&RegionId=cn-hangzhou
&VpcId= vpc-bp1di7uewzmtvfuq8****
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<CreateNatGatewayResponse>
    <BandwidthPackageIds>
  </BandwidthPackageIds>
    <RequestId>7C01CA72-73FD-4056-B16A-42E392D47625</RequestId>
    <SnatTableIds>
          <SnatTableId>stb-wz9aq9mec6f843j45****</SnatTableId>
    </SnatTableIds>
    <ForwardTableIds>
          <ForwardTableId>ftb-wz9sl3znmxhy605f8****</ForwardTableId>
    </ForwardTableIds>
    <NatGatewayId>ngw-wz95lh0c2wj9b6r1z****</NatGatewayId>
</CreateNatGatewayResponse>
```

`JSON` 格式

```
{
	"BandwidthPackageIds": {
		"BandwidthPackageId": []
	},
	"RequestId": "7C01CA72-73FD-4056-B16A-42E392D47625",
	"SnatTableIds": {
		"SnatTableId": [
			"stb-wz9aq9mec6f843j45****"
		]
	},
	"ForwardTableIds": {
		"ForwardTableId": [
			"ftb-wz9sl3znmxhy605f8****"
		]
	},
	"NatGatewayId": "ngw-wz95lh0c2wj9b6r1z****"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidVPCStatus|vpc incorrect status.|该 VPC 状态非法，请您检查 VPC 状态是否输入正确。|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|
|400|InvalidNatGatewayName.MalFormed|NatGateway name is not valid.|网关名称不合法。|
|400|InvalidNatGatewayDescription.MalFormed|NatGateway description is not valid.|网关描述不合法。|
|400|MissingParameter.BandwidthPackage|only support one BandwidthPackage be created with NatGateway.|必须指定一个共享带宽包。|
|404|InvalidVpcId.NotFound|Specified value of VpcId is not found in our record.|该 VPC 不存在，请您检查输入的 VPC 是否正确。|
|400|MissingParameter|Miss mandatory parameter.|缺少必要参数，请您检查必填参数是否都已填后再进行操作。|
|404|InvalidZoneId.NotFound|Specified value of ZoneId is not exists.|该可用区不存在。|
|404|InvalidZoneId.NotFound|Can not find ZoneId for allocated ip.|该IP的可用区不正确。|
|400|QuotaExceeded.BandwidthPackageIps|The specified ipCount exceeded quota.|IP 数量超过上限，可以提交工单申请增加配额。|
|400|InvalidParameter.Name.Malformed|The specified Name is not valid.|该名称不合法，请您按照正确的格式书写名称。|
|400|InvalidParameter.Description.Malformed|The specified Description is not valid.|该描述不合法。|
|400|ZONE\_NO\_AVAILABLE\_IP|The Zone have no available ip.|该可用区没有可用IP。|
|400|InvalidParameter.BandwidthPackage.n.ISP.ValueNotSupport|The specified ISP of BandwidthPackage is not valid.|该共享带宽包的ISP不合法。|
|400|InvalidNatGatewayId.NotFound|The NatGatewayId not exist.|指定的 NatGatewayId 不存在，请您检查填写的 NatGatewayId 是否正确。|
|400|VswitchStatusError|The VSwitch is creating .|交换机正在创建中。|
|400|VpcStatusError|The Vpc is creating .|正在创建VPC。|
|400|InvalidParameter.Spec.ValueNotSupported|The specified Spec is not valid.|该规格不合法。|
|400|Forbidden.CheckEntryRuleQuota|Route entry quota rule check error.|检查路由条目配额时发生了错误。|
|400|NoPermission.CreateServiceLinkedRole|You are not authorized to create service linked role|你没有权限创建SLR|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

