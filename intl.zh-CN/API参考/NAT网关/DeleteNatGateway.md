# DeleteNatGateway

调用DeleteNatGateway接口删除指定的NAT网关。

## API描述

DeleteNatGateway接口属于异步接口，即系统会先返回一个请求ID，但该NAT网关实例并未删除完成，系统后台的删除任务仍在进行。您可以调用[DescribeNatGateways](~~36054~~)查询NAT网关的状态：

-   当NAT网关处于**Deleting**状态时，表示NAT网关正在删除中，在该状态下，您只能执行查询操作，不能执行其他操作。
-   当返回的实例列表为空时，表示NAT网关删除完成。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=DeleteNatGateway&type=RPC&version=2016-04-28)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteNatGateway|要执行的操作，取值：**DeleteNatGateway**。 |
|NatGatewayId|String|是|ngw-bp1uewa15k4iy5770\*\*\*\*|要删除的NAT网关的ID。 |
|RegionId|String|是|cn-hangzhou|NAT网关所在的地域ID。您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。 |
|Force|Boolean|否|false|是否强制删除NAT网关，取值：

 -   **true**：强制删除。当取值为**true**时，说明如下：
    -   如果NAT网关有SNAT规则，系统会自动帮您删除SNAT规则。
    -   如果NAT网关有DNAT规则，系统会自动帮您删除DNAT规则。
    -   如果NAT网关有绑定EIP，系统会自动帮您解绑。
    -   如果您有添加下一跳是NAT网关的路由，系统会自动帮您删除该路由。
    -   如果NAT网关有未删除的NAT带宽包，系统会自动帮您删除NAT带宽包。
-   **false**：不强制删除。当取值为**false**时，说明如下：
    -   如果NAT网关有未删除的NAT带宽包，请先删除NAT带宽包。
    -   如果NAT网关有SNAT规则，请先删除SNAT规则。
    -   如果NAT网关有DNAT规则，请先删除DNAT规则。
    -   如果NAT网关有绑定EIP，请先解绑EIP。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|0ED8D006-F706-4D23-88ED-E11ED28DCAC0|请求ID。 |

## 示例

请求示例

```
https://vpc.aliyuncs.com/?Action=DeleteNatGateway
&NatGatewayId=ngw-bp1uewa15k4iy5770****
&RegionId=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<DeleteNatGatewayResponse>
      <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
</DeleteNatGatewayResponse>
```

`JSON`格式

```
{ 
    "RequestId": "0ED8D006-F706-4D23-88ED-E11ED28DCAC0"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的regionid不存在。|
|404|InvalidNatGatewayId.NotFound|The specified NatGatewayId does not exist in our records.|指定的 NatGatewayId 不存在，请您检查填写的 NatGatewayId 是否正确。|
|400|DependencyViolation.BandwidthPackages|There are BandwidthPackages on specified NatGateway not deleted.|NAT网关上有尚未删除的带宽包，请删除NAT网关下的所有带宽包后再重新操作。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Vpc)查看更多错误码。

