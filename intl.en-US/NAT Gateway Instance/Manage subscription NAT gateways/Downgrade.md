# Downgrade

This topic describes how to downgrade the sizes of Network Address Translation \(NAT\) gateways.

NAT gateways are available in multiple sizes, including small, middle, large, and super large-1 sizes. The sizes of NAT gateways determine the maximum number of Source Network Address Translation \(SNAT\) connections and the number of new SNAT connections per second \(CPS\). However, Destination Network Address Translation \(DNAT\) is not affected by the sizes of NAT gateways. The following table lists the available sizes of NAT gateways.

|Size|Maximum number of SNAT connections|Number of new SNAT connections per second|
|:---|:---------------------------------|:----------------------------------------|
|Small|10,000|1,000|
|Medium|50,000|5,000|
|Large|200,000|10,000|
|Super large-1|1,000,000|50,000|

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the NAT Gateway page, find the NAT gateway that you want to manage, and choose **![More](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/8458039951/p103337.png)** \> **Downgrade** in the **Actions** column.

4.  On the **Downgrade** page, set the following parameters, click **Buy Now**, and then complete the payment.

    |Parameter|Description|
    |---------|-----------|
    |**Instance Type**|Select the size of the NAT gateway that you want to purchase.**Note:** You can only downgrade the sizes of NAT gateways. |
    |**Terms of Service**|Select **NAT Gateway \(Subscription\) Terms of Service**.|


**Related topics**  


[ModifyNatGatewaySpec](/intl.en-US/API reference/NAT Gateway/ModifyNatGatewaySpec.md)

