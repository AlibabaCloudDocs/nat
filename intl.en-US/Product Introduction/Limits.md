---
keyword: [NAT Gateway, limits, SNAT, DNAT]
---

# Limits

This topic describes the limits on NAT Gateway and how to apply for a quota increase.

## Limits on NAT gateways

|Item|Limit|Adjustable|
|----|-----|----------|
|The maximum number of enhanced NAT gateways that can be created for a virtual private cloud \(VPC\)|5.|[Submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex).|
|The maximum number of standard NAT gateways that can be created for a VPC|1.|N/A|
|The number of elastic IP addresses \(EIPs\) that can be associated with a NAT gateway|20. You can associate up to 10 pay-by-data-transfer EIPs with a NAT gateway.|Go to the [Quota Management](https://vpc.console.aliyun.com/quota) page to increase the quota. For more information, see [Quota management](/intl.en-US/User Guide/Common Configurations/Quota management.md). |
|The maximum number of pay-by-data-transfer EIPs that can be associated with a NAT gateway|10.|
|Create a NAT gateway for a VPC that contains a custom route entry whose destination CIDR block is 0.0.0.0/0|-   You can create enhanced NAT gateways for the VPC.
-   You cannot create standard NAT gateways for the VPC.

**Note:** To create standard NAT gateways for the VPC, you must first delete the custom route entry whose destination CIDR block is 0.0.0.0/0.


|N/A|

## Limits on Source Network Address Translation \(SNAT\)

|Item|Limit|Adjustable|
|----|-----|----------|
|The maximum number of SNAT entries that can be added to a NAT gateway|40.|Go to the [Quota Management](https://vpc.console.aliyun.com/quota) page to increase the quota. For more information, see [Quota management](/intl.en-US/User Guide/Common Configurations/Quota management.md). |
|The maximum number of EIPs that can be specified in an SNAT entry|64.|N/A|
|The bandwidth of a VSwitch is limited by the maximum bandwidth of the EIPs in the SNAT entry that is created for the VSwitch|Yes.**Note:** If the EIPs are added to an EIP bandwidth plan, the bandwidth of the VSwitch is limited by the maximum bandwidth of the EIP bandwidth plan.

|N/A|
|Use an EIP for both SNAT and DNAT|-   Enhanced NAT gateway: You can specify an EIP in both a SNAT entry and a DNAT entry when your account is included in the whitelist of NAT Gateway. To apply for a whitelist,[submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex).
-   Standard NAT gateway: You cannot specify an EIP in both a SNAT entry and a DNAT entry. |
|The maximum number of concurrent connections is limited by the number of EIPs specified in the SNAT entry|ECS instances in a VPC may access the same destination IP address and port on the Internet through a NAT gateway. If these ECS instances are not assigned static public IP addresses or EIPs, the maximum number of concurrent connections that the NAT gateway supports depends on the number of EIPs in the SNAT entry. -   If only one EIP is specified, the maximum number of concurrent connections that the NAT gateway supports is 55,000.
-   If multiple EIPs are specified, the maximum number of concurrent connections that the NAT gateway supports is N × 55,000. N represents the number of the EIPs. |
|The maximum bandwidth supported by each EIP in a SNAT entry|If you select multiple EIPs to create a SNAT IP address pool, make sure that you have added these EIPs to the same EIP bandwidth plan. The maximum bandwidth for each public IP address in a SNAT IP address pool is 200 Mbit/s. To maximize the usage of your EIP bandwidth plan and avoid port conflicts caused by insufficient EIPs, we recommend that you add EIPs to the SNAT IP address pool. When you add EIPs to the SNAT IP address pool, take note of the following rules: -   If the maximum bandwidth of the EIP bandwidth plan is 1,024 Mbit/s, specify at least five EIPs in each SNAT entry.
-   If the maximum bandwidth of the EIP bandwidth plan exceeds 1,024 Mbit/s, specify one additional EIP in every SNAT entry for every 200 Mbit/s that exceeds 1,024 Mbit/s.

For more information, see [Create a SNAT IP address pool](/intl.en-US/Best Practices/Create a SNAT IP address pool.md). |

**Note:** If you use the SNAT feature and have added the EIPs in the SNAT IP address pool to an EIP bandwidth plan, transient connection errors may occur when you make the following changes to the maximum bandwidth of the EIP bandwidth plan:

-   Change the maximum bandwidth from a value lower than 1 Gbit/s to a value higher than 1 Gbit/s.
-   Change the maximum bandwidth from a value higher than 1 Gbit/s to a value lower than 1 Gbit/s.

We recommend that you enable automatic reconnection for your workloads to minimize the impacts of transient connection errors.

## Limits on Destination Network Address Translation \(DNAT\)

|Item|Limit|Adjustable|
|----|-----|----------|
|The maximum number of DNAT entries that can be added to a NAT gateway|100.|Go to the [Quota Management](https://vpc.console.aliyun.com/quota) page to increase the quota. For more information, see [Quota management](/intl.en-US/User Guide/Common Configurations/Quota management.md). |
|Use an EIP for both SNAT and DNAT|-   Enhanced NAT gateway: You can specify an EIP in both a SNAT entry and a DNAT entry when your account is included in the whitelist of NAT Gateway. To apply for a whitelist,[submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex).
-   Standard NAT gateway: You cannot specify an EIP in both a SNAT entry and a DNAT entry.

|N/A|
|Create DNAT entries for ECS instances that are associated with EIPs|Not supported.Before you can create DNAT entries for the ECS instances, disassociate the EIPs from the ECS instances. For more information, see [Disassociate an EIP from a cloud resource](/intl.en-US/User Guide/Disassociate an EIP from a cloud resource.md) and [Create a DNAT entry](/intl.en-US/User Guide/DNAT/Create a DNAT entry.md).

**Note:** If you have added DNAT entries to an ECS instance that is associated with an EIP, the ECS instance preferentially uses the EIP to communicate with the Internet. |

