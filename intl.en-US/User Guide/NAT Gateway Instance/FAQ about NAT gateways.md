---
keyword: [NAT gateway, frequently asked questions, FAQ]
---

# FAQ about NAT gateways

This topic provides answers to some commonly asked questions about NAT gateways.

-   [Why am I unable to associate elastic IP addresses \(EIPs\) with a NAT gateway in the Virtual Private Cloud \(VPC\) console?](#section_dxn_v29_z2k)
-   [Why are NAT service plans unavailable in the NAT Gateway console?](#section_g17_xi3_lt0)
-   [How many NAT gateways can I create with an Alibaba Cloud account?](#section_ch5_lda_osh)
-   [How many NAT gateways can I create in a VPC?](#section_8l9_cwy_02b)
-   [How many EIPs can I associate with a NAT gateway?](#section_9hb_4u4_f2e)
-   [Can I specify the same EIP in both a Source Network Address Translation \(SNAT\) entry and a Destination Network Address Translation \(DNAT\) entry?](#section_9qf_el8_09i)
-   [Can Elastic Compute Service \(ECS\) instances use SNAT to access services that use DNAT to provide external access when the same enhanced NAT gateway is used for SNAT and DNAT?](#section_wdq_wze_1yj)
-   [Why is the outbound traffic unable to reach the maximum bandwidth of an EIP after I associate the EIP with a NAT gateway?](#section_i0c_yb8_sw1)

## Why am I unable to associate elastic IP addresses \(EIPs\) with a NAT gateway in the Virtual Private Cloud \(VPC\) console?

If you have purchased a NAT service plan beforeJanuary 26, 2018, you can only associate the public IP addresses that are provided by the NAT service plan with the NAT gateway. To associate EIPs with the NAT gateway, perform the following operations based on the billing method of your NAT service plan.

-   If the NAT service plan is charged on a pay-by-bandwidth basis, you can convert the public IP addresses to EIPs in the VPC console. For more information, see [Convert a NAT service plan to an EIP bandwidth plan](/intl.en-US/Bandwidth Package (Archive)/Convert a NAT service plan to an EIP bandwidth plan.md).
-   If the NAT service plan is charged on a pay-by-data-transfer basis, submit a ticket to convert the public IP addresses in the NAT service plan to EIPs. For more information, see [Convert a NAT service plan to an EIP bandwidth plan](/intl.en-US/Bandwidth Package (Archive)/Convert a NAT service plan to an EIP bandwidth plan.md). To submit a ticket, click[submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex).

## Why are NAT service plans unavailable in the NAT Gateway console?

If you did not purchase a NAT service plan beforeJanuary 26, 2018, you must associate an EIP with the NAT gateway before the NAT gateway can access the Internet. For more information, see [Associate an EIP with a NAT gateway](/intl.en-US/User Guide/NAT Gateway Instance/Manage EIPs/Associate an EIP with a NAT gateway.md).

## How many NAT gateways can I create with an Alibaba Cloud account?

The number of NAT gateways that you can create with an Alibaba Cloud account is not limited.

## How many NAT gateways can I create in a VPC?

The number of NAT gateways that can be created in a VPC depends on the type of NAT gateway.

-   You can create only one standard NAT gateway in a VPC. The quota cannot be increased.
-   You can create up to five enhanced NAT gateways in a VPC. To increase the quota,[submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex).

## How many EIPs can I associate with a NAT gateway?

By default, you can associate up to 20 EIPs with a NAT gateway. You can associate up to 10 pay-by-data-transfer EIPs with a NAT gateway.

If you want to increase the quota, go to the [Quota Management](https://vpc.console.aliyun.com/quota) page. For more information, see [Quota management](/intl.en-US/User Guide/Common Configurations/Quota management.md).

## Can I specify the same EIP in both a Source Network Address Translation \(SNAT\) entry and a Destination Network Address Translation \(DNAT\) entry?

Whether you can specify an EIP in both a SNAT entry and a DNAT entry depends on the type of NAT gateway.

-   Standard NAT gateway: You cannot specify an EIP in both a SNAT entry and a DNAT entry.
-   Enhanced NAT gateway: You can specify an EIP in both a SNAT entry and a DNAT entry when your account is included in the whitelist. To apply for a whitelist,[submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex).

## Can Elastic Compute Service \(ECS\) instances use SNAT to access services that use DNAT to provide external access when the same enhanced NAT gateway is used for SNAT and DNAT?

No.

If you created both SNAT and DNAT entries on the enhanced NAT gateway, the ECS instances cannot use SNAT to access services that use DNAT to provide external access in the same VPC.

If you want the ECS instances to access the services that use DNAT to provide external access in the same VPC, we recommend that you create another enhanced NAT gateway. Then, create DNAT entries and SNAT entries on the two NAT gateways separately.

## Why is the outbound traffic unable to reach the maximum bandwidth of an EIP after I associate the EIP with a NAT gateway?

The maximum number of concurrent connections that a NAT gateway supports is limited by the number of EIPs that are associated with the NAT gateway. If only one EIP is associated with the NAT gateway, the maximum number of concurrent connections that the NAT gateway supports is 55,000.

For example, you have multiple ECS instances that are deployed in a VPC. The ECS instances access the Internet through the same destination IP address and port by using a NAT gateway. The bandwidth of the NAT gateway is higher than 2 Gbit/s. To avoid packet loss caused by the limit on concurrent connections for each EIP, we recommend that you associate four to eight EIPs with the NAT gateway and create a SNAT IP address pool. For more information, see [Create a SNAT IP address pool](/intl.en-US/Best Practices/Create a SNAT IP address pool.md).

