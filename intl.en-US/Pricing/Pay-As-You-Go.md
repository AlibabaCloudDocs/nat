# Pay-As-You-Go

This topic describes pay-as-you-go NAT gateways. The pay-as-you-go billing method is available for both standard and enhanced NAT gateways.

**Note:** Enhanced NAT gateways are available in all regions except Australia \(Sydney\).

## Overview

The pay-as-you-go billing method allows you to pay only for the amount of resources that you use. Pay-as-you-go NAT gateways provide the following features:

-   You can release pay-as-you-go NAT gateways at any time. After a NAT gateway is released, the bill of the current hour or day is generated the next hour or day. Then, fees are deducted from your account.
-   Pay-as-you-go supports two metering methods: pay-by-specification and pay-by-data-transfer. The following table lists the metering methods of standard NAT gateways and enhanced NAT gateways.

    **Note:** A hyphen "-" indicates that the metering method is not supported for the instance. A tick "√" indicates that the metering method is supported for the instance.

    |Gateway type|Pay-by-data-transfer|Pay-by-specification|
    |------------|--------------------|--------------------|
    |Standard NAT gateway|-|√|
    |Enhanced NAT gateway|√|√|


## Pay-by-specification

The fee of a NAT gateway that is billed by specification = Instance unit price \(USD/day\) × Usage duration

-   The usage duration of a NAT gateway is calculated from the time when the gateway is created to when it is released. Standard NAT gateways and enhanced NAT gateways that are billed by specification have different billing cycles.
    -   Pay-by-specification standard NAT gateways are billed daily and bills are generated on a daily basis. If a standard NAT gateway is used for less than one day, the usage duration is rounded up to one day.
    -   Pay-by-specification enhanced NAT gateways are billed hourly and bills are generated on an hourly basis. If an enhanced NAT gateway is used for less than one hour, the usage duration is rounded up to one hour.
-   NAT gateways are available in different sizes. The instance fee varies based on different sizes of NAT gateways.
-   If you have modified the size of a NAT gateway, you are charged based on the largest size that you have set for the NAT gateway.

The following table lists the unit prices of NAT gateways in different sizes.

**Note:** The prices provided in the table are for reference only.The actual prices on the [buy page](https://common-buy-intl.alibabacloud.com/?&commodityCode=nat_gw_intl#/buy) at the time of purchase shall prevail.

|Region|Small \(USD/day\)|Medium \(USD/day\)|Large \(USD/day\)|Super Large-1 \(USD/day\)|
|:-----|:----------------|:-----------------|:----------------|:------------------------|
|China \(Qingdao\), China \(Beijing\), China \(Zhangjiakou-Beijing Winter Olympics\), China \(Hohhot\), China \(Ulanqab\), China \(Hangzhou\), China \(Shanghai\), China \(Shenzhen\), China \(Heyuan\), and China \(Chengdu\)|1.829|3.505|6.858|12.192|
|US \(Virginia\) and China \(Hong Kong\)|2.438|4.572|8.991|15.849|
|Japan \(Tokyo\)|2.926|5.608|10.972|19.507|
|Singapore \(Singapore\) and Indonesia \(Jakarta\)|2.743|5.334|10.363|18.287|
|Australia \(Sydney\)|3.657|5.334|13.716|24.383|
|Malaysia \(Kuala Lumpur\)|2.606|5.068|9.845|17.374|
|US \(Silicon Valley\)|2.591|5.029|9.601|17.068|
|UAE \(Dubai\)|5.486|10.515|20.573|36.575|
|India \(Mumbai\)|2.606|5.068|9.845|17.374|
|Germany \(Frankfurt\)|3.292|6.309|12.344|21.945|
|UK \(London\)|3.168|6.072|11.856|21.072|

## Pay-by-data-transfer

The fee of a NAT gateway that is billed by data transfer = Instance fee + Capacity unit fee. You are charged and billed on an hourly basis. If you use a NAT gateway for less than one hour, the usage duration is rounded up to one hour.

**Note:** You can purchase enhanced NAT gateways that are charged on a pay-by-data-transfer basis in the following regions: China \(Chengdu\), Malaysia \(Kuala Lumpur\), India \(Mumbai\), Indonesia \(Jakarta\), Germany \(Frankfurt\), and UK \(London\).

The instance fee and capacity unit fee are calculated based on the following formulas:

-   Instance fee = Instance unit price \(CNY/hour\) × Usage duration \(hours\)

    The usage duration of a NAT gateway is calculated from the time when the gateway is created to when it is released.

-   Capacity unit fee per hour = Unit price of capacity unit \(CNY/unit\) × Number of capacity units

    The number of capacity units per hour depends on the number of new connections, the number of concurrent connections, and the amount of data transfer. The following table lists the metering methods of standard NAT gateways and enhanced NAT gateways.

    |Metric|Metering unit|Capacity unit coefficient|Calculation of the number of capacity units per hour based on each metric|
    |------|-------------|-------------------------|-------------------------------------------------------------------------|
    |New connections per second \(CPS\)|Second|1,000|The system collects all CPS values within a billing cycle and then divides the highest CPS value by the capacity unit coefficient to calculate the number of capacity units. |
    |Concurrent connections per minute \(CONNS\)|Minute|10,000|The system collects all CONNS values within a billing cycle and then divides the highest CONNS value by the capacity unit coefficient to calculate the number of capacity units.|
    |Data transfer \(bytes\)|Hour|1GB|The system collects the total amount of data transfer including the inbound and outbound traffic within a billing cycle, and then divides the total amount by the capacity unit coefficient to calculate the number of capacity units. **Note:** The amount of outbound and inbound network traffic collected by the system equals the amount of network traffic to be processed by a NAT gateway. |

    The number of capacity units per hour of a NAT gateway equals the capacity units of CPS, CONNS, or data transfer, whichever is the highest. For more information, see [Example](#section_nje_1sw_nmd).

    **Note:** Within a billing cycle, if the number of capacity units of a NAT gateway per hour is less than 1, the system rounds up the value to 1. In other cases, the number of capacity units per hour equals the calculated value.


The following table lists the instance unit prices and capacity unit prices for pay-by-data-transfer NAT gateways.

**Note:** The prices provided in the table are for reference only.The actual prices on the [buy page](https://common-buy-intl.alibabacloud.com/?&commodityCode=nat_gw_intl#/buy) at the time of purchase shall prevail.

|Region|Instance unit price \(CNY/hour\)|Capacity unit price \(CNY/hour\)|
|------|--------------------------------|--------------------------------|
|UK \(London\) and Germany \(Frankfurt\)|0.3|0.3|

## Example

You created an enhanced NAT gateway that was billed by data transfer in UK \(London\) at 08:10 on July 8, 2020, and then released the gateway at 08:50 on July 8, 2020. Within the time period from 08:10 to 08:50, the highest CPS value of the NAT gateway is 1,100, the highest CONNS value is 20,000, and the total amount of data transfer is 3.5 GB. The following formulas show how to calculate the number of capacity units based on these indicators.

-   Number of capacity units calculated based on the highest CPS value: 1,100/1,000 = 1.1
-   Number of capacity units calculated based on the highest CONNS value: 20,000/10,000 = 2
-   Number of capacity units calculated based on the total amount of data transferred: 3.5/1 = 3.5

Based on the preceding results, the number of capacity units of the NAT gateway within the billing cycle equals the highest value of capacity units, which is 3.5. The NAT gateway fee = Instance fee + Capacity unit fee = 0.3 + \(3.5 × 0.3\) = CNY 1.35.

