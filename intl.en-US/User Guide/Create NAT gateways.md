# Create NAT gateways

This topic describes how to create and delete enhanced NAT gateways, associate elastic IP addresses \(EIPs\) with NAT gateways, disassociate EIPs from NAT gateways, and add tags to NAT gateways.

## Prerequisites

A virtual private cloud \(VPC\) and a vSwitch are created. For more information, see [Create a VPC](/intl.en-US/VPCs and vSwitchs/Create a VPC.md).

## Create a NAT gateway

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  On the **NAT Gateway** page, click **Create NAT Gateway**.

3.  When you purchase a NAT gateway for the first time, you must create a service-linked role for NAT Gateway. In the lower part of the **NAT Gateway \(Pay-As-You-Go\)** page, click **Create** in the Notes on Creating Service-linked Roles section. After a service-linked role is created, you can purchase a NAT gateway.

    ![Create a role](../images/p225001.png)

4.  On the **NAT Gateway \(Pay-As-You-Go\)** page, set the following parameters and click **Buy Now**.

    -   **Region and Zone**: Select the region where you want to deploy the NAT gateway.
    -   **Zone**: Select the zone where you want to deploy the NAT gateway.
    -   **VPC ID**: Select the VPC where you want to deploy the NAT gateway. After you create a NAT gateway, you cannot change the VPC where the NAT gateway is deployed.

        **Note:** If you cannot find the VPC that you want to manage in the list, troubleshoot the issue in the following ways:

        -   Check whether a VPC is created in the selected region.
        -   Check whether the VPC has a custom route entry whose destination CIDR block is 0.0.0.0/0. If the custom route entry exists, delete the custom route entry.
        -   If your account is a RAM user, check whether the RAM user is authorized to access the VPC. If the RAM user is unauthorized to access the VPC, contact the owner of the Alibaba Cloud account that can grant permissions to the RAM user.
    -   **VSwitch ID**: Select the vSwitch to which the NAT gateway is attached.
    -   **Gateway Type**: By default, **Enhanced** is selected.

        Enhanced NAT gateways are upgraded from the technical architecture of standard NAT gateways. Compared with standard NAT gateways, enhanced NAT gateways offer higher elasticity and stability. This helps you manage data transfer in a more efficient manner.

    -   **Billing Method**: Select a billing method for the NAT gateway.

        Only the pay-by-specification billing method is supported.

    -   **Billing Cycle**:displays the billing cycle of the NAT gateway.
5.  On the buy page, check the payment amount and click **Activate Now** to complete the payment.

    When **Order complete.** appears, the purchase is complete.


## Associate an EIP with a NAT gateway

A NAT gateway functions as expected only after an EIP is associated with the NAT gateway. You can associate up to 20 EIPs with a NAT gateway.



-   A NAT gateway and an EIP are created. For more information, see [Purchase a NAT gateway](/intl.en-US/Pricing/Purchase a NAT gateway.md) and [Apply for new EIPs](/intl.en-US/User Guide/Create an EIP/Apply for new EIPs.md).
-   You did not purchase NAT service plans before23:59:00 \(UTC+8\) on January 26, 2018.

    If you purchased a NAT service plan before 23:59:00 \(UTC+8\) on January 26, 2018, you can associate only static public IP addresses in the NAT service plan with the NAT gateway to enable Internet access. For more information about how to associate an EIP with a NAT gateway, see [Why am I unable to associate an EIP with a NAT gateway in the NAT Gateway console?]()


1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is created.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to manage and click **Associate Now** in the **Elastic IP Address** column.

4.  In the Associate EIP dialog box, set the parameters and click **OK**.

    |Parameter|Description|
    |---------|-----------|
    |**Resource Group**|Select the resource group of the EIP.|
    |**EIPs**|Select the EIP that you want to associate with the NAT gateway.    -   **Select an existing EIP**: Select an existing EIP from the drop-down list.
    -   **Purchase and Associate EIP**: The system automatically creates an EIP that is billed on a pay-by-data-transfer basis and associates the EIP with the NAT gateway. |

    After you associate an EIP with the NAT gateway, the EIP appears in the **Elastic IP Address** column.


## Disassociate an EIP from a NAT gateway

If you do not want the NAT gateway to communicate with the Internet, you can disassociate the EIP from the NAT gateway.

The EIP is not used in SNAT or DNAT entries. If the EIP is used in a SNAT or DNAT entry, delete the SNAT or DNAT entry. For more information, see [Delete a SNAT entry](/intl.en-US/User Guide/Create a SNAT entry to access the Internet.md) and [Delete a DNAT entry](/intl.en-US/User Guide/Create a DNAT entry to provide Internet-facing services.md).

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is created.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to manage and click the EIP in the **Elastic IP Address** column.

