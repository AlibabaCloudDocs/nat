# Associate an EIP with a NAT gateway

A NAT gateway functions only when it is associated with an elastic IP address \(EIP\). This topic describes how to associate an EIP with a NAT gateway. After you create a NAT gateway, you can associate an EIP with the NAT gateway.

Before you associate an EIP with a NAT gateway, make sure that the following requirements are met:

-   You did not purchase NAT service plans before23:59 January 26, 2018.

    If you purchased a NAT service plan before 23:59 January 26, 2018, you can only associate static public IP addresses in the NAT service plan with the NAT gateway to enable Internet access. For more information about how to associate an EIP with a NAT gateway, see the [Why am I unable to associate an EIP with a NAT gateway in the NAT Gateway console]() section in the FAQ topic.

-   A NAT gateway and an EIP are created. For more information, see [Create a NAT gateway](/intl.en-US/User Guide/NAT Gateway Instance/Create a NAT gateway.md) and [Apply for new EIPs](/intl.en-US/User Guide/Create an EIP/Apply for new EIPs.md).

Each NAT gateway can be associated with up to 20 EIPs, among which a maximum of 10 EIPs billed on a pay-by-data-transfer basis can be associated. The bandwidth usage of each paid-by-data-transfer EIP cannot exceed 200 Mbit/s. You can request a quota increase on the quota management page in the console. For more information, see [Quota management](/intl.en-US/User Guide/Common Configurations/Quota management.md).

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top menu bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway with which you want to associate an EIP, and choose **![More](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8458039951/p103337.png)** \> **Bind Elastic IP Address** in the **Actions** column.

4.  In the Bind Elastic IP Address dialog box, set the following parameters, and click **OK**.

    |Parameter|Description|
    |---------|-----------|
    |**Select from the EIP list**|
    |**Usable EIP list**|Select the EIP that you want to associate with the NAT gateway.|
    |**VSwitch**|Select the VSwitch for which you want to add SNAT entries. The system automatically adds SNAT entries. This allows the resources that are connected to the VSwitch to access the Internet. You can skip this step and add SNAT entries manually after you associate an EIP with the NAT gateway. For more information, see [Create a SNAT entry](/intl.en-US/User Guide/SNAT/Create a SNAT entry.md).

**Note:** This parameter is available only when the NAT gateway is not associated with EIPs. |
    |**Purchase an EIP and associate it with a NAT gateway**|
    |**The number of EIPs**|The number of EIPs that you want to purchase. By default, you can purchase only one EIP. The system automatically creates a pay-by-data-transfer EIP and associates it with the NAT gateway. |


**Related topics**  


[AssociateEipAddress](/intl.en-US/API reference/EIP/AssociateEipAddress.md)

