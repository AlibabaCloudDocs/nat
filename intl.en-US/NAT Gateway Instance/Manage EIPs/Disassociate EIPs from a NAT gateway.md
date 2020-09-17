# Disassociate EIPs from a NAT gateway

This topic describes how to disassociate elastic IP addresses \(EIPs\) from a Network Address Translation \(NAT\) gateway.

Before you disassociate an EIP from a NAT gateway, make sure that the EIP is not used in any Source Network Address Translation \(SNAT\) or Destination Network Address Translation \(DNAT\) entries. If the EIP is used in a SNAT or DNAT entry, delete the SNAT or DNAT entry. For more information, see [Delete a SNAT entry](/intl.en-US/SNAT/Delete an SNAT entry.md) and [Delete a DNAT entry](/intl.en-US/DNAT/Delete a DNAT entry.md).

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway from which you want to disassociate EIPs, and choose **![More](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/8458039951/p103337.png)** \> **Unbind Elastic IP Address** in the **Actions** column.

4.  In the Unbind Elastic IP Address dialog box, select the EIP that you want to disassociate, and click **OK**.


**Related topics**  


[UnassociateEipAddress](/intl.en-US/API reference/EIP/UnassociateEipAddress.md)

