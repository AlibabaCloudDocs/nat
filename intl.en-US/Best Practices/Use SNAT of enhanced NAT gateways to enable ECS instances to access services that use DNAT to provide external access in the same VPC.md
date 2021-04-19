---
keyword: [enhanced NAT gateway, Internet access]
---

# Use SNAT of enhanced NAT gateways to enable ECS instances to access services that use DNAT to provide external access in the same VPC

This topic describes how to use the Source Network Address Translation \(SNAT\) feature of enhanced NAT gateways to enable Elastic Compute Service \(ECS\) instances to access services that use Destination Network Address Translation \(DNAT\) to provide external access in the same virtual private cloud \(VPC\).

## Scenario

The following scenario is used as an example in this topic.

![Architecture diagram](../images/p184529.png)

A company creates a VPC and two vSwitches named VSW1 and VSW1 in the VPC in the China \(Shanghai\) region. The ECS instance that is connected to VSW1 needs to access the services deployed on the ECS instance that is connected to VSW2 over the Internet.

You can create two enhanced NAT gateways named NAT1 and NAT2 for the VPC that is deployed in the China \(Shanghai\) region. Then, configure SNAT entries on NAT1, configure DNAT entries on NAT2, and then configure route entries for both VSW1 and VSW2. This allows the ECS instance to access services that use DNAT to provide external access in the same VPC over the Internet.

## Prerequisites

Before you start, make sure that the following requirements are met:

