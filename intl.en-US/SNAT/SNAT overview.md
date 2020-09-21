# SNAT overview

NAT gateways support Source Network Address Translation \(SNAT\). SNAT enables Elastic Compute Service \(ECS\) instances in a Virtual Private Cloud \(VPC\) network to access the Internet through a NAT gateway when these ECS instances are not assigned static public IP addresses or elastic IP addresses \(EIPs\).

## SNAT entries

You can create SNAT entries in a SNAT table to enable ECS instances to access the Internet.

A SNAT entry consists of the following elements:

-   **VSwitches or ECS instances**: the VSwitches or ECS instances that require Internet access with SNAT.
-   **EIPs**: the EIPs that are used to access the Internet.

    **Note:**

    -   You can select more than one EIP to create a SNAT address pool. When an ECS instance in a VPC network needs to access the Internet, an EIP in the SNAT address pool is randomly assigned to the ECS instance.
    -   If you have purchased a NAT service plan before January 26, 2018, static public IP addresses in the NAT service plan is used in the SNAT entry.

## VSwitch granularity and ECS granularity

SNAT entries can be created based on the following granularity to enable ECS instances in a VPC network to access the Internet.

-   VSwitch granularity

    If you create a SNAT entry for a VSwitch, the ECS instances attached to the VSwitch access the Internet by using the public IP addresses specified for the SNAT entry and through the NAT gateway on which the SNAT entry is created. By default, all ECS instances attached to the VSwitch can use the specified EIPs to access the Internet.

    **Note:** For example, if an ECS instance is assigned a static public IP address, associated with an EIP, or configured with a Destination Network Address Translation \(DNAT\) IP mapping, such an ECS instance uses the preceding methods to access the Internet instead of SNAT. To manage how ECS instances access the Internet, see [Attach an ENI to an ECS that is allocated with an public IP address](/intl.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Attach an ENI to an ECS that is allocated with an public IP address.md), [Attach an ENI to an ECS instance associated with an EIP](/intl.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Attach an ENI to an ECS instance associated with an EIP.md), and [Attach an ENI to an ECS instance configured with DNAT IP mapping](/intl.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Attach an ENI to an ECS instance configured with DNAT IP mapping.md).

-   ECS granularity

    If you create a SNAT entry for an ECS instance, the ECS instances access the Internet by using the public IP addresses specified for the SNAT entry and through the NAT gateway on which the SNAT entry is created.


