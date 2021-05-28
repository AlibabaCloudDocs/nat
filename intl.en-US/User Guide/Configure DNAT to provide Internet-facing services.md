# Configure DNAT to provide Internet-facing services

This topic describes how to create a Destination Network Address Translation \(DNAT\) entry. DNAT is used to map elastic IP addresses \(EIPs\) to Elastic Compute Service \(ECS\) instances in a virtual private cloud \(VPC\). After you configure DNAT, the ECS instances can provide Internet-facing services. DNAT supports port mapping and IP mapping.

## Background information

You cannot create DNAT entries for ECS instances that are associated with EIPs.

Before you can create DNAT entries for the ECS instances, you must disassociate the EIPs from the ECS instances. Then, you can create DNAT entries for the ECS instances. For more information, see [Disassociate an EIP from a cloud resource](/intl.en-US/User Guide/Disassociate an EIP from a cloud resource.md).

**Note:** If you create DNAT entries for an ECS instance that is associated with an EIP, the ECS instance preferably uses the EIP to communicate with the Internet.

## Prerequisites

A NAT gateway is created and an EIP is associated with the NAT gateway. For more information, see [Create a NAT gateway](/intl.en-US/Pricing/Purchase a NAT gateway.md) and [Associate EIPs](/intl.en-US/User Guide/Create NAT gateways.md).

**Note:** If you purchased a NAT service plan beforeJanuary 26, 2018, make sure that the NAT service plan contains idle public IP addresses.

## Create a DNAT entry

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is created.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to manage and click **Configure DNAT** in the **Actions** column.

4.  On the **DNAT Management** tab, click **Create DNAT Entry**.

5.  On the **Create DNAT Entry** page, set the parameters that are described in the following table and click **Confirm**.

    |Parameter|Description|
    |:--------|:----------|
    |**Select Public IP Address**|Select an EIP. The EIP is used to communicate with the Internet. **Note:** For enhanced NAT gateways, you can specify an EIP in both a SNAT entry and a DNAT entry. |
    |**Select Private IP Address**|Select the ECS instance that uses the DNAT entry to provide Internet-facing services. You can use the following methods to specify the private IP address of the ECS instance that provides Internet-facing services:     -   **Select by ECS or ENI**: Select an ECS instance from the ECS instance list or elastic network interface \(ENI\) list.
    -   **Manual Input**: Enter the private IP address of the selected ECS instance.

**Note:** The private IP address that you enter must be within the CIDR block of the VPC. You can also enter the private IP address of an ECS instance that is already deployed in the VPC. |
    |**Port Settings**|Select a DNAT mapping method:     -   **Any Port**: specifies IP mapping. The requests destined for the EIP are forwarded to the selected ECS instance.
    -   **Specific Port**: specifies port mapping. The NAT gateway forwards requests to the selected ECS instance based on the specified protocol and ports.

After you select Specific Port, set the following parameters based on your business requirements:

        -   **Public Port**: the external port that is used in port forwarding.
        -   **Private Port**: the internal port that is used in port forwarding.
        -   **Protocol Type**: the protocol used by the ports. |
    |**Entry Name**|Enter a name for the DNAT entry. The name must be 2 to 128 characters in length, and can contain digits, underscores \(\_\), and hyphens \(-\). It must start with a letter. |


## Modify a DNAT entry

After you create a DNAT entry, you can change the public IP address, private IP address, port settings, and name of the DNAT entry.

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is created.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to manage and click **Configure DNAT** in the **Actions** column.

4.  In the **DNAT Entry List** section, find the DNAT entry that you want to manage and click **Edit** in the **Actions** column.

5.  On the **Edit DNAT Entry** page, change the public IP address, private IP address, port settings, and name of the DNAT entry. Then, click **Confirm**.


## Delete a DNAT entry

If you no longer need an ECS instance to provide Internet-facing services, you can delete the DNAT entry of the ECS instance.

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is created.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to manage and click **Configure DNAT** in the **Actions** column.

4.  In the DNAT Entry List section, find the DNAT entry that you want to manage and click **Delete** in the **Actions** column.

5.  In the message that appears, click **OK**.


**Related topics**  


[CreateForwardEntry](/intl.en-US/API reference/NAT Gateway/CreateForwardEntry.md)

[ModifyForwardEntry](/intl.en-US/API reference/NAT Gateway/ModifyForwardEntry.md)

[DeleteForwardEntry](/intl.en-US/API reference/NAT Gateway/DeleteForwardEntry.md)

