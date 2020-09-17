# Overview

Network Address Translation \(NAT\) gateways are enterprise-class public network gateways. NAT gateways provide network address translation services \(SNAT and DNAT\), with a throughput capacity of up to10 Gbit/s. NAT gateways can also be used in cross-zone disaster recovery.

![Diagram](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/4158409951/p4440.png)

## Types of NAT gateways

Two types of NAT gateways are available: standard NAT gateways and enhanced NAT gateways. Enhanced NAT gateways support all features of standard NAT gateways. Enhanced NAT gateways are developed with an upgraded technical architecture. Compared with standard NAT gateways, enhanced NAT gateways offer high elasticity and stability. This helps you manage data transfer in a more efficient way.

**Note:** Enhanced NAT gateways are available in regions other than Australia \(Sydney\), US \(Silicon Valley\), UAE \(Dubai\), and Japan \(Tokyo\).

The following table lists the features of enhanced NAT gateways and standard NAT gateways.

|Feature|Enhanced NAT gateway|Standard NAT gateway|
|-------|--------------------|--------------------|
|Multiple NAT gateways for one VPC network|✔|—|
|Associate a NAT gateway with a VSwitch|✔|—|
|Pay-by-data-transfer|✔|—|
|Hourly billing cycle|✔|—|
|Process TCP, UDP, and ICMP segments|✔|—|
|Metric|22|4|
|Associate a NAT gateway with multiple elastic IP addresses \(EIPs\)|✔|✔|
|SNAT|✔|✔|
|Create multiple SNAT entries for a SNAT table|✔|✔|
|Associate a SNAT table with multiple EIPs|✔|✔|
|DNAT|✔|✔|
|Port mapping|✔|✔|
|IP mapping|✔|✔|
|Subscription|✔|✔|
|Daily billing cycle|—|✔|

|Item|Enhanced NAT gateway|Standard NAT gateway|
|----|--------------------|--------------------|
|The maximum number of NAT gateways that can be created for a VPC network|5 \([Submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex) to increase the quota\)|1 \(Not adjustable\)|
|Using a public IP address for both SNAT and DNAT|Not supported \(Not adjustable\)|Not supported \(Not adjustable\)|
|The maximum number of DNAT entries that can be added to a NAT gateway|100 \(To increase the quota, see [Manage quotas](/intl.en-US/Common Configurations/Manage quotas.md)\)|100 \(To increase the quota, see [Manage quotas](/intl.en-US/Common Configurations/Manage quotas.md)\)|
|The maximum number of SNAT entries that can be added to a NAT gateway|40 \(To increase the quota, see [Manage quotas](/intl.en-US/Common Configurations/Manage quotas.md)\)|40 \(To increase the quota, see [Manage quotas](/intl.en-US/Common Configurations/Manage quotas.md)\)|
|The maximum number of public IP addresses that can be associated with a SNAT entry|64 \(Not adjustable\)|64 \(Not adjustable\)|
|Creating a NAT gateway for a VPC network that contains a custom route entry whose destination CIDR block is 0.0.0.0/0|Supported|No \(You must delete the custom route entry 0.0.0.0/0 before you can create a NAT gateway for the VPC network\)|
|Limits on VSwitch by the maximum bandwidth of the EIPs specified in the SNAT entry that is added to the VSwitch|Yes \(If the EIP is added to an EIP bandwidth plan, the VSwitch is limited by the maximum bandwidth of the EIP bandwidth plan\)|Yes \(If the EIP is added to an EIP bandwidth plan, the VSwitch is limited by the maximum bandwidth of the EIP bandwidth plan\)|
|The maximum number of EIPs that can be associated with a NAT gateway|20 \(To increase the quota, see [Manage quotas](/intl.en-US/Common Configurations/Manage quotas.md)\)|20 \(To increase the quota, see [Manage quotas](/intl.en-US/Common Configurations/Manage quotas.md)\)|
|The maximum number of pay-by-data-transfer EIPs that can be associated with a NAT gateway|10 \(To increase the quota, see [Manage quotas](/intl.en-US/Common Configurations/Manage quotas.md)\)|10 \(To increase the quota, see [Manage quotas](/intl.en-US/Common Configurations/Manage quotas.md)\)|
|The maximum bandwidth supported by a pay-by-data-transfer EIP that is associated with a NAT gateway|200 Mbit/s \(Not adjustable\)|200 Mbit/s \(Not adjustable\)|
|The maximum bandwidth of a NAT gateway|5 Gbit/s \(If the total bandwidth of the EIPs or EIP bandwidth plans that are associated with the VSwitch is greater than 5 Gbit/s, [submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex) to increase the quota\)|A NAT gateway does not have a bandwidth limit. The bandwidth limit depends on the bandwidth of the EIPs that are associated with a SNAT entry or a DNAT entry, and the bandwidth of the EIP bandwidth plans to which the EIPs are added. For example, you create a SNAT entry for a NAT gateway, and associate the SNAT entry with five pay-by-data-transfer EIPs and two pay-by-bandwidth EIPs with 500 Mbit/s bandwidth each. The bandwidth of the NAT gateway is limited to 5 × 200 Mbit/s + 2 × 500 Mbit/s = 2,000 Mbit/s. If the seven EIPs are added to the same EIP bandwidth plan, and the bandwidth of the EIP bandwidth plan is limited to 1,000 Mbit/s, the bandwidth limit of the NAT gateway is 1,000 Mbit/s. |
|The maximum number of concurrent connections for an EIP is 55,000.|Yes|Yes|
|The maximum bandwidth of an EIP in an EIP bandwidth plan is 200 Mbit/s.|No|Yes|
|Users of NAT bandwidth plans are not allowed to associate EIPs with NAT gateways.|Yes|Yes|
|Transient connection errors occur when you change the maximum bandwidth of the EIP bandwidth plan that is associated with a NAT gateway. For example, you upgrade the maximum bandwidth from less than 1 Gbit/s to greater than 1 Gbit/s, or downgrade the maximum bandwidth from greater than 1 Gbit/s to less than 1 Gbit/s.|No|Yes|
|Transient connection errors occur because IP addresses in the existing SNAT entries are reduced.|Yes|Yes|
|Transient connection errors occur because IP addresses in the existing SNAT entries are increased.|No|Yes|

