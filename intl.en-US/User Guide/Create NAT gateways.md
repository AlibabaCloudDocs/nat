# Create NAT gateways

This topic describes how to create enhanced NAT gateways, associate elastic IP addresses \(EIPs\) with NAT gateways, and add tags to NAT gateways. This topic also describes how to disassociate EIPs from NAT gateways and delete NAT gateways.

## Prerequisites

A virtual private cloud \(VPC\) and a vSwitch are created. For more information, see [Work with VPCs](/intl.en-US/VPCs and vSwitchs/Work with VPCs.md).

## Create a NAT gateway

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  On the **NAT Gateway** page, click **Create NAT Gateway**.

3.  If this is the first time you purchase a NAT gateway, you must create a service-linked role for NAT Gateway. In the lower part of the **NAT Gateway \(Pay-As-You-Go\)** page, click **Create** in the Notes on Creating Service-linked Roles section. After a service-linked role is created, you can purchase a NAT gateway.

4.  On the **NAT Gateway \(Pay-As-You-Go\)** page, set the following parameters and click **Buy Now**:

    -   **Region and Zone**: Select the region where you want to deploy the NAT gateway.
    -   **Zone**: Select the zone where you want to deploy the NAT gateway.
    -   **VPC ID**: Select the VPC where you want to deploy the NAT gateway. After you create a NAT gateway, you cannot change the VPC where the NAT gateway is deployed.

        **Note:** If you cannot find the VPC that you want to manage in the list, troubleshoot the issue by using the following methods:

        -   Check whether a VPC is created in the region that you selected.
        -   Check whether the VPC has a custom route entry whose destination CIDR block is 0.0.0.0/0. If the custom route entry exists, delete the custom route entry.
        -   If your account is a RAM user, check whether the RAM user is authorized to access the VPC. If the RAM user is unauthorized to access the VPC, contact the owner of the Alibaba Cloud account to grant permissions to the RAM user.
    -   **VSwitch ID**: Select the vSwitch to which the NAT gateway is attached.
    -   **Gateway Type**: By default, **Enhanced** is selected.

        Enhanced NAT gateways are an upgrade from standard NAT gateways and use a more advanced architecture. Compared with standard NAT gateways, enhanced NAT gateways provide higher elasticity and stability. This helps you manage data transfer in a more efficient manner.

    -   **Billing Method**: Select a billing method for the NAT gateway.

        Only **Pay By Actual Usage** is supported.

    -   **Billing Cycle**:displays the billing cycle of the NAT gateway.
5.  On the buy page, check the payment amount and click **Activate Now** to complete the payment.

    When **Order complete.** appears, the purchase is complete.


## Associate EIPs

A NAT gateway works as expected only after you associate an EIP with the NAT gateway. You can associate at most 20 EIPs with a NAT gateway. You can associate at most 10 pay-by-data-transfer EIPs with a NAT gateway. The bandwidth limit of the pay-by-data-transfer EIPs is 200 Mbit/s. You can submit a ticket to increase the quota. For more information, see [Quota management](/intl.en-US/Common Configurations/Quota management.md).



-   A NAT gateway and an EIP are created. For more information, see [Purchase a NAT gateway](/intl.en-US/Pricing/Purchase a NAT gateway.md) and [Apply for new EIPs](/intl.en-US/User Guide/Create an EIP/Apply for new EIPs.md).
-   You did not purchase NAT service plans before23:59 \(UTC+8\) on January 26, 2018.

    If you purchased a NAT service plan before 23:59 \(UTC+8\) on January 26, 2018, you can associate only public IP addresses in the NAT service plan with the NAT gateway to enable Internet access. For more information about how to associate an EIP with a NAT gateway, see [Why am I unable to associate elastic IP addresses \(EIPs\) with a NAT gateway in the Virtual Private Cloud \(VPC\) console?]().


1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to manage and click **Associate Now** in the **Elastic IP Address** column.

