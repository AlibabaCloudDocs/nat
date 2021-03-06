# FAQ about NAT service plans

-   [Why are NAT service plans unavailable in the NAT Gateway console?](#section_bfi_b1c_dzq)
-   [How many NAT service plans can be associated with a NAT gateway?](#section_zye_aty_rlc)
-   [What is the difference between NAT service plans and EIP bandwidth plans?](#section_r8u_xbe_6og)
-   [What is the difference between public IP addresses in NAT service plans and EIPs?](#section_ht8_tnb_0nf)
-   [Does the bandwidth limit of a NAT service plan apply to inbound and outbound data transfer?](#section_w6i_gu2_747)

## Why are NAT service plans unavailable in the NAT Gateway console?

If you did not purchase a NAT service plan for a NAT gateway before 23:59 \(UTC+8\) January 26, 2018, you can associate only elastic IP addresses \(EIPs\) with the NAT gateway to provide public IP addresses for the NAT gateway. For more information about how to associate an EIP with a NAT gateway, see [Associate an EIP with a NAT gateway](/intl.en-US/User Guide/Create NAT gateways.md).

## How many NAT service plans can be associated with a NAT gateway?

By default, you can associate up to four NAT service plans with one NAT gateway.

The name of this service quota is natgw\_quota\_bandwidth\_packages\_num. You can find this service quota on the Quota Management page in the Virtual Private Cloud \(VPC\) console and apply for a quota increase.

## What is the difference between NAT service plans and EIP bandwidth plans?

NAT service plans can be associated only with NAT gateways.

EIP bandwidth plans can be associated with various cloud resources, such as Elastic Compute Service \(ECS\) instances and Server Load Balancer \(SLB\) instances.

## What is the difference between public IP addresses in NAT service plans and EIPs?

Public IP addresses in NAT service plans cannot be disassociated from NAT gateways.

EIPs can be associated with or disassociated from NAT gateways at any time.

## Does the bandwidth limit of a NAT service plan apply to inbound and outbound data transfer?

The bandwidth limit of a NAT service plan applies only to outbound data transfer. However, the inbound data transfer is also throttled based on the bandwidth limit.

