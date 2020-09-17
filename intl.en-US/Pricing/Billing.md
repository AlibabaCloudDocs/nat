# Billing

To enable Network Address Translation \(NAT\) gateways to access the Internet, you must associate elastic IP addresses \(EIPs\) with them. After you associate a NAT gateway with an EIP, you are charged for both the NAT gateway and the EIP. This topic describes the billing method of NAT gateways.

## Instance fee

-   Billing method: pay-as-you-go. For more information, see [Pay-as-you-go](/intl.en-US/Pricing/Pay-as-you-go.md).

    Fees are charged and bills are generated on a daily basis.

-   Billing item: instance fee.
-   Instance fee: NAT gateways are available in different sizes. The instance fee varies based on the size of the NAT gateway.

## Network fee

After you create a NAT gateway, you must associate it with an EIP to enable the NAT gateway to access the Internet. After the NAT gateway is associated with an EIP, a network fee is charged based on the billing method of the EIP.

**Note:** If a NAT service plan was created under your account before January 26, 2018, the NAT gateway can use the public IP address that is provided by the NAT service plan. In this case, the network fee is charged based on the billing method of the NAT service plan. For more information, see [Billing of NAT bandwidth package](/intl.en-US/Bandwidth Package (Archive)/Billing of NAT bandwidth package.md).

If an EIP is associated with an EIP bandwidth plan, a network fee is charged based on the billing method of the EIP bandwidth plan. For more information, see [Billing](/intl.en-US/Pricing/Billing.md).

