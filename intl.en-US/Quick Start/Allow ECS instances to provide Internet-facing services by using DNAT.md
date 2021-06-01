# Allow ECS instances to provide Internet-facing services by using DNAT

This topic describes how to configure Destination Network Address Translation \(DNAT\) for a NAT gateway. DNAT allows Elastic Compute Service \(ECS\) instances to provide Internet-facing services.

## Scenario

The following scenario is used as an example. A company creates an ECS instance on Alibaba Cloud and deploys applications on the ECS instance. The ECS instance is not assigned a static public IP address. In addition, no elastic IP address \(EIP\) is associated with the ECS instance. To meet business requirements, the company wants the applications to be accessible over the Internet.

To map EIPs that are associated with the NAT gateway to ECS instances in a virtual private cloud \(VPC\), you can configure DNAT for the NAT gateway. This way, the ECS instances can provide Internet-facing services.

![Scenario](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8458039951/p158127.png)

## Prerequisites

Before you start, make sure that the following requirements are met:

-   An Alibaba Cloud account is created. If you do not have an Alibaba Cloud account, click [create an Alibaba account](https://account.alibabacloud.com/register/intl_register.htm).
-   A virtual private cloud \(VPC\) and a vSwitch are created. For more information, see [Work with VPCs](/intl.en-US/VPCs and vSwitchs/Work with VPCs.md).
-   ECS instances are created and attached to the vSwitch. Applications are deployed on the ECS instances. For more information, see [Create an instance by using the wizard](/intl.en-US/Instance/Create an instance/Create an instance by using the wizard.md).

## Procedures

![Procedures](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8458039951/p158124.png)

## Step 1: Create a NAT gateway

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  On the **NAT Gateway** page, click **Create NAT Gateway**.

3.  The first time you purchase an enhanced NAT gateway, you must create a service-linked role for NAT Gateway. At the bottom of the **NAT Gateway \(Pay-As-You-Go\)** page, click **Create** in the Notes on Creating Service-linked Roles section. After the service-linked role is created, you can purchase a NAT gateway.

4.  On the **NAT Gateway \(Pay-As-You-Go\)** page, set the following parameters and click **Buy Now**:

    -   **Region and Zone**: Select the region where you want to deploy the NAT gateway.
    -   **Zone**: Select the zone where you want to deploy the NAT gateway.
    -   **VPC ID**: Select the VPC where you want to deploy the NAT gateway. After the NAT gateway is created, you cannot change the VPC where the NAT gateway is deployed.

        **Note:** If you cannot find the VPC where you want to deploy the NAT gateway in the drop-down list, troubleshoot the issue by using the following methods:

        -   Check whether a VPC is created in the selected region.
        -   Check whether the VPC has a custom route entry whose destination CIDR block is 0.0.0.0/0. If the custom route entry exists, delete the custom route entry.
        -   If your account is a Resource Access Management \(RAM\) user, check whether the RAM user is authorized to access the VPC. If the RAM user is unauthorized to access the VPC, contact the owner of the Alibaba Cloud account that can grant permissions to the RAM user.
    -   **VSwitch ID**: Select the vSwitch to which the NAT gateway is attached.
    -   **Gateway Type**: By default, **Enhanced** is selected.

        Enhanced NAT gateways support the features of standard NAT gateways. Enhanced NAT gateways use an upgraded architecture of standard NAT gateways. In addition, enhanced NAT gateways offer higher elasticity and stability. This simplifies the management of data transfer over the Internet.

    -   **Billing Method**: Select a billing method for the NAT gateway.

        Only the pay-by-data-transfer billing method is supported. For more information, see [Pay-by-data-transfer](/intl.en-US/Pricing/Pay-as-you-go.md).

    -   **Billing Cycle**:displays the billing cycle of the NAT gateway.
5.  On the buy page, check the payment amount and click **Activate Now** to complete the payment.

    When **Order complete.** appears, the purchase is completed.


After you create a NAT gateway, you can find the NAT gateway on the **NAT Gateway** page.

## Step 2: Create an EIP and associate it with a NAT gateway

A NAT gateway works as expected only after you associate an EIP with the NAT gateway. After you create a NAT gateway, you can associate EIPs with the NAT gateway.

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to manage and click **Associate Now** in the **Elastic IP Address** column.

4.  In the Associate EIP dialog box, set the following parameters and click **OK**.

    |Parameter|Description|
    |---------|-----------|
    |**Resource Group**|Select the resource group to which the EIP belongs.|
    |**EIPs**|Select the EIP that you want to associate with the NAT gateway. **Purchase EIPs** is selected in this example. The system automatically creates a pay-by-data-transfer EIP and associates the EIP with the NAT gateway. |

    After you associate an EIP with the NAT gateway, the EIP is displayed in the **Elastic IP Address** column.


## Step 3: Create DNAT entries

A DNAT entry maps the EIP of a NAT gateway to an ECS instance. This allows the ECS instance to provide Internet-facing services.

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway and click **Configure DNAT** in the **Actions** column.

4.  On the **DNAT Management** tab, click **Create DNAT Entry**.

5.  On the **Create DNAT Entry** page, set the parameters that are described in the following table and click **Confirm**.

    |Parameter|Description|
    |---------|-----------|
    |**Select Public IP Address**|Select an EIP from the drop-down list. The EIP is used to communicate with the Internet. **Note:**

    -   For standard NAT gateways, you cannot specify an EIP in both a SNAT entry and a DNAT entry.
    -   For enhanced NAT gateways, you can specify an EIP in both a SNAT entry and a DNAT entry. |
    |**Select Private IP Address**|Select the ECS instance that uses the DNAT entry to receive requests from the Internet. You can use one of the following methods to specify the private IP address of the ECS instance that receives requests from the Internet:    -   **Select by ECS or ENI**: Select an ECS instance from the ECS instance list or elastic network interface \(ENI\) list.
    -   **Manual Input**: Enter the private IP address of the selected ECS instance. |
    |**Port Settings**|Select a DNAT mapping method:     -   **Any Port**: specifies IP mapping. Requests destined for the EIP are forwarded to the selected ECS instance.
    -   **Specific Port**: specifies port mapping. The NAT gateway forwards requests to the selected ECS instance based on the specified protocol and ports.
        -   **Public Port**: the external port that is used in port forwarding.
        -   **Private Port**: the internal port that is used in port forwarding.
        -   **Protocol Type**: the protocol used by the ports. |
    |**Entry Name**|Enter a name for the DNAT entry. The name must be 2 to 128 characters in length, and can contain digits, underscores \(\_\), and hyphens \(-\). It must start with a letter. |


## Step 4: Verify network connectivity

After you create a DNAT entry, you can verify the network connectivity by using a computer to access the application that runs on the ECS instance.

**Note:** Make sure that the security group rules of the ECS instance allow the ECS instance to receive requests from the Internet. For more information, see [Overview](/intl.en-US/Security/Security groups/Overview.md).

1.  Open a browser on a computer.

2.  Enter the EIP that is associated with the NAT gateway into the address bar of the browser and access the application that runs on the ECS instance.

    The test result shows that the ECS instance can receive requests from the Internet.

    ![Test result 1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8458039951/p143481.png)


