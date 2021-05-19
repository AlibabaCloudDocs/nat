---
keyword: [NAT gateway, share bandwidth, access the Internet]
---

# Enable multiple applications to share bandwidth \(console\)

This topic describes how to use a NAT gateway to enable multiple applications to share the bandwidth of an EIP bandwidth plan. This reduces the data egress costs.

## Scenario

The following scenario is used as an example in this topic. A company creates two Elastic Compute Service \(ECS\) instances \(ECS 1 and ECS 2\) and deploys an application on each ECS instance. You want the ECS instances to provide Internet-facing services. The service port is port 80. The amount of bandwidth required by the two ECS instances varies within a day:

-   The peak hours of ECS 1 range from 13:00:00 to 18:00:00. During this period of time, the bandwidth that is required by ECS 1 is 700 Mbit/s. During the remaining hours of the day, the bandwidth that is required by ECS 1 is 300 Mbit/s.
-   The peak hours of ECS 2 range from 19:00:00 to 23:00:00. During this period of time, the bandwidth that is required by ECS 2 is 700 Mbit/s. During the remaining hours of the day, the bandwidth that is required by ECS 2 is 300 Mbit/s.

If you want to separately purchase bandwidth for the ECS instances, you must purchase two bandwidth plans with a total bandwidth of 1,000 Mbit/s. However, the ECS instances cannot make full use of the bandwidth during off-peak hours. This causes bandwidth resource waste.

To resolve this problem, you can configure Destination Network Address Translation \(DNAT\) on your NAT gateway and purchase an EIP bandwidth plan.

-   DNAT maps elastic IP addresses \(EIPs\) to ECS instances in a virtual private cloud \(VPC\). Then, the ECS instances can receive requests from the Internet.
-   The EIP bandwidth plan can be shared among multiple applications to reduce the data egress costs.

![Scenario](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2248304061/p170562.png)

## Prerequisites

-   A VPC and a vSwitch are created. For more information, see [Work with VPCs](/intl.en-US/VPCs and vSwitchs/Work with VPCs.md).
-   ECS instances are created and attached to the vSwitch. Applications are deployed on the ECS instances. For more information, see [Create an instance by using the wizard](/intl.en-US/Instance/Create an instance/Create an instance by using the wizard.md).
-   Two EIPs are created for a NAT gateway. The EIPs must meet the following requirements:

    -   The EIPs and the NAT gateway that you want to associate with the EIPs must be in the same region.
    -   The EIPs are billed on a pay-as-you-go basis.
    For more information, see [Apply for new EIPs](/intl.en-US/User Guide/Create an EIP/Apply for new EIPs.md).


## Procedure

![Procedure](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2248304061/p170824.png)

## Step 1: Create a NAT gateway

NAT gateways are enterprise-class gateways that provide network address translation services for Internet access. You must create a NAT gateway before you can create DNAT entries.

To create a NAT gateway, perform the following operations:

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  On the **NAT Gateway** page, click **Create NAT Gateway**.

3.  On the **NAT Gateway \(Pay-As-You-Go\)** page, set the following parameters, click **Buy Now**, and then complete the payment:

    -   **Region and Zone**: Select the region where you want to deploy the NAT gateway.
    -   **Zone**: Select the zone where you want to deploy the NAT gateway.
    -   **VPC ID**: Select the VPC where you want to deploy the NAT gateway. After the NAT gateway is created, you cannot change the VPC where the NAT gateway is deployed.

        **Note:** If you cannot find the VPC that you want to manage in the list, troubleshoot the issue in the following ways:

        -   Check whether the VPC is associated with a NAT gateway. Each VPC can be associated with only one standard NAT gateway.
        -   Check whether the VPC has a custom route entry whose destination CIDR block is 0.0.0.0/0. If the custom route entry exists, delete the custom route entry.
        -   If your account is a Resource Access Management \(RAM\) user, check whether the RAM user is authorized to access the VPC. If the RAM user is unauthorized to access the VPC, contact the owner of the Alibaba Cloud account that can grant permissions to the RAM user.
    -   **VSwitch ID**: Select the vSwitch to which the NAT gateway is attached.

        **Note:** This parameter is available only when you create an enhanced NAT gateway.

    -   **Gateway Type**: Select the type of NAT gateway that you want to create. By default, **Enhanced** is selected.
    -   **Billing Method**: Select a billing method for the NAT gateway.
    -   **Billing Cycle**: displays the billing cycle of the NAT gateway.

