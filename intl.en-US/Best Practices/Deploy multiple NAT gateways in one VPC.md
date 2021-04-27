---
keyword: [NAT gateway, enhanced, network address translation, Internet-facing services, Internet access]
---

# Deploy multiple NAT gateways in one VPC

You can create multiple enhanced NAT gateways in one VPC to forward traffic to different IP addresses. This way, you can better manage traffic that is destined for the Internet. You can also use different services to protect each NAT gateway based on your requirements.

## Scenarios

To meet the requirements in the following scenario, multiple enhanced NAT gateways are deployed in one VPC. The enhanced NAT gateways function as independent Internet ingresses and egresses.

![Architecture](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7267059161/p206992.png)

The vSwitches that are created in this scenario meet the following requirements:

-   vSwitch 1 belongs to the default security domain and is associated with the system route table.

    A dedicated public IP address is used to route network traffic. The bandwidth limit is 50 Mbit/s. The public IP address is not exposed to the Internet. Elastic Compute Service \(ECS\) instances that are attached to vSwitch 1 can only send requests to the Internet, but cannot receive requests from the Internet. The ECS instances require a private network environment.

-   vSwitch 2 belongs to a special security domain and is associated with the subnet route table of the VPC.

    The ECS instances that are attached to vSwitch 2 share the same egress to communicate with the Internet. They can both send requests to the Internet and receive requests from the Internet. The bandwidth limit is 1 Gbit/s.

-   vSwitch 3 belongs to the same special security domain and is associated with the subnet route table of the VPC.

    The ECS instances that are attached to vSwitch 3 share the same egress to communicate with the Internet. They can both send requests to the Internet and receive requests from the Internet. The bandwidth limit is 1 Gbit/s.


## How to deploy multiple NAT gateways in one VPC

To deploy enhanced NAT gateways in the preceding scenario, you must create resources that meet the following requirements:

-   Create a VPC and three vSwitches in the VPC. Deploy a NAT gateway \(NATGW-1\) in the default security domain and another NAT gateway \(NATGW-2\) in an independent security domain. Associate vSwitch 1 with NATGW-1. Then, associate vSwitch 2 and vSwitch 3 with NATGW-2.
-   Create a 50 Mbit/s elastic IP address \(EIP\) and add the EIP to the Source Network Address Translation \(SNAT\) entry of NATGW-1.
-   Purchase an EIP bandwidth plan of 1 Gbit/s in size, and associate it with NATGW-2. Create three EIPs and associate the EIPs with the EIP bandwidth plan. Two EIPs are used to translate destination IP addresses for vSwitch 2 and vSwitch 3. The remaining EIP is used to translate source IP addresses for the two vSwitches.
-   Enable NATGW-2 to monitor the outbound network traffic that is forwarded by the vSwitches. This way, you can check whether the vSwitches work as expected.

## Resources and configurations

|Cloud resource|Configuration|Quantity|
|--------------|-------------|--------|
|VPC|Deployed in the China \(Hohhot\) region|1|
|VSwitch|Deployed across two zones|3|

|Cloud resource|Configuration|Quantity|
|--------------|-------------|--------|
|Enhanced NAT gateway|Billing method: pay-as-you-go.|1|
|EIP|Metering method: pay-by-bandwidth. Bandwidth limit: 50 Mbit/s.|1|
|ECS|ecs.g6e.large|1|

|Cloud resource|Configuration|Quantity|
|--------------|-------------|--------|
|Enhanced NAT gateway|Billing method: pay-as-you-go.|1|
|EIP|Metering method: pay-by-bandwidth. Bandwidth limit: 5 Mbit/s.|3|
|EIP bandwidth plan|Metering method: pay-by-bandwidth. Bandwidth limit: 1 Gbit/s.|1|
|ECS|ecs.g6e.large|2|

## Workflow

![Deploy multiple NAT gateways in one VPC](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6157059161/p206994.png)

## Step 1: Create cloud resources

