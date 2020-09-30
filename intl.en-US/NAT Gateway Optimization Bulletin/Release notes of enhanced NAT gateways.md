# Release notes of enhanced NAT gateways

Alibaba Cloud released enhanced NAT gateways that support all features of standard NAT gateways. Compared with standard NAT gateways, enhanced NAT gateways use an upgraded technical architecture. This ensures higher elasticity and stability, and allows you to better manage network traffic transmitted over the Internet.

**Note:** Enhanced NAT gateways are available in all regions except Australia \(Sydney\).

## Overview of enhanced NAT gateways

Enhanced NAT gateways support all features of standard NAT gateways, including basic features such as destination network address translation \(DNAT\) and source network address translation \(SNAT\). Enhanced NAT gateways provide new features in addition to the features provided by standard NAT gateways. The new features include:

-   More metrics for data transfer monitoring

    Up to 22 metrics are collected for you to monitor data transfer in real time and ensure system stability. For more information, see [View monitoring data](/intl.en-US/Deployment & Maintenance/View monitoring data.md).

-   Multiple NAT gateways for one VPC network

    You can create multiple enhanced NAT gateways for one VPC network to forward traffic to different IP addresses. Then, you can better manage traffic destined for the Internet. You can also use different services to protect each gateway based on your requirements.

    You can also specify the same SNAT or DNAT entry on different NAT gateways, and configure routes to forward network traffic to a specific egress.

    **Note:** To replace a standard NAT gateway with an enhanced NAT gateway, you must reconfigure the routes. This may cause transient connection errors. We recommend that you reconfigure the routes during off-peak hours.

-   Pay-by-data-transfer

    Enhanced NAT gateways are billed on a pay-as-you-go basis instead of pay-by-specification. Therefore, you can choose enhanced NAT gateways to acquire higher performance with lower costs.

    **Note:** Only enhanced NAT gateways in the Germany \(Frankfurt\) and UK \(London\) regions can be billed on a pay-by-data-transfer basis.

    ![Cost comparison](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/7952230061/p161421.png)


## Comparison between enhanced NAT gateways and standard NAT gateways

The following tables list differences and similarities in features and limits between enhanced NAT gateways and standard NAT gateways.

**Note:** "—" indicates that this feature is not supported. "✔" indicates that this feature is supported.

|Feature|Enhanced NAT gateway|Standard NAT gateway|
|-------|--------------------|--------------------|
|Multiple NAT gateways for one VPC network|✔|—|
|Available to be associated with a VSwitch|✔|—|
|Pay-by-data-transfer|✔|—|
|Billed on an hourly basis|✔|—|
|Processing TCP, UDP, and ICMP segments|✔|—|
|Metric|22|4|
|Available to be associated with multiple elastic IP addresses \(EIPs\)|✔|✔|
|SNAT|✔|✔|
|Creating multiple SNAT entries for an SNAT table|✔|✔|
|Associating an SNAT table with multiple EIPs|✔|✔|
|DNAT|✔|✔|
|DNAT Port mapping|✔|✔|
|DNAT IP mapping|✔|✔|
|Subscription|✔|✔|
|Billed on a daily basis|—|✔|

