# Create a SNAT IP address pool

This topic describes how to add multiple elastic IP addresses \(EIPs\) to a Source Network Address Translation \(SNAT\) IP address pool when you create a SNAT entry. After you create a SNAT IP address pool, Elastic Compute Service \(ECS\) instances in a virtual private cloud \(VPC\) can access the Internet by using the EIPs in the SNAT IP address pool.

## Prerequisites

-   A VPC and a vSwitch are created. For more information, see [Create a VPC and a vSwitch](/intl.en-US/Quick Start/Create an IPv4 VPC.md).
-   The EIPs that you want to add to the SNAT IP address pool are created. For more information, see [Apply for new EIPs](/intl.en-US/User Guide/Create an EIP/Apply for new EIPs.md).

## Background information

NAT gateways are enterprise-class gateways that support the SNAT feature. SNAT allows ECS instances in a VPC to access the Internet when no public IP address is associated with the ECS instances. If you configure only one EIP for the specified vSwitch or ECS instance when you create a SNAT entry, the EIP may be unable to withstand traffic spikes if the ECS instance is overloaded.

You can add multiple EIPs to a SNAT IP address pool. When an ECS instance in a VPC requires Internet access, the ECS instance randomly selects an EIP from the SNAT IP address pool.

![SNAT IP address pool](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/217943/156375765647136_en-US.png)

## Step 1: Create a NAT gateway

To create a NAT gateway, perform the following operations:

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).
2.  On the NAT Gateway page, click **Create NAT Gateway**.
3.  On the **NAT Gateway \(Pay-As-You-Go\)** page, configure the NAT gateway and complete the payment.
    -   **Region and Zone**: Select the region where you want to deploy the NAT gateway.
    -   **Zone**: Select the zone where you want to deploy the NAT gateway.
    -   **VPC ID**: Select the VPC where you want to deploy the NAT gateway. After you create a NAT gateway, you cannot change the VPC where the NAT gateway is deployed.

        **Note:** If you cannot find the VPC where you want to deploy the NAT gateway in the drop-down list, troubleshoot the issue by using the following methods:

        -   Check whether a VPC is created in the selected region.
        -   Check whether the VPC has a custom route entry whose destination CIDR block is 0.0.0.0/0. If the custom route entry exists, delete the custom route entry.
        -   If your account is a Resource Access Management \(RAM\) user, check whether the RAM user is authorized to access the VPC. If the RAM user is unauthorized to access the VPC, contact the owner of the Alibaba Cloud account that can grant permissions to the RAM user.
    -   **VSwitch ID**: Select the vSwitch to which the NAT gateway is attached.
    -   **Gateway Type**: By default, **Enhanced** is selected.

        Enhanced NAT gateways support the features of standard NAT gateways. Enhanced NAT gateways use an upgraded architecture of standard NAT gateways. In addition, enhanced NAT gateways offer higher elasticity and stability. This simplifies the management of data transfer over the Internet.

    -   **Billing Method**: Select a billing method for the NAT gateway.

        Only pay-by-specification is supported. For more information, see [t16029.md\#section\_dzk\_6u6\_9e9](/intl.en-US/Pricing/Pay-as-you-go.md).

    -   **Billing Cycle**: displays the billing cycle of the NAT gateway.

## Step 2: Associate an EIP with the NAT gateway

To associate an EIP with the NAT gateway, perform the following operations:

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).
2.  In the top navigation bar, select the region where the NAT gateway is deployed.
3.  On the **NAT Gateway** page, find the NAT gateway that you want to manage and click **Associate Now** in the **Elastic IP Address** column.
4.  In the Associate EIP dialog box, set the following parameters and click **OK**:
    -   **Resource Group**: Select the resource group to which the EIP belongs.
    -   **EIPs**: **Purchase EIPs** is selected in this example. The system automatically creates a pay-by-data-transfer EIP and associates the EIP with the NAT gateway.
5.  Repeat the preceding steps to associate more EIPs with the NAT gateway.