4.  In the Associate EIP dialog box, set the following parameters and click **OK**.

    |Parameter|Description|
    |---------|-----------|
    |**Resource Group**|Select the resource group to which the EIP belongs.|
    |**EIPs**|Select the EIP that you want to associate with the NAT gateway.     -   **Select Existing EIPs**: Select an existing EIP from the drop-down list.
    -   **Purchase EIPs**: The system automatically creates an EIP that is billed on a pay-by-data-transfer basis and associates the EIP with the NAT gateway. |

    After you associate an EIP with the NAT gateway, the EIP appears in the **Elastic IP Address** column.


## Disassociate EIPs

If you do not want a NAT gateway to communicate with the Internet, you can disassociate the EIP from the NAT gateway.

The EIP is not used in SNAT or DNAT entries. If the EIP is used in a SNAT or DNAT entry, delete the SNAT or DNAT entry. For more information, see [Delete a SNAT entry](/intl.en-US/User Guide/Create a SNAT entry to access the Internet.md) and [Delete a DNAT entry](/intl.en-US/User Guide/Create a DNAT entry to provide Internet-facing services.md).

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to manage and click the EIP in the **Elastic IP Address** column.

4.  On the **Associated EIP** tab, select the EIP that you want to disassociate from the NAT gateway and click **Disassociate** in the **Actions** column.

5.  In the message that appears, click **OK**.


## Modify a NAT gateway

You can modify the name and description of a NAT gateway.

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to manage and click **Manage** in the **Actions** column.

4.  On the **Basic Information** tab, click **Edit** next to **Instance Name**. In the dialog box that appears, enter a name for the NAT gateway and click **OK**.

    The name must be 2 to 128 characters in length, and can contain digits, periods \(.\), underscores \(\_\), and hyphens \(-\). It must start with a letter.

5.  Click **Edit** next to Description. In the dialog box that appears, enter a description and click **OK**.

    The description must be 2 to 256 characters in length. It cannot start with `http://` or `https://`.


## Delete a NAT gateway

You can delete NAT gateways that are billed on a pay-as-you-go basis. You cannot delete subscription NAT gateways.

**Note:** On the **Basic Information** tab, if **Deletion Protection** is enabled for the NAT gateway, the NAT gateway cannot be deleted. You must disable **Deletion Protection** before you can delete the NAT gateway.

-   No EIP is associated with the NAT gateway. If an EIP is associated with the NAT gateway, disassociate the EIP from the NAT gateway.
-   The DNAT table is empty. If the DNAT table contains DNAT entries, delete the DNAT entries. For more information, see [Delete a DNAT entry](/intl.en-US/User Guide/Create a DNAT entry to provide Internet-facing services.md).
-   The SNAT table is empty. If the SNAT table contains SNAT entries, delete the SNAT entries. For more information, see [Delete a SNAT entry](/intl.en-US/User Guide/Create a SNAT entry to access the Internet.md).

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to delete and choose **![More](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1280730261/p103337.png)** \> **Delete** in the **Actions** column.

4.  In the **Delete Gateway** dialog box, select **Delete \(Delete NAT gateway and resources\)** and click **OK**.


## References

-   Create a NAT gateway: [CreateNatGateway](/intl.en-US/API reference/NAT Gateway/CreateNatGateway.md).
-   Associate an EIP with a NAT gateway: [AssociateEipAddress](/intl.en-US/API reference/EIP/AssociateEipAddress.md).
-   Disassociate an EIP from a NAT gateway: [UnassociateEipAddress](/intl.en-US/API reference/EIP/UnassociateEipAddress.md).
-   Add tags to NAT gateways: [TagResources](/intl.en-US/API reference/Tags/TagResources.md).
-   Modify a NAT gateway: [ModifyNatGatewayAttribute](/intl.en-US/API reference/NAT Gateway/ModifyNatGatewayAttribute.md).
-   Delete a NAT gateway: [DeleteNatGateway](/intl.en-US/API reference/NAT Gateway/DeleteNatGateway.md).

