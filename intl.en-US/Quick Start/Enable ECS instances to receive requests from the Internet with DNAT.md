# Enable ECS instances to receive requests from the Internet with DNAT

This topic describes how to configure Destination Network Address Translation \(DNAT\) for a NAT gateway. DNAT allows Elastic Compute Service \(ECS\) instances to receive requests from the Internet.

## Scenario

The following scenario is used as an example. For example, a company creates an ECS instance on Alibaba Cloud, and runs website applications on the ECS instance that is not assigned a public IP address or associated with an elastic IP address \(EIP\). To meet business requirements, the company requires website applications that run on the ECS instance to be accessed over the Internet.

You can configure DNAT for a NAT gateway to map public IP addresses to ECS instances in a Virtual Private Cloud \(VPC\) network. This way, the ECS instances can receive requests from the Internet.

![Scenario](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/8458039951/p158127.png)

## Prerequisites

Before you start, make sure that the following requirements are met:

-   An Alibaba Cloud account is created. If you do not have an Alibaba Cloud account, click [Create an Alibaba Cloud account](https://account.alibabacloud.com/register/intl_register.htm).
-   A VPC network and a VSwitch are created. For more information, see [Create a VPC](/intl.en-US/VPCs and VSwitches/VPC management/Create a VPC.md).
-   A website application is deployed on an ECS instance that is attached to the VSwitch. For more information, see [Create an instance by using the provided wizard](/intl.en-US/Instance/Create an instance/Create an instance by using the provided wizard.md).
-   An EIP is created in the region where the NAT gateway to be associated with the EIP is deployed. For more information, see [Apply for new EIPs](/intl.en-US/User Guide/Create an EIP/Apply for new EIPs.md).

## Procedure

![Procedure](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/8458039951/p158124.png)

## Step 1: Create a NAT gateway

A NAT gateway is an enterprise-class gateway that provides address translation services for Internet access. You must create a NAT gateway before you create a DNAT entry.

Take the following steps to create a NAT gateway:

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  On the **NAT Gateway** page, click **Create NAT Gateway**.

3.  In the **Create NAT** dialog box, set the following parameters, click **Buy Now**, and complete the payment.

    -   **Billing Method**: Select a billing method.

        -   **Subscription**: The billing method requires you to pay subscription fees before you can use the service. For more information, see [t16028.md\#]().
        -   **Pay-As-You-Go**: The billing method requires you to pay fees based on the usage. For more information, see [Pay-as-you-go](/intl.en-US/Pricing/Pay-as-you-go.md).
        **Subscription** is selected in this topic.

    -   **Region and Zone**: Select the region and zone where you want to deploy the NAT gateway.

        **Note:** Enhanced NAT gateways are available in regions other than Australia \(Sydney\), US \(Silicon Valley\), UAE \(Dubai\), and Japan \(Tokyo\).

    -   **VPC ID**: Select the VPC network in which the NAT gateway is created. After the NAT gateway is created, you cannot change the VPC network where the NAT gateway is deployed.

        **Note:** If you cannot find the VPC network from the drop-down list, perform the following steps to resolve the problem:

        -   Check whether the VPC network is already associated with a NAT gateway. Each VPC network can be associated with only one NAT gateway.
        -   Check whether the VPC network has a custom route entry with the destination CIDR block set to 0.0.0.0/0. If such a custom route entry exists, delete it.
        -   If your account is a Resource Access Management \(RAM\) user account, check whether the RAM user account is authorized to access the VPC network. If the RAM user account is not authorized, contact the owner of the Alibaba Cloud account that creates the RAM user account to grant permissions.
    -   **VSwitch ID**: Select the VSwitch to which the NAT gateway is attached.

        **Note:** This parameter is available only when you create an enhanced NAT gateway.

    -   **NAT Type**: Select the type of the NAT gateway that you want to create.

        -   **Normal**
        -   **Enhanced**
        Enhanced NAT gateways support all features of standard NAT gateways. Compared with standard NAT gateways, enhanced NAT gateways use an upgraded technical architecture. This ensures higher elasticity and stability and helps you to better manage network traffic sent over the Internet. **Enhanced** is selected in this topic.

    -   **Name**: Enter a name for the NAT gateway.

        The name must be 2 to 128 characters in length, and can contain letters, Chinese characters, digits, underscores \(\_\), and hyphens \(-\). It must start with a letter or Chinese character.

    -   **Specification**: Select a specification for the NAT gateway.

        -   **Small**
        -   **Medium**
        -   **Large**
        -   **Super Large-1**
        The size of a NAT gateway determines its SNAT performance, including the maximum concurrent connections and the number of new connections per second. However, the size does not affect the DNAT performance. For more information, see [Compare NAT gateway sizes](/intl.en-US/NAT Gateway Instance/Types of NAT gateway.md).

        **Small** is selected in this topic.

    -   **Quantity**: Select the number of NAT gateways that you want to purchase.
    -   **Billing Cycle**: Specify the subscription duration.

After you create a NAT gateway, you can view the NAT gateway on the **NAT Gateway** page.

![Create a NAT gateway](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/8458039951/p149224.png)

## Step 2: Associate the NAT gateway with an EIP

A NAT gateway functions as expected only after it is associated with an EIP. After you create a NAT gateway, you can associate it with an EIP.

Take the following steps to associate the NAT gateway with an EIP:

1.  On the **NAT Gateway** page, find the NAT gateway created in Step 1, and choose **![More](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/8458039951/p103337.png)** \> **Bind Elastic IP Address** in the **Actions** column.

2.  In the Bind Elastic IP Address dialog box, set the following parameters, and click **OK**.

    -   **Usable EIP List**: Select the EIP to be associated with the NAT gateway.
    -   **VSwitch**: Select the VSwitch for which you want to add SNAT entries.

        The system automatically adds SNAT entries for the VSwitch so that Alibaba Cloud services connected to this VSwitch can access the Internet. You can also skip this step and manually add SNAT entries after you associate an EIP with the NAT gateway.

        No VSwitch is selected in this topic.

        **Note:** This parameter is available only for NAT gateways that are not associated with EIPs.


## Step 3: Create a DNAT entry

A DNAT entry maps a public IP address to an ECS instance so that the ECS instance can receive requests from the Internet.

Take the following steps to create a DNAT entry:

1.  On the **NAT Gateway** page, find the NAT gateway created in Step 1, and click **Configure DNAT** in the **Actions** column.

2.  In the **DNAT Entry List** section, click **Create DNAT Entry**.

3.  In the **Create DNAT Entry** dialog box, set the following parameters:

    -   **Public IP Address**: Select an EIP. The EIP is used to access the Internet.

        **Note:** If a public IP address is already used in a SNAT entry, it cannot be used in a DNAT entry.

    -   **Private IP Address**: Specify the private IP address of the ECS instance that needs to receive requests from the Internet with DNAT.

        You can specify the private IP address of the ECS instance that you want to manage in the following ways:

        -   **Auto Fill**: Select an ECS instance from the ECS instance or Elastic Network Interface \(ENI\) list.
        -   **Manually Input**: Enter the private IP address of the target ECS instance.

            **Note:** The CIDR block of the private IP address must be within that of the VPC network. You can also enter the private IP address of your ECS instance.

        The ECS instance attached to the VSwitch is selected in this topic.

    -   **Port Settings**: Select a DNAT mapping method.

        -   **All**: IP mapping. All requests destined for the public IP address are forwarded to the target ECS instance.
        -   **Specific Port**: port mapping. All requests received on a public port are forwarded to the specified internal port of the target ECS instance over the specified protocol.

            After you select Specific Port, specify the following parameters:

            -   **Public Port**: the external port where requests from the Internet are received.
            -   **Private Port**: the internal port to which the requests received on the external port are forwarded.
            -   **IP Protocol**: the protocol over which requests are forwarded.
        **All** is selected in this topic.

    -   **Entry Name**: Enter a name for the DNAT entry.

        The name must be 2 to 128 characters in length, and can contain digits, underscores \(\_\), and hyphens \(-\). It must start with a letter or Chinese character.

4.  Click **OK**.


## Step 4: Test the network connectivity

After you create a DNAT entry, you can verify the network connectivity by using a computer to access the website application that runs on the ECS instance.

**Note:** Make sure that the security group rules of the ECS instance allow the ECS instance to receive requests from the Internet.

1.  Open a browser on the computer.

2.  Enter the EIP that is associated with the NAT gateway to access the website application that runs on the ECS instance.

    The test result shows that the ECS instance can receive requests from the Internet.

    ![Test result 1](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/8458039951/p143481.png)


