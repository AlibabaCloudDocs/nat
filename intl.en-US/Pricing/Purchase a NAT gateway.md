# Purchase a NAT gateway

This topic describes how to purchase a NAT gateway. An enhanced NAT gateway is used as an example.

## Prerequisites

A virtual private cloud \(VPC\) and a vSwitch are created. For more information, see [Work with VPCs](/intl.en-US/VPCs and vSwitchs/Work with VPCs.md).

## Create a NAT gateway

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  On the **NAT Gateway** page, click **Create NAT Gateway**.

3.  The first time you purchase a NAT gateway, you must create a service-linked role for NAT Gateway. In the lower part of the **NAT Gateway \(Pay-As-You-Go\)** page, click **Create** in the Notes on Creating Service-linked Roles section. After a service-linked role is created, you can purchase a NAT gateway.

    ![Create a service-linked role](../images/p225001.png)

4.  On the **NAT Gateway \(Pay-As-You-Go\)** page, set the following parameters and click **Buy Now**.

    -   **Region and Zone**: Select the region where you want to deploy the NAT gateway.
    -   **Zone**: Select the zone where you want to deploy the NAT gateway.
    -   **VPC ID**: Select the VPC where you want to deploy the NAT gateway. After you create a NAT gateway, you cannot change the VPC where the NAT gateway is deployed.

        **Note:** If you cannot find the VPC that you want to manage in the list, troubleshoot the issue by using the following methods:

        -   Check whether a VPC is created in the region that you selected.
        -   Check whether the VPC has a custom route entry whose destination CIDR block is 0.0.0.0/0. If the custom route entry exists, delete the custom route entry.
        -   If your account is a RAM user, check whether the RAM user is authorized to access the VPC. If the RAM user is unauthorized to access the VPC, contact the owner of the Alibaba Cloud account to grant permissions to the RAM user.
    -   **VSwitch ID**: Select the vSwitch to which the NAT gateway is attached.
    -   **Gateway Type**: By default, **Enhanced** is selected.

        Enhanced NAT gateways are an upgrade from standard NAT gateways and use a more advanced architecture. Compared with standard NAT gateways, enhanced NAT gateways provide higher elasticity and stability. This helps you manage data transfer in a more efficient manner.

    -   **Billing Method**: Select a billing method for the NAT gateway.

        Only the pay-by-specification billing method is supported.

    -   **Billing Cycle**:displays the billing cycle of the NAT gateway.
5.  On the buy page, check the payment amount and click **Activate Now** to complete the payment.

    When **Order complete.** appears, the purchase is complete.


## Check the result

After you create a NAT gateway, you can view the NAT gateway on the **NAT Gateway** page.

**Related topics**  


[CreateNatGateway](/intl.en-US/API reference/NAT Gateway/CreateNatGateway.md)

