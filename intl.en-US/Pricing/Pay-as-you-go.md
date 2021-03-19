---
keyword: [NAT gateway, Internet egress, network address translation, Internet-facing services, Internet access]
---

# Pay-as-you-go

You can purchase NAT gateways that are billed on a pay-as-you-go basis. If you want to create or delete NAT gateways based on your business requirements, you can purchase pay-as-you-go NAT gateways instead of subscription NAT gateways. This topic describes the billing rules of pay-as-you-go NAT gateways.

## Overview

The pay-as-you-go billing method requires you to pay for the resources that you use.

Pay-as-you-go NAT gateways provide the following features:

-   Pay-as-you-go NAT gateways are billed based on the billing cycle. Bills are generated and fees are deducted from your account after each billing cycle.
-   You can delete pay-as-you-go NAT gateways at any time. After you delete a NAT gateway, the NAT gateway is no longer billed. For more information, see [Delete a NAT gateway](/intl.en-US/User Guide/Create NAT gateways.md).
-   [Pay-by-data-transfer](#section_v5g_sue_5bj): You are charged based on the amount of network traffic that a NAT gateway forwards. Fees may vary in each billing cycle.

## Pay-by-data-transfer

Total amount that you must pay for a pay-by-data-transfer NAT gateway = Instance fee + Capacity unit \(CU\) fee. You are charged and billed on an hourly basis. If you use a NAT gateway for less than 1 hour, the usage duration is rounded up to 1 hour.

The instance fee and CU fee are calculated based on the following formulas:

-   Instance fee = Instance unit price \(CNY/hour\) × Usage duration \(hours\)

    Usage duration refers to the time period from when the NAT gateway is purchased to when it is released.

-   CU fee per hour = CU unit price \(CNY/unit\) × Number of CUs

    **Number of CUs consumed per hour by a NAT gateway = Max\(Number of CUs based on new connections per hour, Number of CUs based on concurrent connections per hour, Number of CUs based on data transfer per hour\)**

    New connections, concurrent connections, and data transfer are three determinants to CUs. The following table describes how the number of CUs per hour is calculated based on these determinants.

    |Metric|Unit|CU coefficient|Calculation of the number of CUs per hour|
    |------|----|--------------|-----------------------------------------|
    |Connections per second \(CPS\)|Second|1,000|The system collects all CPS values within a billing cycle and then divides the highest CPS value by the CU coefficient to calculate the number of CUs.|
    |Concurrent connections \(CONNS\)|Minute|10,000|The system collects all CONNS values within a billing cycle and then divides the highest CONNS value by the CU coefficient to calculate the number of CUs.|
    |Data transfer \(bytes\)|Hour|1 GB|The system collects the total amount of data transfer including the inbound and outbound traffic within a billing cycle, and then divides the total amount by the CU coefficient to calculate the number of CUs.**Note:** The amount of outbound and inbound network traffic collected by the system equals the amount of network traffic to be processed by a NAT gateway. |

    The following table describes the instance unit prices and CU prices for pay-by-data-transfer NAT gateways.

    **Note:** If the prices in this table are different from those on the buy page,the prices on the [buy page](https://common-buy-intl.alibabacloud.com/?&commodityCode=nat_gw_intl#/buy) shall prevail.

    |Region|Instance unit price \(USD/hour\)|CU unit price \(USD/hour\)|
    |------|--------------------------------|--------------------------|
    |China \(Hangzhou\)|0.034|0.034|
    |China \(Shanghai\)|
    |China \(Chengdu\)|
    |China \(Shenzhen\)|
    |China \(Heyuan\)|
    |China \(Qingdao\)|
    |China \(Beijing\)|
    |China \(Zhangjiakou\)|
    |China \(Hohhot\)|
    |China \(Ulanqab\)|
    |China \(Hong Kong\)|0.043|0.043|
    |UK \(London\)|
    |Japan \(Tokyo\)|
    |Singapore \(Singapore\)|
    |Australia \(Sydney\)|
    |Germany \(Frankfurt\)|
    |US \(Silicon Valley\)|
    |US \(Virginia\)|
    |Malaysia \(Kuala Lumpur\)|
    |Indonesia \(Jakarta\)|
    |India \(Mumbai\)|
    |UAE \(Dubai\)|



    You created three enhanced NAT gateways that use the pay-by-data-transfer billing method in the UK \(London\) region at 08:10:00 \(UTC+8\) on July 8, 2020, and released the NAT gateways at 08:50:00 \(UTC+8\) on July 8, 2020. The following table describes the highest CPS value, the highest CONNS value, and the total amount of data transfer of the NAT gateways within the time period from 08:10:00 \(UTC+8\) to 08:50:00 \(UTC+8\).

    |Metric|Data collected from NAT Gateway 1|Data collected from NAT Gateway 2|Data collected from NAT Gateway 3|
    |------|---------------------------------|---------------------------------|---------------------------------|
    |Highest CPS value \(count/second\)|1100|32|0|
    |Highest CONNS value \(count/minute\)|20000|8|0|
    |Total amount of data transfer \(GB/hour\)|3.5|0.0056|0|

    The numbers of CUs based on new connections, concurrent connections, and data transfer, and the CU fee are calculated by using the following formulas:

    The number of CUs is calculated based on the following formulas:

    ```
    Number of CUs based on CPS = Highest CPS value/CU coefficient
    Number of CUs based on CONNS = Highest CONNS value/CU coefficient
    Number of CUs based on data transfer = Total amount of data transfer/CU coefficient
    ```

    The CU fee is calculated based on the following formula:

    ```
    CU fee = Max(Number of CUs based on new connections per hour, Number of CUs based on concurrent connections per hour, Number of CUs based on the amount of data transferred per hour) × CU unit price
    ```

    |Number of CUs|Data collected from NAT Gateway 1|Data collected from NAT Gateway 2|Data collected from NAT Gateway 3|
    |-------------|---------------------------------|---------------------------------|---------------------------------|
    |Number of CUs based on CPS|1100÷1000=1.1|32÷1000=**0.032**|0|
    |Number of CUs based on CONNS|20000÷10000=2|8÷10000=0.0008|0|
    |Number of CUs based on data transfer|3.5÷1=**3.5**|0.0056÷1=0.0056|0|
    |****|***3.5***×0.43=0.1505|***0.032***×0.43=0.001376|0|


## Overdue payments

If a pay-as-you-go NAT gateway has an overdue payment, take note of the following rules:

-   The NAT gateway continues to serve your workloads in the next 14 days from the time when the payment becomes overdue.
-   The NAT gateway is suspended on the 15th day from the time when the payment becomes overdue. After the NAT gateway is suspended, you cannot manage the NAT gateway.
-   If you do not pay the outstanding amount within 15 days after the NAT gateway is suspended, the NAT gateway is automatically deleted. An email is sent to you one day before the NAT gateway is deleted. After the NAT gateway is deleted, the configurations and data of the NAT gateway are deleted and cannot be recovered.

## Top up your account

Before you top up your account, take note of the following rules:

-   If you top up the account within 15 days after the payment becomes overdue, your service is not suspended.
-   If you top up the account within 30 days after the payment becomes overdue, the system automatically pays the outstanding amount. After the system pays the outstanding amount, the NAT gateway immediately starts to provide services.

