---
keyword: [NAT gateway, enhanced, network address translation, Internet-facing services, Internet access]
---

# Terms

Before you use NAT gateways, you must understand the terms that are described in this topic.

## NAT gateways

NAT gateways are enterprise-class gateways that provide the Source Network Address Translation \(SNAT\) and Destination Network Address Translation \(DNAT\) features. Each NAT gateway provides a throughput capacity of up to 10 Gbit/s. NAT gateways support cross-zone disaster recovery.

![Diagram](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8604485061/p4440.png)

NAT gateways are billed based on subscription and pay-as-you-go. Subscription NAT gateways support the pay-by-specification metering method. Pay-as-you-go NAT gateways support the pay-by-data-transfer metering method. The following tables describe the maximum number of concurrent connections and the number of new connections per second that are supported when you choose the two metering methods.

-   **Pay-by-specification**

    NAT gateways are available in multiple sizes, including small, medium, large, and super large-1. The size of a NAT gateway determines the SNAT performance, which includes the maximum number of concurrent connections and the number of new connections per second. However, the size of the NAT gateway does not affect DNAT performance. The following table describes the available sizes of NAT gateways.

    |Size|Maximum number of SNAT connections|Maximum number of new SNAT connections per second|
    |:---|:---------------------------------|:------------------------------------------------|
    |Small|10,000|1,000|
    |Medium|50,000|5,000|
    |Large|200,000|10,000|
    |Super Large-1|1,000,000|50,000|

-   **Pay-by-data-transfer**

    Pay-by-data-transfer NAT gateways offer high elasticity.

    |Size|Maximum number of SNAT connections|Maximum number of new SNAT connections per second|Throughput|
    |----|----------------------------------|-------------------------------------------------|----------|
    |Default size|2,000,000|100,000|5 Gbps|
    |Highest quota that you can apply for by [submitting a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex).|10,000,000|1,000,000|100 Gbps|


When you choose a gateway size, take note of the following features and limits:

-   The bandwidth limit of EIP bandwidth plans and the number of IP addresses that are associated with the EIP bandwidth plans are not limited by the size of the NAT gateway.
-   Cloud Monitor monitors only the maximum number of SNAT connections for NAT gateways. Cloud Monitor does not monitor the number of new SNAT connections per second.
-   The timeout period of SNAT connections on NAT gateways is 900 seconds.
-   To avoid the timeout of SNAT connections that is caused by network congestion or Internet instability, make sure that your applications support automatic reconnection.
-   NAT gateways do not support packet fragmentation.
-   For the same destination public IP address and port, the number of elastic IP addresses \(EIPs\) that are associated with a NAT gateway determines the maximum number of concurrent connections. Each EIP that is associated with a NAT gateway supports up to 55,000 concurrent connections. If multiple EIPs are associated with a NAT gateway, the maximum number of concurrent connections that the NAT gateway supports is N × 55,000.
-   For example, you have multiple Elastic Compute Service \(ECS\) instances that are deployed in a virtual private cloud \(VPC\). The ECS instances are not assigned public IP addresses. The ECS instances access the same destination IP address and port over the Internet by using a NAT gateway. The bandwidth provided by the NAT gateway is higher than 2 Gbit/s.To avoid packet loss that is caused by the upper limit of ports for each public IP address, we recommend that you create a SNAT address pool that contains four to eight public IP addresses for the NAT gateway.

References:

-   [Enhanced NAT gateways \(new\)](/intl.en-US/Enhanced NAT gateway/Enhanced NAT gateways (new).md)
-   [Comparison between enhanced NAT gateways and standard NAT gateways](/intl.en-US/Enhanced NAT gateway/Comparison between enhanced NAT gateways and standard NAT gateways.md)

## SNAT

SNAT allows multiple ECS instances in a VPC to use the same public IP address to access the Internet when no public IP address is associated with these ECS instances.

![Overview](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7274485061/p178164.png)

You can create SNAT entries for a vSwitch or an ECS instance:

