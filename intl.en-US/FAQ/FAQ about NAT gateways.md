---
keyword: [NAT gateway, frequently asked questions, FAQ]
---

# FAQ about NAT gateways

This topic provides answers to some frequently asked questions about NAT gateways.

-   [Why am I unable to associate elastic IP addresses \(EIPs\) with a NAT gateway in the NAT Gateway console?](#section_dxn_v29_z2k)
-   [Why are NAT service plans unavailable in the NAT Gateway console?](#section_g17_xi3_lt0)
-   [How many NAT gateways can I create with an Alibaba Cloud account?](#section_ch5_lda_osh)
-   [How many NAT gateways can I create in a VPC?](#section_8l9_cwy_02b)
-   [How many EIPs can I associate with a NAT gateway?](#section_9hb_4u4_f2e)
-   [Can I specify the same EIP in a Source Network Address Translation \(SNAT\) entry and a Destination Network Address Translation \(DNAT\) entry?](#section_9qf_el8_09i)
-   [Can Elastic Compute Service \(ECS\) instances use SNAT to access services that use DNAT to provide external access if the same enhanced NAT gateway is used for SNAT and DNAT?](#section_wdq_wze_1yj)
-   [Why is the outbound traffic unable to reach the bandwidth limit of an EIP after I associate the EIP with a NAT gateway?](#section_i0c_yb8_sw1)

## Why am I unable to associate elastic IP addresses \(EIPs\) with a NAT gateway in the NAT Gateway console?

If you purchased a NAT service plan before January 26, 2018, you can associate only public IP addresses in the NAT service plan with the NAT gateway to enable Internet access. To associate EIPs with the NAT gateway, perform the following operations based on the metering method of your NAT service plan.

-   If the NAT service plan is charged on a pay-by-bandwidth basis, you can convert the public IP addresses to EIPs in the NAT Gateway console. For more information, see [Convert a NAT service plan to an EIP bandwidth plan](/intl.en-US/Bandwidth Package (Archive)/Convert a NAT service plan to an EIP bandwidth plan.md).
-   If the NAT service plan is charged on a pay-by-data-transfer basis, submit a ticket to convert the public IP addresses in the NAT service plan to EIPs. For more information, see [Convert a NAT service plan to an EIP bandwidth plan](/intl.en-US/Bandwidth Package (Archive)/Convert a NAT service plan to an EIP bandwidth plan.md). To submit a ticket, [submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex).

## Why are NAT service plans unavailable in the NAT Gateway console?

If you did not purchase a NAT service plan before January 26, 2018, you must associate an EIP with the NAT gateway before the NAT gateway can access the Internet. For more information, see [Associate EIPs](/intl.en-US/User Guide/Create NAT gateways.md).

## How many NAT gateways can I create with an Alibaba Cloud account?

The number of NAT gateways that you can create with an Alibaba Cloud account is not limited.

## How many NAT gateways can I create in a VPC?

The number of NAT gateways that can be created in a virtual private cloud \(VPC\) is based on the type of NAT gateway.

-   You can create only one standard NAT gateway in a VPC. The quota cannot be increased.
-   You can create up to five enhanced NAT gateways in a VPC. To increase the quota, [submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex).

## How many EIPs can I associate with a NAT gateway?

By default, you can associate up to 20 EIPs with a NAT gateway. You can associate at most 10 pay-by-data-transfer EIPs with a NAT gateway.

To increase the quota, go to the [Quota Management](https://vpc.console.aliyun.com/quota) page. For more information, see [Quota management](/intl.en-US/Common Configurations/Quota management.md).

## Can I specify the same EIP in a Source Network Address Translation \(SNAT\) entry and a Destination Network Address Translation \(DNAT\) entry?

The type of NAT gateway determines whether you can specify the same EIP in a SNAT entry and a DNAT entry.

-   You cannot specify the same EIP in a SNAT entry and a DNAT entry for a standard NAT gateway.
-   You can specify the same EIP in a SNAT entry and a DNAT entry for an enhanced NAT gateway if your account is included in the whitelist.

## Can Elastic Compute Service \(ECS\) instances use SNAT to access services that use DNAT to provide external access if the same enhanced NAT gateway is used for SNAT and DNAT?

No, the ECS instances cannot access the services in this case.

If you create SNAT and DNAT entries on an enhanced NAT gateway and some services use DNAT of the enhanced NAT gateway to provide external access, the ECS instances in the VPC cannot use SNAT to access the services.

If you want the ECS instances to access the services that use DNAT to provide external access in the same VPC, we recommend that you create another enhanced NAT gateway. Then, create DNAT entries on the new enhanced NAT gateway.

## Why is the outbound traffic unable to reach the bandwidth limit of an EIP after I associate the EIP with a NAT gateway?

The maximum number of concurrent connections supported by a NAT gateway is limited by the number of EIPs that are associated with the NAT gateway. If only one EIP is associated with the NAT gateway, the maximum number of concurrent connections that the NAT gateway supports is 55,000.

For example, you have multiple ECS instances that are deployed in a VPC. The ECS instances use a NAT gateway to access the Internet through the same destination IP address and port. The bandwidth of the NAT gateway is higher than 2 Gbit/s. To avoid packet loss caused by the limit on concurrent connections for each EIP, we recommend that you associate four to eight EIPs with the NAT gateway and create a SNAT IP address pool. For more information, see [Create a SNAT IP address pool](/intl.en-US/Best Practices/Create a SNAT IP address pool.md).

