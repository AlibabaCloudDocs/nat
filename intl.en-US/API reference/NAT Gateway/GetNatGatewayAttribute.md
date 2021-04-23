# GetNatGatewayAttribute

Queries the information about a specified NAT gateway.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Vpc&api=GetNatGatewayAttribute&type=RPC&version=2016-04-28)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|NatGatewayId|String|Yes|ngw-bp1b0lic8uz4r6vf2\*\*\*\*|The ID of the NAT gateway. |
|RegionId|String|Yes|cn-qingdao|The ID of the region where the NAT gateway is deployed.

 You can call the [DescribeRegions](~~36063~~) operation to query region IDs. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|BillingConfig|Struct| |The billing information. |
|AutoPay|String|false|Indicates whether automatic payment is enabled. Valid values:

 -   **false**: Automatic payment is disabled. After an order is generated, you must go to the order center to complete the payment.
-   **true**: Automatic payment is enabled. After an order is generated, the system automatically deducts the fee from your account balance to complete the payment.

 This parameter is required when **InstanceChargeType** is set to **PrePaid**. You do not need to configure this parameter if **InstanceChargeType** is set to **PostPaid**. |
|InstanceChargeType|String|PostPaid|The billing method of the NAT gateway. Valid values:

 -   **PostPaid**: pay-as-you-go.
-   **PrePaid**: subscription.

 **Note:** For the Alibaba Cloud International site, the value is set to **PostPaid**, which indicates the pay-as-you-go billing method. |
|InternetChargeType|String|PayBySpec|The metering method of the NAT gateway. Valid values:

 -   **PayBySpec**: pay by specification.
-   **PayByLcu**: pay by capacity unit \(CU\). |
|Spec|String|Small|The size of the NAT gateway. Valid values:

 -   **Small**: a small-sized NAT gateway.
-   **Middle**: a medium-sized NAT gateway.
-   **Large**: a large-sized NAT gateway. |
|BusinessStatus|String|Normal|The state of the NAT gateway. Valid values:

 -   **Normal**: The NAT gateway runs as expected.
-   **FinancialLocked**: The NAT gateway is locked due to overdue payments. |
|CreationTime|String|2017-06-08T12:20Z|The time when the NAT gateway was created. The time follows the ISO 8601 standard in the yyyy-MM-ddTHH:mm:ssZ format. The time is displayed in UTC. |
|DeletionProtectionInfo|Struct| |The information about the deletion protection feature. |
|Enabled|Boolean|true|Indicates whether the deletion protection feature is enabled. Valid values:

 -   **true**: The deletion protection feature is enabled.
-   **false**: The deletion protection feature is disabled. This is the default value. |
|Description|String|NAT|The description of the NAT gateway. |
|EcsMetricEnabled|Boolean|true|Indicates whether the traffic monitoring feature is enabled. Valid values:

 -   **true**: The traffic monitoring feature is enabled.
-   **false**: The traffic monitoring feature is disabled. This is the default value. |
|ExpiredTime|String|2017-08-26T16:00Z|The time when the NAT gateway expires. |
|ForwardTable|Struct| |The information about DNAT entries. |
|ForwardEntryCount|Integer|1|The number of DNAT entries. |
|ForwardTableId|String|ftb-uf6gj3mhsg94qsqst\*\*\*\*|The ID of the DNAT table. |
|IpList|Array of IpList| |The elastic IP addresses \(EIPs\) that are associated with the NAT gateway. |
|AllocationId|String|eip-bp13e9i2qst4g6jzi\*\*\*\*|The ID of the instance with which the EIP is associated. |
|IpAddress|String|116.xx.xx.33|The EIP. |
|UsingStatus|String|idle|Indicates the association of the EIP. Valid values:

 -   **idle**: The EIP is not specified in a SNAT entry or a DNAT entry.
