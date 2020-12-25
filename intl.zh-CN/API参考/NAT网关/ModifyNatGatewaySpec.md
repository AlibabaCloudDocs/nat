# ModifyNatGatewaySpec

使用ModifyNatGatewaySpec接口修改NAT网关的规格。

## API描述

ModifyNatGatewaySpec接口属于异步接口，即系统会先返回一个请求ID，但该NAT网关实例的规格并未变配完成，系统后台的变配任务仍在进行。您可以调用[DescribeNatGateways](~~36054~~)查询NAT网关的状态：

-   当NAT网关处于**Modifying**状态时，表示NAT网关正在变配中，在该状态下，您只能执行查询操作，不能执行其他操作。
-   当NAT网关处于**Available**状态时，表示NAT网关变配完成。

NAT网关提供不同的规格。NAT网关的规格会影响SNAT功能的最大连接数和每秒新建连接数，但不会影响数据吞吐量。NAT网关规格与SNAT性能的关系如下表所示。

|规格

|最大连接数

|每秒新建连接数 |
|----|-------|---------|
|小型

|1万

|1千 |
|中型

|5万

|5千 |
|大型

|20万

|1万 |
|超大型-1

|100万

|5万 |

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=ModifyNatGatewaySpec&type=RPC&version=2016-04-28)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyNatGatewaySpec|要执行的操作。取值：**ModifyNatGatewaySpec**。 |
|NatGatewayId|String|是|ngw-bp1uewa15k4iy5770\*\*\*\*|要修改规格的NAT网关的ID。 |
|RegionId|String|是|cn-hangzhou|NAT网关所属的地域。 |
|Spec|String|是|Small|NAT网关的规格，取值：

 -   **Small**：小型。
-   **Middle**：中型。
-   **Large**：大型。
-   **XLarge.1**：超大型-1。 |
|AutoPay|Boolean|否|false|是否自动付费。

 -   **true**：开启自动付费。
-   **false**（默认值）：不开启自动付费。 |
|ClientToken|String|否|SHA234js121223\*\*\*\*|保证请求幂等性。从您的客户端生成一个参数值，确保不同请求间该参数值唯一。**ClientToken**只支持ASCII字符，且不能超过64个字符。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|DBD4E4A2-786E-4BD2-8EB6-107FFC2B5B7D|请求ID。 |

## 示例

请求示例

```
https://vpc.aliyuncs.com/?Action=ModifyNatGatewaySpec
&NatGatewayId=ngw-bp1uewa15k4iy5770****
&RegionId=cn-hangzhou
&Spec=Small
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<ModifyNatGatewaySpecResponse>
  <RequestId>DBD4E4A2-786E-4BD2-8EB6-107FFC2B5B7D</RequestId>
</ModifyNatGatewaySpecResponse>
```

`JSON` 格式

```
{
    "RequestId": "DBD4E4A2-786E-4BD2-8EB6-107FFC2B5B7D"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|
|404|InvalidNatGatewayId.NotFound|The specified NatGatewayId does not exist in our records.|指定的 NatGatewayId 不存在，请您检查填写的 NatGatewayId 是否正确。|
|400|NATGW\_MODIFY\_SPEC\_SAME|The specified Spec is same with now.|该规格和当前规格一样。|
|400|InvalidParameter.Spec.ValueNotSupported|The specified Spec is not valid.|该规格不合法。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Vpc)查看更多错误码。

