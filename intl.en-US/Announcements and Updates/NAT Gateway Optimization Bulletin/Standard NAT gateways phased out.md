# Standard NAT gateways phased out

Standard NAT gateways of Alibaba Cloud will soon be phased out.

## Date

Beginning from November 20, 2020, Alibaba Cloud will stop offering standard NAT gateways in all regions. We apologize for any inconvenience this may cause.

## Impact

After standard NAT gateways are phased out, you can use enhanced NAT gateways to enable Internet access. You can choose one of the following methods if you want to use enhanced NAT gateways:

-   [Create an enhanced NAT gateway](#section_0ix_ti4_tkw)
-   [Upgrade a standard NAT gateway to an enhanced NAT gateway](#section_tzu_ypj_t15)

## Create an enhanced NAT gateway

Enhanced NAT gateways are upgraded from the technical architecture of standard NAT gateways and have the following features: high performance, high elasticity, flexible billing, and fine-grained operations and maintenance. For more information, see [Release notes of enhanced NAT gateways](/intl.en-US/Announcements and Updates/NAT Gateway Optimization Bulletin/Release notes of enhanced NAT gateways.md).

You can create an enhanced NAT gateway in the NAT Gateway console or by calling the API.

-   When you create an enhanced NAT gateway in the console, you must specify a VSwitch for the NAT gateway. For more information, see [Create a NAT gateway](/intl.en-US/NAT Gateway Instance/Create a NAT gateway.md).
-   When you call the API to create an enhanced NAT gateway, you must set **NatType** to **Enhanced** and specify the **VSwitchId** parameter. For more information, see [CreateNatGateway](/intl.en-US/API reference/NAT Gateway/CreateNatGateway.md).

## Upgrade a standard NAT gateway to an enhanced NAT gateway

You can continue to use existing standard NAT gateways. If you want to better manage Internet traffic, we recommend that you upgrade your standard NAT gateways to enhanced NAT gateways. For more information, see [Upgrade a standard NAT gateway to an enhanced NAT gateway](/intl.en-US/NAT Gateway Instance/Upgrade a standard NAT gateway to an enhanced NAT gateway.md).

