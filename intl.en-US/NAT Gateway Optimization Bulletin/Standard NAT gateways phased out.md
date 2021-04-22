# Standard NAT gateways phased out

Standard NAT gateways of Alibaba Cloud are phased out.

## Date

Starting November 20, 2020, Alibaba Cloud stops offering standard NAT gateways in all regions. We apologize for the inconvenience that may be caused.

## Impact

After standard NAT gateways are phased out, you can use enhanced NAT gateways to allow Internet access. You can use one of the following methods to use enhanced NAT gateways:

-   [Purchase a NAT gateway](/intl.en-US/Pricing/Purchase a NAT gateway.md)
-   [Immediately upgrade a standard NAT gateway to an enhanced NAT gateway](/intl.en-US/Enhanced NAT gateway/Immediately upgrade a standard NAT gateway to an enhanced NAT gateway.md)

## Create an enhanced NAT gateway

Enhanced NAT gateways are an upgrade from standard NAT gateways and use a more advanced architecture. Compared with standard NAT gateways, enhanced NAT gateways provide higher performance and higher elasticity. Enhanced NAT gateways support flexible billing methods and fine-grained maintenance. For more information, see [Enhanced NAT gateways \(new\)](/intl.en-US/Enhanced NAT gateway/Enhanced NAT gateways (new).md).

You can create an enhanced NAT gateway in the NAT Gateway console. You can also call API operations to create an enhanced NAT gateway.

-   When you create an enhanced NAT gateway in the console, you must specify a vSwitch for the NAT gateway. For more information, see [Create NAT gateways](/intl.en-US/User Guide/Create NAT gateways.md).
-   When you call API operations to create an enhanced NAT gateway, you must set the **NatType** parameter to **Enhanced** and set the **VSwitchId** parameter. For more information, see [CreateNatGateway](/intl.en-US/API reference/NAT Gateway/CreateNatGateway.md).

## Upgrade a standard NAT gateway to an enhanced NAT gateway

You can continue using existing standard NAT gateways. To improve how you manage Internet traffic, we recommend that you upgrade your standard NAT gateways to enhanced NAT gateways. For more information, see [Immediately upgrade a standard NAT gateway to an enhanced NAT gateway](/intl.en-US/Enhanced NAT gateway/Immediately upgrade a standard NAT gateway to an enhanced NAT gateway.md).

