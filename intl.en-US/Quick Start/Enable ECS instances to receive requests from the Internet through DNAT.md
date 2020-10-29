# Enable ECS instances to receive requests from the Internet through DNAT

This topic describes how to configure Destination Network Address Translation \(DNAT\) for a NAT gateway. DNAT enables Elastic Compute Service \(ECS\) instances to receive requests from the Internet.

## Scenario

The following scenario is used as an example. For example, a company creates an ECS instance on Alibaba Cloud, and runs website applications on the ECS instance. The ECS instance is not assigned a static public IP address or associated with an elastic IP address \(EIP\). To meet business requirements, the company requires website applications that run on the ECS instance to be accessed over the Internet.

You can configure DNAT for a NAT gateway to map EIPs to ECS instances in a virtual private cloud \(VPC\). This way, the ECS instances can receive requests from the Internet.

![Scenario](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/8458039951/p158127.png)

## Prerequisites

Make sure that the following requirements are met:

-   An Alibaba Cloud account is created. If you do not have an Alibaba Cloud account,[create an Alibaba Cloud account](https://account.alibabacloud.com/register/intl_register.htm).
-   A VPC and a VSwitch are created. For more information, see [Create a VPC](/intl.en-US/VPCs and VSwitches/VPC management/Create a VPC.md).
-   A website application is deployed on an ECS instance that is attached to the VSwitch. For more information, see [Create an instance by using the wizard](/intl.en-US/Instance/Create an instance/Create an instance by using the wizard.md).
-   An EIP is created in the region where the NAT gateway to be associated with the EIP is deployed. For more information, see [Apply for new EIPs](/intl.en-US/User Guide/Create an EIP/Apply for new EIPs.md).

## Prerequisites

![Procedure](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/8458039951/p158124.png)

## Step 1: Create a NAT gateway

NAT gateways are enterprise-class gateways that provide address translation services for Internet access. You must create a NAT gateway before you can create DNAT entries.

Perform the following steps to create a NAT gateway:

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  On the **NAT Gateway** page, click **Create NAT Gateway**.

3.  On the **NAT Gateway** page, set the following parameters, click **Buy Now**, and complete the payment.

    -   **Region and Zone**: Select the region and zone where you want to deploy the NAT gateway.

        **Note:** Enhanced NAT gateways are available in all regions except Australia \(Sydney\).

    -   **VPC ID**: Select the VPC in which the NAT gateway is created. After the NAT gateway is created, you cannot change the VPC in which the NAT gateway is deployed.

        **Note:** If you cannot find the VPC that you want to manage in the list, perform the following operations:

        -   Check whether the VPC is already associated with a NAT gateway. Each VPC can be associated with only one standard NAT gateway.
        -   Check whether the VPC has a custom route entry with the destination CIDR block set to 0.0.0.0/0. If such a custom route entry exists, delete it.
        -   If your account is a Resource Access Management \(RAM\) user, check whether the RAM user is authorized to access the VPC. If the RAM user is unauthorized, contact the owner of the Alibaba Cloud account that created the RAM user to grant permissions.
    -   **Zone**: Select the zone to which the NAT gateway belongs.
    -   **VSwitch ID**: Select the VSwitch to which the NAT gateway is attached.

        **Note:** This parameter is available only when you create an enhanced NAT gateway.

    -   **NAT Type**: Select the type of the NAT gateway that you want to create.

        -   **Standard**
        -   **Enhanced**
        Enhanced NAT gateways support all features of standard NAT gateways. Enhanced NAT gateways are upgraded from the technical architecture of standard NAT gateways. Compared with standard NAT gateways, enhanced NAT gateways offer higher elasticity and stability. This enables you to manage data transfer in a more efficient way. **Enhanced** is selected in this topic.

    -   **Specification**: Specify the size of the NAT gateway.

        -   **Small**
        -   **Medium**
        -   **Large**
        -   **Super Large-1**
        The size of a NAT gateway determines its SNAT performance, including the maximum number of concurrent connections and the number of new connections per second. However, the size does not affect the DNAT performance. For more information, see [Sizes of NAT gateways]().

        **Small** is selected in this topic.

    -   **Billing Method**: Select a billing method.

        Only pay-by-specification is supported. For more information, see [Pay-by-specification](/intl.en-US/Pricing/Pay-as-you-go.md).

    -   **Billing Cycle**:displays the billing cycle of the NAT gateway.

After you create a NAT gateway, you can view the NAT gateway on the **NAT Gateway** page.

![Create a NAT gateway](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/8458039951/p149224.png)

## Step 2: Associate the NAT gateway with an EIP

A NAT gateway functions as expected only after it is associated with an EIP. After you create a NAT gateway, you can associate it with an EIP.

Perform the following steps to associate the NAT gateway with an EIP:

1.  On the **NAT Gateway** page, find the NAT gateway created in Step 1, and choose **![More](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/8458039951/p103337.png)** \> **Bind Elastic IP Address** in the **Actions** column.

2.  In the Bind Elastic IP Address dialog box, set the following parameters, and click **OK**.

    -   **Usable EIP List**: Select the EIP that you want to associate with the NAT gateway.
    -   **VSwitch**: Select the VSwitch for which you want to add SNAT entries.

        The system automatically adds SNAT entries for the VSwitch so that Alibaba Cloud services attached to the VSwitch can access the Internet. You can also skip this step and manually add SNAT entries after you associate an EIP with the NAT gateway.

        No VSwitch is selected in this topic.

        **Note:** This parameter is available only for NAT gateways that are not associated with EIPs.


## Step 3: Create a DNAT entry

A DNAT entry maps an EIP to an ECS instance so that the ECS instance can receive requests from the Internet.

Perform the following steps to create a DNAT entry:

1.  On the **NAT Gateway** page, find the NAT gateway created in Step 1, and click **Configure DNAT** in the **Actions** column.

2.  In the **DNAT Entry List** section, click **Create DNAT Entry**.

3.  In the **Create DNAT Entry** dialog box, set the following parameters:

    -   **Public IP Address**: Select an EIP. The EIP is used to access the Internet.

        **Note:**

        -   For standard NAT gateways, you cannot specify a public IP address in both SNAT and DNAT entries.
        -   For enhanced NAT gateways, you can specify a public IP address in both SNAT and DNAT entries. If you want to use enhanced NAT gateways,[submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex).
    -   **Private IP Address**: Specify the private IP address of the ECS instance that needs to receive requests from the Internet through DNAT.

        You can specify the private IP address of the ECS instance that receives requests from the Internet in the following ways:

        -   **Auto Fill**: Select an ECS instance from the ECS instance list or Elastic Network Interface \(ENI\) list.
        -   **Manually Input**: Enter the private IP address of the ECS instance.

            **Note:** The CIDR block of the private IP address must be within that of the VPC. You can also enter the private IP address of your ECS instance.

        The ECS instance attached to the VSwitch is selected in this topic.

    -   **Port Settings**: Select a DNAT mapping method.

        -   **All**: This method uses IP mapping. All requests destined for the EIP are forwarded to the selected ECS instance.
        -   **Specific Port**: This method uses port mapping. The NAT gateway forwards requests from the specified protocol and port to the specified port of the selected ECS instance.

            If you select port mapping, you need to specify the following parameters based on your business requirements:

            -   **Public Port**: the external port where requests from the Internet are received.
            -   **Private Port**: the internal port to which the requests received on the external port are forwarded.
            -   **Protocol Type**: the protocol used by the ports.
        **All** is selected in this topic.

    -   **Entry Name**: Enter a name for the DNAT entry.

        The name must be 2 to 128 characters in length, and can contain digits, underscores \(\_\), and hyphens \(-\). It must start with a letter.

4.  Click **OK**.


## Step 4: Test the network connectivity

After you create a DNAT entry, you can test the network connectivity by using a computer to access the website application that runs on the ECS instance.

**Note:** Make sure that the security group rules of the ECS instance allow the ECS instance to receive requests from the Internet.

1.  Open a browser on the computer.

2.  Enter the EIP that is associated with the NAT gateway to access the website application that runs on the ECS instance.

    The test result shows that the ECS instance can receive requests from the Internet.

    ![Test result 1](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/8458039951/p143481.png)


