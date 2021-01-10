---
keyword: [NAT gateway, Internet egress, network address translation, provide Internet-facing services, Internet access]
---

# Pay-as-you-go

You can purchase NAT gateways on a pay-as-you-go basis. If you want to create or delete NAT gateways based on your business requirements, you can purchase pay-as-you-go NAT gateways instead of subscription NAT gateways. This topic describes the billing rules of pay-as-you-go NAT gateways.

## Overview

The pay-as-you-go billing method requires you to pay for resources based on actual usage.

Pay-as-you-go NAT gateways provide the following features:

-   Pay-as-you-go NAT gateways are billed based on the billing cycle. Bills are generated and fees are deducted from your account after each billing cycle.
-   You can delete NAT gateways at any time. After you delete a NAT gateway, the NAT gateway is no longer billed. For more information, see [Delete a NAT gateway](/intl.en-US/User Guide/Manage NAT gateways.md).
-   The pay-as-you-go billing method supports the pay-by-specification metering method. The pay-by-specification metering method is used to meter and bill the usage of a NAT gateway based on the size of the gateway. You are charged a fixed fee for the NAT gateway after each billing cycle. For more information, see [Pay-by-specification](#section_dzk_6u6_9e9).

## Pay-by-specification

Fee of a pay-by-specification NAT gateway = Instance fee + Specification fee

-   Instance fee = Instance unit price × Usage duration
-   Specification fee = Specification unit price × Usage duration

**Note:** The unit price of a NAT gateway consists of the instance unit price \(50%\) and the specification unit price \(50%\).

The usage duration of a NAT gateway is calculated from the time when the gateway is created to the time when the NAT gateway is released. Standard NAT gateways and enhanced NAT gateways that use the pay-by-specification metering method have different billing cycles.

-   Standard NAT gateways that use the pay-by-specification metering method are charged daily. Bills are generated on a daily basis. If you use a standard NAT gateway for less than one day, the usage duration is rounded up to one day.
-   Enhanced NAT gateways that use the pay-by-specification metering method are charged hourly. Bills are generated on an hourly basis. If you use an enhanced NAT gateway for less than one hour, the usage duration is rounded up to one hour.

**Unit price**

NAT gateways are available in the following sizes: Small, Middle, Large, and Super Large-1. The size of a NAT gateway determines the SNAT performance, including the maximum number of concurrent connections and the number of new connections per second. However, the size of the NAT gateway does not affect the DNAT performance.

The size of a NAT gateway determines the unit price of a NAT gateway.The actual prices on the [buy page](https://common-buy-intl.alibabacloud.com/?&commodityCode=nat_gw_intl#/buy) shall prevail.

**Note:** If the prices in this table are different from those on the buy page,the actual prices on the [buy page](https://common-buy-intl.alibabacloud.com/?&commodityCode=nat_gw_intl#/buy) shall prevail.

You created a small enhanced NAT gateway in UK \(London\) at 08:10:00 \(UTC+8\) on October 18, 2020 and released the gateway at 11:50:00 \(UTC+8\) on October 18, 2020. In this case, the gateway uses the pay-by-specification metering method. You are charged for a usage duration of 4 hours. The total fee of the NAT gateway includes:

-   The fee that was charged for the usage from 08:10:00 \(UTC+8\) on October 18, 2020 to 09:00:00 \(UTC+8\) on October 18, 2020.
-   The fee that was charged for the usage from 09:00:00 \(UTC+8\) on October 18, 2020 to 10:00:00 \(UTC+8\) on October 18, 2020.
-   The fee that was charged for the usage from 10:00:00 \(UTC+8\) on October 18, 2020 to 11:00:00 \(UTC+8\) on October 18, 2020.
-   The fee that was charged for the usage from 11:00:00 \(UTC+8\) on October 18, 2020 to 12:00:00 \(UTC+8\) on October 18, 2020.

The total fee of the NAT gateway: 0.132 × 4 = USD 0.528.

## Billing after you upgrade or downgrade a NAT gateway

You can change the size of an enhanced NAT gateway that uses the pay-by-specification metering method. If you change the size of an enhanced NAT gateway within a billing cycle, you are charged based on the largest size that you specified for the enhanced NAT gateway.

For example, you created a Small-sized enhanced NAT gateway at 15:00:00 \(UTC+8\) on October 10, 2020. You changed the size of the enhanced NAT gateway to Middle at 16:30:00 \(UTC+8\) on October 10, 2020, and then you released the enhanced NAT gateway at 17:50:00 \(UTC+8\) on October 10, 2020. The total fee of the enhanced NAT gateway includes:

-   The fee that was charged for the usage of the Small-sized enhanced NAT gateway from 15:00:00 \(UTC+8\) on October 10, 2020 to 16:00:00 \(UTC+8\) on October 10, 2020.
-   The fee that was charged for the usage of the Middle-sized enhanced NAT gateway from 16:00:00 \(UTC+8\) on October 10, 2020 to 17:00:00 \(UTC+8\) on October 10, 2020.
-   The fee that was charged for the usage of the Middle-sized enhanced NAT gateway from 17:00:00 \(UTC+8\) on October 10, 2020 to 18:00:00 \(UTC+8\) on October 10, 2020.

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to manage and choose **![More](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8458039951/p103337.png)** \> **Upgrade** in the **Actions** column.

4.  On the **Upgrade** page, set the parameters and select the Terms of Service check box. Then, click **Buy Now** and complete the payment.


## Switch the billing method from pay-as-you-go to subscription

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the NAT Gateway page, find the NAT gateway that you want to manage and choose **![More](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8458039951/p103337.png)** \> **Convert To PrePay Mode** in the **Actions** column.

4.  On the Convert To PrePay Mode page, select the billing cycle of the NAT gateway and the Terms of Service check box. Then, click **Buy Now** and complete the payment.


## Overdue payments

If a NAT gateway has an overdue payment, take note of the following rules:

-   The NAT gateway continues to serve your workloads in the next 14 days from the time when the payment becomes overdue.
-   On the 15th day from the time when the payment becomes overdue, the NAT gateway is suspended. In this case, you cannot manage the NAT gateway.
-   If you do not complete the overdue payment within 15 days after the NAT gateway is suspended, the NAT gateway is automatically deleted. An email notification is sent to you one day before the NAT gateway is deleted. After the NAT gateway is deleted, the configurations and data of the NAT gateway are deleted and cannot be recovered.

## Top up your account

Before you top up your account, take note of the following rules:

-   If you top up the account within 15 days after the payment becomes overdue, your service is not interrupted.
-   If you top up the account within 30 days after the payment becomes overdue, the system automatically completes the overdue payment. After the overdue payment is completed, the NAT gateway immediately starts to provide services.

