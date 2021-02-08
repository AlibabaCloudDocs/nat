---
keyword: [NAT gateway, enhanced, network address translation, Internet-facing services, access the Internet]
---

# Use SNAT to allow access to the Internet

This topic describes how to configure Source Network Address Translation \(SNAT\) for a NAT gateway. SNAT allows Elastic Compute Service \(ECS\) instances to access the Internet when the ECS instances are not assigned static public IP addresses or elastic IP addresses \(EIPs\).

## Scenario

The following scenario is used as an example. A company creates a virtual private cloud \(VPC\) and a vSwitch on Alibaba Cloud. Multiple ECS instances are attached to the vSwitch. The ECS instances are not assigned static public IP addresses or EIPs. To meet business requirements, the ECS instances must have access to the Internet.

You can configure SNAT for a NAT gateway to allow all ECS instances in a VPC to access the Internet when the ECS instances are not assigned static public IP addresses or EIPs.

![Scenario](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7738039951/p149166.png)

## Prerequisites

-   An Alibaba Cloud account is created. For more information, see [create an Alibaba account](https://account.alibabacloud.com/register/intl_register.htm).
-   A VPC and a vSwitch are created. For more information, see [Create a VPC](/intl.en-US/Build basic Virtual Private Cloud/VPCs and VSwitches/VPC management/Create a VPC.md).

## Procedure

![Procedure](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7738039951/p149588.png)

## Step 1: Authorize NAT Gateway to access cloud resources

If this is the first time you create an enhanced NAT gateway, you must use your Alibaba Cloud account to grant permissions to the Resource Access Management \(RAM\) role of NAT Gateway.

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  Go to the [Cloud Resource Access Authorization](https://ram.console.aliyun.com/role/authorization?request=%7B%22Services%22%3A%5B%7B%22Service%22%3A%22NAT%22%2C%22Roles%22%3A%5B%7B%22RoleName%22%3A%22AliyunNATAccessingNetworkInterfaceRole%22%2C%22TemplateId%22%3A%22ENIRole%22%7D%5D%7D%5D%2C%22ReturnUrl%22%3A%22https%3A%2F%2Fvpc.console.aliyun.com%2Fnat%22%7D) page.

3.  On the **Cloud Resource Access Authorization** page, click **Confirm Authorization Policy**.

    ![Authorize enhanced NAT gateways](../images/p188048.png)


## Step 2: Create a NAT gateway

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  On the **NAT Gateway** page, click **Create NAT Gateway**.

3.  On the **NAT Gateway \(Pay-As-You-Go\)** page, set the following parameters and click **Buy Now**.

    -   **Region and Zone**: Select the region where you want to deploy the NAT gateway.
    -   **Zone**: Select the zone where you want to deploy the NAT gateway.
    -   **VPC ID**: Select the VPC where you want to deploy the NAT gateway. After you create a NAT gateway, you cannot change the VPC where the NAT gateway is deployed.

        **Note:** If you cannot find the VPC that you want to manage in the list, troubleshoot the issue in the following ways:

        -   Check whether a VPC is created in the selected region.
        -   Check whether the VPC has a custom route entry whose destination CIDR block is 0.0.0.0/0. If the custom route entry exists, delete the custom route entry.
        -   If your account is a RAM user, check whether the RAM user is authorized to access the VPC. If the RAM user is unauthorized to access the VPC, contact the owner of the Alibaba Cloud account that can grant permissions to the RAM user.
    -   **VSwitch ID**: Select the vSwitch to which the NAT gateway is attached.
    -   **Gateway Type**: By default, **Enhanced** is selected.

        Enhanced NAT gateways support the features of standard NAT gateways. Enhanced NAT gateways are an upgrade from standard NAT gateways and use a more advanced architecture. Compared with standard NAT gateways, enhanced NAT gateways provide higher elasticity and stability. This helps you manage data transfer in a more efficient manner.

    -   **Billing Method**
        -   **Pay by Data Transfer**: billed based on the actual data transfer. For more information, see [t16029.md\#section\_v5g\_sue\_5bj](/intl.en-US/Pricing/Pay-as-you-go.md).
        -   **Pay by Specification**: billed based on the size of the NAT gateway. You are charged a fixed fee for the NAT gateway after each billing cycle. If you select pay-by-specification, you must set the **Specification** parameter.

            The size of a NAT gateway limits the SNAT performance, which includes the maximum number of concurrent connections and the number of new connections per second. However, the size of a NAT gateway does not affect the DNAT performance. For more information, see [Sizes of NAT gateways]().

    -   **Billing Method**: Select a billing method for the NAT gateway.

        Only pay-by-specification is supported. For more information, see [t16029.md\#section\_dzk\_6u6\_9e9](/intl.en-US/Pricing/Pay-as-you-go.md).

    -   **Billing Cycle**:displays the billing cycle of the NAT gateway.
4.  On the buy page, check the payment amount and click **Activate Now** to complete the payment.

    When **Order complete.** appears, the purchase is completed.


After you create a NAT gateway, you can view the NAT gateway on the **NAT Gateway** page.

![Create a NAT gateway](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8458039951/p149224.png)

## Step 3: Create and associate an EIP

A NAT gateway functions as expected only when you associate an EIP with the NAT gateway. After you create a NAT gateway, you can associate EIPs with the NAT gateway.

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to manage and click **Associate Now** in the **Elastic IP Address** column.

4.  In the Associate EIP dialog box, set the parameters that are described in the following table and click **OK**.

    |Parameter|Description|
    |---------|-----------|
    |**Resource Group**|Select the resource group of the EIP.|
    |**EIPs**|Select **Purchase EIPs** to purchase an EIP that you want to associate with the NAT gateway.The system automatically creates a pay-by-data-transfer EIP and associates the EIP with the NAT gateway. |

    After you associate an EIP with the NAT gateway, the EIP is displayed in the **Elastic IP Address** column.


## Step 4: Create a SNAT entry

SNAT allows ECS instances in a VPC to access the Internet through a NAT gateway when the ECS instances are not assigned static public IP addresses or EIPs.

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to manage and click **Configure SNAT** in the **Actions** column.

4.  On the **SNAT Management** tab, click **Create SNAT Entry**.

5.  On the **Create SNAT Entry** page, set the parameters that are described in the following table and click **Confirm**.

    |Parameter|Description|
    |:--------|:----------|
    |**SNAT Entry**|Specify whether you want to create a SNAT entry for an ECS instance or a vSwitch. **Specify VSwitch**: The ECS instances that are attached to the vSwitch use the specified EIP to access the Internet. This value is specified in this example.    -   **Select VSwitch**: Select a vSwitch from the drop-down list. If no vSwitch is available in the drop-down list, click **Create VSwitch** from the drop-down list. Then, you are redirected to the VPC console where you can create vSwitches.

**Note:** If you select multiple vSwitches, the system creates multiple SNAT entries that use the same EIP.

    -   **VSwitch CIDR Block**: displays the CIDR block of the vSwitch. |
    |**Select Public IP Address**|Select an EIP. The EIP is used to allow access to the Internet. **Use One IP Address**: Select an EIP from the drop-down list. This value is specified in this example.|
    |**Entry Name**|Enter a name for the SNAT entry. The name must be 2 to 128 characters in length, and can contain letters, digits, periods \(.\), underscores \(\_\), and hyphens \(-\). The name must start with a letter. |


## Step 5: Test the connectivity

After you create a SNAT entry, you can test the network connectivity between the ECS instance and the Internet. In this example, an ECS instance that runs a Linux operating system is used to test the network connectivity.

**Note:** Make sure that the security group rule of the ECS instance allows the ECS instance to access the Internet. For more information, see [Overview](/intl.en-US/Security/Security groups/Overview.md).

1.  Log on to the ECS instance that is attached to the vSwitch.

2.  Run the `ping` command to test the network connectivity.

    The test result shows that the ECS instance can access the Internet.

    ![Test the connectivity](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8738039951/p149291.png)