After you create a NAT gateway, you can find the NAT gateway on the **NAT Gateway** page.

## Step 2: Associate EIPs with the NAT gateway

A NAT gateway functions as expected only after it is associated with one or more EIPs. After you create a NAT gateway, you can associate EIPs with the NAT gateway.

To associate EIPs with the NAT gateway, perform the following operations:

1.  On the **NAT Gateway** page, find the NAT gateway that is created in Step 1 and choose **![More](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1280730261/p103337.png)** \> **Bind Elastic IP Address** in the **Actions** column.

2.  In the Associate EIP dialog box, set the following parameters:

    -   **Resource Group**: Select the resource group to which the EIPs belong.
    -   **EIPs**: Select the EIPs that you want to associate with the NAT gateway.

        In this example, **Select Existing EIPs** is selected. Then, select the two EIPs that are described in the Prerequisites section. For more information, see [Prerequisites](#section_0zt_20r_jau).

3.  Click **OK**.


## Step 3: Create DNAT entries

A DNAT entry maps the EIP of a NAT gateway to an ECS instance. This allows the ECS instance to provide Internet-facing services.

To create DNAT entries for ECS 1 and ECS 2, perform the following operations:

1.  On the **NAT Gateway** page, find the NAT gateway that is created in Step 1 and click **Configure DNAT** in the **Actions** column.

2.  In the **DNAT Entry List** section, click **Create DNAT Entry**.

3.  On the **Create DNAT Entry** page, set the following parameters to create a DNAT entry for ECS 1:

    -   **Select Public IP Address**: Select the EIP that is used to communicate with the Internet.

        EIP 1 is selected in this example.

    -   **Select Private IP Address**: Specify the private IP address of the ECS instance. The ECS instance uses the private IP address to receive requests from the Internet through DNAT.

        You can use the following methods to specify the private IP address of the ECS instance that receives requests from the Internet:

        -   **Select by ECS or ENI**: Select an ECS instance from the ECS instance list or Elastic Network Interface \(ENI\) list.
        -   **Manual Input**: Enter the private IP address of the selected ECS instance.

            **Note:** The private IP address that you enter must be within the CIDR block of the VPC. You can also enter the private IP address of an existing ECS instance.

        ECS 1 that is attached to the vSwitch is selected in this example.

    -   **Port Settings**: Select a DNAT mapping method.

        -   **Any Port**: IP mapping. Requests that are destined for the EIP are forwarded to the selected ECS instance.
        -   **Specific Port**: port mapping. The NAT gateway forwards requests from the specified port over the specified protocol to the specified port of the selected ECS instance.

            After you specify a port, set the following parameters based on your business requirements:

            -   **Public Port**: the external port that is used in port forwarding.
            -   **Private Port**: the internal port that is used in port forwarding.
            -   **Protocol Type**: the protocol that is used by the ports.
        **Specific Port** is selected in this example. Then, set **Public Port** to 80, **Private Port** to 80, and **IP Protocol** to TCP.

    -   **Entry Name**: Enter a name for the DNAT entry.

        The name must be 2 to 128 characters in length, and can contain digits, underscores \(\_\), and hyphens \(-\). It must start with a letter.

        DNAT1 is entered in this example.

4.  Click **Confirm**.

5.  In the **DNAT Entry List** section, click **Create DNAT Entry** again.

6.  On the **Create DNAT Entry** page, set the following parameters to create a DNAT entry for ECS 2:

    -   **Select Public IP Address**: Select the EIP that is used to communicate with the Internet.

        EIP 2 is selected in this example.

    -   **Select Private IP Address**: Specify the private IP address of the ECS instance. The ECS instance uses the private IP address to receive requests from the Internet through DNAT.

        ECS 2 that is attached to the vSwitch is selected in this example.

    -   **Port Settings**: Select a DNAT mapping method.

        **Specific Port** is selected in this example. Then, set **Public Port** to 80, **Private Port** to 80, and **IP Protocol** to TCP.

    -   **Entry Name**: Enter a name for the DNAT entry.

        The name must be 2 to 128 characters in length, and can contain digits, underscores \(\_\), and hyphens \(-\). It must start with a letter.

        DNAT2 is entered in this example.

7.  Click **Confirm**.


The following table describes the details about the DNAT entries that are added for ECS 1 and ECS 2.

|Entry name|EIP|External port|Protocol|Private IP address|Internal port|
|----------|---|-------------|--------|------------------|-------------|
|DNAT1|EIP1|80|TCP|ECS1|80|
|DNAT2|EIP2|80|TCP|ECS2|80|

## Step 4: Create an EIP bandwidth plan

EIP bandwidth plans support bandwidth sharing and transfer on a regional scale. You can use EIP bandwidth plans to reduce bandwidth resource costs.

To create an EIP bandwidth plan, perform the following operations:

1.  Log on to the [EIP bandwidth plan console](https://vpc.console.aliyun.com/cbwp/cn-hangzhou/cbwps).

2.  On the **Internet Shared Bandwidth** page, click **Buy Internet Shared Bandwidth**.

3.  On the buy page, set the following parameters, click **Buy Now**, and then complete the payment:

    -   **Region**: Select the region where you want to create the EIP bandwidth plan.

        Make sure that the EIP bandwidth plan is created in the same region as the EIP that you want to associate with the EIP bandwidth plan.

    -   **ISP**: Select an Internet connection type for the EIP bandwidth plan.
        -   **BGP \(Multi-ISP\)**: If you select this option, you can associate only EIPs of BGP \(Multi-ISP\) with the EIP bandwidth plan.
        -   **BGP\(Multi-ISP\)\_PRO**: If you select this option, you can associate only EIPs of BGP \(Multi-ISP\) Pro with the EIP bandwidth plan.

            **Note:** Only the China \(Hong Kong\) region supports BGP \(Multi-ISP\) Pro.

            **BGP \(Multi-ISP\)** is selected in this example.

    -   **Billing Method**: Select a billing method for the EIP bandwidth plan.

        Only pay-by-data-transfer is supported. For more information, see [Billing](/intl.en-US/Pricing/Billing.md).

    -   **Bandwidth**: Specify the bandwidth limit of the EIP bandwidth plan.

        **1000Mbps** is selected in this example.

    -   **Name**: Enter a name for the EIP bandwidth plan.

        The name must be 2 to 128 characters in length, and can contain digits, underscores \(\_\), and hyphens \(-\). It must start with a letter.

    -   **Resource Group**: Select the resource group to which the EIP bandwidth plan belongs.
    -   **Purchase Quantity**: Specify the number of EIP bandwidth plans that you want to purchase.

        One EIP bandwidth plan is purchased in this example.


## Step 5: Associate EIPs with the EIP bandwidth plan

You can associate EIP 1 and EIP 2 with the EIP bandwidth plan that you created. After the EIPs are associated with the EIP bandwidth plan:

-   Services attached to the NAT gateway with which the EIPs are associated share the bandwidth of the EIP bandwidth plan.
-   The predefined bandwidth limits of the EIPs become invalid. The bandwidth limits of the EIPs equal the bandwidth limit of the associated EIP bandwidth plan.
-   The predefined billing methods of the EIPs become invalid. The EIPs function as public IP addresses. Data transfer and bandwidth usage are not charged for the EIPs.

To associate EIP 1 and EIP 2 with the EIP bandwidth plan, perform the following operations:

1.  On the **Internet Shared Bandwidth** page, find the EIP bandwidth plan that is created in Step 4 and click **AddIP** in the **Actions** column.

2.  In the **Add IP** panel, click **Select from EIP List**.Then, select the EIPs that you want to associate with the EIP bandwidth plan.

    EIP 1 and EIP 2 are selected in this example.

3.  Click **OK**.


## Step 6: Verify the network connectivity

You can verify the network connectivity by using a computer to access the applications that are deployed on ECS 1 and ECS 2.

**Note:** Make sure that the security group rules of the ECS instances allow the ECS instances to receive requests from the Internet.

1.  Open a browser on a computer that can access the Internet.

2.  Enter one of the EIPs that are associated with the NAT gateway into the address bar of the browser and access the application that runs on an ECS instance.

    The results indicate that you can access the applications that are deployed on ECS 1 and ECS 2 over the Internet. In addition, the ECS instances share the bandwidth of the EIP bandwidth plan and can handle traffic spikes.

    ![Access the application that runs on ECS 1](../images/p170793.png "Access the application that runs on ECS 1")

    ![Access the application that runs on ECS 2](../images/p170794.png "Access the application that runs on ECS 2")


