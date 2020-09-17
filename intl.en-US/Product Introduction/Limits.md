# Limits

This topic describes the limits on Network Address Translation \(NAT\) gateways and the limits on associating elastic IP addresses \(EIPs\) with NAT gateways.

## Limits on NAT gateways

|Item|Limit|Adjustable|
|----|-----|----------|
|The number of standard NAT gateways that can be configured for a Virtual Private Cloud \(VPC\) network|1|N/A|
|The number of enhanced NAT gateways that can be configured for a VPC network|5|To increase the quota, [submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex).|
|The number of DNAT entries that can be configured for a NAT gateway|100|Go to the [Quota Management](https://vpc.console.aliyun.com/quota) page and request a quota increase. For more information, see [Manage quotas](/intl.en-US/Common Configurations/Manage quotas.md). |
|The number of SNAT entries that can be configured for a NAT gateway|40|
|Using an EIP for both SNAT and DNAT|Not supported|N/A|
|The number of EIPs that can be configured for a SNAT entry|64|
|Creating a NAT gateway for a VPC network that contains a custom route entry whose destination CIDR block is 0.0.0.0/0|Not supported **Note:** You must delete the custom route entry with 0.0.0.0/0 as the destination CIDR block before you can create a NAT gateway for the VPC network. |
|Whether VSwitch bandwidth is limited by the maximum bandwidth of the associated EIPs after a SNAT entry is added to the VSwitch|Yes **Note:** If the EIPs are added to an EIP bandwidth plan, the VSwitch bandwidth is limited by the maximum bandwidth of the EIP bandwidth plan. |

## Limits on associating EIPs with NAT gateways

|Item|Limit|Adjustable|
|----|-----|----------|
|The number of EIPs that can be associated with a NAT gateway|20|Go to the [Quota Management](https://vpc.console.aliyun.com/quota) page to increase the quota. For more information, see [Manage quotas](/intl.en-US/Common Configurations/Manage quotas.md). |
|The number of pay-by-data-transfer EIPs that can be associated with a NAT gateway|10|
|The maximum bandwidth supported by a pay-by-data-transfer EIP that is associated with a NAT gateway|200Mbps|N/A|

## Additional limits

The following limits also apply to NAT gateways:

-   When multiple ECS instances in a VPC network access the same destination IP address and port on the Internet through a NAT gateway and the ECS instances are not assigned static public IP addresses or EIPs, the maximum number of concurrent connections supported by the NAT gateway is limited by the number of EIPs specified in the corresponding SNAT entry.
    -   If only one EIP is specified, the maximum number of concurrent connections supported by the NAT gateway is 55,000.
    -   If multiple EIPs are specified, the maximum number of concurrent connections supported by the NAT gateway is n × 55,000 \(n refers to the number of EIPs\).
-   The maximum bandwidth supported by each EIP in a SNAT address pool is 200 Mbit/s. To make full use of your EIP bandwidth plan and avoid port conflicts caused by insufficient EIPs, we recommend that you add EIPs to the SNAT address pool based on the following considerations:
    -   If the maximum bandwidth of the EIP bandwidth plan is 1,024 Mbit/s, configure at least five EIPs for each SNAT entry.
    -   If the maximum bandwidth of the EIP bandwidth plan is greater than 1,024 Mbit/s, configure another EIP for each SNAT entry for each additional 200 Mbit/s.
-   If you have purchased a NAT service plan for a NAT gateway before 23:59 January 26, 2018, you must associate static public IP addresses in the NAT service plan with the NAT gateway to provide the Internet access service. For more information about how to associate an EIP with a NAT gateway, see the [Why am I unable to associate an EIP with a NAT gateway in the NAT Gateway console](/intl.en-US/FAQ/EIP association FAQ.md) section in the FAQ topic.
-   If you use the SNAT feature and have added the EIPs in the SNAT address pool to an EIP service plan, your workloads may be interrupted intermittently when you make the following changes to the maximum bandwidth of the EIP bandwidth plan:

    -   Change the maximum bandwidth from a value lower than 1 Gbit/s to a value higher than 1 Gbit/s.
    -   Change the maximum bandwidth from a value higher than 1 Gbit/s to a value lower than 1 Gbit/s.
    We recommend that you implement automatic reconnection to minimize the impact of network disconnections on your business.

-   You cannot create DNAT entries for ECS instances that are associated with EIPs.

    To create DNAT entries for such ECS instances, you must disassociate the EIPs from the ECS instances first. After you delete the association, you can create DNAT entries for the ECS instances. For more information, see [Disassociate an EIP from a cloud resource](/intl.en-US/User Guide/Disassociate an EIP from a cloud resource.md) and [Create a DNAT entry](/intl.en-US/DNAT/Create a DNAT entry.md).

    **Note:** If you have added DNAT entries to an ECS instance that is associated with an EIP, the EIP prevails when the ECS instance communicates with the Internet.


