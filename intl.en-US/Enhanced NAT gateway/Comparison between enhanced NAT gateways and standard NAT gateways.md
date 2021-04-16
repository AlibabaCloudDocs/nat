---
keyword: [NAT gateway, enhanced, network address translation, Internet-facing services, Internet access]
---

# Comparison between enhanced NAT gateways and standard NAT gateways

This topic describes the differences in features and limits between enhanced NAT gateways and standard NAT gateways.

## Comparison of features

|Item|Enhanced NAT gateway|Standard NAT gateway|Reference|
|----|--------------------|--------------------|---------|
|Multiple NAT gateways for one virtual private cloud \(VPC\)|Supported|Not supported|[Create a NAT gateway]()|
|Attach a NAT gateway to a vSwitch|Supported|Not supported|
|Billing on an hourly basis|Supported|Not supported|[Pay-by-data-transfer](/intl.en-US/Pricing/Pay-as-you-go.mdsection_v5g_sue_5bj)|
|Billing on a daily basis|Not supported|Supported|[Pay-as-you-go](/intl.en-US/Pricing/Pay-as-you-go.md)|
|Process TCP, UDP, and ICMP segments|Supported|Not supported|N/A|
|Monitoring metrics|22|4|[Monitor and maintain NAT gateways](/intl.en-US/User Guide/Monitor and maintain NAT gateways.md)|
|Network traffic monitoring \(TOP ECS\)|Supported|Not supported|[t147949.md\#section\_l14\_d8f\_gsa](/intl.en-US/User Guide/Monitor and maintain NAT gateways.mdsection_l14_d8f_gsa)|
|Associate multiple elastic IP addresses \(EIPs\) with a NAT gateway|Supported|Supported|[Associate an EIP with a NAT gateway](/intl.en-US/User Guide/Create NAT gateways.md)|
|SNAT|Supported|Supported|[Create a SNAT entry to access the Internet](/intl.en-US/User Guide/Create a SNAT entry to access the Internet.md)|
|Create multiple SNAT entries in a SNAT table|Supported|Supported|[Create a SNAT entry to access the Internet](/intl.en-US/User Guide/Create a SNAT entry to access the Internet.md)|
|Associate multiple EIPs with a SNAT table|Supported|Supported|
|DNAT|Supported|Supported|[Create a DNAT entry to provide Internet-facing services](/intl.en-US/User Guide/Create a DNAT entry to provide Internet-facing services.md)|
|DNAT port mapping|Supported|Supported|[Create a DNAT entry to provide Internet-facing services](/intl.en-US/User Guide/Create a DNAT entry to provide Internet-facing services.md)|
|DNAT IP mapping|Supported|Supported|
|Elastic Compute Service \(ECS\) instances use SNAT to access services that use DNAT to provide Internet-facing services when the same enhanced NAT gateway is used for SNAT and DNAT|Not supported|Supported|[Use SNAT of enhanced NAT gateways to enable ECS instances to access services that use DNAT to provide external access in the same VPC]()|

## Comparison of limits

|Item|Enhanced NAT gateway|Standard NAT gateway|
|----|--------------------|--------------------|
|The maximum number of NAT gateways that can be deployed for a VPC|5. To increase the quota,[submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex).|1 \(not adjustable\)|
|Use an EIP for both SNAT and DNAT|Only selected users can use an EIP for both SNAT and DNAT. To apply to be added to the whitelist,[submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex).|Not supported \(not adjustable\)|
|The maximum number of DNAT entries that can be added to a NAT gateway|100. You can increase the quota. For more information, see [Quota management](/intl.en-US/Common Configurations/Quota management.md).|100. You can increase the quota. For more information, see [Quota management](/intl.en-US/Common Configurations/Quota management.md).|
|The maximum number of SNAT entries that can be added to a NAT gateway|40. You can increase the quota. For more information, see [Quota management](/intl.en-US/Common Configurations/Quota management.md).|40. You can increase the quota. For more information, see [Quota management](/intl.en-US/Common Configurations/Quota management.md).|
|The maximum number of EIPs that can be specified in a SNAT entry|64 \(not adjustable\)|64 \(not adjustable\)|
|Create a NAT gateway for a VPC that contains a custom route entry whose destination CIDR block is 0.0.0.0/0|Yes|Not supported. You must delete the custom route entry whose destination CIDR block is 0.0.0.0/0 before you can create a NAT gateway for the VPC.|
|Limits on a vSwitch by the maximum bandwidth of the EIPs specified in the SNAT entry that is added to the vSwitch|Yes. If the EIPs are associated with an EIP bandwidth plan, the vSwitch is limited by the maximum bandwidth of the EIP bandwidth plan.|Yes. If the EIP is associated with an EIP bandwidth plan, the vSwitch is limited by the maximum bandwidth of the EIP bandwidth plan.|
|The maximum number of EIPs that can be associated with a NAT gateway|20. You can increase the quota. For more information, see [Quota management](/intl.en-US/Common Configurations/Quota management.md).|20. You can increase the quota. For more information, see [Quota management](/intl.en-US/Common Configurations/Quota management.md).|
|The maximum number of pay-by-data-transfer EIPs that can be associated with a NAT gateway|10. You can increase the quota. For more information, see [Quota management](/intl.en-US/Common Configurations/Quota management.md).|10. You can increase the quota. For more information, see [Quota management](/intl.en-US/Common Configurations/Quota management.md).|
|The maximum bandwidth supported by a pay-by-data-transfer EIP that is associated with a NAT gateway|N/A|200 Mbit/s \(not adjustable\)|
|The maximum bandwidth of a NAT gateway|5 Gbit/s. If the total bandwidth of the EIPs or EIP bandwidth plans is greater than 5 Gbit/s,[submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex) to increase the quota.|A NAT gateway does not have a bandwidth limit. The bandwidth limit depends on the bandwidth of the EIPs that are specified in a SNAT entry or a DNAT entry, and the bandwidth of the EIP bandwidth plans with which the EIPs are associated. For example, you create a SNAT entry for a NAT gateway, and specify five pay-by-data-transfer EIPs and two pay-by-bandwidth EIPs with 500 Mbit/s bandwidth each in the SNAT entry. The bandwidth of the NAT gateway is limited to 2,000 Mbit/s. This value is based on the following calculation: 5 × 200 Mbit/s + 2 × 500 Mbit/s = 2,000 Mbit/s. If the seven EIPs are associated with the same EIP bandwidth plan, and the bandwidth of the EIP bandwidth plan is limited to 1,000 Mbit/s, the bandwidth limit of the NAT gateway is 1,000 Mbit/s. |
|The maximum number of concurrent connections for an EIP is 55,000.|Yes|Yes|
|The maximum bandwidth of an EIP in an EIP bandwidth plan is 200 Mbit/s.|No|Yes|
|Users of NAT service plans are not allowed to associate EIPs with NAT gateways.|Yes|Yes|
|Transient connection errors may occur when you change the maximum bandwidth of the EIP bandwidth plan that is associated with a NAT gateway. For example, you can upgrade the maximum bandwidth from less than 1 Gbit/s to greater than 1 Gbit/s, or downgrade the maximum bandwidth from greater than 1 Gbit/s to less than 1 Gbit/s.|No|Yes|
|Transient connection errors may occur when IP addresses in the existing SNAT entries are reduced.|Yes|Yes|
|Transient connection errors may occur when IP addresses in the existing SNAT entries are increased.|No|Yes|

## References

-   [Enhanced NAT gateways \(new\)](/intl.en-US/Enhanced NAT gateway/Enhanced NAT gateways (new).md)
-   [Immediately upgrade a standard NAT gateway to an enhanced NAT gateway](/intl.en-US/Enhanced NAT gateway/Immediately upgrade a standard NAT gateway to an enhanced NAT gateway.md)

