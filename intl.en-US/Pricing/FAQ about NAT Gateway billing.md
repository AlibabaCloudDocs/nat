---
keyword: [NAT gateway, FAQ, billing]
---

# FAQ about NAT Gateway billing

This topic provides answers to some commonly asked questions about NAT Gateway billing.

-   [How am I charged for using NAT gateways?](#section_9x9_l8o_gxj)
-   [What is the metering method for pay-as-you-go NAT gateways?](#section_3tw_bpc_d0o)
-   [Why am I still charged for an EIP and a NAT gateway after I disassociated the EIP from the NAT gateway?](#section_k9h_r41_iol)

## How am I charged for using NAT gateways?

To enable Internet access for a NAT gateway, you must associate an elastic IP address \(EIP\) with the NAT gateway. You are charged for the NAT gateway and the EIP that is associated with the NAT gateway. For more information, see [Billing overview](/intl.en-US/Pricing/Billing overview.md).

## What is the metering method for pay-as-you-go NAT gateways?

Pay-as-you-go NAT gateways support the pay-by-data-transfer metering method. A NAT gateway is charged based on the amount of network traffic that it forwards. For more information, see [Pay-by-data-transfer](/intl.en-US/Pricing/Pay-as-you-go.md).

## Why am I still charged for an EIP and a NAT gateway after I disassociated the EIP from the NAT gateway?

You are still charged for the EIP and NAT gateway because you did not release the EIP and delete the NAT gateway after you disassociated the EIP from the NAT gateway. To stop the billing, release the EIP and delete the NAT gateway. For more information, see [Release an EIP](/intl.en-US/User Guide/Manage Pay-As-You-Go-billed EIPs/Release an EIP.md) and [Delete a NAT gateway](/intl.en-US/User Guide/Create NAT gateways.md).

