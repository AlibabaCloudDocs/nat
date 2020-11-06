---
keyword: [NAT gateway, frequently asked questions, FAQ]
---

# FAQ about NAT gateways

This topic provides answers to some commonly asked questions about NAT gateways.

-   [How many NAT gateways can I create with an Alibaba Cloud account?](#section_ch5_lda_osh)
-   [How many NAT gateways can I create in a virtual private cloud \(VPC\)?](#section_8l9_cwy_02b)
-   [How many elastic IP addresses \(EIPs\) can I associate with a NAT gateway?](#section_9hb_4u4_f2e)
-   [Can I specify the same EIP in both a Source Network Address Translation \(SNAT\) entry and a Destination Network Address Translation \(DNAT\) entry?](#section_9qf_el8_09i)
-   [Why is the outbound traffic unable to reach the maximum bandwidth of an EIP after I associate the EIP with a NAT gateway?](#section_i0c_yb8_sw1)

## How many NAT gateways can I create with an Alibaba Cloud account?

The number of NAT gateways that you can create with an Alibaba Cloud account is not limited.

## How many NAT gateways can I create in a virtual private cloud \(VPC\)?

The number of NAT gateways that can be created in a VPC depends on the type of NAT gateway.

-   You can create only one standard NAT gateway in a VPC. The quota cannot be increased.
-   You can create up to five enhanced NAT gateways in a VPC. To increase the quota,[submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex).

## How many elastic IP addresses \(EIPs\) can I associate with a NAT gateway?

By default, you can associate up to 20 EIPs with a NAT gateway. You can associate up to 10 pay-by-data-transfer EIPs with a NAT gateway.

If you want to increase the quota, go to the [Quota Management](https://vpc.console.aliyun.com/quota) page. For more information, see [Quota management]().

## Can I specify the same EIP in both a Source Network Address Translation \(SNAT\) entry and a Destination Network Address Translation \(DNAT\) entry?

Whether you can specify an EIP in both a SNAT entry and a DNAT entry depends on the type of NAT gateway.

-   Standard NAT gateway: You cannot specify an EIP in both a SNAT entry and a DNAT entry.
-   Enhanced NAT gateway: You can specify an EIP in both a SNAT entry and a DNAT entry when your account is included in the whitelist. To apply for a whitelist,[submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex).

## Why is the outbound traffic unable to reach the maximum bandwidth of an EIP after I associate the EIP with a NAT gateway?

The maximum number of concurrent connections that a NAT gateway supports is limited by the number of EIPs that are associated with the NAT gateway. If only one EIP is associated with the NAT gateway, the maximum number of concurrent connections that the NAT gateway supports is 55,000.

For example, you have multiple Elastic Compute Service \(ECS\) instances that are deployed in a VPC. The ECS instances access the Internet through the same destination IP address and port by using a NAT gateway. The bandwidth of the NAT gateway is higher than 2 Gbit/s. To avoid packet loss caused by the limit on concurrent connections for each EIP, we recommend that you associate four to eight EIPs with the NAT gateway and create a SNAT IP address pool. For more information, see [Create a SNAT IP address pool](/intl.en-US/Best Practices/Create a SNAT IP address pool.md).

