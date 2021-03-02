# GetNatGatewayAttribute

调用GetNatGatewayAttribute接口查询单个NAT网关实例的信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=GetNatGatewayAttribute&type=RPC&version=2016-04-28)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|NatGatewayId|String|是|ngw-bp1b0lic8uz4r6vf2\*\*\*\*|NAT网关实例ID。 |
|RegionId|String|是|cn-qingdao|NAT网关所属的地域ID。

 您可以通过调用[DescribeRegions](36063)接口获取地域ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|BillingConfig|Struct| |账单配置信息。 |
|AutoPay|String|false|是否自动付费，取值：

 -   **false**：不开启自动付费，生成订单后需要到订单中心完成支付。
-   **true**：开启自动付费，自动支付订单。

 当**InstanceChargeType**参数的值为**PrePaid**时，该参数必选；当**InstanceChargeType**参数的值为**PostPaid**时，该参数不填。 |
|InstanceChargeType|String|PostPaid|NAT网关实例的付费模式，取值：

 -   **PostPaid**：按量付费。
-   **PrePaid**：包年包月。

 **说明：** 国际站仅支持**PostPaid**（按量付费）。 |
|InternetChargeType|String|PayBySpec|NAT网关实例的计费类型。

 -   **PayBySpec**：按固定规格计费。
-   **PayByLcu**：按使用量计费。 |
|Spec|String|Small|NAT网关实例的规格。

 -   **Small**：小型。
-   **Middle**：中型。
-   **Large**：大型。 |
|BusinessStatus|String|Normal|NAT网关的业务状态。

 -   **Normal**：正常。
-   **FinancialLocked**：欠费锁定状态。 |
|CreationTime|String|2017-06-08T12:20Z|创建时间。按照ISO8601标准表示，并需要使用UTC时间。格式为：YYYY-MM-DDThh:mmZ。 |
|DeletionProtectionInfo|Struct| |删除保护信息。 |
|Enabled|Boolean|true|是否开启删除保护功能。

 -   **true**：开启了删除保护功能。
-   **false**（默认值）：未开启删除保护功能。 |
|Description|String|NAT|NAT网关实例的描述。 |
|EcsMetricEnabled|Boolean|true|是否开启了网关流量监控功能。

 -   **true**：开启了网关流量监控功能。
-   **false**（默认值）：未开启网关流量监控功能。 |
|ExpiredTime|String|2017-08-26T16:00Z|NAT网关实例的过期时间。 |
|ForwardTable|Struct| |DNAT列表的信息。 |
|ForwardEntryCount|Integer|1|DNAT条目的个数。 |
|ForwardTableId|String|ftb-uf6gj3mhsg94qsqst\*\*\*\*|DNAT表的ID。 |
|IpList|Array of IpList| |NAT网关绑定的弹性公网IP列表。 |
|AllocationId|String|eip-bp13e9i2qst4g6jzi\*\*\*\*|弹性公网IP的实例ID。 |
|IpAddress|String|116.xx.xx.33|弹性公网IP的地址。 |
|UsingStatus|String|idle|弹性公网IP的关联关系。

 -   **idle**：弹性公网IP未关联SNAT条目或DNAT条目。
-   **UsedBySnatTable**：弹性公网IP已关联SNAT条目。
-   **UsedByForwardTable**：弹性公网IP已关联DNAT条目。 |
|Name|String|abc\*\*\*\*|NAT网关实例名称。 |
|NatGatewayId|String|ngw-bp1047e2d4z7kf2ki\*\*\*\*|NAT网关实例的ID。 |
|NatType|String|Enhanced|NAT网关的类型，当前取值为 **Enhanced**，即增强型NAT网关。 |
|PrivateInfo|Struct| |私网信息。 |
|EniInstanceId|String|10|弹性网卡实例ID。 |
|IzNo|String|cn-hangzhou-b|NAT网关实例所属的可用区。 |
|MaxBandwidth|Integer|5120|最大带宽值，单位为Mbps。 |
|PrivateIpAddress|String|192.XX.XX.68|私网IP地址。 |
|VswitchId|String|vsw-bp1s2laxhdf9ayjbo\*\*\*|NAT网关实例所属的交换机ID。 |
|RegionId|String|cn-hangzhou|NAT网关实例的所在地域ID。 |
|RequestId|String|4EC47282-1B74-4534-BD0E-403F3EE64CAF|请求ID。 |
|ResourceGroupId|String|rg-bp67acfmxazb4ph\*\*\*\*|资源组ID。 |
|SnatTable|Struct| |SNAT列表信息。 |
|SnatEntryCount|Integer|1|SANT条目的个数。 |
|SnatTableId|String|stb-SnatTableIds\*\*\*\*|SNAT列表的ID。 |
|Status|String|Available|NAT网关的状态。

 -   **Creating**：创建NAT网关是异步操作，在创建完成之前是Creating状态。
-   **Available**：NAT网关创建完成后的状态，是稳定状态。
-   **Modifying**：变配NAT网关是异步操作，在变配的过程中是Modifying状态。
-   **Deleting**：删除NAT网关是异步操作，在删除的过程中是Deleting状态。
-   **Converting**：普通型NAT网关转换到增强型NAT网关是异步操作，在转换过程中是Converting状态。 |
|VpcId|String|vpc-bp15zckdt37pq72z\*\*\*\*|NAT网关实例所属的VPC的ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=GetNatGatewayAttribute
&NatGatewayId=ngw-bp1b0lic8uz4r6vf2****
&RegionId=cn-qingdao
&<公共请求参数>
```

正常返回示例

`XML`格式

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

