# Enable multiple applications to share bandwidth \(sample code\)

This topic describes how to call the API with Alibaba Cloud SDK for Python to enable multiple applications to share the bandwidth provided by an EIP bandwidth plan. This reduces the costs of Internet data transfer.

## Scenario

A company creates two Elastic Compute Service \(ECS\) instances and deploys an application on each ECS instance. The ECS instances need to receive requests from the Internet. The service port is port 80. The amount of bandwidth required by the two ECS instances varies within a day:

-   The peak hours of ECS 1 range from 13:00:00 to 18:00:00. During this period of time, the bandwidth required is 1,000 Mbit/s. During the remaining hours of the day, the bandwidth required is 500 Mbit/s.
-   The peak hours of ECS 2 range from 19:00:00 to 23:00:00. During this period of time, the bandwidth required is 1,000 Mbit/s. During the remaining hours of the day, the bandwidth required is 500 Mbit/s.

If you want to purchase bandwidth for the ECS instances separately, you must purchase two bandwidth plans with a total bandwidth of 2,000 Mbit/s. However, the ECS instances cannot make full use of the bandwidth during off-peak hours. This causes bandwidth resource wastes.

To resolve this problem, you can configure Destination Network Address Translation \(DNAT\) for your NAT gateway and purchase EIP bandwidth plans.

-   DNAT maps elastic IP addresses \(EIPs\) to ECS instances in a virtual private cloud \(VPC\). Then, the ECS instances can receive requests from the Internet.
-   An EIP bandwidth plan can be shared among multiple applications to reduce the costs of Internet data transfer.

![Scenario](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2248304061/p170562.png)

## Prerequisites

Before you start, make sure that the following requirements are met:

