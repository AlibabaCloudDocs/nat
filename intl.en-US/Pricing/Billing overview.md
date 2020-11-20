---
keyword: [NAT Gateway, Billing, Price]
---

# Billing overview

NAT gateways are enterprise-class gateways that provide Source Network Address Translation \(SNAT\) and Destination Network Address Translation \(DNAT\) services for Internet access. You are charged for using NAT gateways. This topic describes the billing of NAT gateways.

## Overview

Before a NAT gateway can access the Internet, you must associate an elastic IP address \(EIP\) with the NAT gateway. You are charged for NAT gateways and EIPs that are associated with the NAT gateways.

**Note:** If you have purchased NAT service plans before January 26, 2018, you can associate static public IP addresses in the NAT service plan with the NAT gateway to provide Internet access services. You are charged for NAT gateways and NAT service plans that are associated with the NAT gateways.For more information, see [Billing of NAT service plans](/intl.en-US/Bandwidth Package (Archive)/Billing of NAT service plans.md).

## Billing methods

NAT gateways support the subscription and pay-as-you-go billing methods.

|Billing method of NAT gateways|Description|Reference|
|------------------------------|-----------|---------|
|Subscription|Subscription is a billing method that requires you to pay a subscription fee before you can use the service. Subscription NAT gateways are cost-effective. Discounts are offered on subscription NAT gateways.|[t16028.md\#]()|
|Pay-as-you-go|The pay-as-you-go billing method requires you to pay for resources based on the actual usage. If you want to create or delete NAT gateways based on your needs, you can purchase pay-as-you-go NAT gateways instead of subscription NAT gateways.|[Pay-as-you-go](/intl.en-US/Pricing/Pay-as-you-go.md)|

## Billing methods of EIPs

After you create a NAT gateway, you must associate an EIP with the NAT gateway. This enables the NAT gateway to access the Internet. You are charged for the EIPs that are associated with NAT gateways. For more information, see [Subscription](/intl.en-US/Pricing/Subscription.md) and [Pay-as-you-go](/intl.en-US/Pricing/Pay-as-you-go.md).

If an EIP is associated with an EIP bandwidth plan, the predefined billing method of the EIP becomes invalid. The NAT gateway with which the EIP is associated is charged an Internet data transfer fee based on the billing method of the EIP bandwidth plan. For more information, see [Billing](/intl.en-US/Pricing/Billing.md).

