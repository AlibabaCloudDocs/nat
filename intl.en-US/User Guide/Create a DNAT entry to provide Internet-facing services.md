# Create a DNAT entry to provide Internet-facing services

This topic describes how to create a Destination Network Address Translation \(DNAT\) entry. DNAT is used to map elastic IP addresses \(EIPs\) to Elastic Compute Service \(ECS\) instances in a virtual private cloud \(VPC\). This way, the ECS instances can receive requests sent over the Internet. DNAT supports port mapping and IP mapping.

## Background information

You cannot create DNAT entries for ECS instances with which EIPs are associated.

Before you can create DNAT entries for the ECS instances, you must disassociate the EIPs from the ECS instances. Then, you can create DNAT entries for the ECS instances. For more information, see [Disassociate an EIP from a cloud resource](/intl.en-US/User Guide/Disassociate an EIP from a cloud resource.md).

**Note:** If you created DNAT entries for an ECS instance that is assigned an EIP, the ECS instance preferentially uses the EIP to communicate with the Internet.

## Prerequisites

A NAT gateway is created and assigned an EIP. For more information, see [Create a NAT gateway](/intl.en-US/Pricing/Purchase a NAT gateway.md) and [Associate an EIP with a NAT gateway](/intl.en-US/User Guide/Create NAT gateways.md).

**Note:** If you purchased a NAT service plan beforeJanuary 26, 2018, make sure that the NAT service plan has idle public IP addresses.

## Create a DNAT entry

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to manage and click **Configure DNAT** in the **Actions** column.

4.  On the **DNAT Management** tab, click **Create DNAT Entry**.

5.  On the **Create DNAT Entry** page, set the following parameters and click **Confirm**.

    |Parameter|Description|
    |:--------|:----------|
    |**Select Public IP Address**|Select an EIP. The EIP is used to communicate with the Internet. **Note:** For enhanced NAT gateways, you can specify an EIP in both a SNAT entry and a DNAT entry when your account is included in the whitelist. To apply to be added to the whitelist,[submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex). |
    |**Select Private IP Address**|Select the ECS instance that uses the DNAT entry to receive requests from the Internet. You can use one of the following methods to specify the private IP address of the ECS instance that receives requests from the Internet:     -   **Select by ECS or ENI**: Select an ECS instance from the ECS instance list or Elastic Network Interface \(ENI\) list.
    -   **Manual Input**: Enter the private IP address of the selected ECS instance.

**Note:** The private IP address that you enter must be within the CIDR block of the VPC. You can also enter the private IP address of an ECS instance that exists in the VPC. |
    |**Port Settings**|Select a DNAT mapping method:     -   **Any Port**: This method uses IP mapping. Requests destined for the EIP are forwarded to the selected ECS instance.
    -   **Specific Port**: This method uses port mapping. The NAT gateway forwards requests from the specified port over the specified protocol to the specified port of the selected ECS instance.

After you specify a port, set the following parameters based on your business requirements:

        -   **Public Port**: the external port that is used in port forwarding.
        -   **Private Port**: the internal port that is used in port forwarding.
        -   **Protocol Type**: the protocol that is used by the ports. |
    |**Entry Name**|Enter a name for the DNAT entry. The name must be 2 to 128 characters in length, and can contain digits, underscores \(\_\), and hyphens \(-\). It must start with a letter. |


## Modify a DNAT entry

After you create a DNAT entry, you can modify the public IP address, private IP address, ports, and name of the DNAT entry.

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to manage and click **Configure DNAT** in the **Actions** column.

4.  In the **DNAT Entry List** section, find the DNAT entry that you want to manage and click **Edit** in the **Actions** column.

5.  On the **Edit DNAT Entry** page, change the public IP address, private IP address, port settings, and name of the DNAT entry. Then, click **Confirm**.


## Delete a DNAT entry

If you no longer need an ECS instance to provide Internet-facing services, you can delete the DNAT entry of the ECS instance.

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to manage and click **Configure DNAT** in the **Actions** column.

4.  In the DNAT Entry List section, find the DNAT entry that you want to manage and click **Delete** in the **Actions** column.

5.  In the message that appears, click **OK**.


**Related topics**  


[CreateForwardEntry](/intl.en-US/API reference/NAT Gateway/CreateForwardEntry.md)

[ModifyForwardEntry](/intl.en-US/API reference/NAT Gateway/ModifyForwardEntry.md)

[DeleteForwardEntry](/intl.en-US/API reference/NAT Gateway/DeleteForwardEntry.md)