-   An Alibaba Cloud account is created. If you do not have an Alibaba Cloud account, click[create an Alibaba account](https://account.alibabacloud.com/register/intl_register.htm).
-   An AccessKey pair is created. If you do not have an AccessKey pair, go to the [Security Management](https://usercenter.console.aliyun.com/?spm=5176.doc52740.2.3.QKZk8w#/manage/ak) page and create an AccessKey pair.
-   A Python development environment is prepared and Alibaba Cloud SDK for Python is installed. For more information, see [Installation]().
-   A VPC and a vSwitch are created. For more information, see [CreateVpc](/intl.en-US/API reference/Virtual Private Cloud (VPC)/CreateVpc.md).
-   ECS instances are created and attached to the vSwitch. Applications are deployed on the ECS instances. For more information, see [CreateInstance](/intl.en-US/API Reference/Instances/CreateInstance.md).
-   Two EIPs are created for the NAT gateway. The EIPs must meet the following requirements:

    -   The EIPs and the NAT gateway to be associated with the EIPs must be in the same region.
    -   The EIPs are billed on a pay-as-you-go basis.
    For more information, see [AllocateEipAddress](/intl.en-US/API reference/EIP/AllocateEipAddress.md).


## Procedure

![Procedure](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2248304061/p170824.png)

## Step 1: Create a NAT gateway

NAT gateways are enterprise-class gateways that provide network address translation services for Internet access. You must create a NAT gateway before you can create DNAT entries.

**Note:** When you create an enhanced NAT gateway, you must specify a vSwitch for the NAT gateway. Then, the system assigns an unused private IP address from the vSwitch to the enhanced NAT gateway.

-   To create an enhanced NAT gateway that is attached to an existing vSwitch, make sure that the zone to which the vSwitch belongs supports enhanced NAT gateways. In addition, the vSwitch must have unused public IP addresses.
-   If you do not have a vSwitch in the specified VPC, create a vSwitch in the zone that supports enhanced NAT gateways. Then, specify the vSwitch for the enhanced NAT gateway.

You can call [ListEnhanhcedNatGatewayAvailableZones](/intl.en-US/API reference/NAT Gateway/ListEnhanhcedNatGatewayAvailableZones.md) to query the zones that support enhanced NAT gateways and call [DescribeVSwitches](/intl.en-US/API reference/VSwitch/DescribeVSwitches.md) to query unused IP addresses in a vSwitch.

1.  The following sample code shows how to create a NAT gateway:

    ```
    from aliyunsdkcore.client import AcsClient
    from aliyunsdkcore.acs_exception.exceptions import ClientException
    from aliyunsdkcore.acs_exception.exceptions import ServerException
    from aliyunsdkvpc.request.v20160428.CreateNatGatewayRequest import CreateNatGatewayRequest
    
    # Create an AcsClient instance.
    # yourAccessKeyId: your AccessKey ID.
    # yourAccessKeySecret: your AccessKey secret.
    # yourRegionId: the region ID.
    client = AcsClient("yourAccessKeyId","yourAccessKeySecret","yourRegionId")
    
    # Create a NAT gateway.
    request = CreateNatGatewayRequest()
    request.set_accept_format('json')
    
    # The ID of the VPC where the NAT gateway is deployed.
    request.set_VpcId("vpc-uf68wppzf839896z7****")
    
    # The name of the NAT gateway.
    request.set_Name("test")
    
    # The description of the NAT gateway.
    request.set_Description("test")
    
    # The size of the NAT gateway.
    # Valid values: Small (default), Middle, Large, and Super Large-1. The parameter is set to Small in this example. Set the parameter based on your business requirements.
    request.set_Spec("Small")
    
    # The billing method of the NAT gateway.
    # Valid values: PostPaid (pay-as-you-go) and PrePaid (subscription). The default value is PostPaid.
    request.set_InstanceChargeType("PrePaid")
    
    # The billing cycle of subscriptions.
    # Valid values: Month and Year. The default value is Month.
    # This parameter is required when InstanceChargeType is set to PrePaid. You do not need to set this parameter when InstanceChargeType is set to PostPaid.
    request.set_PricingCycle("Month")
    
    # The subscription duration.
    # When PricingCycle is set to Month, Period can be set from 1 to 9. When PricingCycle is set to Year, Period can be set from 1 to 3.
    request.set_Duration("1")
    
    # Automatic payment.
    # Valid values: false and true. false: disables automatic payment. After an order is generated, you must go to the Order Center to complete the payment. true: enables automatic payment. Payments are automatically completed.
    request.set_AutoPay(True)
    
    # The ID of the vSwitch to which the NAT gateway is attached.
    # When you create an enhanced NAT gateway, you must specify the vSwitch to which the NAT gateway is attached. The system automatically assigns an unused private IP address from the vSwitch to the enhanced NAT gateway.
    request.set_VSwitchId("vsw-uf6gnat6e5tk0gnbm****")
    
    # The type of the NAT gateway.
    # Valid values: Normal (standard NAT gateways) and Enhanced (enhanced NAT gateways).
    # Enhanced NAT gateways are upgraded from the technical architecture of standard NAT gateways. Enhanced NAT gateways offer higher elasticity and stability, and enable you to better manage data transfer over the Internet.
    request.set_NatType("Enhanced")
    
    # The metering method of the NAT gateway.
    # Valid values: PayBySpec (pay-by-specification) and PayByLcu (pay-by-LCU).
    request.set_InternetChargeType("PayBySpec")
    
    # Make an API request and print the response.
    response = client.do_action_with_exception(request)
    
    # python2:  print(response)
    print(str(response, encoding='utf-8'))
    ```

    The following response is returned:

    ```
    {
        "RequestId": "3164006B-33DB-46BB-B77D-FC80094D1F10",
        "SnatTableIds": {
            "SnatTableId": []
        },
        "ForwardTableIds": {
            "ForwardTableId": []
        },
        "NatGatewayId": "ngw-uf6htj15rgyp8ivix****"
    }
    ```

2.  The following sample code shows how to query details of the NAT gateway:

    ```
    from aliyunsdkcore.client import AcsClient
    from aliyunsdkcore.acs_exception.exceptions import ClientException
    from aliyunsdkcore.acs_exception.exceptions import ServerException
    from aliyunsdkvpc.request.v20160428.DescribeNatGatewaysRequest import DescribeNatGatewaysRequest
    
    # Create an AcsClient instance.
    # yourAccessKeyId: your AccessKey ID.
    # yourAccessKeySecret: your AccessKey secret.
    # yourRegionId: the region ID.
    client = AcsClient("yourAccessKeyId","yourAccessKeySecret","yourRegionId")
    
    # Query details about the NAT gateway.
    request = DescribeNatGatewaysRequest()
    request.set_accept_format('json')
    
    # The ID of the NAT gateway that you want to query.
    request.set_NatGatewayId("ngw-uf6htj15rgyp8ivix****")
    
    # Make an API request and print the response.
    response = client.do_action_with_exception(request)
    
    # python2:  print(response)
    print(str(response, encoding='utf-8'))
    ```

    The following response is returned:

    ```
    {
        "TotalCount": 1,
        "RequestId": "4040A37C-45C0-4C85-B16D-0F7EA3084108",
        "PageSize": 10,
        "PageNumber": 1,
        "NatGateways": {
            "NatGateway": [{
                "Status": "Available",
                "Description": "test",
                "ResourceGroupId": "rg-acfmx2k5un****",
                "InstanceChargeType": "PrePaid",
                "ForwardTableIds": {
                    "ForwardTableId": ["ftb-uf6hdobgppflyr2ng****"]
                },
                "IpLists": {
                    "IpList": []
                },
                "BandwidthPackageIds": {
                    "BandwidthPackageId": []
                },
                "AutoPay": false,
                "DeletionProtection": false,
                "BusinessStatus": "Normal",
                "NatType": "Enhanced",
                "Name": "test",
                "InternetChargeType": "PayBySpec",
                "NatGatewayPrivateInfo": {
                    "IzNo": "",
                    "PrivateIpAddress": "",
                    "EniInstanceId": "",
                    "VswitchId": ""
                },
                "EcsMetricEnabled": false,
                "VpcId": "vpc-uf68wppzf839896z7****",
                "SnatTableIds": {
                    "SnatTableId": ["stb-uf6qneg0l83lxignc****"]
                },
                "ExpiredTime": "2020-10-28T16:00Z",
                "CreationTime": "2020-09-28T07:24:09Z",
                "RegionId": "cn-shanghai",
                "Spec": "Small",
                "NatGatewayId": "ngw-uf6htj15rgyp8ivix****"
            }]
        }
    }
    ```


## Step 2: Associate EIPs with the NAT gateway

A NAT gateway functions as expected only after it is associated with one or more EIPs.

The following sample code shows how to associate EIPs with the NAT gateway:

```
from aliyunsdkcore.client import AcsClient
from aliyunsdkcore.acs_exception.exceptions import ClientException
from aliyunsdkcore.acs_exception.exceptions import ServerException
from aliyunsdkvpc.request.v20160428.AssociateEipAddressRequest import AssociateEipAddressRequest

# The IDs of the EIPs that you want to associate with the NAT gateway. This parameter is set to the IDs of EIP 1 and EIP 2 in this example.
allocationIds = ["eip-uf6pvlaprugu1azc8****", "eip-uf69ls0f3qgv0alk6****"]

# Create an AcsClient instance.
# yourAccessKeyId: your AccessKey ID.
# yourAccessKeySecret: your AccessKey secret.
# yourRegionId: the region ID.
client = AcsClient("yourAccessKeyId","yourAccessKeySecret","yourRegionId")

# Associate the EIPs with the NAT gateway.
for i in range(0, 2):
    request = AssociateEipAddressRequest()
    request.set_accept_format('json')

    # The ID of the NAT gateway with which you want to associate EIPs.
    request.set_InstanceId("ngw-uf6htj15rgyp8ivix****")

    # The IDs of the EIPs with which you want to associate EIPs.
    request.set_AllocationId(allocationIds[i])

    # The type of the resource with which you want to associate EIPs.
    request.set_InstanceType("NAT")
    
    # Make an API request and print the response.
    response = client.do_action_with_exception(request)

    # python2:  print(response)
    print(str(response, encoding='utf-8'))
```

The following response is returned:

```
{
    "RequestId": "8292A46D-F720-4AEE-98FB-7D3352BA2B63"
}
{
    "RequestId": "E62EEBF8-D327-440E-95BC-8884832C1326"
}
```

## Step 3: Create DNAT entries

A DNAT entry maps the EIP of a NAT gateway to an ECS instance so that the ECS instance can receive requests from the Internet. The following table shows the DNAT entries for ECS 1 and ECS 2 in this example.

|Entry name|EIP|External port|Protocol|Private IP address|Internal port|
|----------|---|-------------|--------|------------------|-------------|
|DNAT1|EIP1|80|TCP|ECS1|80|
|DNAT2|EIP2|80|TCP|ECS2|80|

1.  The following sample code shows how to create a DNAT entry for ECS 1:

    ```
    from aliyunsdkcore.client import AcsClient
    from aliyunsdkcore.acs_exception.exceptions import ClientException
    from aliyunsdkcore.acs_exception.exceptions import ServerException
    from aliyunsdkvpc.request.v20160428.CreateForwardEntryRequest import CreateForwardEntryRequest
    
    # Create an AcsClient instance.
    # yourAccessKeyId: your AccessKey ID.
    # yourAccessKeySecret: your AccessKey secret.
    # yourRegionId: the region ID.
    client = AcsClient("yourAccessKeyId","yourAccessKeySecret","yourRegionId")
    
    # Create a DNAT entry.
    request = CreateForwardEntryRequest()
    request.set_accept_format('json')
    
    # The ID of the DNAT table in which you want to create the DNAT entry.
    request.set_ForwardTableId("ftb-uf6hdobgppflyr2ng****")
    
    # Specify the EIP for Internet access. This parameter is set to the IP address of EIP 1 in this example.
    request.set_ExternalIp("101.xx.xx.137")
    
    # The external port where requests from the Internet are received. Valid values: 1 to 65535. This parameter is set to 80 in this example.
    request.set_ExternalPort("80")
    
    # Specify the private IP address of the ECS instance that wants to receive requests from the Internet. This parameter is set to the private IP address of ECS 1 in this example.
    request.set_InternalIp("192.xx.xx.100")
    
    # The internal port to which the requests received on the external port are forwarded. Valid values: 1 to 65535. This parameter is set to 80 in this example.
    request.set_InternalPort("80")
    
    # The protocol used by the external and internal ports.
    # Valid values: TCP, UDP, and Any. TCP: forwards TCP packets. UDP: forwards UDP packets. Any: forwards all packets.
    request.set_IpProtocol("TCP")
    
    # The name of the DNAT entry. The name is set to DNAT 1 in this example.
    request.set_ForwardEntryName("DNAT1")
    
    # Make an API request and print the response.
    response = client.do_action_with_exception(request)
    
    # python2:  print(response)
    print(str(response, encoding='utf-8'))
    ```

    The following response is returned:

    ```
    {
        "RequestId": "93A6E13E-C168-4444-9DF1-F4B22B1E0A12",
        "ForwardEntryId": "fwd-uf69gp4nyj8b9aa2n****"
    }
    ```

2.  The following sample code shows how to create a DNAT entry for ECS 2:

    ```
    from aliyunsdkcore.client import AcsClient
    from aliyunsdkcore.acs_exception.exceptions import ClientException
    from aliyunsdkcore.acs_exception.exceptions import ServerException
    from aliyunsdkvpc.request.v20160428.CreateForwardEntryRequest import CreateForwardEntryRequest
    
    # Create an AcsClient instance.
    # yourAccessKeyId: your AccessKey ID.
    # yourAccessKeySecret: your AccessKey secret.
    # yourRegionId: the region ID.
    client = AcsClient("yourAccessKeyId","yourAccessKeySecret","yourRegionId")
    
    # Create a DNAT entry.
    request = CreateForwardEntryRequest()
    request.set_accept_format('json')
    
    # The ID of the DNAT table in which you want to create the DNAT entry.
    request.set_ForwardTableId("ftb-uf6hdobgppflyr2ng****")
    
    # Specify the EIP for Internet access. This parameter is set to the IP address of EIP 1 in this example.
    request.set_ExternalIp("106.xx.xx.94")
    
    # The external port where requests from the Internet are received. Valid values: 1 to 65535. This parameter is set to 80 in this example.
    request.set_ExternalPort("80")
    
    # Specify the private IP address of the ECS instance that wants to receive requests from the Internet. This parameter is set to the private IP address of ECS 1 in this example.
    request.set_InternalIp("192.xx.xx.101")
    
    # The internal port to which the requests received on the external port are forwarded. Valid values: 1 to 65535. This parameter is set to 80 in this example.
    request.set_InternalPort("80")
    
    # The protocol used by the external and internal ports.
    # Valid values: TCP, UDP, and Any. TCP: forwards TCP packets. UDP: forwards UDP packets. Any: forwards all packets.
    request.set_IpProtocol("TCP")
    
    # The name of the DNAT entry. The name is set to DNAT 2 in this example.
    request.set_ForwardEntryName("DNAT2")
    
    # Make an API request and print the response.
    response = client.do_action_with_exception(request)
    
    # python2:  print(response)
    print(str(response, encoding='utf-8'))
    ```

    The following response is returned:

    ```
    {
        "RequestId": "EB455CB3-222E-4F62-AF20-FAF908615717",
        "ForwardEntryId": "fwd-uf6g8gu2ld36nohly****"
    }
    ```


## Step 4: Create an EIP bandwidth plan

EIP bandwidth plans support regional bandwidth sharing and transferring. You can use EIP bandwidth plans to reduce bandwidth usage costs.

The following sample code shows how to create an EIP bandwidth plan:

```
from aliyunsdkcore.client import AcsClient
from aliyunsdkcore.acs_exception.exceptions import ClientException
from aliyunsdkcore.acs_exception.exceptions import ServerException
from aliyunsdkvpc.request.v20160428.CreateCommonBandwidthPackageRequest import CreateCommonBandwidthPackageRequest

# Create an AcsClient instance.
# yourAccessKeyId: your AccessKey ID.
# yourAccessKeySecret: your AccessKey secret.
# yourRegionId: the region ID.
client = AcsClient("yourAccessKeyId","yourAccessKeySecret","yourRegionId")

# Create an EIP bandwidth plan.
request = CreateCommonBandwidthPackageRequest()
request.set_accept_format('json')

# Specify the maximum bandwidth of the EIP bandwidth plan. Valid values: 1000 to 5000. Unit: Mbit/s. This parameter is set to 1500 in this example. You can set the parameter based on your business requirements.
request.set_Bandwidth(1500)

# The connection type.
# Valid values: BGP and BGP_PRO. BGP: represents BGP (Multi-ISP). BGP_PRO: represents BGP (Multi-ISP) Premium.
request.set_ISP("BGP")

# The name of the EIP bandwidth plan.
request.set_Name("test")

# The description of the EIP bandwidth plan.
request.set_Description("test")

# The billing method of the EIP bandwidth plan.
# Valid values: PayByBandwidth and PayBy95. PayByBandwidth: The EIP bandwidth plan is charged based on bandwidth usage. PayBy95: The EIP bandwidth plan is charged based on the enhanced 95th percentile bandwidth. The default value is PayByBandwidth.
request.set_InternetChargeType("PayByBandwidth")

# Make an API request and print the response.
response = client.do_action_with_exception(request)

# python2:  print(response)
print(str(response, encoding='utf-8'))
```

The following response is returned:

```
{
    "RequestId": "592C8AB6-09AC-4751-9B17-231BF8FEEA44",
    "ResourceGroupId": "rg-acfmx2k5unk****",
    "BandwidthPackageId": "cbwp-uf6jvfp1wqps1vywa****"
}
```

## Step 5: Associate EIPs with the EIP bandwidth plan

You can associate EIP 1 and EIP 2 with the created EIP bandwidth plan. After the EIPs are associated with the EIP bandwidth plan:

-   Services attached to the NAT gateway that is associated with the EIPs share the bandwidth of the EIP bandwidth plan.
-   The predefined maximum bandwidths of the EIPs become invalid. The maximum bandwidths of the EIPs equal the maximum bandwidth of the associated EIP bandwidth plan.
-   The predefined billing methods of the EIPs become invalid. The EIPs function as public IP addresses. No fees are charged for data transfer and bandwidth usage of the EIPs.

The following sample code shows how to associate EIP 1 and EIP 2 with the EIP bandwidth plan:

```
from aliyunsdkcore.client import AcsClient
from aliyunsdkcore.acs_exception.exceptions import ClientException
from aliyunsdkcore.acs_exception.exceptions import ServerException
from aliyunsdkvpc.request.v20160428.AddCommonBandwidthPackageIpRequest import AddCommonBandwidthPackageIpRequest

# Specify the EIPs that you want to associate with the EIP bandwidth plan. This parameter is set to EIP 1 and EIP 2 in this example.
IpInstanceIds = ["eip-uf6pvlaprugu1azc8****","eip-uf69ls0f3qgv0alk6****"]

# Create an AcsClient instance.
# yourAccessKeyId: your AccessKey ID.
# yourAccessKeySecret: your AccessKey secret.
# yourRegionId: the region ID.
client = AcsClient("yourAccessKeyId","yourAccessKeySecret","yourRegionId")

for i in range(0, 2):
    # Associate the EIPs with the EIP bandwidth plan.
    request = AddCommonBandwidthPackageIpRequest()
    request.set_accept_format('json')
    
    # The ID of the EIP bandwidth plan.
    request.set_BandwidthPackageId("cbwp-uf6jvfp1wqps1vywa****")

    # The EIPs to be associated with the EIP bandwidth plan.
    request.set_IpInstanceId(IpInstanceIds[i])

    # Make an API request and print the response.
    response = client.do_action_with_exception(request)

    # python2:  print(response)
    print(str(response, encoding='utf-8'))
                
```

The following response is returned:

```
{
    "RequestId": "658D8E3C-A85E-406C-AE49-EE6ECA2B9252"
}
{
    "RequestId": "166E9BF2-C12B-45B6-A712-633AD535B446"
}
```

## Step 6: Test network connectivity

You can verify the network connectivity by using a computer to access the applications that are deployed on ECS 1 and ECS 2.

**Note:** Make sure that the security group rules of the ECS instances allow the ECS instances to receive requests from the Internet.

1.  Open a browser on a computer that can access the Internet.

2.  Enter one of the EIPs that are associated with the NAT gateway to access the application that runs on an ECS instance.

    The test results indicate that you can access the applications that are deployed on ECS 1 and ECS 2 over the Internet. It also shows that the ECS instances share the bandwidth of the EIP bandwidth plan and can handle traffic spikes.

    ![Test the connectivity to ECS 1](../images/p171126.png "Access the application that run on ECS 1")

    ![Test the connectivity to ECS 2](../images/p171125.png "Access the application that run on ECS 2")


