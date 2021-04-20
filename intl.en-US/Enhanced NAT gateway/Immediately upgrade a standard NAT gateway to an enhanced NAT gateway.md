---
keyword: [NAT gateway, enhanced, network address translation, Internet-facing services, Internet access]
---

# Immediately upgrade a standard NAT gateway to an enhanced NAT gateway

Enhanced NAT gateways are an upgrade from standard NAT gateways and use a more advanced architecture. Compared with standard NAT gateways, enhanced NAT gateways provide higher elasticity and stability. This helps you manage data transfer in a more efficient manner. You can immediately upgrade standard NAT gateways to enhanced NAT gateways in the Virtual Private Cloud \(VPC\) console. The upgrade is free of charge. The time period for free upgrades is extended from December 31, 2020 to September 30, 2021.

## Upgrade

Before you upgrade a standard NAT gateway to an enhanced NAT gateway, take note of the instructions in the following figure.

![Instructions](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0082659951/p147943.png)

The method that you can use to upgrade a standard NAT gateway varies based on whether NAT service plans are associated with the standard NAT gateway.

|Whether NAT service plans are associated|How to upgrade|
|----------------------------------------|--------------|
|No NAT service plan is associated|-   Immediate upgrade: Select the standard NAT gateway that you want to upgrade and click OK. The standard NAT gateway is immediately upgraded to an enhanced NAT gateway.
-   Scheduled upgrade: Set the related parameters for the standard NAT gateway that you want to upgrade and click OK. You can select more than one standard NAT gateway if you use this method. A scheduled upgrade task is generated, and the standard NAT gateway is upgraded in the background at the specified time. |
|One or more NAT service plans are associated|Scheduled upgrade: Set the related parameters for the standard NAT gateway that you want to upgrade and click OK. You can select more than one standard NAT gateway if you use this method. A scheduled upgrade task is generated, and the standard NAT gateway is upgraded in the background at the specified time. |

## Immediately upgrade a standard NAT gateway to an enhanced NAT gateway

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the standard NAT gateway is deployed.

3.  On the **NAT Gateway** page, click **Upgrade Now**.

    If this is not the first time you upgrade standard NAT gateways, click **Continue to Upgrade**.

    ![Upgrade Now](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6618369951/p146934.png)

4.  In the **Upgrade to Enhanced NAT Gateway** dialog box, select **I have read and understand the preceding information. I want to upgrade the instance to enhanced NAT gateway.** Then, set the following parameters and click **OK**.

    ![The Upgrade to Enhanced NAT Gateway dialog box](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7307773061/p148992.png)

    |Parameter|Description|
    |---------|-----------|
    |**NAT Gateway**|Select the standard NAT gateway that you want to upgrade.|
    |**Select a VSwitch for the enhanced NAT gateway**|Select a zone and a vSwitch for the enhanced NAT gateway. **Note:** You must specify a vSwitch for the enhanced NAT gateway. After you specify a vSwitch, the system automatically selects an IP address from the CIDR block of the vSwitch to transmit data. Make sure that the CIDR block of the vSwitch has sufficient idle IP addresses. |

5.  After you submit the application, click **Back**.

6.  You can check the progress of the upgrade on the **NAT Gateway** page. Find the NAT gateway and click **View Progress** in the **Status** column.

    It requires approximately 5 minutes to upgrade a standard NAT gateway to an enhanced NAT gateway. During the upgrade process, the NAT gateway may be disconnected for 1 to 2 seconds. The service resumes after your workloads are reconnected.

    ![Check the upgrade progress](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6618369951/p147358.png)


**Related topics**  


[Enhanced NAT gateways \(new\)](/intl.en-US/Enhanced NAT gateway/Enhanced NAT gateways (new).md)

[Comparison between enhanced NAT gateways and standard NAT gateways](/intl.en-US/Enhanced NAT gateway/Comparison between enhanced NAT gateways and standard NAT gateways.md)

[Upgrade a standard NAT gateway to an enhanced NAT gateway at a scheduled time](/intl.en-US/Enhanced NAT gateway/Upgrade a standard NAT gateway to an enhanced NAT gateway at a scheduled time.md)

