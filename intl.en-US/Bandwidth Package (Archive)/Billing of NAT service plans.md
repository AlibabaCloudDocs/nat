# Billing of NAT service plans

A NAT service plan consists of bandwidth resources and one or more public IP addresses. When you use a NAT service plan, you are charged a rental fee for the public IP address and a data transfer fee.

## Billing methods

NAT service plans are billed on a pay-as-you-go basis. You are charged and billed on an hourly basis. If you use a NAT service plan for less than one hour within a billing cycle, the usage duration is rounded up to one hour.

## Billable items

When you use a NAT service plan, you are charged a rental fee for the public IP address and a data transfer fee. The fees are calculated based on the following formulas:

-   Public IP address rental fee = Unit price × Number of public IP addresses × Rental period

-   Data transfer fee = Unit price × Volume of outbound data transfer

    -   You are charged only for outbound data transfer \(from Alibaba Cloud to the Internet\). You are not charged for inbound data transfer.

    -   The unit price for outbound data transfer is fixed and does not vary with the bandwidth limit of the NAT service plan. We recommend that you set the bandwidth limit based on your service requirements. This helps you prevent unnecessary costs that may be caused by malicious requests or service malfunction.


The following table describes the unit prices for data transfer and public IP address rental in different regions.

**Note:** If the prices in this table are different from those on the buy page, the prices on the buy page shall prevail.

|Region|Unit price of public IP address rental \(USD/public IP address/hour\)|Unit price of data transfer \(USD/GB\)|
|:-----|:--------------------------------------------------------------------|:-------------------------------------|
|China \(Qingdao\)|0.003|0.113|
|China \(Hangzhou\), China \(Shanghai\), China \(Beijing\), China \(Zhangjiakou\), and China \(Shenzhen\)|0.003|0.125|
|China \(Hong Kong\)|0.009|0.156|
|Singapore \(Singapore\)|0.125|0.081|
|US \(Virginia\)|0.005|0.078|
|US \(Silicon Valley\)|0.005|0.078|
|Japan \(Tokyo\)|0.005|0.12|
|UAE \(Dubai\)|0.009|0.447|
|Australia \(Sydney\)|0.006|0.13|
|Malaysia \(Kuala Lumpur\)|0.112|0.13|
|Germany \(Frankfurt\)|0.006|0.07|

