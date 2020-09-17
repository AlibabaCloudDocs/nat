# Create a NAT gateway

A NAT gateway is an enterprise-class gateway that provides NAT proxy services. Before you configure SNAT and DNAT entries, you must create a NAT gateway.

A VPC network is created. For more information, see [t2435.md\#section\_ufw\_rhv\_rdb](/intl.en-US/VPCs and VSwitches/VPC management/Create a VPC.md).

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  On the **NAT Gateway** page, click **Create NAT Gateway**.

3.  On the buy page, set the following parameters and complete the payment.

    |Parameter|Description|
    |:--------|:----------|
    |**Region**|Select the region of the VPC network for which you want to create the NAT gateway.|
    |**VPC ID**|Select the VPC network for which you want to create the NAT gateway. After the NAT gateway is created, you cannot change the VPC network that is associated with the gateway. **Note:** If you cannot find the target VPC network in the list, perform the following operations:

    -   Check whether the VPC network is already associated with a NAT gateway. Each VPC network can be associated with only one NAT gateway.
    -   Check whether the VPC network has a custom route entry with the destination CIDR block set to 0.0.0.0/0. If such a custom route entry exists, it must be deleted. |
    |**Specification**|Select the size of the NAT gateway. The size of a NAT gateway determines the maximum number of SNAT connections and the number of SNAT connections per second \(CPS\). However, the size does not affect the data throughput. **Note:** The specifications of NAT Gateway do not limit the number of DNAT connections and the corresponding data throughput. For more information, see [Overview](/intl.en-US/NAT Gateway Instance/Overview.md). |
    |**Billing cycle**|Select a billing cycle for the NAT gateway.|


**Related topics**  


[CreateNatGateway](/intl.en-US/API reference/NAT Gateway/CreateNatGateway.md)

