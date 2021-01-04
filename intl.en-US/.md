# Manage NAT gateways

This topic describes how to create and delete enhanced NAT gateways, associate elastic IP addresses \(EIPs\) with NAT gateways, disassociate EIPs from NAT gateways, and add tags to NAT gateways.

## Associate an EIP with a NAT gateway

A NAT gateway functions as expected only when the NAT gateway is associated with an EIP. You can associate up to 20 EIPs with a NAT gateway. You can associate up to 10 pay-by-data-transfer EIPs with a NAT gateway. Each pay-by-data-transfer EIP supports the maximum bandwidth of 200 Mbit/s. You can submit a ticket to increase the quota. For more information, see [Quota management](/intl.en-US/User Guide/Common Configurations/Quota management.md).



-   A NAT gateway and an EIP are created. For more information, see [t2003027.md\#]() and [Apply for new EIPs](/intl.en-US/User Guide/Create an EIP/Apply for new EIPs.md).
-   You did not purchase NAT service plans before 23:59:00 \(UTC+8\) January 26, 2018.

    If you purchased a NAT service plan before 23:59:00 \(UTC+8\) January 26, 2018, you can only associate static public IP addresses in the NAT service plan with the NAT gateway to enable Internet access. For more information about how to associate an EIP with a NAT gateway, see [Why am I unable to associate an EIP with a NAT gateway in the NAT Gateway console?]()


1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to manage and click **Associate Now** in the **Elastic IP Address** column.

4.  In the Bind Elastic IP Address pane, configure the parameters that are described in the following table and click **OK**.

    |Parameter|Description|
    |---------|-----------|
    |**Resource Group**|Select the resource group of the EIP.|
    |**EIPs**|Select the EIP that you want to associate with the NAT gateway.    -   **Select an existing EIP**: Select an existing EIP from the drop-down list.
    -   **Purchase and Associate EIP**: The system automatically creates a pay-by-data-transfer EIP and associates the EIP with the NAT gateway. |

    After the NAT gateway is associated with an EIP, the EIP is displayed in the **Elastic IP Address** column.


## Disassociate an EIP from a NAT gateway

If you do not want the NAT gateway to communicate with the Internet, you can disassociate the EIP from the NAT gateway.

Make sure that the EIP is not used in SNAT or DNAT entries. If the EIP is used in a SNAT or DNAT entry, delete the SNAT or DNAT entry. For more information, see [Delete a SNAT entry](/intl.en-US/User Guide/SNAT/Delete a SNAT entry.md) and [Delete a DNAT entry](/intl.en-US/User Guide/DNAT/Delete a DNAT entry.md).

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to manage and click the EIP in the **Elastic IP Address** column.

4.  On the **Elastic IP Addresses** page, select the EIP that you want to disassociate from the NAT gateway and click **Unbind** in the **Actions** column.

5.  In the message that appears, click **OK**.


## Add tags to NAT gateways

If you have a large number of NAT gateways, it may be difficult to manage the NAT gateways. You can add tags to the NAT gateways and manage the NAT gateways in different groups. This allows you to search and filter NAT gateways by tag.

A tag is a label that you can add to an instance. Each tag consists of a key and a value. Before you add tags, take note of the following limits:

-   The key of each tag that is added to each NAT gateway must be unique.
-   When you create tags, you must add the tags to NAT gateways. Otherwise, the tags cannot be created.
-   Tag information is not shared across regions.

    For example, in the China \(Shanghai\) region, you cannot view tags of instances that are created in the China \(Hangzhou\) region.

-   You can modify the key and value of a tag, or remove a tag from a NAT gateway at any time. If you delete a NAT gateway, the tags that are added to the NAT gateway are deleted.
-   You can add up to 20 tags to each NAT gateway. You cannot increase the quota.

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway to which you want to add tags, move the pointer over the ![The Tag icon](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8508559951/p67422.png) icon in the **Tags** column, and then click **Add**.

4.  In the **Configure Tags** dialog box, configure the parameters that are described in the following table and click **OK**.

    |Parameter|Description|
    |---------|-----------|
    |**Tag Key**|The key of a tag. You can select or enter a tag key. The tag key must be 1 to 64 characters in length, and cannot start with `aliyun` or `acs:`. It cannot contain `http://` or `https://`. |
    |**Tag Value**|The value of a tag. You can select or enter a tag value. The tag value must be 1 to 128 characters in length, and cannot start with `aliyun` or `acs:`. It cannot contain `http://` or `https://`. |

5.  Go back to the **NAT Gateway** page and click **Filter by Tag**. In the **Filter by Tag** dialog box, you can filter NAT gateways based on tag keys and tag values.


## Modify a NAT gateway

You can modify the name and description of a NAT gateway.

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to manage and click **Manage** in the **Actions** column.

4.  On the **Basic Information** page, click **Edit** next to **Instance Name**. In the dialog box that appears, enter a new name for the NAT gateway and click **OK**.

    The name must be 2 to 128 characters in length, and can contain digits, periods \(.\), underscores \(\_\), and hyphens \(-\). It must start with a letter.

5.  Click **Edit** next to the description. In the dialog box that appears, enter a new description and click **OK**.

    The description must be 2 to 256 characters in length. It cannot start with `http://` or `https://`.


## Delete a NAT gateway

You can delete NAT gateways that are billed on a pay-as-you-go basis. You cannot delete subscription NAT gateways.

**Note:** In the NAT Gateway console, if **Deletion Protection** is enabled on the **Basic Information** page for a NAT gateway, the NAT gateway cannot be deleted. To delete the NAT gateway, disable **Deletion Protection** for the NAT gateway.

-   No EIP is associated with the NAT gateway. If an EIP is associated with the NAT gateway, disassociate the EIP from the NAT gateway. For more information, see [Disassociate EIPs from a NAT gateway](/intl.en-US/User Guide/NAT Gateway Instance/Manage EIPs/Disassociate EIPs from a NAT gateway.md).
-   The DNAT table is empty. If the DNAT table contains DNAT entries, delete the DNAT entries. For more information, see [Delete a DNAT entry](/intl.en-US/User Guide/DNAT/Delete a DNAT entry.md).
-   The SNAT table is empty. If the SNAT table contains SNAT entries, delete the SNAT entries. For more information, see [Delete a SNAT entry](/intl.en-US/User Guide/SNAT/Delete a SNAT entry.md).

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to delete and click **![More](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8458039951/p103337.png)** \> **Delete** in the **Actions** column.

4.  In the **Delete Gateway** dialog box, select **Delete \(Delete NAT gateway and resources\)** and click **OK**.


## References

-   Create a NAT gateway: [CreateNatGateway](/intl.en-US/API reference/NAT Gateway/CreateNatGateway.md).
-   Associate an EIP with a NAT gateway: [AssociateEipAddress](/intl.en-US/API reference/EIP/AssociateEipAddress.md).
-   Disassociate an EIP from a NAT gateway: [UnassociateEipAddress](/intl.en-US/API reference/EIP/UnassociateEipAddress.md).
-   Add tags to NAT gateways: [TagResources](/intl.en-US/API reference/Tags/TagResources.md).
-   Modify a NAT gateway: [ModifyNatGatewayAttribute](/intl.en-US/API reference/NAT Gateway/ModifyNatGatewayAttribute.md).
-   Delete a NAT gateway: [DeleteNatGateway](/intl.en-US/API reference/NAT Gateway/DeleteNatGateway.md).

