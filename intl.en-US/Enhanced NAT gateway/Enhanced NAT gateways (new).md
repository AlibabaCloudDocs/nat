---
keyword: [NAT gateway, enhanced, network address translation, Internet-facing services, Internet access]
---

# Enhanced NAT gateways \(new\)

Enhanced NAT gateways are an upgrade from standard NAT gateways and use a more advanced architecture. Compared with standard NAT gateways, enhanced NAT gateways offer higher elasticity and stability. This improves how you can manage data transfer.

## Features

Enhanced NAT gateways are an upgrade from standard NAT gateways and use a more advanced architecture. Compared with standard NAT gateways, enhanced NAT gateways provide higher performance and higher elasticity. Enhanced NAT gateways support flexible billing methods and fine-grained maintenance.

![Features of enhanced NAT gateways](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0082659951/p147923.png)

## Benefits

Enhanced NAT gateways and standard NAT gateways support basic features such as Destination Network Address Translation \(DNAT\) and Source Network Address Translation \(SNAT\) for Internet access. Enhanced NAT gateways provide new features in addition to the features of standard NAT gateways. The new features include:

-   More metrics for data transfer monitoring

    Up to 22 metrics are collected in real time. You can use the metrics to monitor data transfer and ensure system stability. For more information, see [Monitor and maintain NAT gateways](/intl.en-US/User Guide/Monitor and maintain NAT gateways.md).

-   Multiple NAT gateways for one virtual private cloud \(VPC\)

    You can deploy more than one enhanced NAT gateway for one VPC to forward network traffic to different destinations. In addition, you can use various security services to protect different enhanced NAT gateways. This facilitates how you manage network traffic sent to and received from the Internet.

    You can also specify the same SNAT \(to access the Internet\) entry or DNAT \(to provide Internet-facing services\) entry on different NAT gateways, and configure routes to forward network traffic to a specific egress.

    **Note:**

    -   To replace a standard NAT gateway with an enhanced NAT gateway, you must reconfigure the routes. During this process, your service may be interrupted for a short period of time. We recommend that you reconfigure the routes during off-peak hours.
    -   If you created both SNAT and DNAT entries on an enhanced NAT gateway, the Elastic Compute Service \(ECS\) instances cannot use SNAT to access services that use DNAT of the same enhanced NAT gateway to provide external access in the same VPC. If you want the ECS instances to access the services that use DNAT to provide external access in the same VPC, we recommend that you create another enhanced NAT gateway. Then, create DNAT entries on one NAT gateway and create SNAT entries on the other NAT gateway.

## Manage enhanced NAT gateways

Enhanced NAT gateways are used in the same way as standard NAT gateways. However, when you create an enhanced NAT gateway, you must specify the gateway type, and the virtual private cloud \(VPC\) and vSwitch that you want to associate with the enhanced NAT gateway. After the enhanced NAT gateway is created, the system assigns an idle private IP address from the vSwitch to the enhanced NAT gateway.

For more information about how to create an enhanced NAT gateway, see [Purchase a NAT gateway](/intl.en-US/Pricing/Purchase a NAT gateway.md).

**Related topics**  


[Comparison between enhanced NAT gateways and standard NAT gateways](/intl.en-US/Enhanced NAT gateway/Comparison between enhanced NAT gateways and standard NAT gateways.md)

[Immediately upgrade a standard NAT gateway to an enhanced NAT gateway](/intl.en-US/Enhanced NAT gateway/Immediately upgrade a standard NAT gateway to an enhanced NAT gateway.md)

[Upgrade a standard NAT gateway to an enhanced NAT gateway at a scheduled time](/intl.en-US/Enhanced NAT gateway/Upgrade a standard NAT gateway to an enhanced NAT gateway at a scheduled time.md)

[FAQ about how to upgrade standard NAT gateways to enhanced NAT gateways](/intl.en-US/FAQ/FAQ about how to upgrade standard NAT gateways to enhanced NAT gateways.md)

