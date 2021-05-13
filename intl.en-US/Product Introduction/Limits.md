---
keyword: [NAT Gateway, limits, SNAT, DNAT]
---

# Limits

This topic describes the limits on NAT Gateway and how to increase quotas.

## Limits on NAT gateways

|Item|Limit|Adjustable|
|----|-----|----------|
|The maximum number of enhanced NAT gateways that can be created for a virtual private cloud \(VPC\)|5|[Submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex).|
|The maximum number of standard NAT gateways that can be created for a VPC|1|N/A|
|The maximum number of elastic IP addresses \(EIPs\) that can be associated with a NAT gateway|20. You can associate up to 10 pay-by-data-transfer EIPs with a NAT gateway.|To increase the quota, go to the [Quota Management](https://vpc.console.aliyun.com/quota) page. For more information, see [Quota management](/intl.en-US/Common Configurations/Quota management.md). |
|The maximum number of pay-by-data-transfer EIPs that can be associated with a NAT gateway|10|
|Creating a NAT gateway for a VPC that contains a custom route entry whose destination CIDR block is 0.0.0.0/0|-   You can create enhanced NAT gateways for the VPC.
-   You cannot create standard NAT gateways for the VPC.

**Note:** If you want to create standard NAT gateways for the VPC, you must first delete the custom route entry whose destination CIDR block is 0.0.0.0/0.


|N/A|

## Limits on SNAT

|Item|Limit|Adjustable|
|----|-----|----------|
|The maximum number of Source Network Address Translation \(SNAT\) entries that can be added to a NAT gateway|40|To increase the quota, go to the [Quota Management](https://vpc.console.aliyun.com/quota) page. For more information, see [Quota management](/intl.en-US/Common Configurations/Quota management.md). |
|The maximum number of EIPs that can be specified in a SNAT entry|64|N/A|
|Limits on a vSwitch by the bandwidth limit of the EIPs in the SNAT entry that is added to the vSwitch|Yes **Note:** If the EIPs are added to an EIP bandwidth plan, the bandwidth of the vSwitch is limited by the bandwidth limit of the EIP bandwidth plan.

|N/A|
|The maximum number of concurrent connections is limited by the number of EIPs specified in the SNAT entry|Elastic Compute Service \(ECS\) instances in a VPC may access the same destination IP address and port on the Internet by using a NAT gateway. If static public IP addresses or EIPs are not associated with the ECS instances, the maximum number of concurrent connections that the NAT gateway supports is based on the number of EIPs in the SNAT entry. -   If only one EIP is specified, the maximum number of concurrent connections that the NAT gateway supports is 55,000.
-   If multiple EIPs are specified in the SNAT entry, the maximum number of concurrent connections that the NAT gateway supports is N × 55,000. In this formula, N represents the number of the EIPs. |
|The bandwidth limit of each EIP in a SNAT entry|If you select multiple EIPs to create a SNAT IP address pool, make sure that you associate these EIPs with the same EIP bandwidth plan. -   For enhanced NAT gateways, the bandwidth limit of EIPs that are added to the SNAT IP address pool is not limited.
-   The bandwidth limit of each EIP in a SNAT IP address pool is 200 Mbit/s. To maximize the usage of your EIP bandwidth plan and avoid port conflicts caused by insufficient EIPs, we recommend that you add EIPs to the SNAT IP address pool. When you add EIPs to the SNAT IP address pool, take note of the following rules:
    -   If the bandwidth limit of the EIP bandwidth plan is 1,024 Mbit/s, specify at least five EIPs in each SNAT entry.
    -   If the bandwidth limit of the EIP bandwidth plan exceeds 1,024 Mbit/s, specify one additional EIP in every SNAT entry for every 200 Mbit/s that exceeds 1,024 Mbit/s.

For more information, see [Create a SNAT IP address pool](/intl.en-US/Best Practices/Create a SNAT IP address pool.md). |

**Note:** If you enable SNAT and associate EIPs in the SNAT IP address pool with an EIP bandwidth plan, do not make the following changes. If you make the following changes to the bandwidth limit of the EIP bandwidth plan, your service may be temporarily interrupted:

-   Change the bandwidth limit from a value that is smaller than 1 Gbit/s to a value that is larger than 1 Gbit/s.
-   Change the bandwidth limit from a value that is larger than 1 Gbit/s to a value that is smaller than 1 Gbit/s.

We recommend that you enable automatic reconnection for your workloads to minimize the impact of service interruptions.

## Limits on DNAT

|Item|Limit|Adjustable|
|----|-----|----------|
|The maximum number of DNAT entries that can be added to a NAT gateway|100|To increase the quota, go to the [Quota Management](https://vpc.console.aliyun.com/quota) page. For more information, see [Quota management](/intl.en-US/Common Configurations/Quota management.md). |
|Creating DNAT entries for ECS instances with which EIPs are associated|Not supported. Before you can create DNAT entries for the ECS instances, disassociate the EIPs from the ECS instances. For more information, see [Disassociate an EIP from a cloud resource](/intl.en-US/User Guide/Disassociate an EIP from a cloud resource.md) and [Create a DNAT entry to provide Internet-facing services](/intl.en-US/User Guide/Create a DNAT entry to provide Internet-facing services.md).

**Note:** If you add DNAT entries to an ECS instance with which an EIP is associated, the ECS instance preferably uses the EIP to communicate with the Internet.

|N/A|

