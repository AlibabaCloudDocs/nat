---
keyword: [NAT gateway, enhanced, network address translation, Internet-facing services, Internet access]
---

# Use SNAT to enable Internet access

This topic describes how to configure Source Network Address Translation \(SNAT\) for a NAT gateway. SNAT allows Elastic Compute Service \(ECS\) instances to access the Internet when the ECS instances are not assigned static public IP addresses or elastic IP addresses \(EIPs\).

## Scenario

The following scenario is used as an example. A company creates a virtual private cloud \(VPC\) and a vSwitch on Alibaba Cloud. Multiple ECS instances are attached to the vSwitch. The ECS instances are not assigned static public IP addresses or EIPs. To meet business requirements, all ECS instances must access the Internet.

You can configure SNAT for a NAT gateway to allow all ECS instances in a VPC to access the Internet when the ECS instances are not assigned static public IP addresses or EIPs.

![Scenario](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7738039951/p149166.png)

## Prerequisites

-   An Alibaba Cloud account is created. For more information, see[create an Alibaba account](https://account.alibabacloud.com/register/intl_register.htm).
-   A VPC and a vSwitch are created. For more information, see [Create a VPC](/intl.en-US/VPCs and vSwitchs/Create a VPC.md).

## Procedure

![Procedure](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7738039951/p149588.png)

## Step 1: Create a NAT gateway

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  On the **NAT Gateway** page, click **Create NAT Gateway**.

3.  When you purchase an enhanced NAT gateway for the first time, you must create a service-linked role for NAT Gateway. At the bottom of the **NAT Gateway \(Pay-As-You-Go\)** page, click **Create** in the Notes on Creating Service-linked Roles section. After a service-linked role is created, you can purchase a NAT gateway.

4.  On the **NAT Gateway \(Pay-As-You-Go\)** page, set the following parameters and click **Buy Now**.

    -   **Region and Zone**: Select the region where you want to deploy the NAT gateway.
    -   **Zone**: Select the zone where you want to deploy the NAT gateway.
    -   **VPC ID**: Select the VPC where you want to deploy the NAT gateway. After you create a NAT gateway, you cannot change the VPC where the NAT gateway is deployed.

        **Note:** If you cannot find the VPC where you want to deploy the NAT gateway in the drop-down list, troubleshoot the issue in the following ways:

        -   Check whether a VPC is created in the selected region.
        -   Check whether the VPC has a custom route entry whose destination CIDR block is 0.0.0.0/0. If the custom route entry exists, delete the custom route entry.
        -   If your account is a RAM user, check whether the RAM user is authorized to access the VPC. If the RAM user is unauthorized to access the VPC, contact the owner of the Alibaba Cloud account that can grant permissions to the RAM user.
    -   **VSwitch ID**: Select the vSwitch to which the NAT gateway is attached.
    -   **Gateway Type**: By default, **Enhanced** is selected.

        Enhanced NAT gateways support the features of standard NAT gateways. Enhanced NAT gateways are an upgrade from standard NAT gateways and use a more advanced architecture. Compared with standard NAT gateways, enhanced NAT gateways provide higher elasticity and stability. This helps you manage data transfer in a more efficient manner.

    -   **Billing Method**: Select a billing method for the NAT gateway.

        Only pay-by-specification is supported. For more information, see [Pay-as-you-go](/intl.en-US/Pricing/Pay-as-you-go.md).

    -   **Billing Cycle**:displays the billing cycle of the NAT gateway.
5.  On the buy page, check the payment amount and click **Activate Now** to complete the payment.

    When **Order complete.** appears, the purchase is completed.


After you create a NAT gateway, you can view the NAT gateway on the **NAT Gateway** page.

## Step 2: Create and associate an EIP

A NAT gateway functions as expected only when you associate an EIP with the NAT gateway. After you create a NAT gateway, you can associate EIPs with the NAT gateway.

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to manage and click **Associate Now** in the **Elastic IP Address** column.

4.  In the Associate EIP dialog box, set the parameters and click **OK**. The following table describes the parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Resource Group**|Select the resource group of the EIP.|
    |**EIPs**|Select **Purchase EIPs** to purchase an EIP that you want to associate with the NAT gateway.The system automatically creates a pay-by-data-transfer EIP and associates the EIP with the NAT gateway. |

    After you associate an EIP with the NAT gateway, the EIP is displayed in the **Elastic IP Address** column.


## Step 3: Create a SNAT entry

SNAT allows ECS instances in a VPC to access the Internet through a NAT gateway when the ECS instances are not assigned static public IP addresses or EIPs.

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to manage and click **Configure SNAT** in the **Actions** column.

4.  On the **SNAT Management** tab, click **Create SNAT Entry**.

5.  On the **Create SNAT Entry** page, set the parameters that are described in the following table and click **Confirm**.

    |Parameter|Description|
    |:--------|:----------|
    |**SNAT Entry**|Specify whether you want to create a SNAT entry for an ECS instance or a vSwitch. **Specify VSwitch**: The ECS instances that are attached to the vSwitch use the specified EIP to access the Internet. This option is selected in this example.    -   **Select VSwitch**: Select a vSwitch from the drop-down list. If no vSwitch is available in the drop-down list, click **Create VSwitch** from the drop-down list. Then, you are redirected to the VPC console where you can create vSwitches.

**Note:** If you select multiple vSwitches, the system creates multiple SNAT entries that use the same EIP.

    -   **VSwitch CIDR Block**: displays the CIDR block of the vSwitch. |
    |**Select Public IP Address**|Select an EIP. The EIP is used to communicate with the Internet. You can select an EIP from the drop-down list. **Use One IP Address** is specified in this example. If no EIPs are available in the drop-down list, click **Purchase and Associate EIP** from the drop-down list to purchase an EIP.|
    |**Entry Name**|Enter a name for the SNAT entry. The name must be 2 to 128 characters in length, and can contain digits, underscores \(\_\), and hyphens \(-\). It must start with a letter. |


## Step 4: Test the connectivity

After you create a SNAT entry, you can test the network connectivity of the ECS instance. In this example, an ECS instance that runs a Linux operating system is used to test the network connectivity.

**Note:** Make sure that the security group rule of the ECS instance allows the ECS instance to access the Internet. For more information, see [Overview](/intl.en-US/Security/Security groups/Overview.md).

1.  Log on to the ECS instance that is attached to the vSwitch.

2.  Run the `ping` command to test the network connectivity.

    The test result shows that the ECS instance can access the Internet.

    ![Test the connectivity](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8738039951/p149291.png)


