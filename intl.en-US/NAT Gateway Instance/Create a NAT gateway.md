# Create a NAT gateway

NAT gateways are enterprise-class public network gateways. NAT gateways provide network address translation services \(SNAT and DNAT\). Before you configure Source Network Address Translation \(SNAT\) and Destination Network Address Translation \(DNAT\) entries, you must create a NAT gateway.

A virtual private cloud \(VPC\) is created. For more information, see [t2435.md\#section\_ufw\_rhv\_rdb](/intl.en-US/VPCs and VSwitches/VPC management/Create a VPC.md).

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  On the **NAT Gateway** page, click **Create NAT Gateway**.

3.  On the **NAT Gateway** page, set the following parameters, click **Buy Now**, and complete the payment.

    |Parameter|Description|
    |:--------|:----------|
    |**Region and Zone**|Select the region where you want to deploy the NAT gateway.**Note:** Enhanced NAT gateways are available in all regions except Australia \(Sydney\). |
    |**Gateway Type**|Select the type of NAT gateway that you want to create. Valid values:    -   **Standard**
    -   **Enhanced**
Enhanced NAT gateways support all features of standard NAT gateways. Enhanced NAT gateways are developed with an upgraded technical architecture. Enhanced NAT gateways offer higher elasticity and stability. This helps you manage data transfer in a more efficient way. For more information, see [Types of NAT gateways](/intl.en-US/NAT Gateway Instance/Overview.md). |
    |**VPC ID**|Select the VPC where you want to deploy the NAT gateway. After the NAT gateway is created, you cannot change the VPC where the NAT gateway is deployed. **Note:** If you cannot find the VPC that you want to manage in the list, perform the following operations:

    -   Check whether the VPC is already associated with a NAT gateway. Each VPC can be associated with only one NAT gateway.
    -   Check whether the VPC has a custom route entry with the destination CIDR block set to 0.0.0.0/0. If such a custom route entry exists, delete it.
    -   If your account is a Resource Access Management \(RAM\) user, check whether the RAM user is authorized to access the VPC. If the RAM user is not authorized, contact the owner of the Alibaba Cloud account that creates the RAM user to grant permissions. |
    |**Zone**|Select the zone where you want to deploy the NAT gateway.|
    |**VSwitch ID**|Select a VSwitch for the NAT gateway.**Note:** You can select VSwitches for only enhanced NAT gateways. |
    |**Specification**|Select the size of the NAT gateway. Valid values:    -   **Small**
    -   **Medium**
    -   **Large**
    -   **Super Large-1**
The size of a NAT gateway determines its SNAT performance, including the maximum number of concurrent connections and the number of new connections per second. However, the gateway size does not affect the DNAT performance. For more information about difference sizes of NAT gateways, see [Sizes of NAT gateways](/intl.en-US/NAT Gateway Instance/Overview.md). |
    |**Billing Method**|The billing method of the NAT gateway:    -   **Pay by Data Transfer**: billed based on the actual data transfer. Fees vary in each billing cycle. For more information about pay-by-data-transfer NAT gateways, see [Pay-by-data-transfer](/intl.en-US/Pricing/Pay-as-you-go.md).
    -   **Pay by Specification**: billed based on the size of the NAT gateway. Fees in each billing cycle are the same. For more information about pay-by-specification NAT gateways, see [Pay-by-specification](/intl.en-US/Pricing/Pay-as-you-go.md).
**Note:** Only selected users in the following regions can purchase enhanced NAT gateways on a pay-by-data-transfer basis: China \(Chengdu\), Malaysia \(Kuala Lumpur\), India \(Mumbai\), Indonesia \(Jakarta\), Germany \(Frankfurt\) and UK \(London\). |
    |**Billing Cycle**|Select a billing cycle for the NAT gateway.|


**Related topics**  


[CreateNatGateway](/intl.en-US/API reference/NAT Gateway/CreateNatGateway.md)

