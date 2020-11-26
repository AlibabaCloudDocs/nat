# Switch from a self-managed SNAT gateway to an Alibaba Cloud NAT gateway without service disruption

This topic describes how to switch Elastic Compute Service \(ECS\) instances from a self-managed Source Network Address Translation \(SNAT\) gateway to an Alibaba Cloud NAT gateway without service disruption. This task is performed based on the longest prefix matching rule of route tables.

If you have created a SNAT gateway for ECS instances in a virtual private cloud \(VPC\), but you want the ECS instances to access the Internet through a NAT gateway, you can delete the SNAT gateway. Then, create and configure a NAT gateway for the ECS instances. However, this operation interrupts the SNAT service for a short period of time.

To switch the ECS instances from a self-managed SNAT gateway to an Alibaba Cloud NAT gateway without service disruption, you can use certain features provided by route tables. The main feature is the longest prefix matching rule. This avoids SNAT service disruption. Only a transient TCP connection error occurs during the switchover process.

The VPC and ECS instances used in this topic are configured based on the following information:

-   Two ECS instances are created in the VPC.

    -   A self-managed SNAT gateway is configured for ECS instance i-9410jxxxx. An elastic IP address \(EIP\) is associated with the ECS instance. The forwarding service is enabled and iptables rules are configured for the ECS instance to implement SNAT-based forwarding.
    -   ECS instance i-94kjwxxxx requires the SNAT service to access the Internet.
-   A custom route entry is added to the VRouter of the VPC. The destination CIDR block of the route entry is 0.0.0.0/0 and the next hop of the route entry is ECS instance i-9410jxxxx.


1.  Add eight route entries to the VRouter of the VPC to overwrite the existing route entry.

    The destination CIDR blocks of the route entries to be added are 1.0.0.0/8, 2.0.0.0/7, 4.0.0.0/6, 8.0.0.0/5, 16.0.0.0/4, 32.0.0.0/3, 64.0.0.0/2, and 128.0.0.0/1. The next hops of these route entries are ECS instance i-9410jxxxx.

    Based on the longest prefix matching rule, the route entry with the longest subnet mask has the highest priority. All packets match one of the eight route entries regardless of the destination IP addresses of the packets. Therefore, the route entry whose destination CIDR block is 0.0.0.0/0 is no longer matched.

2.  Delete the route entry whose destination CIDR block is 0.0.0.0/0.

3.  Create a NAT gateway.

    After you create the NAT gateway, the system automatically adds a route entry that points to the NAT gateway. The destination CIDR block of the route entry is 0.0.0.0/0.

4.  Associate an EIP with the NAT gateway.

    **Note:** Make sure that the maximum bandwidth of the EIP is the same as that of the self-managed SNAT gateway. You only need to create SNAT entries on the NAT gateway. Therefore, the outbound traffic of ECS instances specified in the SNAT entries is throttled by the maximum bandwidth of the EIP.

5.  Configure SNAT entries.

6.  Delete the eight route entries that are added to the VRouter of the VPC. Then, the VRouter forwards requests from the Internet to the NAT gateway instead of the self-managed SNAT gateway.

    After you perform this step, the ECS instances are successfully switched from the self-managed SNAT gateway to the Alibaba Cloud NAT gateway.


