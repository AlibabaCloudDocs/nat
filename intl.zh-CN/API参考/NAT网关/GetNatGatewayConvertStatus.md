# GetNatGatewayConvertStatus

调用GetNatGatewayConvertStatus接口查看NAT网关转换状态列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=GetNatGatewayConvertStatus&type=RPC&version=2016-04-28)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetNatGatewayConvertStatus|要执行的操作，取值：**GetNatGatewayConvertStatus**。 |
|NatGatewayId|String|是|ngw-bp1b0lic8uz4r6vf2\*\*\*\*|要查看转换状态的NAT网关实例ID。 |
|RegionId|String|是|cn-qingdao|要查看转换状态的NAT网关所属的地域ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ConvertSteps|Array of ConvertStep| |转换过程中的状态变化。 |
|StepName|String|init|切换步骤的名称：

 -   **init**：初始化。
-   **check**：配置检查。
-   **configure**：配置下发
-   **activate**：引流切换。
-   **conf\_delete**：配置删除。
-   **rollback**：回滚。
-   **end\_success**：切换成功。
-   **end\_fail**：切换失败。 |
|StepStartTime|String|2020-08-26T08:27:19Z|切换步骤的开始时间。 |
|StepStatus|String|successful|切换的状态：

 -   **processing**：切换中。
-   **successful**：切换成功。
-   **failed**：切换失败。 |
|DstNatType|String|Enhanced|目标网关类型。 |
|NatGatewayId|String|ngw-bp1b0lic8uz4r6vf2\*\*\*\*|NAT网关实例ID。 |
|RequestId|String|0ED8D006-F706-4D23-88ED-E11ED28DCAC0|请求ID。 |

## 示例

请求示例

```
http(s)://vpc.aliyuncs.com/?Action=GetNatGatewayConvertStatus
&NatGatewayId=ngw-bp1b0lic8uz4r6vf2****
&RegionId=cn-qingdao
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<GetNatGatewayConvertStatusResponse>
  <RequestId>566678F2-BF11-4701-9569-D888191DAF5F</RequestId>
  <DstNatType>Enhanced</DstNatType>
  <Bid>12345</Bid>
  <ConvertSteps>
        <StepName>init</StepName>
        <StepStatus>successful</StepStatus>
        <StepStartTime>2020-08-26T08:27:19Z</StepStartTime>
  </ConvertSteps>
  <ConvertSteps>
        <StepName>check</StepName>
        <StepStatus>successful</StepStatus>
        <StepStartTime>2020-08-26T08:27:19Z</StepStartTime>
  </ConvertSteps>
  <ConvertSteps>
        <StepName>configure</StepName>
        <StepStatus>successful</StepStatus>
        <StepStartTime>2020-08-26T08:27:19Z</StepStartTime>
  </ConvertSteps>
  <ConvertSteps>
        <StepName>activate</StepName>
        <StepStatus>successful</StepStatus>
        <StepStartTime>2020-08-26T08:27:54Z</StepStartTime>
  </ConvertSteps>
  <ConvertSteps>
        <StepName>conf_delete</StepName>
        <StepStatus>successful</StepStatus>
        <StepStartTime>2020-08-26T08:27:58Z</StepStartTime>
  </ConvertSteps>
  <ConvertSteps>
        <StepName>end_success</StepName>
        <StepStatus>successful</StepStatus>
        <StepStartTime>2020-08-26T08:28:00Z</StepStartTime>
  </ConvertSteps>
  <NatGatewayId>ngw-p0w4fb0mospbkaw9n****</NatGatewayId>
  <AliUid>12345678</AliUid>
</GetNatGatewayConvertStatusResponse>
```

`JSON` 格式

```
{
  "RequestId": "566678F2-BF11-4701-9569-D888191DAF5F",
  "DstNatType": "Enhanced",
  "Bid": "12345",
  "ConvertSteps": [
    {
      "StepName": "init",
      "StepStatus": "successful",
      "StepStartTime": "2020-08-26T08:27:19Z"
    },
    {
      "StepName": "check",
      "StepStatus": "successful",
      "StepStartTime": "2020-08-26T08:27:19Z"
    },
    {
      "StepName": "configure",
      "StepStatus": "successful",
      "StepStartTime": "2020-08-26T08:27:19Z"
    },
    {
      "StepName": "activate",
      "StepStatus": "successful",
      "StepStartTime": "2020-08-26T08:27:54Z"
    },
    {
      "StepName": "conf_delete",
      "StepStatus": "successful",
      "StepStartTime": "2020-08-26T08:27:58Z"
    },
    {
      "StepName": "end_success",
      "StepStatus": "successful",
      "StepStartTime": "2020-08-26T08:28:00Z"
    }
  ],
  "NatGatewayId": "ngw-p0w4fb0mospbkaw9n****",
  "AliUid": "12345678"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Vpc)查看更多错误码。

