# Configure ECS instances that are associated with EIPs to use the same EIP to access the Internet

To better manage your workloads, you can configure Elastic Compute Service \(ECS\) instances in a virtual private cloud \(VPC\) to use the same elastic IP address \(EIP\) to access the Internet. This topic describes how to configure ECS instances that are associated with EIPs to use the same EIP to access the Internet.

## Prerequisites

Source Network Address Translation \(SNAT\) entries are configured for the VPC in which the ECS instances are deployed. For more information, see [Create a SNAT entry to access the Internet](/intl.en-US/User Guide/Create a SNAT entry to access the Internet.md).

## Background information

NAT gateways support the SNAT feature. SNAT enables ECS instances in a VPC to access the Internet when the ECS instances are not assigned public IP addresses. In a VPC, ECS instances with which EIPs are associated preferably use the EIPs to access the Internet. ECS instances that are not associated with EIPs access the Internet through the SNAT service provided by a NAT gateway. Consequently, the ECS instances in the VPC use different IP addresses to access the Internet, which complicates management operations.

![NAT gateway](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1604651261/p49564.png)

You can configure ECS instances in the VPC to use the same EIP to access the Internet by associating elastic network interfaces \(ENIs\) with the ECS instances.

In the following example, you can create an ENI for the ECS instance, associate the ENI with the ECS instance, and then associate an EIP with the ENI. This way, the ECS instance uses the ENI to receive requests from the Internet and accesses the Internet through the NAT gateway.

![NAT gateway 2](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5753651261/p49551.png)

## Step 1: Create an ENI

To create an ENI for the ECS instance, perform the following operations:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  In the left-side navigation pane, choose **Network & Security** \> **ENIs**.
3.  Select the region where you want to create the ENI.

    **Note:** The ENI and the ECS instance must belong to the same region.

4.  On the **Network Interfaces** page, click **Create ENI**.
5.  In the **Create ENI** dialog box, set the following parameters and click **OK**:
    -   **ENI Name**: Enter a name for the ENI.
    -   **VPC**: Select the VPC where the ECS instance is deployed.
    -   **VSwitch**: Select the vSwitch of the zone where the ECS instance is deployed.
    -   **Primary Private IP**: Optional. Enter the primary private IPv4 address of the ENI. The IPv4 address must be an idle IP address within the CIDR block of the vSwitch. If you do not specify an IPv4 address, an idle private IPv4 address is automatically assigned to the ENI after the ENI is created.
    -   **Secondary Private IP Addresses**: Optional. You can specify this parameter based on your business requirements.
    -   **Security Group**: Select a security group that is created for the selected VPC.
    -   **Description**: Optional. Enter a description for the ENI.
    -   **Resource Group**: Optional. Select the resource group of the ENI.
    -   **Tag**: Optional. Select or enter a tag key.

## Step 2: Associate the ENI with the ECS instance

To associate the ENI with the ECS instance, perform the following operations:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  In the left-side navigation pane, choose **Network & Security** \> **ENIs**.
3.  Select the region where the ENI is deployed.
4.  On the **Network Interfaces** page, find the ENI that you want to manage and click **Bind to Instance** in the **Actions** column.
5.  In the dialog box that appears, select the ECS instance with which you want to associate the ENI and click **OK**.

## Step 3: Disassociate the EIP from the ECS instance

To disassociate the EIP from the ECS instance, perform the following operations:

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com/).
2.  In the left-side navigation pane, click **Elastic IP Addresses**.
3.  Select the region where the EIP is created.
4.  On the **Elastic IP Addresses** page, find the EIP that you want to manage and click **Unbind** in the **Actions** column.
5.  In the message that appears, click **OK**.

## Step 4: Associate the EIP with the ENI

To associate the EIP with the ENI, perform the following operations:

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com/).
2.  In the left-side navigation pane, click **Elastic IP Addresses**.
3.  Select the region where the EIP is created.
4.  On the **Elastic IP Addresses** page, find the EIP that you want to associate and click **Bind Resources** in the **Actions** column.
5.  In the **Bind Elastic IP Address to Resources** dialog box, set the following parameters and click **OK**:
    -   **Instance Type**: Select a secondary ENI.
    -   **Resource Group**: Optional. Select the resource group to which the EIP belongs.
    -   **Binding Mode**: Optional. Select the mode in which you want to associate the EIP with the ENI.
    -   **Select an instance to bind**: Select the secondary ENI with which you want to associate the EIP.

## Step 5: Verify network connectivity

Perform the following operations to check whether the ECS instance can use the EIP that is associated with the ENI to receive requests from the Internet. In this example, an on-premises Linux machine is used to connect to an ECS instance that runs Linux.

**Note:** To connect to the ECS instance that runs Linux, you must add a rule to the security group to accept traffic received on Secure Shell \(SSH\) port 22. For more information, see [Add security group rules](/intl.en-US/Security/Security groups/Add security group rules.md).

1.  Log on to the on-premises Linux machine.
2.  Run the `ssh root @ public IP` command and enter the password of the ECS instance that runs Linux to check whether you can connect to the ECS instance from a remote device. If the following message appears, you are connected to the ECS instance.

    ```
    Welcome to Alibaba Cloud Elastic Compute Service!
    ```

    ![ECS instance 1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4360712261/p267346.png)


Perform the following operations to check whether an ECS instance can access the Internet through the SNAT service provided by the NAT gateway. In this example, the public IP address of an ECS instance that runs Linux is checked.

1.  Log on to the ECS instance.
2.  Run the `curl https://myip.ipip.net` command to check the public IP address that the ECS instance uses to access the Internet. If the public IP address is the EIP in the SNAT entry that is created for the ECS instance, it indicates that the ECS instance preferably uses the EIP to access the Internet.

    ![ECS instance 2](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4360712261/p267347.png)


