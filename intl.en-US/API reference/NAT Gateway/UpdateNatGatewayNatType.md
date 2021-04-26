# UpdateNatGatewayNatType

Upgrades a standard NAT gateway to an enhanced NAT gateway.

## Description

Before you call the UpdateNatGatewayNatType operation, pay attention to the following considerations:

-   UpdateNatGatewayNatType is an asynchronous operation. After you make a request, the ID of the request is returned but the NAT gateway is not upgraded. The system upgrades the NAT gateway in the background. You can call the GetNatGatewayConvertStatus operation to query the upgrade status of a NAT gateway. For more information, see [GetNatGatewayConvertStatus](~~184744~~).
    -   **processing**: indicates that the NAT gateway is being upgraded. You can only perform query the state of the NAT gateway, but cannot perform other operations.
    -   **successful**: indicates that the standard NAT gateway is upgraded.
    -   **failed**: indicates that the upgrade failed.
-   You are charged the same fee for using enhanced NAT gateways and standard NAT gateways, and the upgrade is free of charge.
-   It takes about five minutes to upgrade a standard NAT gateway to an enhanced NAT gateway. During the upgrade process, the NAT gateway may be disconnected for 1 to 2 seconds. The service resumes after your workloads are reconnected.
-   You can only upgrade standard NAT gateways to enhanced NAT gateways. You are not allowed to degrade enhanced NAT gateways to standard NAT gateways.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Vpc&api=UpdateNatGatewayNatType&type=RPC&version=2016-04-28)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|UpdateNatGatewayNatType|The operation that you want to perform. Set the value to **UpdateNatGatewayNatType**. |
|NatGatewayId|String|Yes|ngw-bp1b0lic8uz4r6vf2\*\*\*\*|The ID of the NAT gateway that you want to upgrade. |
|NatType|String|Yes|Enhanced|The type of NAT gateway to which you want to upgrade. Set the value to **Enhanced** \(enhanced NAT gateway\). |
|RegionId|String|Yes|cn-qingdao|The ID of the region where the standard NAT gateway to be upgraded is created. |
|VSwitchId|String|Yes|vsw-bp17nszybg8epodke\*\*\*\*|The vSwitch to which the enhanced NAT gateway is attached.

 **Note:** If you do not specify this parameter, the system randomly selects a vSwitch in the virtual private cloud \(VPC\) of the enhanced NAT gateway and attaches the enhanced NAT gateway to the vSwitch. |
|DryRun|Boolean|No|false|Specifies whether to precheck only this request. Valid values:

 **true**: The validity of the request is checked but the standard NAT gateway is not upgraded. The system checks whether your AccessKey pair is valid, whether the Resource Access Management \(RAM\) user is authorized, and whether the required parameters are specified. If the request fails the precheck, the corresponding error code is returned. If the request passes the precheck, the `DryRunOperation` error code is returned.

 **false** \(default\): The validity of the request is checked. If the request passes the precheck, a 2XX HTTP status code is returned and the standard NAT gateway is upgraded. |
|ClientToken|String|No|0c593ea1-3bea-11e9-b96b-88e9fe637760|The client token that is used to ensure the idempotence of the request. You can use the client to generate a value that is unique among different requests. **ClientToken** can contain only ASCII characters. It must be 1 to 64 characters in length. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|0ED8D006-F706-4D23-88ED-E11ED28DCAC0|The ID of the request. |

## Examples

Sample requests

```
http(s)://vpc.aliyuncs.com/? Action=UpdateNatGatewayNatType
&NatGatewayId=ngw-bp1b0lic8uz4r6vf2****
&NatType=Enhanced
&RegionId=cn-qingdao
&VSwitchId=vsw-bp17nszybg8epodke****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<UpdateNatGatewayNatTypeResponse>    
      <RequestId>7C01CA72-73FD-4056-B16A-42E392D47625</RequestId>
</UpdateNatGatewayNatTypeResponse>
```

`JSON` format

