---
keyword: [NAT gateway, enhanced, network address translation, Internet-facing services, Internet access]
---

# Create a SNAT entry to access the Internet

You can configure Source Network Address Translation \(SNAT\) for a NAT gateway to allow all Elastic Compute Service \(ECS\) instances in a virtual private cloud \(VPC\) to access the Internet when the ECS instances are not assigned static public IP addresses or elastic IP addresses \(EIPs\).

## Limits

The following limits apply to the EIPs in the SNAT address pool:

-   The bandwidth limit supported by each EIP that is associated with a standard NAT gateway is 200 Mbit/s.
-   The maximum number of concurrent connections to each EIP is 55,000.

To make full use of your EIP bandwidth plan and avoid port conflicts caused by insufficient EIPs, we recommend that you add EIPs to the SNAT address pool based on the following rules:

-   For standard NAT gateways, if the bandwidth limit of the EIP bandwidth plan is 1,024 Mbit/s, specify at least five EIPs in each SNAT entry.
-   For standard NAT gateways, if the bandwidth limit of the EIP bandwidth plan exceeds 1,024 Mbit/s, specify one additional EIP in every SNAT entry for every 200 Mbit/s that exceeds 1,024 Mbit/s.

If an ECS instance is assigned a static public IP address, an EIP, or configured with DNAT IP mapping, the ECS instance uses the preceding methods to access the Internet instead of SNAT. For more information about how to configure ECS instances in a VPC to use the same public IP address to access the Internet, see [Attach an ENI to an ECS that is allocated with an public IP address](/intl.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Configure ECS instances that are assigned static public IP addresses to use the same EIP to access the Internet.md) and [Configure ECS instances that use DNAT IP mapping to use the same EIP to access the Internet](/intl.en-US/Best Practices/Uniformly manage public IP addresses of ECS instances in a VPC/Configure ECS instances that use DNAT IP mapping to use the same EIP to access the
         Internet.md).

For enhanced NAT gateways, you can specify an EIP in both a SNAT entry and a DNAT entry when your account is included in the whitelist. To apply to be added to a whitelist,[submit a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex).

## Prerequisites

Before you create a SNAT entry, make sure that the following requirements are met:

-   A NAT gateway is created, and an EIP is associated with the NAT gateway. For more information, see [Create a NAT gateway](/intl.en-US/Pricing/Purchase a NAT gateway.md) and [Associate an EIP with a NAT gateway](/intl.en-US/User Guide/Create NAT gateways.md).

    **Note:** If you purchased a NAT service plan before January 26, 2018, make sure that the NAT service plan has idle public IP addresses.

-   To create SNAT entries for a vSwitch, make sure that the vSwitch is created in the VPC that is associated with the NAT gateway. For more information, see [Work with vSwitches](/intl.en-US/VPCs and vSwitchs/Work with vSwitches.md).
-   To create SNAT entries for an ECS instance, make sure that the ECS instance is created in the VPC that is associated with the NAT gateway. For more information, see [Create an instance by using the wizard](/intl.en-US/Instance/Create an instance/Create an instance by using the wizard.md).

## Create a SNAT entry

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to manage and click **Configure SNAT** in the **Actions** column.

4.  On the **SNAT Management** tab, click **Create SNAT Entry**.

5.  On the **Create SNAT Entry** page, set the parameters that are described in the following table and click **Confirm**.

    |Parameter|Description|
    |:--------|:----------|
    |**SNAT Entry**|Specify whether you want to create a SNAT entry for an ECS instance or a vSwitch.    -   **Specify VSwitch**: The ECS instances that are attached to the vSwitch use the specified EIP to access the Internet.
        -   **Select VSwitch**: Select a vSwitch from the drop-down list. If no vSwitch is available in the drop-down list, click **Create VSwitch** from the drop-down list. Then, you are redirected to the VPC console where you can create vSwitches.

**Note:** If you select multiple vSwitches, the system creates multiple SNAT entries that use the same EIP.

        -   **VSwitch CIDR Block**: displays the CIDR block of the vSwitch.
    -   **Specify ECS Instance**: The specified ECS instances use the specified EIP to access the Internet.
        -   **Select ECS Instance**: Select an ECS instance from the drop-down list. The selected ECS instance uses the specified EIP to access the Internet. Make sure that the following requirements are met:

            -   The ECS instance is in the Running state.
            -   The ECS instance is not assigned an EIP or static public IP address.
**Note:**

            -   If no ECS instance is available in the drop-down list, click **Create ECS Instance** from the drop-down list. Then, you are redirected to the ECS console where you can create ECS instances.
            -   If you select multiple ECS instances, the system creates multiple SNAT entries that use the same EIP.
        -   **ECS CIDR Block**: displays the CIDR block of the ECS instance. |
    |**Select Public IP Address**|Select an EIP. The EIP is used to allow access to the Internet.     -   **Use One IP Address**: Select an EIP from the drop-down list. If no EIPs are available in the drop-down list, click **Purchase and Associate EIP** from the drop-down list. Then, you can purchase an EIP in the dialog box that appears.
    -   **Use Multiple IP Addresses**: If multiple EIPs are specified in a SNAT IP address pool, make sure that the specified EIPs are associated with the same EIP bandwidth plan. To allow an ECS instance in a VPC to access the Internet, an EIP in the SNAT address pool is randomly assigned to the ECS instance.
        -   **EIP Bandwidth Plan**: Select an EIP bandwidth plan from the drop-down list. If no EIP bandwidth plan is available in the drop-down list, click **Create EIP Bandwidth Plan** from the drop-down list. Then, you can purchase an EIP bandwidth plan on the buy page that appears.
        -   **Public IP Address**: Select an EIP that is associated with the selected EIP bandwidth plan from the drop-down list. |
    |**Entry Name**|Enter a name for the SNAT entry. The name must be 2 to 128 characters in length, and can contain digits, underscores \(\_\), and hyphens \(-\). It must start with a letter. |


## Modify a SNAT entry

You can modify the name and EIP of a SNAT entry after you create the SNAT entry. However, you cannot modify the vSwitch and ECS instances that are specified in the SNAT entry.

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to manage and click **Configure SNAT** in the **Actions** column.

4.  In the **Used in SNAT Entry** section, find the SNAT entry that you want to manage and click **Edit** in the **Actions** column.

5.  On the **Edit SNAT Entry** page, change the EIP or name of the SNAT entry and click **Confirm**.

    **Note:** Your service may be interrupted after you add EIPs to or remove EIPs from a SNAT entry. The service resumes after your workloads are reconnected. Proceed with caution.


## Delete a SNAT entry

You can delete a SNAT entry if the ECS instances that are not assigned public IP addresses in a VPC no longer need the SNAT service to access the Internet.

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to manage and click **Configure SNAT** in the **Actions** column.

4.  In the **Used in SNAT Entry** section, find the SNAT entry that you want to delete and click **Remove** in the **Actions** column.

5.  In the dialog box that appears, click **OK**.


**Related topics**  


[CreateSnatEntry](/intl.en-US/API reference/NAT Gateway/CreateSnatEntry.md)

[ModifySnatEntry](/intl.en-US/API reference/NAT Gateway/ModifySnatEntry.md)

[DeleteSnatEntry](/intl.en-US/API reference/NAT Gateway/DeleteSnatEntry.md)

