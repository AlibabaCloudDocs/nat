---
keyword: [NAT Gateway, enhanced, network address translation, Internet-facing services, Internet access]
---

# Deploy multiple NAT gateways in one VPC

You can create multiple enhanced NAT gateways for one VPC to forward traffic to different IP addresses. This way, you can better manage traffic that is destined for the Internet. You can also use different services to protect each NAT gateway based on your requirements.

## Scenarios

To meet the requirements in the following scenario, multiple enhanced NAT gateways are deployed in one VPC. These enhanced NAT gateways function as independent Internet ingresses and egresses.

The vSwitches that are created in this scenario meet the following requirements:

-   vSwitch 1 belongs to the default security domain and is associated with the system route table.

    A dedicated public IP address is used to route network traffic. The bandwidth limit is 50 Mbit/s. The public IP address is not exposed to the Internet. ECS instances that are attached to vSwitch 1 can only send requests to the Internet, but cannot receive requests from the Internet. These ECS instances require a private network environment.

-   vSwitch 2 belongs to a special security domain and is associated with the subnet route table of the VPC.

    The ECS instances that are attached to vSwitch 2 share the same egress to communicate with the Internet. They can both send requests to the Internet and receive requests from the Internet. The bandwidth limit is 1 Gbit/s.

-   vSwitch 3 belongs to the same special security domain and is associated with the subnet route table of the VPC.

    The ECS instances that are attached to vSwitch 3 share the same egress to communicate with the Internet. They can both send requests to the Internet and receive requests from the Internet. The bandwidth limit is 1 Gbit/s.


## How to deploy multiple NAT gateways for one VPC

To deploy enhanced NAT gateways in the preceding scenario, you must create resources that meet the following requirements:

-   Create a VPC and three vSwitches in the VPC. Deploy a NAT gateway \(NATGW-1\) in the default security domain and another NAT gateway \(NATGW-2\) in an independent security domain. Associate vSwitch 1 with NATGW-1, and associate vSwitch 2 and vSwitch 3 with NATGW-2.
-   Create a 50 Mbit/s elastic IP address \(EIP\) and add the EIP to the Source Network Address Translation \(SNAT\) entry of NATGW-1.
-   Purchase an EIP bandwidth plan of 1 Gbit/s in size, and associate it with NATGW-2. Create three EIPs and associate the EIPs with the EIP bandwidth plan. Two EIPs are used to translate destination IP addresses for vSwitch 2 and vSwitch 3. The remaining EIP is used to translate source IP addresses for the two vSwitches.
-   Enable NATGW-2 to monitor the outbound network traffic that is forwarded by the vSwitches. This way, you can check whether the vSwitches work as expected.

## Resources and configurations

|Cloud resource|Configuration|Quantity|
|--------------|-------------|--------|
|VPC|Deployed in the China \(Hohhot\) region|1|
|VSwitch|Deployed across two zones|3|
|Enhanced NAT gateway|Deployed in the same VPC|2|

|Cloud resource|Configuration|Quantity|
|--------------|-------------|--------|
|Enhanced NAT gateway|Billing method: pay-as-you-go. Size: small.|1|
|EIP|Metering method: pay-by-bandwidth. Bandwidth limit: 50 Mbit/s.|1|
|ECS|ecs.g6e.large|1|

|Cloud resource|Configuration|Quantity|
|--------------|-------------|--------|
|Enhanced NAT gateway|Billing method: pay-as-you-go. Size: medium.|1|
|EIP|Metering method: pay-by-bandwidth. Bandwidth limit: 5 Mbit/s.|3|
|EIP bandwidth plan|Metering method: pay-by-bandwidth. Bandwidth limit: 1 Gbit/s.|1|
|ECS|ecs.g6e.large|2|