```
{
	"RequestId": "7C01CA72-73FD-4056-B16A-42E392D47625"
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The error message returned because the specified region ID does not exist. Check whether the region ID is valid.|
|400|OperationUnsupported.NatConvert|The NAT gateway conversion function is not supported.|The error message returned because the NAT gateway upgrade feature is not supported.|
|400|NATGW\_NOT\_EXIST|The specified NAT gateway does not exist.|The error message returned because the specified NAT gateway does not exist.|
|400|OperationFailed.VpcNotExist|The specified VPC does not exist.|The error message returned because the specified VPC does not exist.|
|400|OperationFailed.VswNotExist|The specified VSwitch does not exist.|The error message returned because the specified vSwitch does not exist.|
|400|OperationFailed.NatTypeNotEnhanced|Operation failed because the specified NAT gateway type is not enhanced.|The error message returned because the specified gateway type is not enhanced NAT gateway.|
|400|OperationFailed.NatGwBindWithBandwidthPackage|Operation failed because the NAT gateway is bound to bandwidth packages.|The error message returned because one or more NAT service plans are associated with the NAT gateway.|
|400|IncorrectStatus.NatGateway|The status of NAT gateway is incorrect.|The error message returned because the state of the NAT gateway is invalid.|
|400|OperationFailed.EipInMiddleStatus|Operation failed because the status of EIP associated with the specified NAT gateway is abnormal.|The error message returned because the state of the elastic IP address \(EIP\) that is associated with the specified NAT gateway is abnormal.|
|400|OperationFailed.SnatInMiddleStatus|Operation failed because the status of the SNAT entry of the specified NAT gateway is abnormal.|The error message returned because the state of the Source Network Address Translation \(SNAT\) entry for the NAT gateway is abnormal.|
|400|OperationFailed.DnatInMiddleStatus|Operation failed because the status of the DNAT entry associated with the NAT gateway is abnormal.|The error message returned because the state of the Destination Network Address Translation \(DNAT\) entry for the NAT gateway is abnormal.|
|400|OperationFailed.NatGwRouteInMiddleStatus|Operation failed because the status of the route entry associated with the NAT gateway is abnormal.|The error message returned because the state of the route entry associated with the NAT gateway is abnormal.|
|400|OperationFailed.EnhancedInventoryNotEnough|The enhanced NAT gateway inventory is insufficient in the specified zone.|The error message returned because the stock of enhanced NAT gateways is insufficient in the specified zone.|
|400|OperationFailed.EnhancedUserIsUnAuthorized|Operation failed because the user is not authorized to create an enhanced NAT gateway.|The error message returned because the user is not authorized to create enhanced NAT gateways.|
|400|OperationFailed.EnhancedRegion|Operation failed because enhanced NAT gateways are not available for sale in the specified region.|The error message returned because enhanced NAT gateways are not available for sale in the specified region.|
|400|OperationFailed.EnhancedQuotaExceed|Operation failed because the maximum number of enhanced NAT gateways in the same VPC is exceeded.|The error message returned because the number of enhanced NAT gateways in the specified VPC has reached the upper limit.|
|400|InvalidBandwidthPackageIdNumber.NotSupported|The number of BandwidthPackageIds exceeds the limit.|The error message returned because the number of EIP bandwidth plans reaches the quota limit.|
|400|OperationFailed.VswNotBelongToVpc|Operation failed because the specified VSwitch is not bound to the same VPC with NAT gateway.|The error message returned because the specified vSwitch and NAT gateway are not deployed in the same VPC.|
|400|OperationUnsupported.VpcAttachedCen|Operation failed because the VPC is attached to CEN.|The error message returned because the VPC is attached to a Cloud Enterprise Network \(CEN\) instance.|
|400|OperationUnsupported.RouterInterfaceExist|Operation failed because the VPC has a router interface.|The error message returned because the VPC has a router interface.|
|400|OperationFailed.VRouterNotExist|Operation failed because the VRouter does not exist.|The error message returned because the VRouter does not exist.|
|400|OperationFailed.SnatQuotaExceed|Operation failed because the maximum number of SNAT entry is exceeded.|The error message returned because the number of SNAT entries has reached the upper limit.|
|400|OperationFailed.DnatQuotaExceed|Operation failed because the maximum number of forward entry is exceeded.|The error message returned because the number of DNAT entries has reached the upper limit.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Vpc).

