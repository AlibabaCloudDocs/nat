# DescribeNatGateways

Queries created NAT gateways.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Vpc&api=DescribeNatGateways&type=RPC&version=2016-04-28)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeNatGateways|The operation that you want to perform. Set the value to **DescribeNatGateways**. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the NAT gateways are deployed. You can call the [DescribeRegions](~~36063~~) operation to query region IDs. |
|NatGatewayId|String|No|ngw-bp1uewa15k4iy5770\*\*\*\*|The ID of the NAT gateway that you want to query. |
|VpcId|String|No|vpc-bp15zckdt37pq72z\*\*\*\*|The ID of the virtual private cloud \(VPC\) to which the NAT gateway belongs. |
|Name|String|No|test|The name of the NAT gateway. |
|InstanceChargeType|String|No|PostPaid|The billing method of the NAT gateway. Valid values:

-   **PostPaid**: pay-as-you-go.
-   **PrePaid**: subscription.

**Note:** For the Alibaba Cloud International site, set the value to **PostPaid** \(pay-as-you-go\). |
|Spec|String|No|Large|The size of the NAT gateway. Valid values:

-   **Small**: a small-sized NAT gateway. This is the default value.
-   **Middle**: a middle-sized NAT gateway.
-   **Large**: a large-sized NAT gateway.
-   **XLarge.1**: a super large-sized NAT gateway. |
|NatType|String|No|Normal|The type of NAT gateway. Valid values:

-   **Normal**: a standard NAT gateway.
-   **Enhanced**: an enhanced NAT gateway. |
|ResourceGroupId|String|No|rg-bp67acfmxazb4ph\*\*\*\*|The ID of the resource group to which the NAT gateway belongs. |
|PageNumber|Integer|No|10|The number of the page to return. Default value: **1**. |
|PageSize|Integer|No|1|The number of entries to return on each page. Valid values: 1 to **50**. Default value: **10**. |
|DryRun|Boolean|No|true|Specifies whether to precheck only this request. Valid values:

**true**: The request is checked but NAT gateways are not queried. The system checks whether your AccessKey pair is valid, whether the Resource Access Management \(RAM\) user is authorized, and whether required parameters are specified. If the request fails the precheck, the corresponding error code is returned. If the request passes the precheck, the `DryRunOperation` error code is returned.

**false**: The request is checked. This is the default value. If the request passes the precheck, a 2XX HTTP status code is returned and NAT gateways are queried. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|NatGateways|Array of NatGateway| |The details of the NAT gateway. |
|NatGateway| | | |
|BusinessStatus|String|Normal|The status of the NAT gateway.

-   **Normal**: The NAT gateway runs as expected.
-   **FinancialLocked**: The NAT gateway is locked due to overdue payments. |
|CreationTime|String|2017-06-08T12:20:55|The time when the NAT gateway was created. Specify the time in the ISO 8601 standard in the YYYY-MM-DDThh:mmZ format. The time is displayed in UTC. |
|DeletionProtection|Boolean|true|Indicates whether deletion protection is enabled. Valid values:

-   **true**: The deletion protection feature is enabled.
-   **false**: The deletion protection feature is disabled. |
|Description|String|NAT|The description of the NAT gateway. |
|EcsMetricEnabled|Boolean|true|Indicates whether the traffic monitoring feature is enabled. Valid values:

-   **true**: The traffic monitoring feature is enabled.
-   **false**: The traffic monitoring feature is disabled. |
|ExpiredTime|String|2017-08-26T16:00Z|The time when the NAT gateway expires. |
|ForwardTableIds|List|ftb-uf6gj3mhsg94qsqst\*\*\*\*|The ID of the Destination Network Address Translation \(DNAT\) table. |
|InstanceChargeType|String|PostPaid|The billing method of the NAT gateway. Valid values:

-   **PostPaid**: pay-as-you-go.
-   **PrePaid**: subscription.

**Note:** For the Alibaba Cloud International site, set this parameter to **PostPaid** \(pay-as-you-go\). |
|InternetChargeType|String|PayBySpec|The billing method of the NAT gateway. Valid values:

-   **PayBySpec**: pay-by-specification.
-   **PayByLcu**: pay-by-LCU. |
|IpLists|Array of IpList| |The elastic IP address \(EIP\) that is associated with the NAT gateway. |
|IpList| | | |
|IpAddress|String|116.62.222.xx|The EIP. |
|SnatEntryEnabled|Boolean|false|Whether the EIP that is used in a DNAT entry can also be used in a Source Network Address Translation \(SNAT\) entry. Valid values:

-   **true**: The EIP can be used in a SNAT entry.
-   **false**: The EIP cannot be used in a SNAT entry |
|Name|String|abc|The name of the NAT gateway. |
|NatGatewayId|String|ngw-bp1047e2d4z7kf2ki\*\*\*\*|The ID of the NAT gateway. |
|NatGatewayPrivateInfo|Struct| |The information of the virtual private cloud \(VPC\) to which the enhanced NAT gateway belongs.

**Note:** If the value of **NatType** is **Normal**, all parameters returned in this list are empty. |
|EniInstanceId|String|10|The instance ID of the elastic network interface \(ENI\). |
|IzNo|String|cn-hangzhou-b|The zone to which the NAT gateway belongs. |
|MaxBandwidth|Integer|5120|The maximum bandwidth. Unit: Mbit/s. |
|PrivateIpAddress|String|192.168.1.xx|The private IP address. |
|VswitchId|String|vsw-bp1s2laxhdf9ayjbo\*\*\*\*|The ID of the VSwitch to which the NAT gateway is attached. |
|NatType|String|Normal|The type of the NAT gateway.

