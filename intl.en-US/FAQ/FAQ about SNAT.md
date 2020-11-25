---
keyword: [NAT Gateway, SNAT, FAQ, Internet access]
---

# FAQ about SNAT

This topic provides answers to some commonly asked questions about Source Network Address Translation \(SNAT\).

-   [How many SNAT entries can I add to a NAT gateway?](#section_1ca_x5e_789)
-   [How many elastic IP addresses \(EIPs\) can I specify in a SNAT entry?](#section_h4h_468_si4)
-   [Can I create a SNAT address pool for a SNAT entry?](#section_pq1_mx8_13k)
-   [How can I configure Elastic Compute Service \(ECS\) instances in a virtual private cloud \(VPC\) to use the same public IP address to access the Internet?](#section_nr6_yu9_rjy)
-   [Why am I unable to find the EIP that I created from the public IP address list when I create a SNAT entry?](#section_khm_d8g_c21)
-   [If an ECS instance is assigned a static public IP address and a SNAT entry is created for the ECS instance, what can I do if I want the ECS instance to prioritize the use of the EIP in the SNAT entry to access the Internet?](#section_uap_mm1_v62)
-   [If an ECS instance is assigned an EIP and a SNAT entry is created for the ECS instance, what can I do if I want the ECS instance to prioritize the use of the EIP in the SNAT entry to access the Internet?](#section_0kw_7t6_1or)
-   [If an ECS instance has a Destination Network Address Translation \(DNAT\) IP mapping and a SNAT entry is configured, what can I do if I want the ECS instance to prioritize the use of the EIP in the SNAT entry to access the Internet?](#section_t8x_nbi_kjc)

## How many SNAT entries can I add to a NAT gateway?

By default, a NAT gateway supports up to 40 SNAT entries.

To increase the quota, go to the [Quota Management](https://vpc.console.aliyun.com/quota) page. For more information, see [Quota management](/intl.en-US/User Guide/Common Configurations/Quota management.md).

## How many elastic IP addresses \(EIPs\) can I specify in a SNAT entry?

You can specify up to 64 EIPs in a SNAT entry. The quota is not adjustable.

## Can I create a SNAT address pool for a SNAT entry?

Yes, you can create a SNAT IP address pool for a SNAT entry. For more information, see [Create a SNAT IP address pool](/intl.en-US/Best Practices/Create a SNAT IP address pool.md).

## How can I configure Elastic Compute Service \(ECS\) instances in a virtual private cloud \(VPC\) to use the same public IP address to access the Internet?

Configure a SNAT entry for the ECS instances in the VPC. Then, the ECS instances access the Internet by using the SNAT IP. If an ECS instance is assigned a public IP address, associated with an EIP, or configured with DNAT IP mapping, the ECS instance uses the public IP address to access the Internet instead of the SNAT IP. For more information about how to configure ECS instances in a VPC to use the same public IP address to access the Internet, see [Attach an ENI to an ECS that is allocated with an public IP address](/intl.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Attach an ENI to an ECS that is allocated with an public IP address.md), [Attach an ENI to an ECS instance associated with an EIP](/intl.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Attach an ENI to an ECS instance associated with an EIP.md), and [Attach an ENI to an ECS instance configured with DNAT IP mapping](/intl.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Attach an ENI to an ECS instance configured with DNAT IP mapping.md).

## Why am I unable to find the EIP that I created from the public IP address list when I create a SNAT entry?

Before you create a SNAT entry, make sure that a NAT gateway is created and associated with the EIP that you have created. For more information, see [t395012.md\#](/intl.en-US/User Guide/SNAT/Create a SNAT entry.md).

## If an ECS instance is assigned a static public IP address and a SNAT entry is created for the ECS instance, what can I do if I want the ECS instance to prioritize the use of the EIP in the SNAT entry to access the Internet?

Perform the following steps: Create an elastic network interface \(ENI\), attach the ENI to the ECS instance, convert the static public IP address to an EIP, and then associate the EIP with the ENI. This way, the ECS instance prioritizes the use of the EIP in the SNAT entry to access the Internet. The ECS instance uses the ENI to receive requests from the Internet. For more information, see [Attach an ENI to an ECS that is allocated with an public IP address](/intl.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Attach an ENI to an ECS that is allocated with an public IP address.md).

## If an ECS instance is assigned an EIP and a SNAT entry is created for the ECS instance, what can I do if I want the ECS instance to prioritize the use of the EIP in the SNAT entry to access the Internet?

Perform the following steps: Create an ENI, attach the ENI to the ECS instance, disassociate the EIP from the ECS instance, and then associate the EIP with the ENI. This way, the ECS instance prioritizes the use of the EIP in the SNAT entry to access the Internet. The ECS instance uses the ENI to receive requests that are sent over the Internet. For more information, see [Attach an ENI to an ECS instance associated with an EIP](/intl.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Attach an ENI to an ECS instance associated with an EIP.md).

## If an ECS instance has a Destination Network Address Translation \(DNAT\) IP mapping and a SNAT entry is configured, what can I do if I want the ECS instance to prioritize the use of the EIP in the SNAT entry to access the Internet?

Perform the following steps: Attach the ENI to the ECS instance, delete the DNAT IP mapping from the NAT gateway, and then create a DNAT entry to map the EIP of the NAT gateway to the ENI of the ECS instance. This way, the ECS instance prioritizes the use of the EIP in the SNAT entry to access the Internet. The ECS instance uses the ENI to receive requests that are sent over the Internet. For more information, see [Attach an ENI to an ECS instance configured with DNAT IP mapping](/intl.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Attach an ENI to an ECS instance configured with DNAT IP mapping.md).