## Sizes of NAT gateways

NAT gateways are available in multiple sizes, including small, middle, large, and super large-1 sizes. The sizes of NAT gateways determine the maximum number of Source Network Address Translation \(SNAT\) connections and the number of new SNAT connections per second \(CPS\). However, Destination Network Address Translation \(DNAT\) is not affected by the sizes of NAT gateways. The following table lists the available sizes of NAT gateways.

|Size|Maximum number of SNAT connections|Number of new SNAT connections per second|
|:---|:---------------------------------|:----------------------------------------|
|Small|10,000|1,000|
|Medium|50,000|5,000|
|Large|200,000|10,000|
|Super large-1|1,000,000|50,000|

When you specify the size of a NAT gateway, note that:

-   The sizes of NAT gateways and those of EIP bandwidth plans do not affect each other.
-   Cloud Monitor monitors only the maximum number of SNAT connections for NAT gateways. It does not monitor the number of new SNAT connections per second.
-   The timeout of SNAT connections on NAT gateways is 900 seconds.
-   To avoid the timeout of SNAT connections caused by network congestion and Internet instability, make sure that your applications support automatic reconnection.
-   NAT gateways do not support packet fragmentation.
-   For the same destination public IP address and port, the number of elastic IP addresses \(EIPs\) that are associated with a NAT gateway determines the maximum number of concurrent connections. Each EIP that is associated with a NAT gateway supports up to 55,000 concurrent connections. If N EIPs are associated with a NAT gateway, the maximum number of concurrent connections that the NAT gateway supports is N × 55,000.
-   Assume that you have multiple Elastic Compute Service \(ECS\) instances that are deployed in a Virtual Private Cloud \(VPC\) network, and the ECS instances are not assigned public IP addresses. The ECS instances access the same destination IP address and port on the Internet through a NAT gateway at a bandwidth higher than 2 Gbit/s. To avoid packet loss caused by the upper limit of ports for each public IP address, we recommend that you assign 4 to 8 public IP addresses to the NAT gateway and create a SNAT address pool.