-   **Normal**: standard NAT gateway.
-   **Enhanced**: enhanced NAT gateway. |
|RegionId|String|cn-hangzhou|The ID of the region where the NAT gateway is deployed. |
|ResourceGroupId|String|rg-bp67acfmxazb4ph\*\*\*\*|The ID of the resource group. |
|SnatTableIds|List|stb-uf6dalcdu0krz423p\*\*\*\*|The ID of the SNAT table for the NAT gateway. |
|Spec|String|Small|The size of the NAT gateway.

-   **Small**: a small-sized NAT gateway.
-   **Middle**: a middle-sized NAT gateway.
-   **Large**: a large-sized NAT gateway.
-   **XLarge.1**: a super large-sized NAT gateway. |
|Status|String|Initiating|The state of the NAT gateway.

**Creating**: CreateNatGateway is an asynchronous operation. After you make a request, the NAT gateway is in the Creating state. The system creates the NAT gateway in the background.

**Available**: The NAT gateway is in the Available state after it is created.

**Modifying**: ModifyNatGatewaySpec is an asynchronous operation. After you make a request, the NAT gateway is in the Modifying state. The system modifies the NAT gateway in the background.

**Deleting**: DeleteNatGateway is an asynchronous operation. After you make a request, the NAT gateway is in the Deleting state. The system deletes the NAT gateway in the background.

**Converting**: UpdateNatGatewayNatType is an asynchronous operation. After you make a request, the NAT gateway is in the Converting state. The system upgrades the NAT gateway in the background. |
|VpcId|String|vpc-bp15zckdt37pq72z\*\*\*\*|The ID of the VPC to which the NAT gateway belongs. |
|PageNumber|Integer|10|The page number of the returned page. |
|PageSize|Integer|10|The number of entries returned per page. |
|RequestId|String|4EC47282-1B74-4534-BD0E-403F3EE64CAF|The ID of the request. |
|TotalCount|Integer|10|The total number of entries returned. |

## Examples

Sample requests

```
http(s)://vpc.aliyuncs.com/? Action=DescribeNatGateways
&RegionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeNatGatewaysResponse>
    <PageNumber>1</PageNumber>
    <TotalCount>1</TotalCount>
    <PageSize>10</PageSize>
    <RequestId>1207C80C-7CAB-4874-A9A0-D19EC9F35490</RequestId>
    <NatGateways>
            <NatGateway>
                    <Description></Description>
                    <Spec>Small</Spec>
                    <IpLists>
                            <IpList>
                                    <IpAddress>118.xx.xx.181</IpAddress>
                                    <AllocationId>eip-bp1xyg5ipmh3nledx****</AllocationId>
                                    <UsingStatus>UsedBySnatTable</UsingStatus>
                            </IpList>
                            <IpList>
                                    <IpAddress>47.xx.xx.34</IpAddress>
                                    <AllocationId>eip-bp19eue77u20cffjc****</AllocationId>
                                    <UsingStatus>UsedByForwardTable</UsingStatus>
                            </IpList>
                    </IpLists>
                    <ForwardTableIds>
                            <ForwardTableId>ftb-bp15o9aylj19vfvgt****</ForwardTableId>
                    </ForwardTableIds>
                    <VpcId>vpc-bp15k6sx6fhdz2jw4****</VpcId>
                    <NatGatewayId>ngw-bp1047e2d4z7kf2ki****</NatGatewayId>
                    <CreationTime>2018-01-10T09:48:29Z</CreationTime>
                    <Name></Name>
                    <Status>Available</Status>
                    <BusinessStatus>Normal</BusinessStatus>
                    <RegionId>cn-hangzhou</RegionId>
                    <SnatTableIds>
                            <SnatTableId>stb-bp1tyr0o48w6wymur****</SnatTableId>
                    </SnatTableIds>
                    <InstanceChargeType>PostPaid</InstanceChargeType>
            </NatGateway>
    </NatGateways>
</DescribeNatGatewaysResponse>
```

`JSON` format

```
{
    "PageNumber": 1, 
    "TotalCount": 1, 
    "PageSize": 10, 
    "RequestId": "1207C80C-7CAB-4874-A9A0-D19EC9F35490", 
    "NatGateways": {
        "NatGateway": [ 
            {
                "Description": "", 
                "Spec": "Small", 
                "IpLists": {
                    "IpList": [
                        {
                            "IpAddress": "118.xx.xx.181", 
                            "AllocationId": "eip-bp1xyg5ipmh3nledx****", 
                            "UsingStatus": "UsedBySnatTable"
                        }, 
                        {
                            "IpAddress": "47.xx.xx.34", 
                            "AllocationId": "eip-bp19eue77u20cffjc****", 
                            "UsingStatus": "UsedByForwardTable"
                        }
                    ]
                }, 
                "ForwardTableIds": {
                    "ForwardTableId": [
                        "ftb-bp15o9aylj19vfvgt****"
                    ]
                }, 
                "VpcId": "vpc-bp15k6sx6fhdz2jw4****", 
                "NatGatewayId": "ngw-bp1047e2d4z7kf2ki****", 
                "CreationTime": "2018-01-10T09:48:29Z", 
                "Name": "", 
                "Status": "Available", 
                "BusinessStatus": "Normal", 
                "RegionId": "cn-hangzhou", 
                "SnatTableIds": {
                    "SnatTableId": [
                        "stb-bp1tyr0o48w6wymur****"
                    ]
                }, 
                "InstanceChargeType": "PostPaid"
            }
        ]
    }
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The error message returned because the specified region ID does not exist. Check whether the region ID is valid.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Vpc).

