---
keyword: [NAT gateway, enhanced, network address translation, receive requests from the Internet, access the Internet]
---

# Upgrade a standard NAT gateway to an enhanced NAT gateway

Enhanced NAT gateways are upgraded from the technical architecture of standard NAT gateways. Compared with standard NAT gateways, enhanced NAT gateways offer higher elasticity and stability. This helps you manage data transfer in a more efficient way. Starting from October 1, 2020 until March 30, 2021, you can upgrade standard NAT gateways to enhanced NAT gateways free of charge in the Virtual Private Cloud \(VPC\) console.

## Upgrade

Before you upgrade standard NAT gateways to enhanced NAT gateways, take note of the considerations in the following figure.

![Considerations](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0082659951/p147943.png)

## Upgrade standard NAT gateways to enhanced NAT gateways

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, click **Upgrade Now**.

    If you have upgraded standard NAT gateways before, click **Continue to Upgrade**.

    ![Upgrade Now](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6618369951/p146934.png)

4.  In the **Upgrade to Enhanced NAT Gateway** dialog box, select **I have read and understand the preceding information. I want to perform the upgrade operation**. Then, configure the NAT gateway to be upgraded based on the following information and click **OK**.

    ![Upgrade to Enhanced NAT Gateway](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7307773061/p148992.png)

    |Parameter|Description|
    |---------|-----------|
    |**NAT Gateway**|Select the standard NAT gateway that you want to upgrade.|
    |**Select a VSwitch for the enhanced NAT gateway**|Select a zone and a vSwitch for the enhanced NAT gateway.**Note:** You must specify a vSwitch for the enhanced NAT gateway. After a vSwitch is specified, the system automatically selects an IP address from the CIDR block of the vSwitch for data transmission. Make sure that the CIDR block of the vSwitch has sufficient idle IP addresses. |

5.  After the application is submitted, click **Back**.

6.  You can check the progress of the upgrade on the **NAT Gateway** page. Find the NAT gateway and click **View Progress** in the **Status** column.

    It takes about five minutes to upgrade a standard NAT gateway to an enhanced NAT gateway. During the upgrade process, the NAT gateway may be disconnected for 1 to 2 seconds. The service resumes after your workloads are reconnected.

    ![Check the upgrade state of the NAT gateway](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6618369951/p147358.png)


**Related topics**  


[Enhanced NAT gateways \(new\)](/intl.en-US/Types of NAT gateways/Enhanced NAT gateways (new).md)

[Comparison between enhanced NAT gateways and standard NAT gateways](/intl.en-US/Types of NAT gateways/Comparison between enhanced NAT gateways and standard NAT gateways.md)

