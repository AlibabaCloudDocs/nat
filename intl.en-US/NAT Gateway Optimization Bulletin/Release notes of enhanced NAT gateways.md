---
keyword: [NAT gateway, enhanced, network address translation, Internet-facing services, Internet access]
---

# Release notes of enhanced NAT gateways

Alibaba Cloud has released enhanced NAT gateways. Enhanced NAT gateways are an upgrade from standard NAT gateways and use a more advanced architecture. Compared with standard NAT gateways, enhanced NAT gateways provide higher elasticity and stability. This helps you manage data transfer in a more efficient manner.

## Overview of enhanced NAT gateways

Enhanced NAT gateways and standard NAT gateways support basic features such as Destination Network Address Translation \(DNAT\) and Source Network Address Translation \(SNAT\) for Internet access. Enhanced NAT gateways provide new features in addition to the features of standard NAT gateways.

-   More metrics for data transfer monitoring

    Up to 22 metrics are collected in real time. You can use the metrics to monitor data transfer and ensure system stability. For more information, see [Monitor and maintain NAT gateways](/intl.en-US/User Guide/Monitor and maintain NAT gateways.md).

-   Multiple NAT gateways for one virtual private cloud \(VPC\)

    You can deploy more than one enhanced NAT gateway for one VPC to forward network traffic to different destinations. In addition, you can use various security services to protect different enhanced NAT gateways. This facilitates how you manage network traffic sent to and received from the Internet.

    You can also specify the same SNAT \(to access the Internet\) entry or DNAT \(to provide Internet-facing services\) entry on different NAT gateways, and configure routes to forward network traffic to a specific egress.

    **Note:**

    -   To replace a standard NAT gateway with an enhanced NAT gateway, you must reconfigure the routes. During this process, your service may be interrupted for a short period of time. We recommend that you reconfigure the routes during off-peak hours.
    -   If you created both SNAT and DNAT entries on an enhanced NAT gateway, the Elastic Compute Service \(ECS\) instances cannot use SNAT to access services that use DNAT of the same enhanced NAT gateway to provide external access in the same VPC. If you want the ECS instances to access the services that use DNAT to provide external access in the same VPC, we recommend that you create another enhanced NAT gateway. Then, create DNAT entries on one NAT gateway and create SNAT entries on the other NAT gateway.

## Comparison between enhanced NAT gateways and standard NAT gateways

The following tables describe differences and similarities in features and limits between enhanced NAT gateways and standard NAT gateways.

|Item|Enhanced NAT gateway|Standard NAT gateway|Reference|
|----|--------------------|--------------------|---------|
|Multiple NAT gateways for one virtual private cloud \(VPC\)|Supported|Not supported|[Deploy multiple NAT gateways in one VPC](/intl.en-US/Best Practices/Deploy multiple NAT gateways in one VPC.md)|
|Associating a vSwitch with a NAT gateway|Supported|Not supported|N/A|
|Billing on an hourly basis|Supported|Not supported|[Pay-by-data-transfer](/intl.en-US/Pricing/Pay-as-you-go.mdsection_v5g_sue_5bj)|
|Billing on a daily basis|Not supported|Supported|[Pay-as-you-go](/intl.en-US/Pricing/Pay-as-you-go.md)|
|Processing TCP, UDP, and ICMP segments|Supported|Not supported|N/A|
|Metrics|22|4|[Monitor and maintain NAT gateways](/intl.en-US/User Guide/Monitor and maintain NAT gateways.md)|
|Associating multiple elastic IP addresses \(EIPs\) with a NAT gateway|Supported|Supported|[Associate an EIP with a NAT gateway](/intl.en-US/User Guide/Create NAT gateways.md)|
|Source Network Address Translation \(SNAT\)|Supported|Supported|[Create a SNAT entry to access the Internet](/intl.en-US/User Guide/Create a SNAT entry to access the Internet.md)|
|Creating multiple SNAT entries in a SNAT table|Supported|Supported|
|Associating multiple EIPs with a SNAT table|Supported|Supported|
|Destination Network Address Translation \(DNAT\)|Supported|Supported|[Create a DNAT entry to provide Internet-facing services](/intl.en-US/User Guide/Create a DNAT entry to provide Internet-facing services.md)|
|DNAT port mapping|Supported|Supported|
|DNAT IP mapping|Supported|Supported|
|Elastic Compute Service \(ECS\) instances use SNAT to access services that use DNAT to provide Internet-facing services if the same enhanced NAT gateway is used for SNAT and DNAT|Not supported|Supported|[Use SNAT of enhanced NAT gateways to enable ECS instances to access Internet-facing services that use DNAT in the same VPC](/intl.en-US/Best Practices/Use SNAT of enhanced NAT gateways to enable ECS instances to access Internet-facing services that use DNAT in the same VPC.md)|