-   An Alibaba Cloud account is created. If you do not have an Alibaba Cloud account,[create an Alibaba account](https://account.alibabacloud.com/register/intl_register.htm).
-   A VPC is created and two vSwitches named VSW1 and VSW1 are created in the VPC. For more information, see [Work with VPCs](/intl.en-US/VPCs and vSwitchs/Work with VPCs.md) and [Create a vSwitch](/intl.en-US/VPCs and vSwitchs/Work with vSwitches.md).
-   An ECS instance named ECS1 is connected to VSW1. Another ECS instance named ECS2 is connected to VSW1. Services are deployed on ECS2. For more information, see [Create an instance by using the wizard](/intl.en-US/Instance/Create an instance/Create an instance by using the wizard.md).
-   Two elastic IP addresses \(EIPs\) named EIP1 and EIP2 are created. For more information, see [Apply for new EIPs](/intl.en-US/User Guide/Create an EIP/Apply for new EIPs.md).

## Procedure

![Procedure](../images/p184940.png)

## Step 1: Create an enhanced NAT gateway

Similar to standard NAT gateways, enhanced NAT gateways provide network address translation services \(SNAT and DNAT\). You must create a NAT gateway before you can configure SNAT and DNAT entries.

To create two enhanced NAT gateways in the same VPC, perform the following steps:

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  On the **NAT Gateway** page, click **Create NAT Gateway**.

3.  On the **NAT Gateway \(Pay-As-You-Go\)** page, configure the NAT gateway based on the following information, click **Buy Now**, and then complete the payment.

    -   **Region and Zone**: Select the region where you want to deploy the NAT gateway.

        **China \(Shanghai\)** is selected in this example.

    -   **Gateway Type**: Select the type of NAT gateway that you want to create.

        **Enhanced** is selected in this example. Enhanced NAT gateways support all features of standard NAT gateways. Enhanced NAT gateways are an upgrade from standard NAT gateways and use a more advanced architecture. Compared with standard NAT gateways, enhanced NAT gateways provide higher elasticity and stability. This helps you manage data transfer in a more efficient manner. For more information, see [Types of NAT gateway]().

    -   **VPC ID**: Select the VPC where you want to deploy the NAT gateway. After the NAT gateway is created, you cannot change the VPC where the NAT gateway is deployed.
    -   **Zone**: Select the zone where you want to deploy the NAT gateway.
    -   **VSwitch ID**: Select the vSwitch to which the NAT gateway is attached.
    -   **Specification**: Specify the size of the NAT gateway.

        -   **Small**
        -   **Medium**
        -   **Large**
        -   **Super Large-1**
        The size of a NAT gateway limits the SNAT performance, which includes the maximum number of concurrent connections and the number of new connections per second. However, the gateway size does not affect the DNAT performance. For more information, see [Sizes of NAT gateways]().

        **Small** is selected in this example.

    -   **Billing Method**: Select a billing method for the NAT gateway.
        -   **Pay by Actual Usage**: You are charged based on the actual data transfer. Fees may vary in each billing cycle. For more information, see [t16029.md\#section\_v5g\_sue\_5bj](/intl.en-US/Pricing/Pay-as-you-go.md).
        -   **Pay by Specification**: You are charged based on the size of the NAT gateway. Fees for each billing cycle are fixed. For more information, see [t16029.md\#section\_dzk\_6u6\_9e9](/intl.en-US/Pricing/Pay-as-you-go.md).
    -   **Billing Cycle**: specifies the subscription duration of the NAT gateway.
4.  Repeat the preceding steps to create another enhanced NAT gateway in the same VPC and name the NAT gateway NAT2.


After the NAT gateways are created, you can view the **enhanced** NAT gateways on the **NAT Gateway** page.

![Create an enhanced NAT gateway](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2106657061/p184776.png)

## Step 2: Associate EIPs

You can associate EIPs with the NAT gateways. After you associate EIPs with the NAT gateways, you can use the EIPs to configure DNAT and SNAT entries.

To associate EIPs with the enhanced NAT gateways, perform the following steps:

1.  On the **NAT Gateway** page, find NAT1 that is created in Step 1. In the **Actions** column, choose **![More](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8458039951/p103337.png)** \> **Bind Elastic IP Address**.

2.  In the **Associate EIP** dialog box, set the following parameters and click **OK**:

    -   **Select Existing EIPs**: Select the EIP that you want to associate with the NAT gateway.

        In this example, EIP1 is selected.

    -   **VSwitch**: Select the vSwitch for which you want to add SNAT entries.

        The system automatically adds SNAT entries. This allows the resources that are connected to the vSwitch to access the Internet. You can skip this step and manually add SNAT entries after you associate an EIP with the NAT gateway. For more information, see [Create a SNAT entry to access the Internet](/intl.en-US/User Guide/Create a SNAT entry to access the Internet.md).

        **Note:** This parameter is available only when no EIPs are associated with the NAT gateway.

        No vSwitch is selected in this example.

3.  Repeat the preceding steps to associate EIP2 with NAT2 that is created in Step 1.


After you associate EIPs with NAT1 and NAT2, you can view the EIPs on the **NAT Gateway** page.

![Associate EIPs](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3106657061/p184781.png)

## Step 3: Create a SNAT entry on NAT1

NAT gateways support the SNAT feature. SNAT enables ECS instances in a VPC to access the Internet when the ECS instances are not assigned public IP addresses.

To create SNAT entries and enable the ECS instance that is connected to VSW1 to access the Internet, perform the following steps:

1.  On the **NAT Gateway** page, find NAT1 that is created in Step 1 and click **Configure SNAT** in the **Actions** column.

2.  On the **SNAT Management** tab, click **Create SNAT Entry**.

3.  On the **Create SNAT Entry** page, set the following parameters and click **Confirm**.

    |Parameter|Description|
    |:--------|:----------|
    |**SNAT Entry**|Specify whether you want to create a SNAT entry for an ECS instance or a vSwitch. **Specify VSwitch**: The ECS instances that are attached to the vSwitch use the specified EIP to access the Internet. This option is selected in this example.    -   **Select VSwitch**: Select a vSwitch from the drop-down list. If no vSwitch is available in the drop-down list, click **Create VSwitch** from the drop-down list. Then, you are redirected to the VPC console where you can create vSwitches. In this example, VSW1 is selected.

**Note:** If you select multiple vSwitches, the system creates multiple SNAT entries that use the same EIP.

    -   **VSwitch CIDR Block**: displays the CIDR block of the vSwitch. |
    |**Select Public IP Address**|Select an EIP. The EIP is used to communicate with the Internet. You can select an EIP from the drop-down list. **Use One IP Address** is specified in this example. If no EIPs are available in the drop-down list, click **Purchase and Associate EIP** from the drop-down list to purchase an EIP. In this example, EIP1 is selected.|
    |**Entry Name**|Enter a name for the SNAT entry. The name must be 2 to 128 characters in length, and can contain digits, underscores \(\_\), and hyphens \(-\). It must start with a letter. |


After a SNAT entry is created, you can view the SNAT entry that is in the **Available** state in the **Used in SNAT Entry** section.

![SNAT](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3106657061/p184786.png)

## Step 4: Create a DNAT entry on NAT2

NAT gateways support the DNAT feature. DNAT maps public IP addresses to ECS instances in a VPC. This way, the ECS instances can receive requests that are sent over the Internet.

To create a DNAT entry and map EIP2 to ECS2, perform the following steps:

1.  On the **NAT Gateway** page, find NAT2 that is created in Step 1 and click **Configure DNAT** in the **Actions** column.

2.  On the **DNAT Management** tab, click **Create DNAT Entry**.

3.  On the **Create DNAT Entry** page, set the following parameters and click **Confirm**.

    |Parameter|Description|
    |---------|-----------|
    |**Select Public IP Address**|Select an EIP from the drop-down list. The EIP is used to communicate with the Internet. In this example, EIP2 is selected.|
    |**Select Private IP Address**|Select the ECS instance that uses the DNAT entry to receive requests from the Internet. You can use the following methods to specify the private IP address of the ECS instance that receives requests from the Internet:    -   **Select by ECS or ENI**: Select an ECS instance from the ECS instance list or Elastic Network Interface \(ENI\) list.
    -   **Manual Input**: Enter the private IP address of the selected ECS instance.
ECS2 is selected in this example.|
    |**Port Settings**|Select a DNAT mapping method.    -   **Any Port**: This method uses IP mapping. Requests destined for the EIP are forwarded to the selected ECS instance.
    -   **Specific Port**: This method uses port mapping. The NAT gateway forwards requests from the specified port over the specified protocol to the specified port of the selected ECS instance.
        -   **Public Port**: the external port where requests from the Internet are received.
        -   **Private Port**: the internal port to which the requests received on the external port are forwarded.
        -   **Protocol Type**: the protocol used by the ports.
**Specific Port** is selected in this example. Then, set **Public Port** to 80, **Private Port** to 80, and **IP Protocol** to TCP. |
    |**Entry Name**|The name of the DNAT entry.The name must be 2 to 128 characters in length, and can contain digits, underscores \(\_\), and hyphens \(-\). It must start with a letter. |


After a DNAT entry is created, you can view the DNAT entry that is in the **Available** state in the **DNAT Entry List** section.

![DNAT](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3106657061/p184785.png)

## Step 5: Configure route entries for VSW1

Create a custom route table in the VPC, add a route entry to the custom route table, and then associate the custom route table with the vSwitch to manage data transfer on the vSwitch.

**Note:** All regions support custom route tables, except the China \(Beijing\), China \(Shenzhen\), and China \(Hangzhou\) regions.

To configure a route entry for VSW1, perform the following steps:

1.  Create a custom route table.

    1.  In the left-side navigation pane, click **Route Tables**.

    2.  On the **Route Tables** page, click **Create Route Table**.

    3.  On the **Create Route Table** page, set the following parameters and click **OK**:

        -   **Resource Group**: Select the resource group to which the route table belongs.
        -   **VPC**: Select the VPC to which the route table belongs.

            In this example, the VPC to which the enhanced NAT gateways belong is selected.

        -   **Name**: Enter a name for the route table.

            The name must be 2 to 128 characters in length, and can contain digits, underscores \(\_\), and hyphens \(-\). It must start with a letter.

            **VTB1** is entered in this example.

2.  Add a custom route entry to the custom route table named VTB1.

    1.  On the **Route Tables** page, find VTB1 and click its ID.

    2.  On the **Route Entry List** tab, click **Add Route Entry**.

    3.  In the **Add Route Entry** panel, set the following parameters and click **OK**:

        -   **Name**: Enter a name for the route entry.

            The name must be 2 to 128 characters in length, and can contain digits, underscores \(\_\), and hyphens \(-\). It must start with a letter.

            **Route1** is entered in this example.

        -   **Destination CIDR Block**: Enter the destination CIDR block of the route entry.

            **0.0.0.0/0** is entered in this example.

        -   **Next Hop Type**: Select the type of the next hop of the route entry.

            In this example, **NAT Gateway** is selected. Then, select NAT1 as the next hop of the route entry.

3.  Associate VTB1 with VSW1.

    1.  Click the **Associated VSwitch** tab and click **Associate VSwitch**.

    2.  In the **Associate VSwitch** panel, select the vSwitch that you want to manage and click **OK**.

        In this example, VSW1 is selected.


## Step 6: Configure route entries for VSW2

Create a custom route table in the VPC, add a route entry to the custom route table, and then associate the custom route table with the vSwitch to manage data transfer on the vSwitch.

**Note:** All regions support custom route tables, except the China \(Beijing\), China \(Shenzhen\), and China \(Hangzhou\) regions.

To configure a route entry for VSW2, perform the following steps:

1.  Create a custom route table.

    1.  In the left-side navigation pane, click **Route Tables**.

    2.  On the **Route Tables** page, click **Create Route Table**.

    3.  On the **Create Route Table** page, set the following parameters and click **OK**:

        -   **Resource Group**: Select the resource group to which the route table belongs.
        -   **VPC**: Select the VPC to which the route table belongs.

            In this example, the VPC to which the enhanced NAT gateways belong is selected.

        -   **Name**: Enter a name for the route table.

            The name must be 2 to 128 characters in length, and can contain digits, underscores \(\_\), and hyphens \(-\). It must start with a letter.

            **VTB2** is entered in this example.

2.  Add a custom route entry to the custom route table named VTB2.

    1.  On the **Route Tables** page, find VTB2 and click its ID.

    2.  On the **Route Entry List** tab, click **Add Route Entry**.

    3.  In the **Add Route Entry** panel, set the following parameters and click **OK**:

        -   **Name**: Enter a name for the route entry.

            The name must be 2 to 128 characters in length, and can contain digits, underscores \(\_\), and hyphens \(-\). It must start with a letter.

            **Route 2** is entered in this example.

        -   **Destination CIDR Block**: Enter the destination CIDR block of the route entry.

            **0.0.0.0/0** is entered in this example.

        -   **Next Hop Type**: Select the type of the next hop of the route entry.

            In this example, **NAT Gateway** is selected. Then, select NAT2 as the next hop of the route entry.

3.  Associate VTB2 with VSW2.

    1.  Click the **Associated VSwitch** tab and click **Associate VSwitch**.

    2.  In the **Associate VSwitch** panel, select the vSwitch that you want to manage and click **OK**.

        In this example, VSW2 is selected.


## Step 7: Check the connectivity

After route entries are configured, you can check whether ECS1 can access the services that are deployed on ECS2.

**Note:** Make sure that the security group rules of the ECS instances meet the following requirements:

-   The security group rules of ECS1 allow ECS1 to access the Internet.
-   The security group rules of ECS2 enable Internet access to the services that are deployed on ECS2.

For more information, see [Add security group rules](/intl.en-US/Security/Security groups/Add security group rules.md).

1.  Log on to ECS1.

2.  Run the curl http://<EIP2\> command to check whether ECS1 can access services that are deployed on ECS2.

    **Note:** EIP2 is associated with NAT2.

    The check result shows that ECS1 can access the services that are deployed on ECS2 over the Internet.

    ![Check the network connectivity](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3106657061/p184935.png)