-   Create a SNAT entry for a vSwitch

    If you create a SNAT entry for a vSwitch, the ECS instances that are attached to the vSwitch can access the Internet by using the IP address in the SNAT entry.

    **Note:** For example, if an ECS instance is assigned a static public IP address or an EIP, or configured with a DNAT IP mapping, the ECS instance uses the preceding method to access the Internet, instead of using the IP address in the SNAT entry.

-   Create a SNAT entry for an ECS instance

    If you create a SNAT entry for an ECS instance, only the specified ECS instance can access the Internet by using the SNAT IP in the SNAT entry.


References:

-   [Create a SNAT entry to access the Internet](/intl.en-US/User Guide/Create a SNAT entry to access the Internet.md)
-   [Configure ECS instances that are assigned static public IP addresses to use the same EIP to access the Internet](/intl.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Configure ECS instances that are assigned static public IP addresses to use the same EIP to access the Internet.md)
-   [Configure ECS instances that are assigned EIPs to use the same EIP to access the Internet](/intl.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Configure ECS instances that are assigned EIPs to use the same EIP to access the Internet.md)
-   [Configure ECS instances that use DNAT IP mapping to use the same EIP to access the Internet](/intl.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Configure ECS instances that use DNAT IP mapping to use the same EIP to access the
         Internet.md)

## DNAT

DNAT enables ECS instances in a VPC to provide Internet-facing services. DNAT maps DNAT IPs \(EIPs in DNAT entries\) to ECS instances in a VPC. Requests destined for the DNAT IPs are forwarded to the ECS instances based on the user-defined mappings.

![Architecture](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9754485061/p178170.png)

DNAT supports port mapping and IP mapping.

-   Port mapping

    After you configure port mapping on a NAT gateway, the NAT gateway forwards the requests that are destined for a DNAT IP to the specified ECS instance. The requests are forwarded based on the specified source and destination ports and the specified protocol used by the source and destination ports. The following table describes the examples of DNAT entries that are used as port mappings.

    |DNAT entry|Public IP address|External port|Private IP address|Internal port|Protocol|
    |:---------|:----------------|:------------|:-----------------|:------------|:-------|
    |Entry 1|1.x.x.1|80|192.168.1.1|80|TCP|
    |Entry 2|2.x.x.2|8080|192.168.1.2|8000|UDP|

    -   Entry 1: The NAT gateway forwards the requests that are received on TCP port 80 and destined for 1.x.x.1 to TCP port 80 of ECS instance 192.168.1.1.
    -   Entry 2: The NAT gateway forwards the requests that are received on UDP port 8080 and destined for 2.x.x.2 to UDP port 8000 of ECS instance 192.168.1.2.
-   IP mapping

    After you configure IP mapping on a NAT gateway, the NAT gateway forwards the requests that are destined for a DNAT IP to the specified ECS instance. The following table describes the examples of DNAT entries that are used as IP mappings.

    |DNAT entry|Public IP address|External port|Private IP address|Internal port|Protocol|
    |:---------|:----------------|:------------|:-----------------|:------------|:-------|
    |Entry 3|3.x.x.3|Any|192.168.1.3|Any|Any|

    Entry 3: The NAT gateway forwards the requests that are destined for 3.x.x.3 to ECS instance 192.168.1.3.


References:

[Create a DNAT entry to provide Internet-facing services](/intl.en-US/User Guide/Create a DNAT entry to provide Internet-facing services.md)

## Terms

-   EIPs

    An EIP is a public IP address that you can purchase and use as an independent resource. You can associate EIPs with the following network instances that are deployed in VPCs: ECS instances, internal-facing SLB instances, and secondary elastic network interfaces \(ENIs\). You can also associate EIPs with NAT gateways and high-availability virtual IP addresses \(HAVIPs\). For more information, see [What is an EIP?](/intl.en-US/.md)

-   EIP bandwidth plans

    You can use an EIP bandwidth plan as an independent service. EIP bandwidth plans support regional bandwidth sharing and transfer. After you associate EIPs that belong to the same region with an EIP bandwidth plan, the ECS instances, NAT gateways, or SLB instances that are assigned the EIPs can use the bandwidth of the EIP bandwidth plan. For more information, see [What is an EIP bandwidth plan?](/intl.en-US/.md)


