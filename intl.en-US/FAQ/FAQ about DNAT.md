---
keyword: [NAT Gateway, FAQ, DNAT, Internet access]
---

# FAQ about DNAT

This topic provides answers to some frequently asked questions about Destination Network Address Translation \(DNAT\).

-   [How many DNAT entries can I add to a NAT gateway?](#section_wk1_9rh_68u)
-   [Why am I unable to find an existing EIP from the list of public IP addresses when I create a DNAT entry?](#section_pq2_99h_dt6)
-   [Can I add DNAT entries to ECS instances that are assigned EIPs?](#section_ade_vnf_0a0)

## How many DNAT entries can I add to a NAT gateway?

By default, you can add up to 100 DNAT entries to a NAT gateway.

To increase the quota, go to the [Quota Management](https://vpc.console.aliyun.com/quota) page. For more information, see [Quota management](/intl.en-US/Common Configurations/Quota management.md).

## Why am I unable to find an existing EIP from the list of public IP addresses when I create a DNAT entry?

Before you create a DNAT entry, make sure that a NAT gateway is created and associated with an elastic IP address \(EIP\). For more information, see [Create a DNAT entry to provide Internet-facing services](/intl.en-US/User Guide/Create a DNAT entry to provide Internet-facing services.md).

## Can I add DNAT entries to ECS instances that are assigned EIPs?

No, you cannot add DNAT entries to Elastic Compute Service \(ECS\) instances that are assigned EIPs.

Before you can add DNAT entries to the ECS instances, you must disassociate the EIPs from the ECS instances. For more information, see [Disassociate an EIP from a cloud resource](/intl.en-US/User Guide/Disassociate an EIP from a cloud resource.md) and [Create a DNAT entry to provide Internet-facing services](/intl.en-US/User Guide/Create a DNAT entry to provide Internet-facing services.md).

**Note:** If you add DNAT entries to an ECS instance that is assigned an EIP, the ECS instance preferably uses the EIP to communicate with the Internet.

