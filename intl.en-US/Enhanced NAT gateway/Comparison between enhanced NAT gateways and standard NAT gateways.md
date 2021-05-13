---
keyword: [NAT gateway, enhanced, network address translation, Internet-facing services, Internet access]
---

# Comparison between enhanced NAT gateways and standard NAT gateways

This topic describes the differences in features and limits between enhanced NAT gateways and standard NAT gateways.

## Comparison of features

|Item|Enhanced NAT gateway|Standard NAT gateway|Reference|
|----|--------------------|--------------------|---------|
|Multiple NAT gateways in one VPC|Supported|Not supported|[Deploy multiple NAT gateways in one VPC](/intl.en-US/Best Practices/Deploy multiple NAT gateways in one VPC.md)|
|Associating a vSwitch with a NAT gateway|Supported|Not supported|N/A|
|Billing on an hourly basis|Supported|Not supported|[Pay-by-data-transfer](/intl.en-US/Pricing/Pay-as-you-go.md)|
|Processing TCP, UDP, and ICMP segments|Supported|Not supported|N/A|
|Metrics|22|4|[Monitor and maintain NAT gateways](/intl.en-US/User Guide/Monitor and maintain NAT gateways.md)|
|Associating multiple elastic IP addresses \(EIPs\) with a NAT gateway|Supported|Supported|[Associate an EIP with a NAT gateway](/intl.en-US/User Guide/Create NAT gateways.md)|
|SNAT|Supported|Supported|[Create a SNAT entry to access the Internet](/intl.en-US/User Guide/Create a SNAT entry to access the Internet.md)|
|Creating multiple SNAT entries in a SNAT table|Supported|Supported|
|Associating multiple EIPs with a SNAT table|Supported|Supported|
|DNAT|Supported|Supported|[Create a DNAT entry to provide Internet-facing services](/intl.en-US/User Guide/Create a DNAT entry to provide Internet-facing services.md)|
|DNAT port mapping|Supported|Supported|
|DNAT IP mapping|Supported|Supported|
|Elastic Compute Service \(ECS\) instances use SNAT to access services that use DNAT to provide Internet-facing services if the same enhanced NAT gateway is used for SNAT and DNAT|Not supported|Supported|[Use SNAT of enhanced NAT gateways to enable ECS instances to access Internet-facing services that use DNAT in the same VPC](/intl.en-US/Best Practices/Use SNAT of enhanced NAT gateways to enable ECS instances to access Internet-facing services that use DNAT in the same VPC.md)|
|Using an EIP for both SNAT and DNAT|Supported|Not supported|-   [Create a SNAT entry to access the Internet](/intl.en-US/User Guide/Create a SNAT entry to access the Internet.md)
-   [Create a DNAT entry to provide Internet-facing services](/intl.en-US/User Guide/Create a DNAT entry to provide Internet-facing services.md) |

## Comparison of limits

