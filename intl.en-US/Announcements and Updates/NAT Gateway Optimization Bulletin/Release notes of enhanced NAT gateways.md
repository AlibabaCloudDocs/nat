# Release notes of enhanced NAT gateways

Alibaba Cloud has released enhanced NAT gateways. Enhanced NAT gateways are upgraded from the technical architecture of standard NAT gateways and have the following features: higher performance, higher elasticity, flexible billing, and fine-grained maintenance. Enhanced NAT gateways optimizes the management of network traffic transmitted over the Internet.

**Note:** Enhanced NAT gateways are available in all regions except Australia \(Sydney\).

## Overview of enhanced NAT gateways

Enhanced NAT gateways and standard NAT gateways all support basic features such as destination network address translation \(DNAT\) and source network address translation \(SNAT\). Enhanced NAT gateways provide new features in addition to the features of standard NAT gateways. The new features include:

-   More metrics for data transfer monitoring

    Up to 22 metrics are collected for you to monitor data transfer in real time and ensure system stability. For more information, see [View monitoring data]().

-   Multiple NAT gateways for one virtual private cloud \(VPC\)

    You can create multiple enhanced NAT gateways for one VPC to forward traffic to different IP addresses. Then, you can better manage traffic destined for the Internet. You can also use different services to protect each gateway based on your requirements.

    You can also create the same SNAT or DNAT entry on different NAT gateways, and configure routes to forward network traffic to a specific egress.

    **Note:** To replace a standard NAT gateway with an enhanced NAT gateway, you must reconfigure the routes. This may cause transient connection errors. We recommend that you reconfigure the routes during off-peak hours.

-   Pay-by-data-transfer metering method
    -   Compared with the pay-by-specification metering method, the pay-by-data-transfer metering method is more cost-effective.

        **Note:** You can purchase enhanced NAT gateways that are charged on a pay-by-data-transfer basis in the following regions: China \(Shanghai\), China \(Beijing\), China \(Zhangjiakou-Beijing Winter Olympics\), China \(Hohhot\), China \(Ulanqab\), China \(Heyuan\), China \(Chengdu\), Singapore \(Singapore\), Malaysia \(Kuala Lumpur\), India \(Mumbai\), Indonesia \(Jakarta\), Germany \(Frankfurt\), and UK \(London\).

        ![Cost comparison](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/7952230061/p161421.png)

    -   Enhanced NAT gateways support the pay-by-data-transfer metering method and provide the optimal performance to process traffic spikes. The following table describes the performances between pay-by-data-transfer NAT gateways and pay-by-specification NAT gateways.

        |Metering method|Maximum number of connections|Number of new connections per second|Throughput|
        |---------------|-----------------------------|------------------------------------|----------|
        |Pay-by-data-transfer|Supports up to 5,000,000 SNAT connections|Supports up to 1,000,000 SNAT connections|5 Gbps|
        |Pay-by-specification|The maximum number of connections depends on the size of the NAT gateway and cannot be adjusted:        -   Small: 10,000
        -   Medium: 50,000
        -   Large: 200,000
        -   Super Large-1: 1,000,000
|The number of new connections per second depends on the size of the NAT gateway and cannot be adjusted:        -   Small: 1,000
        -   Medium: 5,000
        -   Large: 10,000
        -   Super Large-1: 50,000
|Not limited|


## Comparison between enhanced NAT gateways and standard NAT gateways

The following tables describe differences and similarities in features and limits between enhanced NAT gateways and standard NAT gateways.

**Note:** A hyphen "-" indicates that this feature is not supported. A tick "√" indicates that this feature is supported.

|Feature|Enhanced NAT gateway|Standard NAT gateway|
|-------|--------------------|--------------------|
|Multiple NAT gateways for one VPC|✔|-|
|Attach a NAT gateway to a VSwitch|✔|-|
|Pay-by-data-transfer|✔|-|
|Billed on an hourly basis|✔|-|
|Process TCP, UDP, and ICMP segments|✔|-|
|Metric|22|4|
|Traffic monitoring|✔|-|
|Associate multiple elastic IP addresses \(EIPs\) with a NAT gateway|✔|✔|
|SNAT|✔|✔|
|Create multiple SNAT entries for an SNAT table|✔|✔|
|Associate an SNAT table with multiple EIPs|✔|✔|
|DNAT|✔|✔|
|DNAT port mapping|✔|✔|
|DNAT IP mapping|✔|✔|
|Subscription|✔|✔|
|Billed on a daily basis|-|✔|

