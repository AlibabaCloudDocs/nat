# Enable multiple applications to share bandwidth \(sample code\)

This topic describes how to enable multiple applications to share the bandwidth of an EIP bandwidth plan by calling an API operation through Alibaba Cloud SDK for Python. This reduces the data egress costs.

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

-   An Alibaba Cloud account is created. If you do not have an Alibaba Cloud account, [create an Alibaba account](https://account.alibabacloud.com/register/intl_register.htm).
-   An AccessKey pair is created. If you do not have an AccessKey pair, go to the [Security Management](https://usercenter.console.aliyun.com/?spm=5176.doc52740.2.3.QKZk8w#/manage/ak) page and create an AccessKey pair.
-   A Python development environment is prepared and Alibaba Cloud SDK for Python is installed. For more information, see [Installation]().
-   A virtual private cloud \(VPC\) and a vSwitch are created. For more information, see [CreateVpc](/intl.en-US/API reference/Virtual Private Cloud (VPC)/CreateVpc.md).
-   Elastic Compute Service \(ECS\) instances are created and attached to the vSwitch. Applications are deployed on the ECS instances. For more information, see [CreateInstance](/intl.en-US/API Reference/Instances/CreateInstance.md).
-   Two elastic IP addresses \(EIPs\) are created for the NAT gateway. The EIPs must meet the following requirements:

    -   The EIPs must be in the same region as the NAT gateway with which you want to associate the EIPs.
    -   The EIPs are billed on a pay-as-you-go basis.
    For more information, see [AllocateEipAddress](/intl.en-US/API reference/EIP/AllocateEipAddress.md).


## Procedure

![Procedure](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2248304061/p170824.png)

## Step 1: Create a NAT gateway

NAT gateways are enterprise-class gateways that provide network address translation services for Internet access. You must create a NAT gateway before you can create DNAT entries.

**Note:** When you create an enhanced NAT gateway, you must specify a vSwitch for the NAT gateway. Then, the system assigns an idle private IP address from the vSwitch to the NAT gateway.

-   To create an enhanced NAT gateway that is attached to an existing vSwitch, make sure that the zone to which the vSwitch belongs supports enhanced NAT gateways. In addition, the vSwitch must have idle IP addresses.
-   If you do not have a vSwitch in the specified VPC, create a vSwitch in a zone that supports enhanced NAT gateways. Then, specify the vSwitch for the enhanced NAT gateway.

You can call [ListEnhanhcedNatGatewayAvailableZones](/intl.en-US/API reference/NAT Gateway/ListEnhanhcedNatGatewayAvailableZones.md) to query the zones that support enhanced NAT gateways and call [DescribeVSwitches](/intl.en-US/API reference/VSwitch/DescribeVSwitches.md) to query idle IP addresses in a vSwitch.

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
    # Valid values: Small, Medium, and Large. Default value: Small. In this example, the parameter is set to Small. You can select a gateway size to meet your business requirements.
    request.set_Spec("Small")
    
    # The billing method of the NAT gateway.
    # Valid values: PostPaid and PrePaid. PostPaid: indicates the pay-as-you-go billing method. PrePaid: indicates the subscription billing method. Default value: PostPaid.
    request.set_InstanceChargeType("PrePaid")
    
    # The billing cycle of the subscription NAT gateway.
    # Valid values: Month and Year. Default value: Month.
    # If InstanceChargeType is set to PrePaid, this parameter is required. If InstanceChargeType is set to PostPaid, you do not need to set this parameter.
    request.set_PricingCycle("Month")
    
    # The subscription duration.
    # If you set PricingCycle to Month, you can set Period to a value from 1 to 9. If you set PricingCycle to Year, you can set Period to a value from 1 to 3.
    request.set_Duration("1")
    
    # Automatic payment.
    # Valid values: false and true. false: disables automatic payment. If you set this parameter to false, you must go to the Order Center to complete the payment after an order is generated. true: enables automatic payment. If you set this parameter to true, payments are automatically completed.
    request.set_AutoPay(True)
    
    # The ID of the vSwitch to which the NAT gateway is attached.
    # When you create an enhanced NAT gateway, you must specify the vSwitch to which the NAT gateway is attached. Then, the system automatically assigns an idle private IP address from the vSwitch to the enhanced NAT gateway.
    request.set_VSwitchId("vsw-uf6gnat6e5tk0gnbm****")
    
    # The type of NAT gateway.
    # Valid values: Normal and Enhanced. Normal: indicates a standard NAT gateway. Enhanced: indicates an enhanced NAT gateway.
    # Enhanced NAT gateways are an upgrade from standard NAT gateways and use a more advanced architecture. Compared with standard NAT gateways, enhanced NAT gateways offer higher elasticity and stability. This improves how you can manage data transfer.
    request.set_NatType("Enhanced")
    
    # The metering method of the NAT gateway.
    # Valid values: PayBySpec and PayByLcu. PayBySpec: indicates the pay-by-specification metering method. PayByLcu: indicates the pay-by-CU metering method.
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

2.  The following sample code shows how to query the details about the NAT gateway:

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
    
    # Query the details about the NAT gateway.
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

A NAT gateway works as expected only after you associate an EIP with the NAT gateway.

The following sample code shows how to associate EIPs with the NAT gateway:

```
from aliyunsdkcore.client import AcsClient
from aliyunsdkcore.acs_exception.exceptions import ClientException
from aliyunsdkcore.acs_exception.exceptions import ServerException
from aliyunsdkvpc.request.v20160428.AssociateEipAddressRequest import AssociateEipAddressRequest

# The IDs of the EIPs that you want to associate with the NAT gateway. In this example, the IDs of EIP 1 and EIP 2 are specified.
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

    # The IDs of the EIPs that you want to associate with the NAT gateway.
    request.set_AllocationId(allocationIds[i])

    # The type of resource with which you want to associate EIPs.
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

A DNAT entry maps the EIP of a NAT gateway to an ECS instance. This allows the ECS instance to provide Internet-facing services. In this example, configure the DNAT entries that are described in the following table for ECS 1 and ECS 2.

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
    
    # The ID of the DNAT table to which you want to add the DNAT entry.
    request.set_ForwardTableId("ftb-uf6hdobgppflyr2ng****")
    
    # Specify the EIP that is used to communicate with the Internet. In this example, the IP address of EIP 1 is specified.
    request.set_ExternalIp("101.xx.xx.137")
    
    # The external port that is used in port forwarding. Valid values: 1 to 65535. In this example, this parameter is set to 80.
    request.set_ExternalPort("80")
    
    # Specify the private IP address of the ECS instance that wants to receive requests from the Internet. In this example, this parameter is set to the private IP address of ECS 1.
    request.set_InternalIp("192.xx.xx.100")
    
    # The internal port that is used in port forwarding. Valid values: 1 to 65535. In this example, this parameter is set to 80.
    request.set_InternalPort("80")
    
    # The protocol that is used by the ports.
    # Valid values: TCP, UDP, and Any. TCP: Only TCP packets are forwarded. UDP: Only UDP packets are forwarded. Any: All packets are forwarded.
    request.set_IpProtocol("TCP")
    
    # The name of the DNAT entry. In this example, the name is set to DNAT1.
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
    
    # The ID of the DNAT table to which you want to add the DNAT entry.
    request.set_ForwardTableId("ftb-uf6hdobgppflyr2ng****")
    
    # Specify the EIP that is used to communicate with the Internet. In this example, the IP address of EIP 1 is specified.
    request.set_ExternalIp("106.xx.xx.94")
    
    # The external port that is used in port forwarding. Valid values: 1 to 65535. In this example, this parameter is set to 80.
    request.set_ExternalPort("80")
    
    # Specify the private IP address of the ECS instance that wants to receive requests from the Internet. In this example, this parameter is set to the private IP address of ECS 1.
    request.set_InternalIp("192.xx.xx.101")
    
    # The internal port that is used in port forwarding. Valid values: 1 to 65535. In this example, this parameter is set to 80.
    request.set_InternalPort("80")
    
    # The protocol that is used by the ports.
    # Valid values: TCP, UDP, and Any. TCP: Only TCP packets are forwarded. UDP: Only UDP packets are forwarded. Any: All packets are forwarded.
    request.set_IpProtocol("TCP")
    
    # The name of the DNAT entry. In this example, the name is set to DNAT2.
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

EIP bandwidth plans support bandwidth sharing and transfer on a regional scale. You can use EIP bandwidth plans to reduce bandwidth resource costs.

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

# Specify the bandwidth limit of the EIP bandwidth plan. Valid values: 1000 to 5000. Unit: Mbit/s. In this example, this parameter is set to 1500. You can set the parameter based on your business requirements.
request.set_Bandwidth(1500)

# The connection type.
# Valid values: BGP and BGP_PRO. BGP: BGP (Multi-ISP). BGP_PRO: BGP (Multi-ISP) Pro.
request.set_ISP("BGP")

# The name of the EIP bandwidth plan.
request.set_Name("test")

# The description of the EIP bandwidth plan.
request.set_Description("test")

# The billing method of the EIP bandwidth plan.
# Valid values: PayByBandwidth and PayBy95. PayByBandwidth: The EIP bandwidth plan is charged based on bandwidth usage. PayBy95: The EIP bandwidth plan is charged based on the enhanced 95th percentile bandwidth. Default value: PayByBandwidth.
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

You can associate EIP 1 and EIP 2 with the EIP bandwidth plan that you created. After you associate the EIPs with the EIP bandwidth plan, the EIPs are subject to the following changes:

-   Services attached to the NAT gateway with which the EIPs are associated share the bandwidth of the EIP bandwidth plan.
-   The predefined bandwidth limits of the EIPs become invalid. The bandwidth limits of the EIPs equal the bandwidth limit of the associated EIP bandwidth plan.
-   The predefined billing methods of the EIPs become invalid. The EIPs function as public IP addresses. You are not charged for data transfer and bandwidth usage of the EIPs.

The following sample code shows how to associate EIP 1 and EIP 2 with the EIP bandwidth plan:

```
from aliyunsdkcore.client import AcsClient
from aliyunsdkcore.acs_exception.exceptions import ClientException
from aliyunsdkcore.acs_exception.exceptions import ServerException
from aliyunsdkvpc.request.v20160428.AddCommonBandwidthPackageIpRequest import AddCommonBandwidthPackageIpRequest

# Specify the EIPs that you want to associate with the EIP bandwidth plan. In this example, EIP 1 and EIP 2 are specified.
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

    # The EIPs that you want to associate with the EIP bandwidth plan.
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

## Step 6: Verify the network connectivity

You can verify the network connectivity by using a computer to access the applications that are deployed on ECS 1 and ECS 2.

**Note:** Make sure that the security group rules of the ECS instances allow the ECS instances to receive requests from the Internet.

1.  Open a browser on a computer that can access the Internet.

2.  Enter one of the EIPs that are associated with the NAT gateway into the address bar of the browser and access the application that runs on an ECS instance.

    The results indicate that you can access the applications that are deployed on ECS 1 and ECS 2 over the Internet. In addition, the ECS instances share the bandwidth of the EIP bandwidth plan and can handle traffic spikes.

    ![Verify the network connectivity to ECS 1](../images/p171126.png "Access the application that runs on ECS 1")

    ![Verify the network connectivity to ECS 2](../images/p171125.png "Access the application that runs on ECS 2")


