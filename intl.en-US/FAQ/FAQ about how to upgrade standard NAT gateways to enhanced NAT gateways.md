---
keyword: [NAT gateway, enhanced, network address translation, Internet-facing services, Internet access]
---

# FAQ about how to upgrade standard NAT gateways to enhanced NAT gateways

This topic provides answers to some frequently asked questions about how to upgrade standard NAT gateways to enhanced NAT gateways.

-   [Does Alibaba Cloud charge an upgrade fee if I upgrade a standard NAT gateway to an enhanced NAT gateway?](#section_udq_uv0_vis)
-   [Does the upgrade have negative impacts on my workloads?](#section_tgz_o4i_qtu)
-   [Can I roll back an upgrade?](#section_71v_j51_6ux)
-   [After a standard NAT gateway is upgraded to an enhanced NAT gateway, do the configurations and public IP addresses of the standard NAT gateway change?](#section_e9f_xlz_kfl)
-   [When does Alibaba Cloud discontinue standard NAT gateways? Can I continue using my standard NAT gateways after Alibaba Cloud discontinues them?](#section_hqt_bez_40f)
-   [How can I upgrade a standard NAT gateway to an enhanced NAT gateway?](#section_si1_4s7_ubh)
-   [What are the differences between enhanced NAT gateways and standard NAT gateways?](#section_755_idw_kx9)
-   [Do enhanced NAT gateways support multi-zone disaster recovery?](#section_p65_r38_nh5)
-   [What are the scenarios in which a standard NAT gateway cannot be upgraded?](#section_uq4_ajg_zil)
-   [How can I upgrade a standard NAT gateway that is associated with NAT service plans?](#section_yrz_cz0_erw)
-   [Why am I unable to find the upgrade button to upgrade my standard NAT gateway in the console?](#section_6qb_45g_gsj)
-   [Why is a new security group created after my standard NAT gateway is upgraded to an enhanced NAT gateway?](#section_5wf_6ju_z5w)
-   [What are the permissions required for upgrading a standard NAT gateway?](#section_0v2_0jp_gjd)
-   [Multiple ENIs are attached to an ECS instance, and an EIP is associated with one of the ENIs. Why do I fail to access the EIP of the ECS instance after I upgrade my standard NAT gateway to an enhanced NAT gateway?](#section_ruc_ard_v38)
-   [Why am I unable to obtain monitoring data by calling the Cloud Monitor API operations after I upgrade a standard NAT gateway to an enhanced NAT gateway?](#section_8ew_r0k_zbq)

## Does Alibaba Cloud charge an upgrade fee if I upgrade a standard NAT gateway to an enhanced NAT gateway?

You can upgrade a standard NAT gateway to an enhanced NAT gateway free of charge.

-   After a pay-as-you-go NAT gateway is upgraded, the billing cycle of the NAT gateway changes from daily to hourly. However, the total cost does not change. For example, before a small-sized NAT gateway is upgraded, the unit price of the small-sized NAT gateway is CNY 12/day. After the small-sized NAT gateway is upgraded, the unit price of the small-sized NAT gateway is CNY 0.5/hour \(CNY 0.5/hour × 24 hours = CNY 12/day\).
-   After a subscription NAT gateway is upgraded, the billing of the NAT gateway remains unchanged.

## Does the upgrade have negative impacts on my workloads?

The time required to upgrade a standard NAT gateway to an enhanced NAT gateway is approximately 5 minutes. During the upgrade process, the NAT gateway may be disconnected for 1 to 2 seconds. The service resumes after your workloads are reconnected.

## Can I roll back an upgrade?

The system monitors the process when you upgrade a standard NAT gateway to an enhanced NAT gateway. If an exception occurs during the upgrade, the system rolls back the upgrade. If an exception occurs after the upgrade is complete, you can contact technical support to downgrade the enhanced NAT gateway to a standard NAT gateway.

## After a standard NAT gateway is upgraded to an enhanced NAT gateway, do the configurations and public IP addresses of the standard NAT gateway change?

The configurations of the elastic IP addresses \(EIPs\), Source Network Address Translation \(SNAT\) rules, and Destination Network Address Translation \(DNAT\) rules of the standard NAT gateway remain unchanged during the upgrade. You do not need to modify the configurations after the NAT gateway is upgraded.

If the standard NAT gateway to be upgraded is associated with NAT service plans, the public IP addresses provided by the NAT service plans are converted to EIPs. The bandwidth limit and billing method remain unchanged after the NAT service plans are converted to EIP bandwidth plans. Only the NAT service plans are converted to EIP bandwidth plans. The IP addresses, SNAT rules, and DNAT rules remain unchanged. For more information, see [Upgrade notes for standard NAT gateways that are associated with NAT service plans](/intl.en-US/Enhanced NAT gateway/Upgrade a standard NAT gateway to an enhanced NAT gateway at a scheduled time.md).

## When does Alibaba Cloud discontinue standard NAT gateways? Can I continue using my standard NAT gateways after Alibaba Cloud discontinues them?

Alibaba Cloud discontinued standard NAT gateways in November 2020. Standard NAT gateways are no longer updated. Enhanced NAT gateways are highly scalable and provide advanced features. To improve how you can manage your services, we recommend that you use the following methods to upgrade your standard NAT gateways:

-   [Immediately upgrade a standard NAT gateway to an enhanced NAT gateway](/intl.en-US/Enhanced NAT gateway/Immediately upgrade a standard NAT gateway to an enhanced NAT gateway.md)
-   [Upgrade a standard NAT gateway to an enhanced NAT gateway at a scheduled time](/intl.en-US/Enhanced NAT gateway/Upgrade a standard NAT gateway to an enhanced NAT gateway at a scheduled time.md)

## How can I upgrade a standard NAT gateway to an enhanced NAT gateway?

You can use one of the following methods to upgrade a standard NAT gateway to an enhanced NAT gateway:

-   Immediately upgrade a standard NAT gateway to an enhanced NAT gateway in the console. For more information, see [Immediately upgrade a standard NAT gateway to an enhanced NAT gateway](/intl.en-US/Enhanced NAT gateway/Immediately upgrade a standard NAT gateway to an enhanced NAT gateway.md).
-   Create a schedule to upgrade a standard NAT gateway to an enhanced NAT gateway in the console. We recommend that you set the scheduled time to off-peak hours. For more information, see [Upgrade a standard NAT gateway to an enhanced NAT gateway at a scheduled time](/intl.en-US/Enhanced NAT gateway/Upgrade a standard NAT gateway to an enhanced NAT gateway at a scheduled time.md).

## What are the differences between enhanced NAT gateways and standard NAT gateways?

|Item|Enhanced NAT gateway|Standard NAT gateway|Reference|
|----|--------------------|--------------------|---------|
|Whether a vSwitch must be associated when you create or upgrade a NAT gateway|Yes|No|[Create NAT gateways](/intl.en-US/User Guide/Create NAT gateways.md)|
|Whether an IP address must be assigned from a vSwitch to a NAT gateway|Yes|No|
|Associating a vSwitch with a NAT gateway|Supported|Not supported|
|Multiple NAT gateways for one virtual private cloud \(VPC\)|Supported|Not supported|[t2035785.md\#](/intl.en-US/Best Practices/Deploy multiple NAT gateways in one VPC.md)|
|Pay-by-data-transfer|Supported|Not supported|[Pay-as-you-go](/intl.en-US/Pricing/Pay-as-you-go.md)|
|Billing on an hourly basis|Supported|Not supported|
|Billing on a daily basis|Not supported|Supported|
|Processing TCP, UDP, and ICMP segments|Supported|Not supported|
|Metrics|22|4|[Monitor and maintain NAT gateways](/intl.en-US/User Guide/Monitor and maintain NAT gateways.md)|
|Network traffic monitoring \(TOP ECS\)|Supported|Not supported|[t147949.md\#section\_m95\_sta\_kek](/intl.en-US/User Guide/Monitor and maintain NAT gateways.mdsection_m95_sta_kek)|
|If the same enhanced NAT gateway is used for SNAT and DNAT, Elastic Compute Service \(ECS\) instances use SNAT to access services that use DNAT to provide Internet-facing services.|Not supported|Supported|[Use SNAT of enhanced NAT gateways to enable ECS instances to access Internet-facing services that use DNAT in the same VPC](/intl.en-US/Best Practices/Use SNAT of enhanced NAT gateways to enable ECS instances to access Internet-facing services that use DNAT in the same VPC.md)|
|Using an EIP for both SNAT and DNAT|Supported|Not supported|[Associate an EIP with a NAT gateway](/intl.en-US/User Guide/Create NAT gateways.mdsection_0q9_2z1_g7q)|

## Do enhanced NAT gateways support multi-zone disaster recovery?

Yes, enhanced NAT gateways support multi-zone disaster recovery.

When you create an enhanced NAT gateway or upgrade a standard NAT gateway to an enhanced NAT gateway, you need to specify only the vSwitch for the primary zone. You do not need to specify the vSwitch for the secondary zone. When the primary zone is down, the enhanced NAT gateway automatically performs multi-zone disaster recovery.

## What are the scenarios in which a standard NAT gateway cannot be upgraded?

If the same enhanced NAT gateway is used for SNAT and DNAT, you cannot use SNAT to access the EIPs that are associated with DNAT. In this scenario, you cannot upgrade the standard NAT gateway.

## How can I upgrade a standard NAT gateway that is associated with NAT service plans?

NAT service plans cannot be associated with enhanced NAT gateways. You can create a schedule to upgrade a standard NAT gateway that is associated with NAT service plans in the console. You can convert the NAT service plans to EIP bandwidth plans before you upgrade the standard NAT gateway. For more information about how to upgrade standard NAT gateways, see [How can I upgrade a standard NAT gateway to an enhanced NAT gateway?](#section_si1_4s7_ubh)

## Why am I unable to find the upgrade button to upgrade my standard NAT gateway in the console?

If the same enhanced NAT gateway is used for SNAT and DNAT, you cannot use SNAT to access EIPs that are associated with DNAT. In this case, if you use SNAT to access the EIPs that are associated with DNAT, the standard NAT gateway is included in a blacklist and cannot be upgraded.

## Why is a new security group created after my standard NAT gateway is upgraded to an enhanced NAT gateway?

When you create an enhanced NAT gateway, you must associate a vSwitch with the enhanced NAT gateway. The vSwitch assigns a private IP address to the NAT gateway and creates an elastic network interface \(ENI\) in the VPC where the NAT gateway is deployed. The vSwitch also creates a security group and associates the security group with the ENI. You are not allowed to modify this security group.

## What are the permissions required for upgrading a standard NAT gateway?

An ENI is created in the VPC where the standard NAT gateway that you want to upgrade is deployed. To create an ENI in the VPC, you must create the service-linked role for NAT Gateway. After you create the service-linked role, NAT Gateway creates only one ENI and one security group. No other operations are performed. For more information, see [Service-linked roles for NAT Gateway](/intl.en-US/Common Configurations/Service-linked roles for NAT Gateway.md).

## Multiple ENIs are attached to an ECS instance, and an EIP is associated with one of the ENIs. Why do I fail to access the EIP of the ECS instance after I upgrade my standard NAT gateway to an enhanced NAT gateway?

Multiple ENIs are attached to an ECS instance, and an EIP is associated with one of the ENIs. Different ENIs are used to forward the inbound and outbound traffic of the ECS instance. After you upgrade your standard NAT gateway to an enhanced NAT gateway, the network traffic of the ECS instance is blocked. To avoid this issue, you must modify the route of the ECS instance before you upgrade the standard NAT gateway to an enhanced NAT gateway. Make sure that the inbound and outbound traffic of the ECS instance is forwarded by using the same ENI. For more information, see [Configure routes for ENIs](/intl.en-US/Network/Elastic Network Interfaces/Configure an ENI.md).

## Why am I unable to obtain monitoring data by calling the Cloud Monitor API operations after I upgrade a standard NAT gateway to an enhanced NAT gateway?

Enhanced NAT gateways support more metrics than standard NAT gateways and some metrics use different names than those supported by standard NAT gateways. Therefore, you cannot collect monitoring data from an enhanced NAT gateway if you specify the names of metrics supported by standard NAT gateways when you call the [DescribeMetricList](/intl.en-US/API Reference/Cloud Products/DescribeMetricList.md) operation. You must specify the names of metrics supported by enhanced NAT gateways when you collect monitoring data from an enhanced NAT gateway. For more information, see [enhanced\_nat\_gateway](/intl.en-US/Appendix 1: Metrics/Cloud essentials/Networking/enhanced_nat_gateway.md).

