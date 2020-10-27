# GetNatGatewayConvertStatus

Queries the upgrade state of a NAT gateway.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Vpc&api=GetNatGatewayConvertStatus&type=RPC&version=2016-04-28)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|GetNatGatewayConvertStatus|The operation that you want to perform. Set the value to **GetNatGatewayConvertStatus**. |
|NatGatewayId|String|Yes|ngw-bp1b0lic8uz4r6vf2\*\*\*\*|The ID of the NAT gateway. |
|RegionId|String|Yes|cn-qingdao|The ID of the region to which the NAT gateway belongs. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|ConvertSteps|Array of ConvertStep| |The list of states that the NAT gateway may experience during an upgrade process. |
|StepName|String|init|The state of the NAT gateway. Valid values:

 -   **init**: Initializing the upgrading process.
-   **check**: Checking the configurations.
-   **configure**: Configuring the NAT gateway.
-   **activate**: Activating the upgraded NAT gateway.
-   **conf\_delete**: Deleting the configuration.
-   **rollback**: Rolling back the upgrade.
-   **end\_success**: The NAT gateway is upgraded.
-   **end\_fail**: The upgrade failed. |
|StepStartTime|String|2020-08-26T08:27:19Z|The time when the upgrade was started. |
|StepStatus|String|successful|The state of the upgrade. Valid values:

 -   **processing**: indicates that the upgrade is in progress.
-   **successful**: indicates that the upgrade is successful.
-   **failed**: indicates that the upgrade failed. |
|DstNatType|String|Enhanced|The type of NAT gateway to which the specified NAT gateway is upgraded. |
|NatGatewayId|String|ngw-bp1b0lic8uz4r6vf2\*\*\*\*|The ID of the NAT gateway. |
|RequestId|String|0ED8D006-F706-4D23-88ED-E11ED28DCAC0|The ID of the request. |

## Examples

Sample requests

```
http(s)://vpc.aliyuncs.com/? Action=GetNatGatewayConvertStatus
&NatGatewayId=ngw-bp1b0lic8uz4r6vf2****
&RegionId=cn-qingdao
&<Common request parameters>
```

Sample success responses

`XML` format

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

`JSON` format

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

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The error message returned because the specified region ID does not exist. Check whether the region ID is valid.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Vpc).

