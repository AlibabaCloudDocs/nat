# CreateNatGateway

调用CreateNatGateway接口创建增强型NAT网关。

## API描述

在调用本接口创建NAT网关时，请注意：

-   首次创建增强型NAT网关时，系统会自动创建一个名称为AliyunServiceRoleForNatgw的服务关联角色，并且为该角色添加名称为AliyunServiceRolePolicyForNatgw的权限策略，授予NAT网关拥有访问其他云资源的权限。更多信息，请参见[服务关联角色](~~174251~~)。
-   CreateNatGateway接口属于异步接口，即系统会先返回一个NAT网关实例ID，但该NAT网关实例并未创建完成，系统后台的创建任务仍在进行。您可以调用[DescribeNatGateways](~~36054~~)查询NAT网关的状态：
    -   当NAT网关处于**Creating**状态时，表示NAT网关正在创建中，在该状态下，您只能执行查询操作，不能执行其他操作。
    -   当NAT网关处于**Available**状态时，表示NAT网关创建完成。

**说明：** NAT网关创建一般需要1~3分钟，请您耐心等待。

-   NAT网关创建后，系统会在VPC的路由表中自动添加一条目标网段为0.0.0.0/0，下一跳为NAT网关的路由条目，用于将流量路由到NAT网关。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=CreateNatGateway&type=RPC&version=2016-04-28)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateNatGateway|要执行的操作，取值：**CreateNatGateway**。 |
|RegionId|String|是|cn-hangzhou|NAT网关所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。 |
|VpcId|String|是|vpc-bp1di7uewzmtvfuq8\*\*\*\*|需要创建NAT网关的VPC的ID。 |
|VSwitchId|String|是|vsw-bp1e3se98n9fq8hle\*\*\*\*|NAT网关所属的交换机的ID。

 创建增强型NAT网关时，您必须指定NAT网关所属的交换机，系统会为增强型NAT网关分配一个交换机内的空闲私网IP地址。

 -   如果您要在存量交换机中创建增强型NAT网关，请确保交换机所属的可用区支持创建增强型NAT网关，且交换机有可用的IP。
-   如果您还未创建交换机，请先在支持创建增强型NAT网关的可用区创建交换机，然后再指定增强型NAT网关所属的交换机。

 您可以通过[ListEnhanhcedNatGatewayAvailableZones](~~182292~~)接口查询增强型NAT网关的资源可用区，通过[DescribeVSwitches](~~35748~~)接口查询交换机中的可用IP数。 |
|NatType|String|是|Enhanced|NAT网关的类型，取值：**Enhanced**，增强型NAT网关。增强型NAT网关详情，请参见[增强型NAT网关发布公告](~~163610~~)。 |
|Name|String|否|fortest|NAT网关的名称。

 名称长度为2~128个字符之间，必须以英文字母或中文开头，不能以`http://`和`https://`开头，可包含数字、点号（.）、下划线（\_）或短划线（-）。

 如果没有指定该参数，默认使用网关ID作为名称。 |
|Description|String|否|testnat|NAT网关的描述。

 描述长度为2~256个字符之间，不能以`http://`和`https://`开头。 |
|ClientToken|String|否|shefffxxddjehfh123|保证请求幂等性。从您的客户端生成一个参数值，确保不同请求间该参数值唯一。**ClientToken**只支持ASCII字符，且不能超过64个字符。 |
|Spec|String|否|Small|NAT网关的规格，取值：

 -   **Small**（默认值）：小型。
-   **Middle**：中型。
-   **Large**：大型。
-   **XLarge.1**：超大型-1。 |
|InstanceChargeType|String|否|PostPaid|NAT网关的付费模式，取值：

 **PostPaid**（默认值）：按量付费。

 **PrePaid**：包年包月。

 包年包月和按量付费的详细信息，请参见[包年包月](~~88657~~)和[按量付费](~~88658~~)。 |
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
|InternetChargeType|String|否|PayBySpec|NAT网关的计费类型，取值：

 -   **PayBySpec**：按固定规格计费。
-   **PayByLcu**：按使用量计费。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|NatGatewayId|String|ngw-112za33e4\*\*\*\*|创建的NAT网关的实例ID。 |
|ForwardTableIds|List|ftb-11tc6xgmv\*\*\*\*|DNAT列表。 |
|RequestId|String|2315DEB7-5E92-423A-91F7-4C1EC9AD97C3|请求ID。 |
|SnatTableIds|List|stb-SnatTableIds\*\*\*\*|SNAT列表。 |

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
      <RequestId>5AF873FB-6669-4AD5-A4DA-478D535C8F0D</RequestId>
      <SnatTableIds>
            <SnatTableId>stb-bp1evej8rk6ww1djl****</SnatTableId>
      </SnatTableIds>
      <ForwardTableIds>
            <ForwardTableId>ftb-bp1d09hosgndxs154****</ForwardTableId>
      </ForwardTableIds>
      <NatGatewayId>ngw-bp1m842e0dz1t5cos****</NatGatewayId>
</CreateNatGatewayResponse>
```

`JSON` 格式

```
{
	"RequestId": "5AF873FB-6669-4AD5-A4DA-478D535C8F0D",
	"SnatTableIds": {
		"SnatTableId": [
			"stb-bp1evej8rk6ww1djl****"
		]
	},
	"ForwardTableIds": {
		"ForwardTableId": [
			"ftb-bp1d09hosgndxs154****"
		]
	},
	"NatGatewayId": "ngw-bp1m842e0dz1t5cos****"
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
|400|OperationFailed.VswNotBelongToVpc|Operation failed because the specified VSwitch is not bound to the same VPC with NAT gateway.|操作失败因为VSW和NATGW不属于同一个VPC。|
|400|OperationFailed.EnhancedUserIsUnAuthorized|Operation failed because the user is not authorized to create an enhanced NAT gateway.|操作失败因为用户未授权创建增强型NAT网关。|
|400|OperationUnsupported.PrePaidPyByLcu|The operation failed because the subscription NAT gateway does not support the pay-by-LCU billing method.|预付费的NAT网关实例不支持PayByLcu的计费方式。|
|400|OperationFailed.NormalInventoryNotEnough|Operation failed because the inventory of standard NAT gateway is insufficient.|操作失败因为普通型NAT网关的库存不足。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

