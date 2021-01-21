---
keyword: [NAT gateway, enhanced, network address translation, Internet-facing services, Internet access]
---

# FAQ about upgrading standard NAT gateways to enhanced NAT gateways

This topic provides answers to some commonly asked questions about upgrading standard NAT gateways to enhanced NAT gateways.

-   [Does Alibaba Cloud charge an upgrade fee if I upgrade a standard NAT gateway to an enhanced NAT gateway?](#section_udq_uv0_vis)
-   [Does the upgrade has negative impacts on my workloads?](#section_tgz_o4i_qtu)
-   [Can I roll back an upgrade?](#section_71v_j51_6ux)
-   [After a standard NAT gateway is upgraded to an enhanced NAT gateway, are the configurations and public IP addresses of the standard NAT gateway changed?](#section_e9f_xlz_kfl)
-   [When will Alibaba Cloud discontinue standard NAT gateways? Can I continue to use my standard NAT gateways after Alibaba Cloud discontinues standard NAT gateways?](#section_hqt_bez_40f)
-   [How can I upgrade a standard NAT gateway to an enhanced NAT gateway?](#section_si1_4s7_ubh)
-   [What are the differences between enhanced NAT gateways and standard NAT gateways?](#section_755_idw_kx9)
-   [Do enhanced NAT gateways support multi-zone disaster recovery?](#section_p65_r38_nh5)
-   [What are the scenarios in which a standard NAT gateway cannot be upgraded?](#section_uq4_ajg_zil)
-   [How can I upgrade a standard NAT gateway that is associated with NAT service plans?](#section_yrz_cz0_erw)
-   [Why am I unable to find the upgrade button to upgrade my standard NAT gateway in the console?](#section_6qb_45g_gsj)
-   [Why is a new security group created after my standard NAT gateway is upgraded to an enhanced NAT gateway?](#section_5wf_6ju_z5w)
-   [What permissions are required to upgrade a standard NAT gateway?](#section_0v2_0jp_gjd)

## Does Alibaba Cloud charge an upgrade fee if I upgrade a standard NAT gateway to an enhanced NAT gateway?

You can upgrade a standard NAT gateway to an enhanced NAT gateway free of charge.

-   After a pay-as-you-go NAT gateway is upgraded, the billing cycle of the NAT gateway is changed from daily to hourly. This does not change the total cost. For example, before a small-sized NAT gateway is upgraded, the unit price of the small-sized NAT gateway is CNY 12/day. After the small-sized NAT gateway is upgraded, the unit price of the small-sized NAT gateway is CNY 0.5/hour \(CNY 0.5/hour × 24 hours = CNY 12/day\).
-   After a subscription NAT gateway is upgraded, the billing of the subscription NAT gateway remains unchanged.

## Does the upgrade has negative impacts on my workloads?

It requires approximately 5 minutes to upgrade a standard NAT gateway to an enhanced NAT gateway. During the upgrade process, the NAT gateway may be disconnected for 1 to 2 seconds. The service resumes after your workloads are reconnected.

## Can I roll back an upgrade?

The system monitors the process when you upgrade a standard NAT gateway to an enhanced NAT gateway. If an exception occurs during the upgrade, the system rolls back the upgrade. If an exception occurs after the upgrade is completed, you can contact the technical support to downgrade the enhanced NAT gateway to a standard NAT gateway.

## After a standard NAT gateway is upgraded to an enhanced NAT gateway, are the configurations and public IP addresses of the standard NAT gateway changed?

The configurations of the elastic IP addresses \(EIPs\), SNAT rules, and DNAT rules on the standard NAT gateway remain unchanged during the upgrade. You do not need to modify the configurations after the upgrade is complete.

If the standard NAT gateway that is upgraded to an enhanced NAT gateway is associated with NAT service plans, the public IP addresses provided by the NAT service plans are converted to EIPs. The maximum bandwidth and billing method remain unchanged after the NAT service plans are converted to EIP bandwidth plans. Only NAT service plans are converted to EIP bandwidth plans. The IP addresses, SNAT rules, and DNAT rules remain unchanged. For more information, see [Upgrade notes for standard NAT gateways that are associated with NAT service plans](/intl.en-US/Types of NAT gateways/Upgrade a standard NAT gateway to an enhanced NAT gateway at a scheduled time.md).

## When will Alibaba Cloud discontinue standard NAT gateways? Can I continue to use my standard NAT gateways after Alibaba Cloud discontinues standard NAT gateways?

Alibaba Cloud discontinued standard NAT gateways in November 2020. Standard NAT gateways are no longer updated. Enhanced NAT gateways are highly scalable and provide advanced features. To improve how you can manage your services, we recommend that you use the following methods to upgrade your standard NAT gateways:

-   [Immediately upgrade a standard NAT gateway to an enhanced NAT gateway](/intl.en-US/Types of NAT gateways/Immediately upgrade a standard NAT gateway to an enhanced NAT gateway.md)
-   [Upgrade a standard NAT gateway to an enhanced NAT gateway at a scheduled time](/intl.en-US/Types of NAT gateways/Upgrade a standard NAT gateway to an enhanced NAT gateway at a scheduled time.md)

If you cannot upgrade a standard NAT gateway due to business issues, please contact us.

## How can I upgrade a standard NAT gateway to an enhanced NAT gateway?

You can use the following methods to upgrade a standard NAT gateway:

-   Immediately upgrade a standard NAT gateway to an enhanced NAT gateway in the console. For more information, see [Immediately upgrade a standard NAT gateway to an enhanced NAT gateway](/intl.en-US/Types of NAT gateways/Immediately upgrade a standard NAT gateway to an enhanced NAT gateway.md).
-   Create a schedule to upgrade a standard NAT gateway to an enhanced NAT gateway in the console. We recommend that you use this method during off-peak hours. For more information, see [Upgrade a standard NAT gateway to an enhanced NAT gateway at a scheduled time](/intl.en-US/Types of NAT gateways/Upgrade a standard NAT gateway to an enhanced NAT gateway at a scheduled time.md).

## What are the differences between enhanced NAT gateways and standard NAT gateways?

|Feature|Enhanced NAT gateway|Standard NAT gateway|Reference|
|-------|--------------------|--------------------|---------|
|Whether a vSwitch must be associated when you create or upgrade a NAT gateway|Yes|No|[Manage NAT gateways](/intl.en-US/User Guide/Manage NAT gateways.md)|
|Whether an IP address must be assigned from a vSwitch to a NAT gateway|Yes|No|
|Associating a vSwitch with a NAT gateway|Supported|Not supported|
|Deploying multiple NAT gateways for one virtual private cloud \(VPC\)|Supported|Not supported|[t2020912.md\#]()|
|Pay-by-data-transfer|Supported|Not supported|[Pay-as-you-go](/intl.en-US/Pricing/Pay-as-you-go.md)|
|Billing on an hourly basis|Supported|Not supported|
|Billing on a daily basis|Not supported|Supported|
|Processing TCP, UDP, and ICMP segments|Supported|Not supported|
|Monitoring metrics|22|4|[Use Cloud Monitor to monitor NAT gateways](/intl.en-US/User Guide/Use Cloud Monitor to monitor NAT gateways.md)|
|Network traffic monitoring \(TOP ECS\)|Supported|Not supported|[t147949.md\#section\_l14\_d8f\_gsa](/intl.en-US/User Guide/Use Cloud Monitor to monitor NAT gateways.mdsection_l14_d8f_gsa)|
|Elastic Compute Service \(ECS\) instances use SNAT to access services that use DNAT to provide external access when the same enhanced NAT gateway is used for SNAT and DNAT|Not supported|Supported|[t1997525.md\#]()|
|Using an EIP for both SNAT and DNAT|Supported|Not supported|[Associate an EIP with a NAT gateway](/intl.en-US/User Guide/Manage NAT gateways.md)|

## Do enhanced NAT gateways support multi-zone disaster recovery?

Yes, enhanced NAT gateways support multi-zone disaster recovery.

When you create an enhanced NAT gateway or upgrade to an enhanced NAT gateway, you only need to specify the vSwitch of the primary zone. You do not need to specify the vSwitch of the secondary zone. When the primary zone is down, the enhanced NAT gateway automatically performs multi-zone disaster recovery.

## What are the scenarios in which a standard NAT gateway cannot be upgraded?

You cannot use SNAT to access EIPs that are associated with DNAT when the same enhanced NAT gateway is used for SNAT and DNAT. Therefore, you cannot upgrade a standard NAT gateway when the standard NAT gateway is used in this scenario.

## How can I upgrade a standard NAT gateway that is associated with NAT service plans?

NAT service plans cannot be associated with enhanced NAT gateways. You can create a schedule to upgrade a standard NAT gateway that is associated with NAT service plans in the console. You can convert the NAT service plans to EIP bandwidth plans before you upgrade the standard NAT gateway. For more information about how to upgrade standard NAT gateways, see [How can I upgrade a standard NAT gateway to an enhanced NAT gateway?](#section_si1_4s7_ubh)

## Why am I unable to find the upgrade button to upgrade my standard NAT gateway in the console?

You cannot use SNAT to access EIPs that are associated with DNAT when the same enhanced NAT gateway is used for SNAT and DNAT. Therefore, if you use SNAT to access the EIPs that are associated with DNAT when the same standard NAT gateway is used for SNAT and DNAT, the standard NAT gateway is included in a blacklist and cannot be upgraded. If you confirm that your standard NAT gateway is not used in the preceding scenario, you can contact us to remove the NAT gateway from the blacklist and upgrade the NAT gateway in the console.

## Why is a new security group created after my standard NAT gateway is upgraded to an enhanced NAT gateway?

When you create an enhanced NAT gateway, you must associate a vSwitch with the enhanced NAT gateway. The vSwitch assigns a private IP address to the NAT gateway and creates an elastic network interface \(ENI\) in the VPC where the NAT gateway is deployed. At the same time, a security group is created and associated with the ENI. You are not allowed to modify this security group.

## What permissions are required to upgrade a standard NAT gateway?

An ENI is created in the VPC where the standard NAT gateway that you want to upgrade is deployed. To create an ENI in the VPC, you must grant permissions to the service-linked role. NAT Gateway requires the permissions to create an ENI and a security group. No other operations are performed. For more information, see [Service-linked roles for NAT Gateway](/intl.en-US/Common Configurations/Service-linked roles for NAT Gateway.md).

