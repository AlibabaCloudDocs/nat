# UpdateNatGatewayNatType

调用UpdateNatGatewayNatType接口将普通型NAT网关升级为增强型NAT网关。

## API描述

调用UpdateNatGatewayNatType接口前，请先了解：

-   UpdateNatGatewayNatType接口属于异步接口，即系统会先返回一个请求ID，但NAT网关的网关类型并未升级完成，系统后台的升级任务仍在进行。您可以调用GetNatGatewayConvertStatus查询NAT网关的升级状态，更多信息，请参见[GetNatGatewayConvertStatus](~~184744~~)。
    -   当NAT网关的升级状态处于**processing**时，表示正在升级中，在该状态下，您只能执行查询操作，不能执行其他操作。
    -   当NAT网关的升级状态处于**successful**时，表示NAT网关的网关类型升级完成。
    -   当NAT网关的升级状态处于**failed**时，表示NAT网关的网关类型升级失败。
-   增强型NAT网关与普通型NAT网关的计费相同，升级过程和升级后不会产生新的计费。
-   每个资源升级过程可能会持续5分钟，升级过程中会出现1~2次秒级闪断，业务重连即可恢复。
-   仅支持将普通型NAT网关升级至增强型NAT网关，不支持将增强型NAT网关降级至普通型NAT网关。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=UpdateNatGatewayNatType&type=RPC&version=2016-04-28)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateNatGatewayNatType|要执行的操作，取值：**UpdateNatGatewayNatType**。 |
|NatGatewayId|String|是|ngw-bp1b0lic8uz4r6vf2\*\*\*\*|要升级网关类型的NAT网关实例ID。 |
|NatType|String|是|Enhanced|NAT网关类型，仅可取值：**Enhanced**（增强型NAT网关）。 |
|RegionId|String|是|cn-qingdao|要升级的NAT网关所属的地域ID。 |
|VSwitchId|String|是|vsw-bp17nszybg8epodke\*\*\*\*|增强型NAT网关所属的交换机。

 **说明：** 如果不传该参数，系统会随机将增强型NAT网关创建在VPC内的任意一台交换机。 |
|DryRun|Boolean|否|false|是否只预检此次请求，取值：

 **true**：发送请求，不会升级NAT网关类型。检查项包括AccessKey是否有效、RAM用户的授权情况和是否填写了必需参数。如果检查不通过，则返回对应错误。如果检查通过，会返回错误码`DryRunOperation`。

 **false**（默认值）：发送正常请求，通过检查后返回2XX HTTP状态码并直接升级NAT网关类型。 |
|ClientToken|String|否|0c593ea1-3bea-11e9-b96b-88e9fe637760|保证请求幂等性。从您的客户端生成一个参数值，确保不同请求间该参数值唯一。**ClientToken**只支持ASCII字符，且不能超过64个字符。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|0ED8D006-F706-4D23-88ED-E11ED28DCAC0|请求ID。 |

## 示例

请求示例

```
http(s)://vpc.aliyuncs.com/?Action=UpdateNatGatewayNatType
&NatGatewayId=ngw-bp1b0lic8uz4r6vf2****
&NatType=Enhanced
&RegionId=cn-qingdao
&VSwitchId=vsw-bp17nszybg8epodke****
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<UpdateNatGatewayNatTypeResponse>    
      <RequestId>7C01CA72-73FD-4056-B16A-42E392D47625</RequestId>
</UpdateNatGatewayNatTypeResponse>
```

`JSON` 格式

```
{
	"RequestId": "7C01CA72-73FD-4056-B16A-42E392D47625"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|
|400|OperationUnsupported.NatConvert|The NAT gateway conversion function is not supported.|NAT网关类型转换功能未支持。|
|400|NATGW\_NOT\_EXIST|The specified NAT gateway does not exist.|该 NAT 网关不存在。|
|400|OperationFailed.VpcNotExist|The specified VPC does not exist.|指定的VPC不存在。|
|400|OperationFailed.VswNotExist|The specified VSwitch does not exist.|指定的交换机不存在。|
|400|OperationFailed.NatTypeNotEnhanced|Operation failed because the specified NAT gateway type is not enhanced.|操作失败因为指定的NAT网关类型不是增强型。|
|400|OperationFailed.NatGwBindWithBandwidthPackage|Operation failed because the NAT gateway is bound to bandwidth packages.|操作失败因为NAT网关实例绑定了NAT带宽包。|
|400|IncorrectStatus.NatGateway|The status of NAT gateway is incorrect.|NAT网关状态不对。|
|400|OperationFailed.EipInMiddleStatus|Operation failed because the status of EIP associated with the specified NAT gateway is abnormal.|操作失败因为绑定在此NAT网关上的EIP状态异常。|
|400|OperationFailed.SnatInMiddleStatus|Operation failed because the status of the SNAT entry of the specified NAT gateway is abnormal.|操作失败因为指定的NAT网关的SNAT条目状态异常。|
|400|OperationFailed.DnatInMiddleStatus|Operation failed because the status of the DNAT entry associated with the NAT gateway is abnormal.|操作失败因为NAT网关的DNAT规则状态异常。|
|400|OperationFailed.NatGwRouteInMiddleStatus|Operation failed because the status of the route entry associated with the NAT gateway is abnormal.|操作失败因为NAT网关相关的路由条目状态异常。|
|400|OperationFailed.EnhancedInventoryNotEnough|The enhanced NAT gateway inventory is insufficient in the specified zone.|当前可用区增强NAT网关库存不足.|
|400|OperationFailed.EnhancedUserIsUnAuthorized|Operation failed because the user is not authorized to create an enhanced NAT gateway.|操作失败因为用户未授权创建增强型NAT网关。|
|400|OperationFailed.EnhancedRegion|Operation failed because enhanced NAT gateways are not available for sale in the specified region.|操作失败因为当前地域未开启增强型NAT网关售卖。|
|400|OperationFailed.EnhancedQuotaExceed|Operation failed because the maximum number of enhanced NAT gateways in the same VPC is exceeded.|操作失败因为当前VPC下的增强型NAT网关数量超过限制。|
|400|InvalidBandwidthPackageIdNumber.NotSupported|The number of BandwidthPackageIds exceeds the limit.|共享带宽包的数量超过Quota限制。|
|400|OperationFailed.VswNotBelongToVpc|Operation failed because the specified VSwitch is not bound to the same VPC with NAT gateway.|操作失败因为VSW和NATGW不属于同一个VPC。|
|400|OperationUnsupported.VpcAttachedCen|Operation failed because the VPC is attached to CEN.|操作失败因为VPC加入了CEN。|
|400|OperationUnsupported.RouterInterfaceExist|Operation failed because the VPC has a router interface.|操作失败因为VPC有路由器接口存在。|
|400|OperationFailed.VRouterNotExist|Operation failed because the VRouter does not exist.|操作失败因为虚拟路由器不存在。|
|400|OperationFailed.SnatQuotaExceed|Operation failed because the maximum number of SNAT entry is exceeded.|操作失败因为SNAT条目数量过多。|
|400|OperationFailed.DnatQuotaExceed|Operation failed because the maximum number of forward entry is exceeded.|操作失败因为DNAT条目数量过多。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Vpc)查看更多错误码。