|Item|Enhanced NAT gateway|Standard NAT gateway|
|----|--------------------|--------------------|
|The maximum number of NAT gateways that can be deployed in a VPC|5. To increase the quota,[submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex).|1 \(not adjustable\)|
|The maximum number of DNAT entries that can be added to a NAT gateway|100. You can increase the quota. For more information, see [Quota management](/intl.en-US/Common Configurations/Quota management.md).|100. You can increase the quota. For more information, see [Quota management](/intl.en-US/Common Configurations/Quota management.md).|
|The maximum number of SNAT entries that you can add to a NAT gateway|40. You can increase the quota. For more information, see [Quota management](/intl.en-US/Common Configurations/Quota management.md).|40. You can increase the quota. For more information, see [Quota management](/intl.en-US/Common Configurations/Quota management.md).|
|The maximum number of EIPs that you can specify in a SNAT entry|64 \(not adjustable\)|64 \(not adjustable\)|
|Creating a NAT gateway for a VPC that contains a custom route entry whose destination CIDR block is 0.0.0.0/0|Supported|Not supported. You must delete the custom route entry whose destination CIDR block is 0.0.0.0/0 before you can create a NAT gateway for the VPC.|
|Limits on a vSwitch by the bandwidth limit of the EIPs specified in the SNAT entry that is added to the vSwitch|Yes. If the EIPs are associated with an EIP bandwidth plan, the vSwitch is limited by the bandwidth limit of the EIP bandwidth plan.|Yes. If the EIPs are associated with an EIP bandwidth plan, the vSwitch is limited by the bandwidth limit of the EIP bandwidth plan.|
|The maximum number of EIPs that can be associated with a NAT gateway|20. You can increase the quota. For more information, see [Quota management](/intl.en-US/Common Configurations/Quota management.md).|20. You can increase the quota. For more information, see [Quota management](/intl.en-US/Common Configurations/Quota management.md).|
|The maximum number of pay-by-data-transfer EIPs that you can associate with a NAT gateway|10. You can increase the quota. For more information, see [Quota management](/intl.en-US/Common Configurations/Quota management.md).|10. You can increase the quota. For more information, see [Quota management](/intl.en-US/Common Configurations/Quota management.md).|
|The bandwidth limit of a pay-by-data-transfer EIP that is associated with a NAT gateway|200 Mbit/s. If the EIP is associated with an EIP bandwidth plan, the bandwidth of the EIP that is associated with the enhanced NAT gateway is unlimited.|200 Mbit/s \(not adjustable\)|
|The bandwidth limit of a NAT gateway|5 Gbit/s. If the total bandwidth of the EIPs or EIP bandwidth plans is greater than 5 Gbit/s,[submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex) to increase the quota.|A NAT gateway does not have a bandwidth limit. The bandwidth limit depends on the bandwidth limit of the EIPs that are associated with SNAT or DNAT entries. The bandwidth limit also depends on the bandwidth limit of the EIP bandwidth plans with which the EIPs are associated. For example, you create a SNAT entry for a NAT gateway, and specify five pay-by-data-transfer EIPs and two pay-by-bandwidth EIPs whose bandwidth limits are 500 Mbit/s bandwidth in the SNAT entry. The bandwidth of the NAT gateway is limited to 2,000 Mbit/s. This value is calculated based on the following formula: 5 × 200 Mbit/s + 2 × 500 Mbit/s = 2,000 Mbit/s. If the seven EIPs are associated with the same EIP bandwidth plan, and the bandwidth of the EIP bandwidth plan is limited to 1,000 Mbit/s, the bandwidth limit of the NAT gateway is 1,000 Mbit/s. |
|The maximum number of concurrent connections for an EIP is 55,000.|Yes|Yes|
|The bandwidth limit of an EIP in an EIP bandwidth plan is 200 Mbit/s.|No|Yes|
|Users of NAT service plans cannot associate EIPs with NAT gateways.|Yes|Yes|
|You can change the bandwidth limit of the EIP bandwidth plan that is associated with a NAT gateway. For example, you can upgrade the bandwidth limit from less than 1 Gbit/s to greater than 1 Gbit/s. You can also downgrade the bandwidth limit from greater than 1 Gbit/s to less than 1 Gbit/s. When you change the bandwidth limit of the EIP bandwidth plan, your service may be temporarily interrupted.|No|Yes|
|Your service may be temporarily interrupted when IP addresses in the existing SNAT entries are reduced.|Yes|Yes|
|Your service may be temporarily interrupted when IP addresses in the existing SNAT entries are increased.|No|Yes|
|Multiple elastic network interfaces \(ENIs\) are attached to an ECS instance, and an EIP is associated with one of the ENIs. Different ENIs are used to forward the inbound and outbound traffic of the ECS instance. In this scenario, the ECS instance can be accessed from the Internet.|No. You must modify the route of the ECS instance before you upgrade the standard NAT gateway to an enhanced NAT gateway. Make sure that the inbound and outbound traffic of the ECS instance is forwarded by using the same ENI. For more information, see [Configure routes for ENIs](/intl.en-US/Network/Elastic Network Interfaces/Configure an ENI.md).|Yes|

## References

-   [Enhanced NAT gateways \(new\)](/intl.en-US/Enhanced NAT gateway/Enhanced NAT gateways (new).md)
-   [Immediately upgrade a standard NAT gateway to an enhanced NAT gateway](/intl.en-US/Enhanced NAT gateway/Immediately upgrade a standard NAT gateway to an enhanced NAT gateway.md)