|Item|Enhanced NAT gateway|Standard NAT gateway|
|----|--------------------|--------------------|
|The maximum number of NAT gateways that can be deployed for a VPC|5. To increase the quota, [submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex).|1 \(not adjustable\)|
|Using an EIP for both SNAT and DNAT|Only selected users can use an EIP for both SNAT and DNAT. To apply to be added to the whitelist, [submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex).|Not supported \(not adjustable\)|
|The maximum number of DNAT entries that can be added to a NAT gateway|100. You can increase the quota. For more information, see [Quota management](/intl.en-US/Common Configurations/Quota management.md).|100. You can increase the quota. For more information, see [Quota management](/intl.en-US/Common Configurations/Quota management.md).|
|The maximum number of SNAT entries that can be added to a NAT gateway|40. You can increase the quota. For more information, see [Quota management](/intl.en-US/Common Configurations/Quota management.md).|40. You can increase the quota. For more information, see [Quota management](/intl.en-US/Common Configurations/Quota management.md).|
|The maximum number of EIPs that can be specified in a SNAT entry|64 \(not adjustable\)|64 \(not adjustable\)|
|Creating a NAT gateway for a VPC that contains a custom route entry whose destination CIDR block is 0.0.0.0/0|Supported|Not supported. You must delete the custom route entry whose destination CIDR block is 0.0.0.0/0 before you can create a NAT gateway for the VPC.|
|Limits on a vSwitch by the bandwidth limit of the EIPs specified in the SNAT entry that is added to the vSwitch|Yes. If the EIPs are associated with an EIP bandwidth plan, the vSwitch is limited by the bandwidth limit of the EIP bandwidth plan.|Yes. If the EIPs are associated with an EIP bandwidth plan, the vSwitch is limited by the bandwidth limit of the EIP bandwidth plan.|
|The maximum number of EIPs that can be associated with a NAT gateway|20. You can increase the quota. For more information, see [Quota management](/intl.en-US/Common Configurations/Quota management.md).|20. You can increase the quota. For more information, see [Quota management](/intl.en-US/Common Configurations/Quota management.md).|
|The maximum number of pay-by-data-transfer EIPs that can be associated with a NAT gateway|10. You can increase the quota. For more information, see [Quota management](/intl.en-US/Common Configurations/Quota management.md).|10. You can increase the quota. For more information, see [Quota management](/intl.en-US/Common Configurations/Quota management.md).|
|The bandwidth limit of a pay-by-data-transfer EIP that is associated with a NAT gateway|200 Mbit/s. If the EIP is associated with an EIP bandwidth plan, the bandwidth of the EIP that is associated with the enhanced NAT gateway is unlimited.|200 Mbit/s \(not adjustable\)|
|The bandwidth limit of a NAT gateway|5 Gbit/s. If the total bandwidth of the EIPs or EIP bandwidth plans is greater than 5 Gbit/s, [submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex) to increase the quota.|A NAT gateway does not have a bandwidth limit. The bandwidth limit is based on the bandwidth limit of the EIPs that are associated with a SNAT entry or a DNAT entry. The bandwidth limit is also based on the bandwidth limit of the EIP bandwidth plans to which the EIPs are added. For example, you create a SNAT entry for a NAT gateway, and specify five pay-by-data-transfer EIPs and two pay-by-bandwidth EIPs with 500 Mbit/s bandwidth each in the SNAT entry. The bandwidth of the NAT gateway is limited to 2,000 Mbit/s. This value is based on the following calculation: 5 × 200 Mbit/s + 2 × 500 Mbit/s = 2,000 Mbit/s. If the seven EIPs are associated with the same EIP bandwidth plan, and the bandwidth of the EIP bandwidth plan is limited to 1,000 Mbit/s, the bandwidth limit of the NAT gateway is 1,000 Mbit/s. |
|The maximum number of concurrent connections for an EIP is 55,000.|Yes|Yes|
|The bandwidth limit of an EIP in an EIP bandwidth plan is 200 Mbit/s.|No|Yes|
|Users of NAT service plans are not allowed to associate EIPs with NAT gateways.|Yes|Yes|
|Your service may be temporarily interrupted when you change the bandwidth limit of the EIP bandwidth plan that is associated with a NAT gateway. For example, you can upgrade the bandwidth limit from less than 1 Gbit/s to greater than 1 Gbit/s. You can also downgrade the bandwidth limit from greater than 1 Gbit/s to less than 1 Gbit/s.|No|Yes|
|Your service may be temporarily interrupted when IP addresses in the existing SNAT entries are reduced.|Yes|Yes|
|Your service may be temporarily interrupted when IP addresses in the existing SNAT entries are increased.|No|Yes|
|Multiple ENIs are attached to an ECS instance, and an EIP is associated with one of the ENIs. Different ENIs are used to forward the inbound and outbound traffic of the ECS instance. In this scenario, the ECS instance can be accessed from the Internet.|No. You must modify the route of the ECS instance before you upgrade the standard NAT gateway to an enhanced NAT gateway. Make sure that the inbound and outbound traffic of the ECS instance is forwarded by using the same ENI. For more information, see [Configure routes for ENIs](/intl.en-US/Network/Elastic Network Interfaces/Configure an ENI.md).|Yes|

## Configure an enhanced NAT gateway

Enhanced NAT gateways are used in the same way as standard NAT gateways. However, when you create an enhanced NAT gateway, you must select enhanced NAT gateway as the gateway type. In addition, you must specify the VPC and vSwitch to be associated with the enhanced NAT gateway. After the enhanced NAT gateway is created, the system assigns an idle private IP address from the vSwitch to the enhanced NAT gateway.

**Note:** To create an enhanced NAT gateway as a Resource Access Management \(RAM\) user, you must first use your Alibaba Cloud account to authorize the RAM user. [Authorize a RAM user](https://ram.console.aliyun.com/#/role/authorize?request=%7B%22Requests%22:%20%7B%22request1%22:%20%7B%22RoleName%22:%20%22AliyunNATAccessingNetworkInterfaceRole%22,%20%22TemplateId%22:%20%22ENIRole%22%7D%7D,%20%22ReturnUrl%22:%20%22https:%2F%2Fvpc.console.aliyun.com%2Fnat%22,%20%22Service%22:%20%22NAT%22%7D).

![创建增强型NAT网关 ](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5216645951/p101531.png)

The following figure shows how to use an enhanced NAT gateway.

![NAT 2.0 workflow](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5216645951/p101647.png)