4.  On the **Elastic IP Addresses** page, select the EIP that you want to disassociate from the NAT gateway and click **Disassociate** in the **Actions** column.

5.  In the message that appears, click **OK**.


## Add tags to NAT gateways

It is difficult to manage a large number of NAT gateways. To manage your NAT gateways by group, you can add tags to them. After you add tags, you can search and filter your NAT gateways by tag.

A tag is a label that you can add to an instance. Each tag consists of a key and a value. Before you add tags, take note of the following limits:

-   The key of each tag that is added to each NAT gateway must be unique.
-   You cannot create tags without adding them to NAT gateways. All tags must be added to NAT gateways.
-   Tag information is not shared across regions.

    For example, if you are in the China \(Shanghai\) region, you cannot view the tags of instances that are created in the China \(Hangzhou\) region.

-   You can modify the key and value of a tag or remove a tag from a NAT gateway at any time. If you delete a NAT gateway, the tags that are added to the NAT gateway are deleted.
-   You can add up to 20 tags to each NAT gateway. You cannot increase the quota.

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is created.

3.  On the **NAT Gateway** page, find the NAT gateway to which you want to add tags, move the pointer over the ![The Tag icon](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8508559951/p67422.png) icon in the **Tags** column, and then click **Add**.

4.  In the **Configure Tags** dialog box, set the following parameters and click **OK**.

    |Parameter|Description|
    |---------|-----------|
    |**Tag Key**|The key of a tag. You can select or enter a key. The key must be 1 to 64 characters in length, and cannot start with `aliyun` or `acs:`. It cannot contain `http://` or `https://`. |
    |**Tag Value**|The value of a tag. You can select or enter a value. The value must be 1 to 128 characters in length, and cannot start with `aliyun` or `acs:`. It cannot contain `http://` or `https://`. |

5.  Go back to the **NAT Gateway** page and click **Filter by Tag**. In the **Filter by Tag** dialog box, you can specify tag keys and values to filter NAT gateways.


## Modify a NAT gateway

You can modify the name and description of a NAT gateway.

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to manage and click **Manage** in the **Actions** column.

4.  On the **Basic Information** page, click **Edit** next to **Instance Name**. In the dialog box that appears, enter a name for the NAT gateway and click **OK**.

    The name must be 2 to 128 characters in length, and can contain digits, underscores \(\_\), and hyphens \(-\). It must start with a letter.

5.  Click **Edit** next to the description. In the dialog box that appears, enter a description and click **OK**.

    The description must be 2 to 256 characters in length. It cannot start with `http://` or `https://`.


## Delete a NAT gateway

You can delete NAT gateways that are billed on a pay-as-you-go basis. You cannot delete subscription NAT gateways.

**Note:** On the **Basic Information** page for the NAT gateway, if **Deletion Protection** is enabled for the NAT gateway, the NAT gateway cannot be deleted. To delete the NAT gateway, disable **Deletion Protection** first.

-   No EIP is associated with the NAT gateway. If an EIP is associated with the NAT gateway, disassociate the EIP from the NAT gateway. For more information, see [Disassociate EIPs from a NAT gateway]().
-   The DNAT table is empty. If the DNAT table contains DNAT entries, delete the DNAT entries. For more information, see [Delete a DNAT entry](/intl.en-US/User Guide/Create a DNAT entry to provide Internet-facing services.md).
-   The SNAT table is empty. If the SNAT table contains SNAT entries, delete the SNAT entries. For more information, see [Delete a SNAT entry](/intl.en-US/User Guide/Create a SNAT entry to access the Internet.md).

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to delete and choose **![More](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8458039951/p103337.png)** \> **Delete** in the **Actions** column.

4.  In the **Delete Gateway** dialog box, select **Delete \(Delete NAT gateway and resources\)** and click **OK**.


## References

-   Create a NAT gateway: [CreateNatGateway](/intl.en-US/API reference/NAT Gateway/CreateNatGateway.md).
-   Associate an EIP with a NAT gateway: [AssociateEipAddress](/intl.en-US/API reference/EIP/AssociateEipAddress.md).
-   Disassociate an EIP from a NAT gateway: [UnassociateEipAddress](/intl.en-US/API reference/EIP/UnassociateEipAddress.md).
-   Add tags to NAT gateways: [TagResources](/intl.en-US/API reference/Tags/TagResources.md).
-   Modify a NAT gateway: [ModifyNatGatewayAttribute](/intl.en-US/API reference/NAT Gateway/ModifyNatGatewayAttribute.md).
-   Delete a NAT gateway: [DeleteNatGateway](/intl.en-US/API reference/NAT Gateway/DeleteNatGateway.md).

