# DescribeNatGateways

Queries NAT gateways.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Vpc&api=DescribeNatGateways&type=RPC&version=2016-04-28)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeNatGateways|The operation that you want to perform. Set the value to **DescribeNatGateways**. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the NAT gateways are deployed. You can call the [DescribeRegions](~~36063~~) operation to query region IDs. |
|NatGatewayId|String|No|ngw-bp1uewa15k4iy5770\*\*\*\*|The ID of the NAT gateway that you want to query. |
|VpcId|String|No|vpc-bp15zckdt37pq72z\*\*\*\*|The ID of the virtual private cloud \(VPC\) where the NAT gateway is deployed. |
|Name|String|No|test|The name of the NAT gateway. |
|InstanceChargeType|String|No|PostPaid|The billing method of the NAT gateway. Valid values:

 -   **PostPaid**: pay-as-you-go.
-   **PrePaid**: subscription.

 **Note:** On the Alibaba Cloud International site, the value is set to **PostPaid**, which indicates the pay-as-you-go billing method. |
|Spec|String|No|Large|The size of the NAT gateway. Valid values:

 -   **Small**: a small-sized NAT gateway. This is the default value.
-   **Middle**: a medium-sized NAT gateway.
-   **Large**: a large-sized NAT gateway. |
|NatType|String|No|Normal|The type of NAT gateway. Valid values:

 -   **Normal**: a standard NAT gateway.
-   **Enhanced**: an enhanced NAT gateway. |
|ResourceGroupId|String|No|rg-bp67acfmxazb4ph\*\*\*\*|The ID of the resource group to which the NAT gateway belongs. |
|PageNumber|Integer|No|10|The number of the page to return. Default value: **1**. |
|PageSize|Integer|No|1|The number of entries to return on each page. Maximum value: **50**. Default value: **10**. |
|DryRun|Boolean|No|true|Specifies whether to precheck only this request. Valid values:

 -   **true**: The request is prechecked but NAT gateways are not queried. The system checks whether your AccessKey pair is valid, whether the RAM user is authorized, and whether the required parameters are set. If the request fails the precheck, the corresponding error code is returned. If the request passes the precheck, the `DryRunOperation` error message is returned.
-   **false**: The request is prechecked. This is the default value. If the request passes the precheck, a 2XX HTTP status code is returned and NAT gateways are queried. |
|Status|String|No|Available|The state of the NAT gateway. Valid values:

 -   **Creating**: The system is creating the NAT gateway. After you send a request to create a NAT gateway, the system creates the NAT gateway in the background. The NAT gateway remains in the **Creating** state until the operation is complete.
-   **Available**: The NAT gateway is created. If the operation to create a NAT gateway is successful, the state of the NAT gateway changes from Creating to Available.
-   **Modifying**: The NAT gateway is being modified. After you send a request to modify a NAT gateway, the system modifies the NAT gateway in the background. The NAT gateway remains in the **Modifying** state until the operation is complete.
-   **Deleting**: The NAT gateway is being deleted. After you send a request to delete a NAT gateway, the system deletes the NAT gateway in the background. The NAT gateway remains in the **Deleting** state until the operation is complete.
-   **Converting**: The NAT gateway is being upgraded. After you send a request to upgrade a standard NAT gateway to an enhanced NAT gateway, the system upgrades the NAT gateway in the background. The NAT gateway remains in the **Converting** state until the operation is complete. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|NatGateways|Array of NatGateway| |The details about the NAT gateway. |
|NatGateway| | | |
|BusinessStatus|String|Normal|The state of the NAT gateway. Valid values:

 -   **Normal**: The NAT gateway runs as expected.
-   **FinancialLocked**: The NAT gateway is locked due to overdue payments. |
|CreationTime|String|2017-06-08T12:20Z|The time when the NAT gateway was created. The time follows the ISO 8601 standard in the yyyy-MM-ddTHH:mm:ssZ format. The time is displayed in UTC. |
|DeletionProtection|Boolean|true|Indicates whether deletion protection is enabled. Valid values:

 -   **true**: Deletion protection is enabled.
-   **false**: Deletion protection is disabled. |
|Description|String|NAT|The description of the NAT gateway. |
|EcsMetricEnabled|Boolean|true|Indicates whether the traffic monitoring feature is enabled. Valid values:

 -   **true**: The traffic monitoring feature is enabled.
-   **false**: The traffic monitoring feature is disabled. |
|ExpiredTime|String|2017-08-26T16:00Z|The time when the NAT gateway expires. |
|ForwardTableIds|List|ftb-uf6gj3mhsg94qsqst\*\*\*\*|The ID of the Destination Network Address Translation \(DNAT\) table. |
|InstanceChargeType|String|PostPaid|The billing method of the NAT gateway. Valid values:

 -   **PostPaid**: pay-as-you-go.
