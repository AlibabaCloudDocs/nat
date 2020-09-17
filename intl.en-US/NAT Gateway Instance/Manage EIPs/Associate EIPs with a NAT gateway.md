# Associate EIPs with a NAT gateway

To enable Network Address Translation \(NAT\) gateways to access the Internet, you must associate public IP addresses with them. This topic describes how to associate EIPs with a NAT gateway. After you create a NAT gateway, you can associate it with one or more elastic IP addresses \(EIPs\).

Before you associate EIPs with a NAT gateway, make sure that the following requirements are met:

-   No NAT service plan was created before 23:59 January 26, 2018.

    If you have purchased a NAT service plan for a NAT gateway before 23:59 January 26, 2018, you must associate static public IP addresses in the NAT service plan with the NAT gateway to enable Internet access. For more information about how to associate EIPs with a NAT gateway, see the [Why am I unable to associate an EIP with a NAT gateway in the NAT Gateway console](/intl.en-US/FAQ/EIP association FAQ.md) section in the FAQ topic.

-   A NAT gateway and an EIP are created. For more information, see [Create a NAT gateway]() and [Apply for new EIPs](/intl.en-US/User Guide/Create an EIP/Apply for new EIPs.md).

Each NAT gateway can be associated with up to 20 EIPs, among which a maximum of 10 EIPs billed on a pay-by-data-transfer basis can be associated. The bandwidth usage of each paid-by-data-transfer EIP cannot exceed 200 Mbit/s. You can request a quota increase on the quota management page in the console. For more information, see [Manage quotas](/intl.en-US/Common Configurations/Manage quotas.md).

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway with which you want to associate EIPs, and choose **![More](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/8458039951/p103337.png)** \> **Bind Elastic IP Address** in the **Actions** column.

4.  In the Bind Elastic IP Address dialog box, set the following parameters, and then click **OK**.

    |Parameter|Description|
    |---------|-----------|
    |**Select from the EIP list**|
    |**Usable EIP list**|Select the EIP to be associated with the NAT gateway.|
    |**VSwitch**|Select the VSwitch for which you want to add Source Network Address Translation \(SNAT\) entries. The system automatically adds SNAT entries so that the resources that are connected to this VSwitch can access the Internet. You can also skip this step and add SNAT entries after you associate an EIP with the NAT gateway. For more information, see [Create a SNAT entry]().

**Note:** This option is available only for NAT gateways that are not associated with EIPs. |
    |**Purchase an EIP and associate it with a NAT gateway**|
    |**The number of EIPs**|The number of EIPs that you want to purchase. By default, you can purchase only one EIP. The system automatically creates a pay-by-data-transfer EIP and associates it with the NAT gateway. |


**Related topics**  


[AssociateEipAddress](/intl.en-US/API reference/EIP/AssociateEipAddress.md)