-   **UsedBySnatTable**: The EIP is specified in a SNAT entry.
-   **UsedByForwardTable**: The EIP is specified in a DNAT entry. |
|Name|String|abc\*\*\*\*|The name of the NAT gateway. |
|NatGatewayId|String|ngw-bp1047e2d4z7kf2ki\*\*\*\*|The ID of the NAT gateway. |
|NatType|String|Enhanced|The type of NAT gateway. The value is set to **Enhanced** \(enhanced NAT gateway\). |
|PrivateInfo|Struct| |The information about the private network. |
|EniInstanceId|String|10|The ID of the elastic network interface \(ENI\). |
|IzNo|String|cn-hangzhou-b|The zone where the NAT gateway is deployed. |
|MaxBandwidth|Integer|5120|The bandwidth limit. Unit: Mbit/s. |
|PrivateIpAddress|String|192.XX.XX.68|The private IP address. |
|VswitchId|String|vsw-bp1s2laxhdf9ayjbo\*\*\*|The ID of the vSwitch to which the NAT gateway belongs. |
|RegionId|String|cn-hangzhou|The ID of the region where the NAT gateway is deployed. |
|RequestId|String|4EC47282-1B74-4534-BD0E-403F3EE64CAF|The ID of the request. |
|ResourceGroupId|String|rg-bp67acfmxazb4ph\*\*\*\*|The ID of the resource group. |
|SnatTable|Struct| |The information about the SNAT entries. |
|SnatEntryCount|Integer|1|The number of SNAT entries. |
|SnatTableId|String|stb-SnatTableIds\*\*\*\*|The ID of the SNAT table. |
|Status|String|Available|The state of the NAT gateway. Valid values:

 -   **Creating**: The system is creating the NAT gateway. After you send a request to create a NAT gateway, the system creates the NAT gateway in the background. The NAT gateway remains in the Creating state until the operation is complete.
-   **Available**: The NAT gateway is created. If the operation to create a NAT gateway is successful, the state of the gateway changes from Creating to Available.
-   **Modifying**: The NAT gateway is being modified. After you send a request to modify a NAT gateway, the system modifies the NAT gateway in the background. The NAT gateway remains in the Modifying state until the operation is complete.
-   **Deleting**: The NAT gateway is being deleted. After you send a request to delete a NAT gateway, the system deletes the NAT gateway in the background. The NAT gateway remains in the Deleting state until the operation is complete.
-   **Converting**: The NAT gateway is being upgraded. After you send a request to upgrade a standard NAT gateway to an enhanced NAT gateway, the system upgrades the NAT gateway in the background. The NAT gateway remains in the Converting state until the operation is complete. |
|VpcId|String|vpc-bp15zckdt37pq72z\*\*\*\*|The ID of the VPC to which the NAT gateway belongs. |

## Examples

Sample requests

```
http(s)://[Endpoint]/?Action=GetNatGatewayAttribute
&NatGatewayId=ngw-bp1b0lic8uz4r6vf2****
&RegionId=cn-qingdao
&<Common request parameters>
```

Sample success responses

`XML` format