|Item|Enhanced NAT gateway|Standard NAT gateway|
|----|--------------------|--------------------|
|The maximum number of NAT gateways that can be created for a VPC|5. To increase the quota,[submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex).|1 \(not adjustable\)|
|Use a public IP address for both SNAT and DNAT|Only selected users can use a public IP address for both SNAT and DNAT. To apply for a whitelist,[submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex)|Not supported \(not adjustable\)|
|The maximum number of DNAT entries that can be added to a NAT gateway|100. To increase the quota, see [Quota management]().|100. To increase the quota, see [Quota management]().|
|The maximum number of SNAT entries that can be added to a NAT gateway|40. To increase the quota, see [Quota management]().|40. To increase the quota, see [Quota management]().|
|The maximum number of public IP addresses that can be associated with a SNAT entry|64 \(not adjustable\)|64 \(not adjustable\)|
|Create a NAT gateway for a VPC that contains a custom route entry whose destination CIDR block is 0.0.0.0/0|Supported|No. You must delete the custom route entry whose destination CIDR block is 0.0.0.0/0 before you can create a NAT gateway for the VPC.|
|Limits on VSwitch by the maximum bandwidth of the EIPs specified in the SNAT entry that is added to the VSwitch|Yes. If the EIP is associated with an EIP bandwidth plan, the VSwitch is limited by the maximum bandwidth of the EIP bandwidth plan.|Yes. If the EIP is associated with an EIP bandwidth plan, the VSwitch is limited by the maximum bandwidth of the EIP bandwidth plan.|
|The maximum number of EIPs that can be associated with a NAT gateway|20. To increase the quota, see [Quota management]().|20. To increase the quota, see [Quota management]().|
|The maximum number of pay-by-data-transfer EIPs that can be associated with a NAT gateway|10. To increase the quota, see [Quota management]().|10. To increase the quota, see [Quota management]().|
|The maximum bandwidth supported by a pay-by-data-transfer EIP that is associated with a NAT gateway|200 Mbit/s \(not adjustable\)|200 Mbit/s \(not adjustable\)|
|The maximum bandwidth of a NAT gateway|5 Gbit/s. If the total bandwidth of the EIPs or EIP bandwidth plans is greater than 5 Gbit/s,[submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex) to increase the quota.|A NAT gateway does not have a bandwidth limit. The bandwidth limit depends on the bandwidth of the EIPs that are associated with a SNAT entry or a DNAT entry, and the bandwidth of the EIP bandwidth plans to which the EIPs are added. For example, you create a SNAT entry for a NAT gateway, and associate the SNAT entry with five pay-by-data-transfer EIPs and two pay-by-bandwidth EIPs with 500 Mbit/s bandwidth each. The bandwidth of the NAT gateway is limited to 5 × 200 Mbit/s + 2 × 500 Mbit/s = 2,000 Mbit/s. If the seven EIPs are added to the same EIP bandwidth plan, and the bandwidth of the EIP bandwidth plan is limited to 1,000 Mbit/s, the bandwidth limit of the NAT gateway is 1,000 Mbit/s. |
|The maximum number of concurrent connections for an EIP is 55,000|Yes|Yes|
|The maximum bandwidth of an EIP in an EIP bandwidth plan is 200 Mbit/s|No|Yes|
|Users of NAT bandwidth plans are not allowed to associate EIPs with NAT gateways|Yes|Yes|
|Transient connection errors occur when you change the maximum bandwidth of the EIP bandwidth plan that is associated with a NAT gateway. For example, you upgrade the maximum bandwidth from less than 1 Gbit/s to greater than 1 Gbit/s, or downgrade the maximum bandwidth from greater than 1 Gbit/s to less than 1 Gbit/s|No|Yes|
|Transient connection errors occur because IP addresses in the existing SNAT entries are reduced|Yes|Yes|
|Transient connection errors occur because IP addresses in the existing SNAT entries are increased|No|Yes|

## Configure an enhanced NAT gateway

Enhanced NAT gateways are used in the same way as standard NAT gateways. However, when you create an enhanced NAT gateway, you must specify the gateway type, and the VPC and VSwitch to be associated with the enhanced NAT gateway. After the enhanced NAT gateway is created, the system assigns an idle private IP address of the VSwitch to the enhanced NAT gateway.

**Note:** To create an enhanced NAT gateway as a RAM user, you must first use your Alibaba Cloud account to authorize the RAM user first. [Authorize a RAM user](https://ram.console.aliyun.com/#/role/authorize?request=%7B%22Requests%22:%20%7B%22request1%22:%20%7B%22RoleName%22:%20%22AliyunNATAccessingNetworkInterfaceRole%22,%20%22TemplateId%22:%20%22ENIRole%22%7D%7D,%20%22ReturnUrl%22:%20%22https:%2F%2Fvpc.console.aliyun.com%2Fnat%22,%20%22Service%22:%20%22NAT%22%7D).

![Create an enhanced NAT gateway](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/5216645951/p101531.png)

The following figure shows how to use an enhanced NAT gateway.

![NAT 2.0 workflow](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/5216645951/p101647.png)

