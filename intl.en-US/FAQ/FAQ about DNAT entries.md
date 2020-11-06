---
keyword: [NAT Gateway, FAQ, DNAT, Internet access]
---

# FAQ about DNAT entries

This topic provides answers to some commonly asked questions about Destination Network Address Translation \(DNAT\) entries.

-   [How many DNAT entries can I add to a NAT gateway?](#section_wk1_9rh_68u)
-   [Why am I unable to find an existing EIP from the list of public IP addresses when I create a DNAT entry?](#section_pq2_99h_dt6)
-   [Can I create DNAT entries for ECS instances that are associated with EIPs?](#section_ade_vnf_0a0)

## How many DNAT entries can I add to a NAT gateway?

You can add up to 100 DNAT entries to a NAT gateway.

If you want to increase the quota, go to the [Quota Management](https://vpc.console.aliyun.com/quota) page. For more information, see [Quota management]().

## Why am I unable to find an existing EIP from the list of public IP addresses when I create a DNAT entry?

Before you create a DNAT entry, make sure that a NAT gateway is created and associated with an existing EIP. For more information, see [Create a DNAT entry]().

## Can I create DNAT entries for ECS instances that are associated with EIPs?

No, you cannot create DNAT entries for ECS instances that are associated with EIPs.

You must disassociate the EIPs from the ECS instances before you can create DNAT entries for the ECS instances. For more information, see [Disassociate an EIP from a cloud resource](/intl.en-US/User Guide/Disassociate an EIP from a cloud resource.md) and [Create a DNAT entry]().

**Note:** If you have added DNAT entries to an ECS instance that is associated with an EIP, the ECS instance prioritizes the use of the EIP to communicate with the Internet.