|Item|Enhanced NAT gateway|Standard NAT gateway|
|----|--------------------|--------------------|
|Number of NAT gateways that can be created for a VPC network|5 \(To increase the quota,[submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex).\)|1 \(Not adjustable\)|
|Using a public IP address for both SNAT and DNAT|Not supported \(Not adjustable\)|Not supported \(Not adjustable\)|
|The maximum number of DNAT entries that can be added to a NAT gateway|100 \(To increase the quota, see [Quota management](/intl.en-US/Common Configurations/Quota management.md).\)|100 \(To increase the quota, see [Quota management](/intl.en-US/Common Configurations/Quota management.md).\)|
|The maximum number of SNAT entries that can be added to a NAT gateway|40 \(To increase the quota, see [Quota management](/intl.en-US/Common Configurations/Quota management.md).\)|40 \(To increase the quota, see [Quota management](/intl.en-US/Common Configurations/Quota management.md).\)|
|The maximum number of public IP addresses that can be associated with a SNAT entry|64 \(Not adjustable\)|64 \(Not adjustable\)|
|Creating a NAT gateway for a VPC network that contains a custom route entry whose destination CIDR block is 0.0.0.0/0|Supported|No \(You must delete the custom route entry 0.0.0.0/0 before you can create a NAT gateway for the VPC network\)|
|Limits on VSwitch by the maximum bandwidth of the EIPs specified in the SNAT entry that is added to the VSwitch|Yes \(If the EIP is associated with an EIP bandwidth plan, the VSwitch is limited by the maximum bandwidth of the EIP bandwidth plan\)|Yes \(If the EIP is associated with an EIP bandwidth plan, the VSwitch is limited by the maximum bandwidth of the EIP bandwidth plan\)|
|Number of EIPs that can be associated with a NAT gateway|20 \(To increase the quota, see [Quota management](/intl.en-US/Common Configurations/Quota management.md)\)|20 \(To increase the quota, see [Quota management](/intl.en-US/Common Configurations/Quota management.md)\)|
|The maximum number of pay-by-data-transfer EIPs that can be associated with a NAT gateway|10 \(To increase the quota, see [Quota management](/intl.en-US/Common Configurations/Quota management.md)\)|10 \(To increase the quota, see [Quota management](/intl.en-US/Common Configurations/Quota management.md)\)|
|The maximum bandwidth supported by a pay-by-data-transfer EIP that is associated with a NAT gateway|200 Mbit/s \(Not adjustable\)|200 Mbit/s \(Not adjustable\)|
|The maximum bandwidth of a NAT gateway|5 Gbit/s \(If the total bandwidth of the EIPs or EIP bandwidth plans is greater than 5 Gbit/s,[submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex) to increase the quota.\)|A NAT gateway does not have a bandwidth limit. The bandwidth limit depends on the bandwidth of the EIPs that are associated with a SNAT entry or a DNAT entry, and the bandwidth of the EIP bandwidth plans to which the EIPs are added. For example, you create a SNAT entry for a NAT gateway, and associate the SNAT entry with five pay-by-data-transfer EIPs and two pay-by-bandwidth EIPs with 500 Mbit/s bandwidth each. The bandwidth of the NAT gateway is limited to 5 × 200 Mbit/s + 2 × 500 Mbit/s = 2,000 Mbit/s. If the seven EIPs are added to the same EIP bandwidth plan, and the bandwidth of the EIP bandwidth plan is limited to 1,000 Mbit/s, the bandwidth limit of the NAT gateway is 1,000 Mbit/s. |
|The maximum number of concurrent connections for an EIP is 55,000.|Yes|Yes|
|The maximum bandwidth of an EIP in an EIP bandwidth plan is 200 Mbit/s.|No|Yes|
|Users of NAT bandwidth plans are not allowed to associate EIPs with NAT gateways.|Yes|Yes|
|Transient connection errors occur when you change the maximum bandwidth of the EIP bandwidth plan that is associated with a NAT gateway. For example, you upgrade the maximum bandwidth from less than 1 Gbit/s to greater than 1 Gbit/s, or downgrade the maximum bandwidth from greater than 1 Gbit/s to less than 1 Gbit/s.|No|Yes|
|Transient connection errors occur because IP addresses in the existing SNAT entries are reduced.|Yes|Yes|
|Transient connection errors occur because IP addresses in the existing SNAT entries are increased.|No|Yes|

## Configure an enhanced NAT gateway

Enhanced NAT gateways are used in the same way as standard NAT gateways. However, when you create an enhanced NAT gateway, you must specify the gateway type, and the VPC network and VSwitch to be associated with the enhanced NAT gateway. After the enhanced NAT gateway is created, the system assigns an idle private IP address of the VSwitch to the enhanced NAT gateway.

**Note:** If you want to create an enhanced NAT gateway as a RAM user, you must use your Alibaba Cloud account to authorize the RAM user first. [Authorize a RAM user](https://ram.console.aliyun.com/#/role/authorize?request=%7B%22Requests%22:%20%7B%22request1%22:%20%7B%22RoleName%22:%20%22AliyunNATAccessingNetworkInterfaceRole%22,%20%22TemplateId%22:%20%22ENIRole%22%7D%7D,%20%22ReturnUrl%22:%20%22https:%2F%2Fvpc.console.aliyun.com%2Fnat%22,%20%22Service%22:%20%22NAT%22%7D).

![Create an enhanced NAT gateway](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/5216645951/p101531.png)

The following figure shows how to use an enhanced NAT gateway.

![NAT 2.0 workflow](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/5216645951/p101647.png)

