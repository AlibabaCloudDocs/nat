---
keyword: [NAT Gateway, SNAT, FAQ, Internet access]
---

# FAQ about SNAT

This topic provides answers to some frequently asked questions about Source Network Address Translation \(SNAT\).

-   [How many SNAT entries can I add to a NAT gateway?](#section_1ca_x5e_789)
-   [How many EIPs can I specify in a SNAT entry?](#section_h4h_468_si4)
-   [Can I create a SNAT IP address pool for a SNAT entry?](#section_pq1_mx8_13k)
-   [How can I configure the ECS instances in a VPC to use the same public IP address to access the Internet?](#section_nr6_yu9_rjy)
-   [Why am I unable to find an existing EIP from the list of public IP addresses when I create a SNAT entry?](#section_khm_d8g_c21)
-   [An ECS instance is assigned a static public IP address and a SNAT entry is created for the ECS instance. In this case, what can I do if I want the ECS instance to preferably use the EIP in the SNAT entry to access the Internet?](#section_uap_mm1_v62)
-   [An EIP is associated with an ECS instance and a SNAT entry is created for the ECS instance. In this case, what can I do if I want the ECS instance to preferably use the EIP in the SNAT entry to access the Internet?](#section_0kw_7t6_1or)
-   [A DNAT IP mapping and a SNAT entry are created for an ECS instance. In this case, what can I do if I want the ECS instance to preferably use the EIP in the SNAT entry to access the Internet?](#section_t8x_nbi_kjc)

## How many SNAT entries can I add to a NAT gateway?

By default, you can add up to 40 SNAT entries to a NAT gateway.

To increase the quota, go to the [Quota Management](https://vpc.console.aliyun.com/quota) page. For more information, see [Quota management](/intl.en-US/Common Configurations/Quota management.md).

## How many EIPs can I specify in a SNAT entry?

You can specify up to 64 elastic IP addresses \(EIPs\) in a SNAT entry. The quota cannot be increased.

## Can I create a SNAT IP address pool for a SNAT entry?

Yes, you can create a SNAT IP address pool for a SNAT entry. For more information, see [Create a SNAT IP address pool](/intl.en-US/Best Practices/Create a SNAT IP address pool.md).

## How can I configure the ECS instances in a VPC to use the same public IP address to access the Internet?

Configure a SNAT entry for the Elastic Compute Service \(ECS\) instances in the virtual private cloud \(VPC\). Then, the ECS instances can access the Internet by using the SNAT IP. An ECS instance can be assigned a public IP address, associated with an EIP, or configured with DNAT IP mapping. In these cases, the ECS instance uses the public IP address instead of the SNAT IP to access the Internet. For more information about how to configure the ECS instances in a VPC to use the same public IP address to access the Internet, see [Attach an ENI to an ECS that is allocated with an public IP address](/intl.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Configure ECS instances that are assigned static public IP addresses to use the same EIP to access the Internet.md), [Configure ECS instances that are assigned EIPs to use the same EIP to access the Internet](/intl.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Configure ECS instances that are assigned EIPs to use the same EIP to access the Internet.md), and [Configure ECS instances that use DNAT IP mapping to use the same EIP to access the Internet](/intl.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Configure ECS instances that use DNAT IP mapping to use the same EIP to access the
         Internet.md).

## Why am I unable to find an existing EIP from the list of public IP addresses when I create a SNAT entry?

Before you create a SNAT entry, make sure that a NAT gateway is created and an EIP is associated with the NAT gateway. For more information, see [Create a SNAT entry to access the Internet](/intl.en-US/User Guide/Create a SNAT entry to access the Internet.md).

## An ECS instance is assigned a static public IP address and a SNAT entry is created for the ECS instance. In this case, what can I do if I want the ECS instance to preferably use the EIP in the SNAT entry to access the Internet?

Perform the following steps: Create an elastic network interface \(ENI\), attach the ENI to the ECS instance, convert the static public IP address to an EIP, and then associate the EIP with the ENI. This way, the ECS instance preferably uses the EIP in the SNAT entry to access the Internet. The ECS instance uses the ENI to receive requests from the Internet. For more information, see [Attach an ENI to an ECS that is allocated with an public IP address](/intl.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Configure ECS instances that are assigned static public IP addresses to use the same EIP to access the Internet.md).

## An EIP is associated with an ECS instance and a SNAT entry is created for the ECS instance. In this case, what can I do if I want the ECS instance to preferably use the EIP in the SNAT entry to access the Internet?

Create an ENI, attach the ENI to the ECS instance, disassociate the EIP from the ECS instance, and then associate the EIP with the ENI. This way, the ECS instance preferably uses the EIP in the SNAT entry to access the Internet. The ECS instance uses the ENI to receive requests from the Internet. For more information, see [Configure ECS instances that are assigned EIPs to use the same EIP to access the Internet](/intl.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Configure ECS instances that are assigned EIPs to use the same EIP to access the Internet.md).

## A DNAT IP mapping and a SNAT entry are created for an ECS instance. In this case, what can I do if I want the ECS instance to preferably use the EIP in the SNAT entry to access the Internet?

Attach the ENI to the ECS instance, and delete the Destination Network Address Translation \(DNAT\) IP mapping from the NAT gateway. Then, create a DNAT entry to map the EIP of the NAT gateway to the ENI of the ECS instance. This way, the ECS instance preferably uses the EIP in the SNAT entry to access the Internet. The ECS instance uses the ENI to receive requests that are sent over the Internet. For more information, see [Configure ECS instances that use DNAT IP mapping to use the same EIP to access the Internet](/intl.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Configure ECS instances that use DNAT IP mapping to use the same EIP to access the
         Internet.md).

