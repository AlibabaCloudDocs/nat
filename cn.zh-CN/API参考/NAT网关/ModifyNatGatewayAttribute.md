# ModifyNatGatewayAttribute

调用ModifyNatGatewayAttribute接口修改NAT网关的名称和描述。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=ModifyNatGatewayAttribute&type=RPC&version=2016-04-28)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyNatGatewayAttribute|要执行的操作，取值： **ModifyNatGatewayAttribute**。 |
|NatGatewayId|String|是|ngw-2ze0dcn4mq31qx2jc\*\*\*\*|要修改的NAT网关的ID。 |
|RegionId|String|是|cn-hangzhou|NAT网关所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。 |
|Name|String|否|nat123|NAT网关的名称。

 长度为2~128个字符，必须以字母或中文开头，可包含数字、英文句点（.）、下划线（\_）和短划线（-）。但不能以`http://` 或`https://`开头。

 **说明：** **Name**和**Description**参数必须至少传一个。 |
|Description|String|否|fortest|NAT网关的描述信息。

 长度为2~256个字符，必须以字母或中文开头，但不能以`http://`或`https://`开头。

 **说明：** **Name**和**Description**参数必须至少传一个。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|AB5F62CF-2B60-4458-A756-42C9DFE108D1|请求ID。 |

## 示例

请求示例

```
https://vpc.aliyuncs.com/?Action=ModifyNatGatewayAttribute
&NatGatewayId=ngw-2ze0dcn4mq31qx2jc****
&RegionId=cn-hangzhou
&Name=nat123
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<ModifyNatGatewayAttributeResponse>
	  <RequestId>2315DEB7-5E92-423A-91F7-4C1EC9AD97C3</RequestId>
</ModifyNatGatewayAttributeResponse>
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
|404|InvalidNatGatewayId.NotFound|The specified NatGatewayId does not exist in our records.|指定的 NatGatewayId 不存在，请您检查填写的 NatGatewayId 是否正确。|
|400|InvalidParameter.Name.Malformed|The specified Name is not valid.|该名称不合法，请您按照正确的格式书写名称。|
|400|InvalidParameter.Description.Malformed|The specified Description is not valid.|该描述不合法。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