Before you deploy NAT gateways for vSwitches, you must first create the following cloud resources: a VPC, vSwitches, ECS instances, EIPs, and an EIP bandwidth plan.

|Cloud resource|Specification|Quantity|Reference|
|--------------|-------------|--------|---------|
|VPC|**Region**: China \(Hohhot\).|1|[Create a VPC and a vSwitch](/intl.en-US/Quick Start/Create an IPv4 VPC.md).|
|VSwitch|**Zone**:-   One vSwitch named vSwitch 1 is created in Hohhot Zone A.
-   Two vSwitches named vSwitch 2 and vSwitch 3 are created in Hohhot Zone B.

|3|[Create a VPC and a vSwitch](/intl.en-US/Quick Start/Create an IPv4 VPC.md).|
|ECS instance|-   **Billing method**: **Pay-as-you-go** is selected in this example.
-   **Region and Zone**: The ECS instances are deployed in the China \(Hohhot\) region in this example.
-   **Instance**: ecs.g6e.large is selected in this example.
-   **Network Type**: Select the VPC and vSwitches that you created.
    -   One vSwitch is selected in Hohhot Zone A.
    -   Two vSwitches are selected in Hohhot Zone B.
-   **Public IP Address**: Clear the check box.
-   **Security Group**: Use the default security group.

|3|[Create an ECS instance](/intl.en-US/Quick Start/Create an IPv4 VPC.md)|
|EIP|-   **Region**: China \(Hohhot\).
-   **Bandwidth limit**: one 50 Mbit/s EIP and three 5 Mbit/s EIPs.

|4|[Apply for new EIPs](/intl.en-US/User Guide/Create an EIP/Apply for new EIPs.md)|
|EIP bandwidth plan|-   **Region**: China \(Hohhot\).
-   **Bandwidth limit**: 1,000 Mbit/s.

|1|[Create an EIP bandwidth plan](/intl.en-US/User Guide/Create an EIP bandwidth plan.md)|

## Step 2: Create two NAT gateways

Create two NAT gateways named NATGW-1 and NATGW-2 that are billed on a pay-as-you-go basis in the VPC. Associate NATGW-1 with vSwitch 1, and associate NATGW-2 with vSwitch 2 and vSwitch 3.

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  On the **NAT Gateway** page, click **Create NAT Gateway**.

3.  When you purchase a NAT gateway for the first time, you must create the required service-linked role for NAT Gateway. In the lower part of the **NAT Gateway \(Pay-As-You-Go\)** page, click **Create** in the Notes on Creating Service-linked Roles section. After the service-linked role is created, you can purchase a NAT gateway.

4.  On the **NAT Gateway \(Pay-As-You-Go\)** page, set the following parameters and click **Buy Now**.

    -   Specify the following parameters for NATGW-1:
        -   **Region and Zone**: **China \(Hohhot\)** is selected in this example.
        -   **Zone**: Select the zone where vSwitch 1 is deployed. Hohhot Zone A is selected in this example.
        -   **VPC ID**: Select the VPC that you created. After you create a NAT gateway, you cannot change the VPC where the NAT gateway is deployed.
        -   **vSwitch ID**: Select the vSwitch that you created. vSwitch 1 is selected in this example.
        -   **Gateway Type**: By default, **Enhanced** is selected.
        -   **Billing Method**: **Pay By Actual Usage** is selected in this example.
        -   **Billing Method**: Select a billing method for the NAT gateway.

            Only the pay-by-specification billing method is supported.

        -   **Billing Cycle**: Specify the billing cycle of the NAT gateway. By default, **By Hour** is selected.
    -   Specify the following parameters for NATGW-2:
        -   **Region and Zone**: **China \(Hohhot\)** is selected in this example.
        -   **Zone**: Select the zone where vSwitch 2 is deployed. Hohhot Zone B is selected in this example.
        -   **VPC ID**: Select the VPC that you created. After you create a NAT gateway, you cannot change the VPC where the NAT gateway is deployed.
        -   **vSwitch ID**: Select the vSwitch that you created. vSwitch 2 is selected in this example.
        -   **Gateway Type**: By default, **Enhanced** is selected.
        -   **Billing Method**: **Pay By Actual Usage** is selected in this example.
        -   **Billing Method**: Select a billing method for the NAT gateway.

            Only the pay-by-specification billing method is supported.

        -   **Billing Cycle**: Specify the billing cycle of the NAT gateway. By default, **By Hour** is selected.
