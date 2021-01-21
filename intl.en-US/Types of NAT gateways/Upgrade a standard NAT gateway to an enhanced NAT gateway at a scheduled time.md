---
keyword: [NAT gateway, enhanced, network address translation, Internet-facing services, Internet access]
---

# Upgrade a standard NAT gateway to an enhanced NAT gateway at a scheduled time

Enhanced NAT gateways are upgraded from the technical architecture of standard NAT gateways. Compared with standard NAT gateways, enhanced NAT gateways offer higher elasticity and stability. This improves how you can manage data transfer. You can upgrade standard NAT gateways to enhanced NAT gateways at a scheduled time free of charge in the Virtual Private Cloud \(VPC\) console. The time period for free upgrades is extended from December 31, 2020 to March 30, 2021.

## Upgrade notes

Before you upgrade a standard NAT gateway to an enhanced NAT gateway, take note of the instructions in the following figure.

![Instructions](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0082659951/p147943.png)

The method that you can use to upgrade a standard NAT gateway varies based on whether NAT service plans are associated with the standard NAT gateway.

|Whether NAT service plans are associated|How to upgrade|
|----------------------------------------|--------------|
|No NAT service plan is associated|-   Immediate upgrade: Select the standard NAT gateway that you want to upgrade and click OK. Then, the standard NAT gateway is immediately upgraded to an enhanced NAT gateway.
-   Scheduled upgrade: Set the related parameters for the standard NAT gateway that you want to upgrade and click OK. You can select more than one standard NAT gateway if you use this method. A scheduled upgrade task is generated, and the standard NAT gateway is upgraded in the background at the specified time. |
|One or more NAT service plans are associated|Scheduled upgrade: Set the related parameters for the standard NAT gateway that you want to upgrade and click OK. You can select more than one standard NAT gateway if you use this method. A scheduled upgrade task is generated, and the standard NAT gateway is upgraded in the background at the specified time. |

## Upgrade notes for standard NAT gateways that are associated with NAT service plans

If a standard NAT gateway is associated with NAT service plans, you can upgrade the standard NAT gateway only by using a scheduled upgrade. You cannot immediately upgrade the standard NAT gateway.

Before you start, take note of the following information:

-   When you schedule an upgrade, you must provide the same information that is required to upgrade a standard NAT gateway without NAT service plans. In addition, you must specify the IDs of the NAT service plans that are associated with your standard NAT gateway. Each NAT gateway can be associated with one or more NAT service plans.
-   To perform a scheduled upgrade, you only need to submit the required information. After you submit the information, the system automatically upgrades the specified NAT gateway in the background at the scheduled time.
-   The upgrade is free of charge.
-   When you upgrade a standard NAT gateway to an enhanced NAT gateway, the configurations of the SNAT and DNAT entries on the NAT gateway remain unchanged. The upgrade does not have negative impacts on your workloads. However, we recommend that you upgrade your standard NAT gateways during off-peak hours.
-   The following table describes the changes to a standard NAT gateway after the standard NAT gateway is upgraded.

    |Service before the upgrade|Service after the upgrade|Remarks|
    |--------------------------|-------------------------|-------|
    |Standard NAT gateways that are associated with NAT service plans|Enhanced NAT gateways|The billing remains unchanged.|
    |NAT service plans|EIP bandwidth plans and elastic IP addresses \(EIPs\)|Public IP addresses are converted to EIPs. The billing method and maximum bandwidth remain unchanged after the NAT service plans are upgraded to EIP bandwidth plans.|


## Upgrade a standard NAT gateway to an enhanced NAT gateway at a scheduled time

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the standard NAT gateway is deployed.

3.  On the **NAT Gateway** page, click **Upgrade Now**.

    If this is not the first time you upgrade standard NAT gateways, click **Continue to Upgrade**.

    ![Upgrade Now](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6618369951/p146934.png)

4.  In the **Upgrade to Enhanced NAT Gateway** dialog box, click **Reserve Switch**. Then, set the parameters that are described in the following table and click **OK**.

    ![Scheduled an upgrade](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9698221161/p213058.png)

    |Parameter|Description|
    |---------|-----------|
    |**NAT Gateway**|Select the standard NAT gateway that you want to upgrade.|
    |**Select Switch Time**|Select the time window during which you want to upgrade the standard NAT gateway.**Note:** You can change or cancel an upgrade schedule before the upgrade starts. |
    |**Contact Information** \(optional\)|Enter your contact information in case an error occurs during the upgrade.|
    |**Select a VSwitch for the enhanced NAT gateway**|Select a zone and a vSwitch for the enhanced NAT gateway.**Note:** You must specify a vSwitch for the enhanced NAT gateway. After you specify a vSwitch, the system automatically selects an IP address from the CIDR block of the vSwitch to transmit data. Make sure that the CIDR block of the vSwitch has sufficient idle IP addresses. |
    |**Note on Creating Service-associated Roles**|To perform a scheduled upgrade, the system automatically creates the service-linked role `AliyunServiceRoleForNatgw`.|

5.  In the **Reserved** message, click **OK**.

    If the upgrade is scheduled, **Reserved** is displayed in the **Status** column.

6.  You can check the progress of the upgrade in the VPC console after the upgrade starts.


## Change an upgrade schedule

You can cancel or change an upgrade schedule before the upgrade starts.

1.  Move the pointer over the ![Message](../images/p213066.png) icon next to **Reserved** in the Status column.

2.  Click **Change Reservation** in the tooltip that appears.

    -   To change an upgrade schedule, change the time window, contact information, and vSwitch in the **Upgrade to Enhanced NAT Gateway** dialog box, and click **OK**.
    -   To cancel an upgrade schedule, click **Cancel Reservation** in the **Upgrade to Enhanced NAT Gateway** dialog box, and click **OK**.

**Related topics**  


[Enhanced NAT gateways \(new\)](/intl.en-US/Types of NAT gateways/Enhanced NAT gateways (new).md)

[Comparison between enhanced NAT gateways and standard NAT gateways](/intl.en-US/Types of NAT gateways/Comparison between enhanced NAT gateways and standard NAT gateways.md)

[Immediately upgrade a standard NAT gateway to an enhanced NAT gateway](/intl.en-US/Types of NAT gateways/Immediately upgrade a standard NAT gateway to an enhanced NAT gateway.md)

