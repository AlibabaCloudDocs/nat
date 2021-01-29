# ModifyNatGatewayAttribute

Modifies the name and description of a NAT gateway.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Vpc&api=ModifyNatGatewayAttribute&type=RPC&version=2016-04-28)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ModifyNatGatewayAttribute|The operation that you want to perform. Set the value to **ModifyNatGatewayAttribute**. |
|NatGatewayId|String|Yes|ngw-2ze0dcn4mq31qx2jc\*\*\*\*|The ID of the NAT gateway that you want to modify. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the NAT gateway is deployed.

 You can call the [DescribeRegions](~~36063~~) operation to query region IDs. |
|Name|String|No|nat123|The name of the NAT gateway.

 The name must be 2 to 128 characters in length, and can contain letters, digits, periods \(.\), underscores \(\_\), and hyphens \(-\). The name cannot start with `http://` or `https://`.

 **Note:** You must specify at least one of the following parameters: **Name** and **Description**. |
|Description|String|No|fortest|The description of the NAT gateway.

 The description must be 2 to 256 characters in length, and start with a letter. It cannot start with `http://` or `https://`.

 **Note:** You must specify at least one of the following parameters: **Name** and **Description**. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|AB5F62CF-2B60-4458-A756-42C9DFE108D1|The ID of the request. |

## Examples

Sample requests

```
https://vpc.aliyuncs.com/?Action=ModifyNatGatewayAttribute
&NatGatewayId=ngw-2ze0dcn4mq31qx2jc****
&RegionId=cn-hangzhou
&Name=nat123
&<Common request parameters>
```

Sample responses

`XML` format

```
<ModifyNatGatewayAttributeResponse>
	  <RequestId>2315DEB7-5E92-423A-91F7-4C1EC9AD97C3</RequestId>
</ModifyNatGatewayAttributeResponse>
```

`JSON` format

```
{
  "RequestId": "2315DEB7-5E92-423A-91F7-4C1EC9AD97C3"
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The error message returned because the specified region ID does not exist. Check whether the region ID is valid.|
|404|InvalidNatGatewayId.NotFound|The specified NatGatewayId does not exist in our records.|The error message returned because the specified NAT gateway ID does not exist. Check whether the value of the NatGatewayId parameter is valid.|
|400|InvalidParameter.Name.Malformed|The specified Name is not valid.|The error message returned because the specified name is invalid.|
|400|InvalidParameter.Description.Malformed|The specified Description is not valid.|The error message returned because the specified description is invalid.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Vpc).