5.  On the Confirm Order page, check the payment amount and click **Activate Now** to complete the payment.

    When **Order complete.** appears, the NAT gateway is purchased.


## Step 3: Create a custom route table to route traffic to vSwitch 2 and vSwitch 3

A route table consists of one or more route entries. Each route entry specifies the destination network to which traffic is routed. You can create a custom route table to manage the inbound and outbound network traffic of subnets in a VPC.

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com/vpc).

2.  In the left-side navigation pane, click **Route Tables**.

3.  Select the region where you want to create a route table.

    For more information about the regions that support custom route tables, see [Regions that support custom route tables]().

4.  On the Route Tables page, click **Create Route Table**.

5.  On the Create Route Table page, set the following parameters and click **OK**.

    |Configuration|Description|
    |-------------|-----------|
    |**Resource Group**|Select the resource group to which the route table belongs.|
    |**VPC**|Select the VPC to which the route table belongs.|
    |**Name**|Enter a name for the route table. The name must be 2 to 128 characters in length, and can contain digits, underscores \(\_\), and hyphens \(-\). It must start with a letter. |
    |**Description**|Enter a description for the route table. The description must be 2 to 256 characters in length and cannot start with `http://` or `https://`. |

    After you create a custom route table, you can go to the Route Tables page to view the route table. The type of route table is displayed as **Custom** in the **Route Table Type** column. The following system routes are automatically added to the custom route table:

    -   A route entry that points to the CIDR block 100.64.0.0/10. After the route entry is added, the cloud resources in the VPC can communicate with each other.
    -   Route entries that point to the CIDR blocks of the vSwitches in the VPC to which the route table belongs. After the route entries are added, the cloud resources that are attached to the vSwitches can communicate with each other.
6.  On the Route Tables page, find the route table that you want to manage and click its ID.

7.  In the Route Table Details section, click the **Associated vSwitch** tab and click **Associate vSwitch**.

8.  In the Associate VSwitch panel, select vSwitch 2 and click **OK**. Repeat this step to associate the route table with vSwitch 3.

