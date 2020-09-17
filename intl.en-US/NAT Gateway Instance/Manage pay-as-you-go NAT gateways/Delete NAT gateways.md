# Delete NAT gateways

This topic describes how to delete Network Address Translation \(NAT\) gateways.

Before you delete a NAT gateway, make sure that the following requirements are met:

-   The NAT gateway is not associated with an elastic IP address \(EIP\). If the NAT gateway is associated with an EIP, disassociate the EIP. For more information, see [Disassociate EIPs from a NAT gateway](/intl.en-US/NAT Gateway Instance/Manage EIPs/Disassociate EIPs from a NAT gateway.md).
-   The Destination Network Address Translation \(DNAT\) table is empty. If the DNAT table contains DNAT entries, delete these entries. For more information, see [Delete a DNAT entry](/intl.en-US/DNAT/Delete a DNAT entry.md).
-   The Source Network Address Translation \(SNAT\) table is empty. If the SNAT table contains SNAT entries, delete these entries. For more information, see [Delete a SNAT entry](/intl.en-US/SNAT/Delete an SNAT entry.md).

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to delete, and then choose **![More](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/8458039951/p103337.png)** \> **Delete** in the **Actions** column.

4.  In the Delete Gateway dialog box, click **OK**.

    **Note:** If you select **Delete \(Delete NAT gateway and resources\)**, the DNAT and SNAT entries of the NAT gateway are automatically deleted. EIPs that are associated with the NAT gateway are disassociated.


**Related topics**  


[DeleteNatGateway](/intl.en-US/API reference/NAT Gateway/DeleteNatGateway.md)

