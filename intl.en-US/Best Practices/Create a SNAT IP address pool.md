# Create a SNAT IP address pool

This topic describes how to add multiple elastic IP addresses \(EIPs\) to a Source Network Address Translation \(SNAT\) IP address pool when you create a SNAT entry. After you create a SNAT IP address pool, Elastic Compute Service \(ECS\) instances in a virtual private cloud \(VPC\) can access the Internet by using the EIPs in the SNAT IP address pool.

## Prerequisites

-   A VPC and a VSwitch are created. For more information, see [t2435.md\#section\_ufw\_rhv\_rdb](/intl.en-US/VPCs and vSwitchs/Work with VPCs.md).
-   EIPs that you want to add to the SNAT IP address pool are created. For more information, see [Apply for new EIPs](/intl.en-US/User Guide/Create an EIP/Apply for new EIPs.md).

## Background information

NAT gateways are enterprise-class gateways that provide the SNAT feature for Internet access. SNAT allows ECS instances to access the Internet when the ECS instances are not assigned static public IP addresses or EIPs. If you configure only one EIP for the specified VSwitch or ECS instance when you create a SNAT entry, the EIP may be unable to support traffic spikes when the ECS instance is overloaded.

You can add multiple EIPs to a SNAT IP address pool. When an ECS instance in a VPC needs to access the Internet, it randomly selects an EIP from the SNAT IP address pool.

![SNAT IP address pool](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/217943/156375765647136_en-US.png)

## Step 1: Create a NAT gateway

Perform the following steps to create a NAT gateway:

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com/nat/).
2.  In the left-side navigation pane, click **NAT Gateway**.
3.  On the NAT Gateway page, click **Create NAT Gateway**.
4.  On the buy page, set the following parameters and complete the payment:
    -   **Region**: Select the region of the VPC in which you want to create the NAT gateway.
    -   **VPC ID**: Select the VPC in which you want to create the NAT gateway. After you create a NAT gateway, you cannot change the VPC for which the NAT gateway is created.

        **Note:** If you cannot find the VPC in which you want to create a NAT gateway, perform the following operations:

        -   Check whether the VPC is associated with a NAT gateway. Each VPC can be associated with only one NAT gateway.
        -   Check whether the VPC has a custom route entry whose destination CIDR block is 0.0.0.0/0. If the VPC has this custom route entry, delete the custom route entry.
    -   **Specification**: Specify the size of the NAT gateway. The size of a NAT gateway affects the SNAT performance, such as the maximum number of connections and the number of new connections per second. The data throughput is not affected.

        **Note:** The size of a NAT gateway does not limit the number of DNAT connections and the data throughput. For more information, see [Enhanced NAT gateways \(new\)](/intl.en-US/Enhanced NAT gateway/Enhanced NAT gateways (new).md).

    -   **Billing Cycle**: Specify the subscription period of the NAT gateway.

## Step 2: Associate an EIP with the NAT gateway

To associate an EIP with the NAT gateway, perform the following steps:

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com/nat/).
2.  In the left-side navigation pane, click **NAT Gateway**.
3.  Select the region where the NAT gateway is deployed.
4.  Find the NAT gateway you want to manage and click **More** \> **Bind Elastic IP Address** in the **Action** column.
5.  In the Bind Elastic IP Address dialog box, set the following parameters and click **OK**:

    -   **Select from EIP list**: Select an EIP from the list of available EIPs and associate the EIP with the NAT gateway.
    -   **Allocate and Bind EIP to NAT Gateway**: The system creates a pay-by-data-transfer EIP and associates the EIP with the NAT gateway.
    **Note:** You can associate up to 20 EIPs with a NAT gateway. You can associate up to 10 pay-by-data-transfer EIPs with a NAT gateway. Each pay-by-data-transfer EIP supports the maximum bandwidth of up to 200 Mbit/s. You can submit a ticket to increase the quota.

6.  Repeat the preceding steps to associate more EIPs with the NAT gateway.

## Step 3: Add an EIP to an EIP bandwidth plan

To add an EIP to an EIP bandwidth plan, perform the following steps:

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com/nat/).
2.  In the left-side navigation pane, click **Elastic IP Addresses**.
3.  Select the region where the EIP is created.
4.  On the Elastic IP Addresses page, find the EIP that you want to manage and choose **More** \> **Add to Shared Bandwidth Plan** in the **Actions** column.
5.  Select the EIP bandwidth plan to which you want to add the EIP, and then click **OK**.

## Step 4: Create a SNAT entry

Perform the following steps to create a SNAT entry and add multiple EIPs to the SNAT IP address pool:

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com/nat/).
2.  In the left-side navigation pane, click **NAT Gateway**.
3.  Select the region where the NAT gateway is deployed.
4.  On the NAT Gateway page, find the NAT gateway you want to manage, and click **Configure SNAT** in the **Actions** column.
5.  On the SNAT Table page, click **Create SNAT Entry**.
6.  In the Create SNAT Entry dialog box, set the following parameters, and click **OK**:

    **VSwitch Granularity**:

    -   **VSwitch**: Select a VSwitch in the VPC. ECS instances that are attached to the VSwitch can access the Internet by using the SNAT entry.
    -   **VSwitch CIDR Block**: The CIDR block of the VSwitch is displayed.
    -   **Public IP Address**: Select the EIP that is used to access the Internet. You can select multiple EIPs to create a SNAT IP address pool.
    -   **Entry Name**: Enter a name for the SNAT entry.
    **ECS Granularity**:

    -   **Available ECS Instances**: Select an ECS instance in the VPC.
    -   **ECS CIDR Block**: The CIDR block of the ECS instance is displayed.
    -   **Public IP Address**: Select the EIP that is used to access the Internet. You can select multiple EIPs to create a SNAT IP address pool.
    -   **Entry Name**: Enter a name for the SNAT entry.

## Step 5: Test whether the SNAT entry functions

Log on to two ECS instances that have SNAT entries configured and view the source IP addresses of the outbound packets.

![View the source IP address of ECS1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/217943/156375765647157_en-US.png)

![View the source IP address of the outbound packets from ECS2](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/217943/156375765647158_en-US.png)