9.  Click the **Route Entry List** tab, and click **Add Route Entry**. In the **Add Route Entry** panel, set the following parameters.

    |Configuration|Description|
    |:------------|:----------|
    |**Name**|Enter a name for the route entry. The name must be 2 to 128 characters in length, and can contain digits, underscores \(\_\), and hyphens \(-\). It must start with a letter. |
    |**Destination CIDR Block**|Enter the destination CIDR block to which you want to route traffic. In this example, the destination CIDR block is set to 0.0.0.0/32.|
    |**Next Hop Type**|**NAT Gateway** is selected in this example. Traffic destined for the specified CIDR block is routed to the specified NAT gateway.|
    |**NAT Gateway**|Select NATGW-2 that you created in [Step 2: Create two NAT gateways](#section_k9k_fg8_9mf) from the drop-down list as the next hop.|

    After the route table is created, a default route that points to the enhanced NAT gateway is added to the route table.


## Step 4: Associate the three 5 Mbit/s EIPs with an EIP bandwidth plan to share resources

1.  Log on to the [EIP bandwidth plan console](https://vpc.console.aliyun.com/cbwp/cn-hangzhou/cbwps).

2.  In the top navigation bar, select the region where the EIP bandwidth plan is created.

3.  On the **Internet Shared Bandwidth** page, find the EIP bandwidth plan that you want to manage and click **Add IP** in the **Actions** column.

4.  In the **Add IP** panel, click the **Select from EIP List** tab.Then, select an idle EIP and click **OK**.


## Step 5: Associate the four EIPs with the NAT gateways in sequence

Associate the EIPs with the NAT gateway that you created in [Step 2: Create two NAT gateways](#section_k9k_fg8_9mf). In this example, associate the 50 Mbit/s EIP with NATGW-1 and associate the three 5 Mbit/s EIPs with NATGW-2.

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the **Associate EIP** dialog box, set the following parameters and click **OK**.

    |Configuration|Description|
    |-------------|-----------|
    |**Resource Group**|Select the resource group of the EIP.|
    |**EIPs**|Select **Select Existing EIPs** and select an EIP from the drop-down list.    -   In this example, the 50 Mbit/s EIP is associated with NATGW-1.
    -   In this example, the three 5 Mbit/s EIPs are associated with NATGW-2. |

    After you associate the EIPs with the NAT gateways, the EIPs appear in the **Elastic IP Address** column.


## Step 6: Create SNAT entries

SNAT allows ECS instances in a VPC to access the Internet through a NAT gateway when the ECS instances are not assigned public IP addresses or EIPs. Create one SNAT entry for NATGW-1, and create two SNAT entries for NATGW-2.

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to manage and click **Configure SNAT** in the **Actions** column.

4.  On the **SNAT Management** tab, click **Create SNAT Entry**.

5.  On the **Create SNAT Entry** page, set the following parameters and click **Confirm**.

    -   In this example, vSwitch 1 is selected when you create a SNAT entry for NATGW-1.
    -   When you create a SNAT entry for NATGW-2, you must point vSwitch 2 and vSwitch 3 to the EIPs that are specified in the same SNAT entry.
    |Parameter|Description|
    |:--------|:----------|
    |**SNAT Entry**|Specify whether you want to create a SNAT entry for an ECS instance or a vSwitch. **Specify VSwitch**: The ECS instances that are attached to the vSwitch use the specified EIP to access the Internet. This option is selected in this example.     -   **Select VSwitch**: Select a vSwitch from the drop-down list. If no vSwitch is available in the drop-down list, click **Create VSwitch** from the drop-down list. Then, you are redirected to the VPC console where you can create vSwitches.

**Note:** If you select multiple vSwitches, the system creates multiple SNAT entries that use the same EIP.

    -   **VSwitch CIDR Block**: displays the CIDR block of the vSwitch. |
    |**Select Public IP Address**|Select an EIP. The EIP is used to communicate with the Internet. You can select an EIP from the drop-down list. **Use One IP Address** is specified in this example. If no EIPs are available in the drop-down list, click **Purchase and Associate EIP** from the drop-down list to purchase an EIP.|
    |**Entry Name**|Enter a name for the SNAT entry. The name must be 2 to 128 characters in length, and can contain digits, underscores \(\_\), and hyphens \(-\). It must start with a letter. |


## Step 7: Create a DNAT entry

A DNAT entry maps the EIP of a NAT gateway to an ECS instance. Then, the ECS instance can provide Internet-facing services.

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to manage and click **Configure DNAT** in the **Actions** column.

4.  On the **DNAT Management** tab, click **Create DNAT Entry**.

5.  On the **Create DNAT Entry** page, set the parameters and click **Confirm**.

    Set the following parameters to create a DNAT entry for vSwitch 2 and vSwitch 3.

    |Configuration|Description|
    |-------------|-----------|
    |**Select Public IP Address**|Select an EIP from the drop-down list. The EIP is used to communicate with the Internet.|
    |**Select Private IP Address**|Select the ECS instance that uses the DNAT entry to receive requests from the Internet. **Select by ECS or ENI**: Select an ECS instance from the ECS instance list or Elastic Network Interface \(ENI\) list.|
    |**Port Settings**|Select a DNAT mapping method. **Specific Port** is selected in this example. The following describes how to set the ports for vSwitch 2 and vSwitch 3:

    -   vSwitch 2:
        -   **Public Port**: the external port that is used in port forwarding. Port 8443 is specified in this example.
        -   **Private Port**: the internal port that is used in port forwarding. Port 443 is specified in this example.
        -   **Protocol Type**: the protocol that is used by the ports. TCP is selected in this example.
    -   vSwitch 3:
        -   **Public Port**: the external port that is used in port forwarding. Port 8800 is specified in this example.
        -   **Private Port**: the internal port that is used in port forwarding. Port 80 is specified in this example.
        -   **Protocol Type**: the protocol that is used by the ports. TCP is selected in this example. |
    |**Entry Name**|The name of the DNAT entry. The name must be 2 to 128 characters in length, and can contain digits, underscores \(\_\), and hyphens \(-\). It must start with a letter. |


## Check the connectivity and view monitoring metrics



Log on to an ECS instance. To check the network connectivity between the ECS instance and the Internet, perform the following steps. You can also query the EIPs in the SNAT entry that is created for the ECS instance. The ECS instance that is attached to vSwitch 1 is used in this example.

1.  Log on to the ECS instance that is attached to vSwitch 1.

2.  Run the `ping` command to check the network connectivity.

    The check result shows that the ECS instance can access the Internet.

    ![Check SNAT](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6157059161/p208573.png)

3.  To query the EIPs in the SNAT entry that is created for the ECS instance, run the `curl myip.ipip.net` command.

    ![Query the EIPs in the SNAT entry](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6157059161/p208574.png)




Create two mappings that point to port 22 on the two ECS instances. After you create the mappings, you can use SSH to log on to the ECS instances. Then, you can check whether the ECS instances can be accessed through DNAT.

1.  Use an on-premises machine to access the external ports in the DNAT entries that are created for vSwitch 2 and vSwitch 3.

    ![Access the ECS instance through DNAT](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6157059161/p208575.png)

2.  Log on to the ECS instance and run the `ifconfig` command. If the IP address returned is the same as the private IP address of the ECS instance, it indicates that the ECS instance can provide Internet-facing services.

    ![Access log](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6157059161/p208576.png)




1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to manage and click the ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6894140061/p41324.png) icon in the **Monitoring** column.

    |Category|Metric|Description|
    |--------|------|-----------|
    |SNAT session statistics|Concurrent connections|The maximum number of concurrent Transmission Control Protocol \(TCP\) or User Datagram Protocol \(UDP\) connections that are supported by a NAT gateway.|
    |Rate of concurrent connections dropped|The rate of concurrent connections that are dropped due to the limit of concurrent connections to a NAT gateway.|
    |Rate of new connections established and rate of new connections dropped|Rate of new connections established: the number of TCP or UDP connections that are established to a NAT gateway per second. Rate of new connections dropped: the number of new connections that are dropped per second due to the limit of new connections that can be established to a NAT gateway per second. |
    |Ratio of concurrent connections and ratio of new connections|Ratio of concurrent connections: the ratio of concurrent connections to the upper limit of connections. Ratio of new connections: the ratio of established new connections to the upper limit of new connections. |
    |Inbound traffic statistics|Inbound traffic rate|The amount of inbound traffic per second:    -   Rate of traffic from the Internet.
    -   Rate of traffic to a VPC. |
    |Inbound traffic|The total amount of inbound traffic:    -   Traffic from the Internet.
    -   Traffic to a VPC. |
    |Inbound packet rate|The number of inbound packets per second:    -   Rate of packets from the Internet.
    -   Rate of packets to a VPC. |
    |Inbound packets|The total number of inbound packets:    -   Packets from the Internet.
    -   Packets to a VPC. |
    |Outbound traffic statistics|Outbound traffic rate|The amount of outbound traffic per second:    -   Rate of traffic to the Internet.
    -   Rate of traffic from a VPC. |
    |Outbound traffic|The total amount of outbound traffic:    -   Traffic to the Internet.
    -   Traffic from a VPC. |
    |Outbound packet rate|The number of outbound packets per second:    -   Rate of packets to the Internet.
    -   Rate of packets from a VPC. |
    |Outbound packets|The number of outbound packets:    -   Packets to the Internet.
    -   Packets from a VPC. |