## Step 3: Associate an EIP with an EIP bandwidth plan

To associate an EIP with an EIP bandwidth plan, perform the following operations:

1.  Log on to the [Elastic IP Addresses console](https://vpc.console.aliyun.com/eip).
2.  In the top navigation bar, select the region where the EIP is deployed.
3.  On the Elastic IP Addresses page, find the EIP that you want to manage and choose **![More](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1382169951/p143776.png)** \> **Add to Shared Bandwidth Plan** in the **Actions** column.
4.  Select the EIP bandwidth plan with which you want to associate the EIP, and click **OK**.

## Step 4: Create a SNAT entry

To create a SNAT entry and add multiple EIPs to the SNAT IP address pool, perform the following operations:

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).
2.  In the top navigation bar, select the region where the NAT gateway is deployed.
3.  On the NAT Gateway page, find the NAT gateway that you want to manage and click **Configure SNAT** in the **Actions** column.
4.  On the SNAT Management tab, click **Create SNAT Entry**.
5.  On the Create SNAT Entry page, set the following parameters and click **Confirm**:

    **Specify VSwitch**:

    -   **Select VSwitch**: Select a vSwitch in a VPC. ECS instances that are attached to the vSwitch can access the Internet by using the SNAT entry.
    -   **VSwitch CIDR Block**: The CIDR block of the vSwitch is displayed.
    -   **Select Public IP Address**: Select the EIP that is used to access the Internet.
        -   **Use One IP Address**: Select an EIP from the drop-down list. If no EIPs are available in the drop-down list, click **Purchase and Associate EIP** from the drop-down list. Then, purchase an EIP in the dialog box that appears.
        -   **Use Multiple IP Addresses**: If multiple EIPs are specified in a SNAT IP address pool, make sure that the specified EIPs are associated with the same EIP bandwidth plan. When an ECS instance in a VPC requires Internet access, an EIP in the SNAT address pool is randomly assigned to the ECS instance.
            -   **EIP Bandwidth Plan**: Select an EIP bandwidth plan from the drop-down list. If no EIP bandwidth plan is available in the drop-down list, click **Create EIP Bandwidth Plan** from the drop-down list. Then, purchase an EIP bandwidth plan on the buy page.
            -   **Public IP Address**: Select an EIP that is associated with the selected EIP bandwidth plan from the drop-down list.
    -   **Entry Name**: Enter a name for the SNAT entry.
    **Specify ECS Instance**:

    -   **Select ECS Instance**: Select an ECS instance in the VPC.
    -   **ECS CIDR Block**: The CIDR block of the ECS instance is displayed.
    -   **Select Public IP Address**: Select the EIP that is used to access the Internet.
        -   **Use One IP Address**: Select an EIP from the drop-down list. If no EIPs are available in the drop-down list, click **Purchase and Associate EIP** from the drop-down list. Then, purchase an EIP in the dialog box that appears.
        -   **Use Multiple IP Addresses**: If multiple EIPs are specified in a SNAT IP address pool, make sure that the specified EIPs are associated with the same EIP bandwidth plan. When an ECS instance in a VPC requires Internet access, an EIP in the SNAT address pool is randomly assigned to the ECS instance.
            -   **EIP Bandwidth Plan**: Select an EIP bandwidth plan from the drop-down list. If no EIP bandwidth plan is available in the drop-down list, click **Create EIP Bandwidth Plan** from the drop-down list. Then, purchase an EIP bandwidth plan on the buy page.
            -   **Public IP Address**: Select an EIP that is associated with the selected EIP bandwidth plan from the drop-down list.
    -   **Entry Name**: Enter a name for the SNAT entry.

## Step 5: Verify the network connectivity

Log on to the two ECS instances that have SNAT entries configured and view the source IP addresses of outbound packets.

![View the source IP addresses of outbound packets on ECS 1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/217943/156375765647157_en-US.png)

![View the source IP addresses of outbound packets on ECS 2](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/217943/156375765647158_en-US.png)

