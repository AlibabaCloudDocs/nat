# Purchase a NAT gateway

This topic describes how to purchase a NAT gateway. An enhanced NAT gateway is used as an example in this topic.

## Prerequisites

A virtual private cloud \(VPC\) and a vSwitch are created. For more information, see [Create a VPC](/intl.en-US/VPCs and vSwitchs/Create a VPC.md).

## Authorize NAT Gateway to access other cloud resources

If this is the first time you create an enhanced NAT gateway, you must use your Alibaba Cloud account to assign the required Resource Access Management \(RAM\) role to NAT Gateway.

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  Go to the [Cloud Resource Access Authorization](https://ram.console.aliyun.com/role/authorization?request=%7B%22Services%22%3A%5B%7B%22Service%22%3A%22NAT%22%2C%22Roles%22%3A%5B%7B%22RoleName%22%3A%22AliyunNATAccessingNetworkInterfaceRole%22%2C%22TemplateId%22%3A%22ENIRole%22%7D%5D%7D%5D%2C%22ReturnUrl%22%3A%22https%3A%2F%2Fvpc.console.aliyun.com%2Fnat%22%7D) page.

3.  On the **Cloud Resource Access Authorization** page, click **Confirm Authorization Policy**.

    ![Authorize enhanced NAT gateways](../images/p188048.png)


## Create a NAT gateway

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  On the **NAT Gateway** page, click **Create NAT Gateway**.

3.  On the **NAT Gateway \(Pay-As-You-Go\)** page, set the following parameters and click **Buy Now**.

    -   **Region and Zone**: Select the region where you want to deploy the NAT gateway.
    -   **Zone**: Select the zone where you want to deploy the NAT gateway.
    -   **VPC ID**: Select the VPC where you want to deploy the NAT gateway. After the NAT gateway is created, you cannot change the VPC where the NAT gateway is deployed.

        **Note:** If you cannot find the VPC that you want to manage in the list, troubleshoot the issue in the following ways:

        -   Check whether a VPC is created in the selected region.
        -   Check whether the VPC has a custom route entry whose destination CIDR block is 0.0.0.0/0. If the custom route entry exists, delete the route entry.
        -   If your account is a RAM user, check whether the RAM user is authorized to access the VPC. If the RAM user is unauthorized to access the VPC, contact the owner of the Alibaba Cloud account that can grant permissions to the RAM user.
    -   **VSwitch ID**: Select the vSwitch to which the NAT gateway is attached.
    -   **Gateway Type**: By default, **Enhanced** is selected.

        Enhanced NAT gateways are upgraded from the technical architecture of standard NAT gateways. Compared with standard NAT gateways, enhanced NAT gateways offer higher elasticity and stability. This helps you manage data transfer in a more efficient manner.

    -   **Billing Method**
        -   **Pay by Data Transfer**: billed based on the actual data transfer. For more information, see [t16029.md\#section\_v5g\_sue\_5bj](/intl.en-US/Pricing/Pay-as-you-go.md).
        -   **Pay by Specification**: billed based on the size of the NAT gateway. You are charged a fixed fee for the NAT gateway after each billing cycle. If you select pay-by-specification, you must set the **Specification** parameter. For more information, see [Pay-by-specification](/intl.en-US/Pricing/Pay-as-you-go.md).
    -   **Billing Method**: Select a billing method for the NAT gateway.

        Only the pay-by-specification billing method is supported.

    -   **Billing Cycle**:displays the billing cycle of the NAT gateway.
4.  On the buy page, check the payment amount and click **Activate Now** to complete the payment.

    When **Order complete.** appears, the purchase is completed.


## Verify the result

After you create a NAT gateway, you can view the NAT gateway on the **NAT Gateway** page.

![Create a NAT gateway](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8458039951/p149224.png)

**Related topics**  


[CreateNatGateway](/intl.en-US/API reference/NAT Gateway/CreateNatGateway.md)

[Purchase a NAT gateway and EIPs as a service bundle]()