-   **PrePaid**: subscription.

 **Note:** On the Alibaba Cloud International site, the value is set to **PostPaid**, which indicates the pay-as-you-go billing method. |
|InternetChargeType|String|PayBySpec|The metering method of the NAT gateway. Valid values:

 -   **PayBySpec**: pay by specification.
-   **PayByLcu**: pay by capacity unit \(CU\). |
|IpLists|Array of IpList| |The elastic IP address \(EIP\) that is associated with the NAT gateway. |
|IpList| | | |
|IpAddress|String|116.62.XX.XX|The EIP. |
|PrivateIpAddress|String|192.168.XX.XX|The private IP address. |
|SnatEntryEnabled|Boolean|false|Indicates whether the EIP that is used in a DNAT entry can also be used in a Source Network Address Translation \(SNAT\) entry. Valid values:

 -   **true**: The EIP can be used in a SNAT entry.
-   **false**: The EIP cannot be used in a SNAT entry |
|Name|String|abc|The name of the NAT gateway. |
|NatGatewayId|String|ngw-bp1047e2d4z7kf2ki\*\*\*\*|The ID of the region where the NAT gateway is deployed. |
|NatGatewayPrivateInfo|Struct| |The information about the private network to which the enhanced NAT gateway belongs.

 **Note:** If the value of **NatType** is **Normal**, all parameters returned in this list are empty. |
|EniInstanceId|String|10|The ID of the elastic network interface \(ENI\). |
|EniType|String|Secondary|The type of the ENI. Valid values:

 -   **Primary**: the primary ENI.
-   **Secondary**: the secondary ENI. |
|IzNo|String|cn-hangzhou-b|The zone to which the NAT gateway belongs. |
|MaxBandwidth|Integer|5120|The bandwidth limit. Unit: Mbit/s. |
|PrivateIpAddress|String|192.168.XX.XX|The private IP address. |
|VswitchId|String|vsw-bp1s2laxhdf9ayjbo\*\*\*\*|The ID of the vSwitch to which the NAT gateway is attached. |
|NatType|String|Normal|The type of NAT gateway. Valid values:

 -   **Normal**: standard NAT gateway.
-   **Enhanced**: enhanced NAT gateway. |
|RegionId|String|cn-hangzhou|The ID of the region where the NAT gateway is deployed. |
|ResourceGroupId|String|rg-bp67acfmxazb4ph\*\*\*\*|The ID of the resource group to which the NAT gateway belongs. |
|SnatTableIds|List|stb-uf6dalcdu0krz423p\*\*\*\*|The ID of the SNAT table of the NAT gateway. |
|Spec|String|Small|The size of the NAT gateway. Valid values:

 -   **Small**: a small-sized NAT gateway.
-   **Middle**: a medium-sized NAT gateway.
-   **Large**: a large-sized NAT gateway. |
|Status|String|Creating|The state of the NAT gateway. Valid values:

 -   **Creating**: The system is creating the NAT gateway. After you send a request to create a NAT gateway, the system creates the NAT gateway in the background. The NAT gateway remains in the Creating state until the operation is complete.
-   **Available**: The NAT gateway is created. If the operation to create a NAT gateway is successful, the state of the NAT gateway changes from Creating to Available.
-   **Modifying**: The NAT gateway is being modified. After you send a request to modify a NAT gateway, the system modifies the NAT gateway in the background. The NAT gateway remains in the Modifying state until the operation is complete.
-   **Deleting**: The NAT gateway is being deleted. After you send a request to delete a NAT gateway, the system deletes the NAT gateway in the background. The NAT gateway remains in the Deleting state until the operation is complete.
-   **Converting**: The NAT gateway is being upgraded. After you send a request to upgrade a standard NAT gateway to an enhanced NAT gateway, the system upgrades the NAT gateway in the background. The NAT gateway remains in the Converting state until the operation is complete. |
|VpcId|String|vpc-bp15zckdt37pq72z\*\*\*\*|The ID of the VPC where the NAT gateway is deployed. |
|PageNumber|Integer|10|The page number of the returned page. |
|PageSize|Integer|10|The number of entries returned per page. |
|RequestId|String|4EC47282-1B74-4534-BD0E-403F3EE64CAF|The ID of the request. |
|TotalCount|Integer|10|The total number of entries returned. |

## Examples

Sample requests

