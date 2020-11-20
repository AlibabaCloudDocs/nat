# Upgrade or downgrade a NAT gateway

This topic describes how to upgrade or downgrade a NAT gateway. You can change the size of a NAT gateway without affecting the workloads.

NAT gateways are available in multiple sizes, including small, middle, large, and super large-1. The size of a NAT gateway determines the maximum number of Source Network Address Translation \(SNAT\) connections and the number of new SNAT connections per second \(CPS\). However, Destination Network Address Translation \(DNAT\) is not affected by the sizes of NAT gateways. The following table lists the available sizes of NAT gateways.

|Type|Maximum number of SNAT connections|Number of new SNAT connections per second|
|:---|:---------------------------------|:----------------------------------------|
|Small|10,000|1,000|
|Middle|50,000|5,000|
|Large|200,000|10,000|
|Super Large-1|1,000,000|50,000|

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top menu bar, select the region where the NAT gateway is deployed.

3.  On the NAT Gateway page, find the NAT gateway that you want to manage, and choose **![More](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8458039951/p103337.png)** \> **Upgrade/Downgrade** in the **Actions** column.

4.  On the **Upgrade/Downgrade** page, set the following parameters to change the size of the NAT gateway, click **Buy Now**, and then complete the payment.

    |Parameter|Description|
    |---------|-----------|
    |**Specification**|Select the size of the NAT gateway.**Note:** You can upgrade or downgrade the size of the NAT gateway. |
    |**Terms of Service**|Select **NAT Gateway \(Pay-As-You-Go\) Terms of Service**.|


**Related topics**  


[ModifyNatGatewaySpec](/intl.en-US/API reference/NAT Gateway/ModifyNatGatewaySpec.md)

