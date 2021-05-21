# Configure ECS instances that are assigned EIPs to use the same EIP to access the Internet

To better manage your workloads, you can configure Elastic Compute Service \(ECS\) instances in a virtual private cloud \(VPC\) to use the same elastic IP address \(EIP\) to access the Internet. This topic describes how to configure ECS instances that are assigned EIPs to use the same EIP to access the Internet.

## Prerequisites

Source Network Address Translation \(SNAT\) entries are configured for the VPC in which the ECS instances are assigned EIPs. For more information, see [Create a SNAT entry to access the Internet](/intl.en-US/User Guide/Create a SNAT entry to access the Internet.md).

## Background information

NAT gateways support the SNAT feature. SNAT enables ECS instances in a VPC to access the Internet when the ECS instances are not assigned public IP addresses. In a VPC, ECS instances that are assigned EIPs preferably use the EIPs to access the Internet. ECS instances that are not assigned EIPs access the Internet through the SNAT service provided by the NAT gateway. Consequently, the ECS instances in the VPC use different IP addresses to access the Internet, which complicates management operations.

![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1604651261/p49564.png)

You can configure ECS instances in the VPC to use the same EIP to access the Internet by attaching an elastic network interface \(ENI\) to the ECS instances.

In the following example, you can create an ENI for the ECS instance, attach the ENI to the ECS instance, and associate an EIP with the ENI. This way, the ECS instance uses the ENI to receive requests from the Internet and accesses the Internet through the NAT gateway.

![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5753651261/p49551.png)

## Step 1: Create an ENI

To create an ENI for an ECS instance, follow these steps:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  In the left-side navigation pane, click **Network and Security** \> **ENI**.
3.  Select the target region.

    **Note:** The ENI and the ECS instance must be in the same region.

4.  On the Network Interfaces page, click **Create ENI**.
5.  On the Create ENI page, configure the ENI according to the following information and click **OK**.
    -   **Network Interface Name**: Enter the name of the ENI.
    -   **VPC**: Select the VPC to which the ECS instance belongs.
    -   **VSwitch**: Select the VSwitch of the zone to which the ECS instance belongs.
    -   **Primary Private IP** \(optional\): Enter the primary private IPv4 address of the ENI. The IPv4 address must be an idle address in the CIDR block of the specified VSwitch. If you do not specify one, an idle private IPv4 address is automatically assigned to your ENI after the ENI is created.
    -   **Security Group**: Select a security group of the VPC.
    -   **Description** \(optional\): Enter a description for the ENI.

## Step 2: Associate the ENI with the ECS instance

To attach the ENI to the ECS instance, follow these steps:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  In the left-side navigation pane, click **Network and Security** \> **ENI**.
3.  Select the target region.
4.  On the Network Interfaces page, find the target ENI, and click **Bind to Instance** in the **Actions** column.
5.  In the displayed dialog box, select the ECS instance to attach and click **OK**.

## Step 3: Disassociate the EIP from the ECS instance

To disassociate the EIP from the ECS instance, follow these steps:

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com).
2.  In the left-side navigation pane, click **Elastic IP Addresses**.
3.  Select the region of the target EIP.
4.  On the Elastic IP Addresses page, find the target EIP and click **Unbind** in the **Actions** column.
5.  In the displayed dialog box, click **OK**.

## Step 4: Associate the EIP with the ENI

To associate the EIP with the ENI, follow these steps:

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com).
2.  In the left-side navigation pane, click **Elastic IP Addresses**.
3.  Select the region of the target EIP.
4.  On the Elastic IP Addresses page, find the target EIP and click **Bind** in the **Actions** column.
5.  On the Bind Elastic IP Address page, associate the EIP with the ENI according to the following information and click **OK**.
    -   **IP Address**: Displays the EIP.
    -   **Instance Type**: Select Secondary ENI.
    -   **Resource Group** \(optional\): Select the resource group to which the EIP belongs.
    -   **Mode** \(optional\): Select the NAT mode.
    -   **Secondary ENI**: Select the ENI to be associated.

## Step 5: Test the network connectivity

Follow these steps to test whether the ECS instance can be accessed from the Internet through the EIP associated with the ENI. In this tutorial, a Linux instance is accessed from a remote Linux client.

**Note:** The security group rules of the Linux instance must allow access from the SSH \(22\) port. For more information, see [Add security group rules](/intl.en-US/Security/Security groups/Add security group rules.md).

1.  Log on to the Linux client.
2.  Run the `ssh root@ public IP address` command and enter the logon password of the Linux instance to check if the remote access is successful.

    If Welcome to Alibaba Cl oud Elastic Compute Service! is displayed,it means that the connection has been established.

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/570109/156144625849595_en-US.png)


Follow these steps to test if the ECS instance can access the Internet through the SNAT function of NAT Gateway. In this tutorial, the public IP address used is checked.

1.  Log on to the ECS instance.
2.  Run the `curl https://myip.ipip.net` to view the public IP address.

    If the public IP address is the same as the IP address in the SNAT entry of the NAT Gateway, it means that the ECS instance accesses the Internet through the SNAT function of NAT Gateway.

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/570109/156144625849596_en-US.png)