```
http(s)://vpc.aliyuncs.com/?Action=DescribeNatGateways
&RegionId=cn-hangzhou
&<Common request parameters>|
```

Sample success responses

`XML` format

```
<DescribeNatGatewaysResponse>
  <TotalCount>10</TotalCount>
  <PageSize>10</PageSize>
  <RequestId>4EC47282-1B74-4534-BD0E-403F3EE64CAF	</RequestId>
  <PageNumber>10</PageNumber>
  <NatGateways>
        <NatGateway>
              <Status>Creating</Status>
              <Description>NAT</Description>
              <ResourceGroupId>rg-bp67acfmxazb4ph****</ResourceGroupId>
              <InstanceChargeType>PostPaid</InstanceChargeType>
              <DeletionProtection>true</DeletionProtection>
              <NatType>Normal</NatType>
              <BusinessStatus>Normal</BusinessStatus>
              <InternetChargeType>PayBySpec</InternetChargeType>
              <Name>abc</Name>
              <EcsMetricEnabled>true</EcsMetricEnabled>
              <VpcId>vpc-bp15zckdt37pq72z****</VpcId>
              <ExpiredTime>2017-08-26T16:00Z</ExpiredTime>
              <CreationTime>2017-06-08T12:20Z</CreationTime>
              <RegionId>cn-hangzhou</RegionId>
              <Spec>Small</Spec>
              <NatGatewayId>ngw-bp1047e2d4z7kf2ki****</NatGatewayId>
              <IpLists>
                    <IpList>
                          <PrivateIpAddress>192.168.XX.XX</PrivateIpAddress>
                          <SnatEntryEnabled>false</SnatEntryEnabled>
                          <IpAddress>116.62.XX.XX</IpAddress>
                    </IpList>
              </IpLists>
              <ForwardTableIds>
                    <ForwardTableId>ftb-uf6gj3mhsg94qsqst****</ForwardTableId>
              </ForwardTableIds>
              <SnatTableIds>
                    <SnatTableId>stb-uf6dalcdu0krz423p****</SnatTableId>
              </SnatTableIds>
              <NatGatewayPrivateInfo>
                    <IzNo>cn-hangzhou-b</IzNo>
                    <PrivateIpAddress>192.168.XX.XX</PrivateIpAddress>
                    <MaxBandwidth>5120</MaxBandwidth>
                    <EniType>Secondary</EniType>
                    <EniInstanceId>10</EniInstanceId>
                    <VswitchId>vsw-bp1s2laxhdf9ayjbo****</VswitchId>
              </NatGatewayPrivateInfo>
        </NatGateway>
  </NatGateways>
</DescribeNatGatewaysResponse>
```

`JSON` format

```
{
    "DescribeNatGatewaysResponse": {
        "TotalCount": 10,
        "PageSize": 10,
        "RequestId": "4EC47282-1B74-4534-BD0E-403F3EE64CAF",
        "PageNumber": 10,
        "NatGateways": {
            "NatGateway": {
                "Status": "Creating",
                "Description": "NAT",
                "ResourceGroupId": "rg-bp67acfmxazb4ph****",
                "InstanceChargeType": "PostPaid",
                "DeletionProtection": true,
                "NatType": "Normal",
                "BusinessStatus": "Normal",
                "InternetChargeType": "PayBySpec",
                "Name": "abc",
                "EcsMetricEnabled": true,
                "VpcId": "vpc-bp15zckdt37pq72z****",
                "ExpiredTime": "2017-08-26T16:00Z",
                "CreationTime": "2017-06-08T12:20Z",
                "RegionId": "cn-hangzhou",
                "Spec": "Small",
                "NatGatewayId": "ngw-bp1047e2d4z7kf2ki****",
                "IpLists": {
                    "IpList": {
                        "PrivateIpAddress": "192.168.XX.XX",
                        "SnatEntryEnabled": false,
                        "IpAddress": "116.62.XX.XX"
                    }
                },
                "ForwardTableIds": {
                    "ForwardTableId": "ftb-uf6gj3mhsg94qsqst****"
                },
                "SnatTableIds": {
                    "SnatTableId": "stb-uf6dalcdu0krz423p****"
                },
                "NatGatewayPrivateInfo": {
                    "IzNo": "cn-hangzhou-b",
                    "PrivateIpAddress": "192.168.XX.XX",
                    "MaxBandwidth": 5120,
                    "EniType": "Secondary",
                    "EniInstanceId": 10,
                    "VswitchId": "vsw-bp1s2laxhdf9ayjbo****"
                }
            }
        }
    }
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The error message returned because the specified region ID does not exist.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Vpc).

