# FAQ about NAT gateways

-   [Can I specify the same elastic IP address \(EIP\) in both a Destination Network Address Translation \(DNAT\) entry and a Source Network Address Translation \(SNAT\) entry?](#section_vlv_m2f_2bf)
-   [How many NAT gateways can I create with an Alibaba Cloud account?](#section_0wp_8zk_c6u)
-   [How many DNAT entries can I add to a NAT gateway?](#section_igf_d4c_mui)
-   [How many SNAT entries can I add to a NAT gateway?](#section_rsx_1cu_8cd)
-   [How many EIPs can be specified in a SNAT entry?](#section_oyo_bvw_tt3)
-   [Can I view the data transfer of each VSwitch in the console of the corresponding NAT gateway?](#section_vcs_0wp_vsg)
-   [If an Elastic Compute Service \(ECS\) instance is assigned a static public IP address and a SNAT entry is created for the ECS instance, what can I do if I want the ECS instance to prioritize the use of the EIP in the SNAT entry to access the Internet?](#section_534_7dp_bs8)
-   [If an ECS instance is assigned an EIP and a SNAT entry is created for the ECS instance, what can I do if I want the ECS instance to prioritize the use of the EIP in the SNAT entry to access the Internet?](#section_u9j_9ts_jo0)
-   [If an ECS instance has a DNAT IP mapping and a SNAT entry is configured, what can I do if I want the ECS instance to prioritize the use of the EIP in the SNAT entry to access the Internet?](#section_0wq_838_rp7)

## Can I specify the same elastic IP address \(EIP\) in both a Destination Network Address Translation \(DNAT\) entry and a Source Network Address Translation \(SNAT\) entry?

It depends on the type of the NAT gateway that you use.

-   Standard NAT gateway: You cannot specify an EIP in both a SNAT entry and a DNAT entry.
-   Enhanced NAT gateway: You can specify an EIP in both a SNAT entry and a DNAT entry. If you want to use enhanced NAT gateways,[submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex).

## How many NAT gateways can I create with an Alibaba Cloud account?

You can create only one NAT gateway for each virtual private cloud \(VPC\). The number of NAT gateways that you can create with an Alibaba Cloud account is not limited.

## How many DNAT entries can I add to a NAT gateway?

You can add up to 100 DNAT entries to a NAT gateway.

The name of this service quota is natgw\_quota\_dnat\_entry\_num. You can find it on the Quota Management page and apply for a quota increase.

## How many SNAT entries can I add to a NAT gateway?

You can add up to 40 SNAT entries to a NAT gateway.

The name of this service quota is natgw\_quota\_snat\_entry\_num. You can find it on the Quota Management page and apply for a quota increase.

## How many EIPs can be specified in a SNAT entry?

You can specify up to 64 EIPs in a SNAT entry. This quota is not adjustable.

## Can I view the data transfer of each VSwitch in the console of the corresponding NAT gateway?

No.

If you want to view the data transfer of each VSwitch, associate an EIP with each VSwitch. Then, you can view the data transfer of each VSwitch by checking the data transfer of the corresponding EIP.

## If an Elastic Compute Service \(ECS\) instance is assigned a static public IP address and a SNAT entry is created for the ECS instance, what can I do if I want the ECS instance to prioritize the use of the EIP in the SNAT entry to access the Internet?

You can create an elastic network interface \(ENI\), attach the ENI to the ECS instance, and convert the public IP address to an EIP. Then, associate the EIP with the ENI. This way, the ECS instance prioritizes the use of the EIP in the SNAT entry to access the Internet. The ECS instance uses the ENI to receive requests sent over the Internet. For more information, see [Attach an ENI to an ECS that is allocated with an public IP address](/intl.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Attach an ENI to an ECS that is allocated with an public IP address.md).

## If an ECS instance is assigned an EIP and a SNAT entry is created for the ECS instance, what can I do if I want the ECS instance to prioritize the use of the EIP in the SNAT entry to access the Internet?

You can create an ENI and attach the ENI to the ECS instance. Then, disassociate the EIP from the ECS instance and associate the EIP with the ENI. This way, the ECS instance prioritizes the use of the EIP in the SNAT entry to access the Internet. The ECS instance uses the ENI to receive requests sent over the Internet. For more information, see [Attach an ENI to an ECS instance associated with an EIP](/intl.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Attach an ENI to an ECS instance associated with an EIP.md).

## If an ECS instance has a DNAT IP mapping and a SNAT entry is configured, what can I do if I want the ECS instance to prioritize the use of the EIP in the SNAT entry to access the Internet?

You can create an ENI, attach the ENI to the ECS instance, and delete the DNAT IP mapping from the NAT gateway. Then, create a DNAT entry to map the EIP of the NAT gateway to the ENI of the ECS instance. This way, the ECS instance prioritizes the use of the EIP in the SNAT entry to access the Internet. The ECS instance uses the ENI to receive requests sent over the Internet. For more information, see [Attach an ENI to an ECS instance configured with DNAT IP mapping](/intl.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Attach an ENI to an ECS instance configured with DNAT IP mapping.md).