```
<GetNatGatewayAttributeResponse>
  <Status>Available</Status>
  <ForwardTable>
        <ForwardEntryCount>1</ForwardEntryCount>
        <ForwardTableId>ftb-uf6gj3mhsg94qsqst****</ForwardTableId>
  </ForwardTable>
  <Description>NAT</Description>
  <ResourceGroupId>rg-bp67acfmxazb4ph****</ResourceGroupId>
  <RequestId>4EC47282-1B74-4534-BD0E-403F3EE64CAF</RequestId>
  <IpList>
        <UsingStatus>idle</UsingStatus>
        <AllocationId>eip-bp13e9i2qst4g6jzi****</AllocationId>
        <IpAddress>116.xx.xx.33</IpAddress>
  </IpList>
  <BillingConfig>
        <InstanceChargeType>PostPaid</InstanceChargeType>
        <AutoPay>false</AutoPay>
        <Spec>Small</Spec>
        <InternetChargeType>PayBySpec</InternetChargeType>
  </BillingConfig>
  <DeletionProtectionInfo>
        <Enabled>true</Enabled>
  </DeletionProtectionInfo>
  <BusinessStatus>Normal</BusinessStatus>
  <NatType>Enhanced</NatType>
  <SnatTable>
        <SnatEntryCount>1</SnatEntryCount>
        <SnatTableId>stb-SnatTableIds****</SnatTableId>
  </SnatTable>
  <Name>abc****</Name>
  <EcsMetricEnabled>true</EcsMetricEnabled>
  <VpcId>vpc-bp15zckdt37pq72z****</VpcId>
  <ExpiredTime>2017-08-26T16:00Z</ExpiredTime>
  <CreationTime>2017-06-08T12:20Z</CreationTime>
  <PrivateInfo>
        <IzNo>cn-hangzhou-b</IzNo>
        <PrivateIpAddress>192.XX.XX.68</PrivateIpAddress>
        <MaxBandwidth>5120</MaxBandwidth>
        <EniInstanceId>10</EniInstanceId>
        <VswitchId>vsw-bp1s2laxhdf9ayjbo***</VswitchId>
  </PrivateInfo>
  <RegionId>cn-hangzhou</RegionId>
  <NatGatewayId>ngw-bp1047e2d4z7kf2ki****</NatGatewayId>
</GetNatGatewayAttributeResponse>
  <ForwardTable>
        <ForwardEntryCount>1</ForwardEntryCount>
        <ForwardTableId>ftb-uf6gj3mhsg94qsqst****</ForwardTableId>
  </ForwardTable>
  <Description>NAT</Description>
  <ResourceGroupId>rg-bp67acfmxazb4ph****</ResourceGroupId>
  <RequestId>4EC47282-1B74-4534-BD0E-403F3EE64CAF</RequestId>
  <IpList>
        <UsingStatus>idle</UsingStatus>
        <AllocationId>eip-bp13e9i2qst4g6jzi****</AllocationId>
        <IpAddress>116.xx.xx.33</IpAddress>
  </IpList>
  <BillingConfig>
        <InstanceChargeType>PostPaid</InstanceChargeType>
        <AutoPay>false</AutoPay>
        <Spec>Small</Spec>
        <InternetChargeType>PayBySpec</InternetChargeType>
  </BillingConfig>
  <DeletionProtectionInfo>
        <Enabled>true</Enabled>
  </DeletionProtectionInfo>
  <BusinessStatus>Normal</BusinessStatus>
  <NatType>Enhanced</NatType>
  <SnatTable>
        <SnatEntryCount>1</SnatEntryCount>
        <SnatTableId>stb-SnatTableIds****</SnatTableId>
  </SnatTable>
  <Name>abc****</Name>
  <EcsMetricEnabled>true</EcsMetricEnabled>
  <VpcId>vpc-bp15zckdt37pq72z****</VpcId>
  <ExpiredTime>2017-08-26T16:00Z</ExpiredTime>
  <CreationTime>2017-06-08T12:20Z</CreationTime>
  <PrivateInfo>
        <IzNo>cn-hangzhou-b</IzNo>
        <PrivateIpAddress>192.XX.XX.68</PrivateIpAddress>
        <MaxBandwidth>5120</MaxBandwidth>
        <EniInstanceId>10</EniInstanceId>
        <VswitchId>vsw-bp1s2laxhdf9ayjbo***</VswitchId>
  </PrivateInfo>
  <RegionId>cn-hangzhou</RegionId>
  <NatGatewayId>ngw-bp1047e2d4z7kf2ki****</NatGatewayId>
</GetNatGatewayAttributeResponse>
```

`JSON`格式

```
{
    "Status": "Available",
    "ForwardTable": {
        "ForwardEntryCount": 1,
        "ForwardTableId": "ftb-uf6gj3mhsg94qsqst****"
    },
    "Description": "NAT",
    "ResourceGroupId": "rg-bp67acfmxazb4ph****",
    "RequestId": "4EC47282-1B74-4534-BD0E-403F3EE64CAF",
    "IpList": {
        "UsingStatus": "idle",
        "AllocationId": "eip-bp13e9i2qst4g6jzi****",
        "IpAddress": "116.xx.xx.33"
    },
    "BillingConfig": {
        "InstanceChargeType": "PostPaid",
        "AutoPay": false,
        "Spec": "Small",
        "InternetChargeType": "PayBySpec"
    },
    "DeletionProtectionInfo": {
        "Enabled": true
    },
    "BusinessStatus": "Normal",
    "NatType": "Enhanced",
    "SnatTable": {
        "SnatEntryCount": 1,
        "SnatTableId": "stb-SnatTableIds****"
    },
    "Name": "abc****",
    "EcsMetricEnabled": true,
    "VpcId": "vpc-bp15zckdt37pq72z****",
    "ExpiredTime": "2017-08-26T16:00Z",
    "CreationTime": "2017-06-08T12:20Z",
    "PrivateInfo": {
        "IzNo": "cn-hangzhou-b",
        "PrivateIpAddress": "192.XX.XX.68",
        "MaxBandwidth": 5120,
        "EniInstanceId": 10,
        "VswitchId": "vsw-bp1s2laxhdf9ayjbo***"
    },
    "RegionId": "cn-hangzhou",
    "NatGatewayId": "ngw-bp1047e2d4z7kf2ki****"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Vpc)查看更多错误码。

