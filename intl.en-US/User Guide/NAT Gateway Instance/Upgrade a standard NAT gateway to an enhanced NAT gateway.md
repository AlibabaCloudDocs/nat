# Upgrade a standard NAT gateway to an enhanced NAT gateway

Enhanced NAT gateways are upgraded from the technical architecture of standard NAT gateways. Compared with standard NAT gateways, enhanced NAT gateways offer higher elasticity and stability. This helps you manage data transfer in a more efficient way. We recommend that you upgrade standard NAT gateways to enhanced NAT gateways.

Starting from October 1, 2020 until December 31, 2020, you can upgrade standard NAT gateways to enhanced NAT gateways free of charge in the Virtual Private Cloud \(VPC\) console.

**Note:** Only selected users in the following regions can not upgrade standard NAT gateways to enhanced NAT gateways: China \(Beijing\), China \(Hangzhou\), China \(Shanghai\) and China \(Shenzhen\).

Before you upgrade standard NAT gateways to enhanced NAT gateways, pay attention to the upgrade instructions in the following figure.

![Upgrade instructions](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0082659951/p147943.png)

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, click **Upgrade Now**.

    If you have upgraded standard NAT gateways before, click **Continue to Upgrade**.

    ![Upgrade Now](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6618369951/p146934.png)

4.  In the **Upgrade to Enhanced NAT Gateway** dialog box, set the following parameters.

    ![Upgrade to Enhanced NAT Gateway](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7307773061/p148992.png)

    |Parameter|Description|
    |---------|-----------|
    |**NAT Gateway**|Select the standard NAT gateway that you want to upgrade.|
    |**Select a VSwitch for the enhanced NAT gateway**|Select a zone and a VSwitch for the enhanced NAT gateway.**Note:** You must specify a VSwitch for the enhanced NAT gateway. After a VSwitch is specified, the system automatically selects an IP address from the CIDR block of the VSwitch for data transmission. Make sure that the CIDR block of the VSwitch has sufficient unused IP addresses. |

5.  Click **OK**.

6.  After the request is submitted, click **Back**.

7.  You can check the progress of the upgrade on the **NAT Gateway** page. Find the NAT gateway and click **View Progress** in the **Status** column.

    It takes about five minutes to upgrade a standard NAT gateway to an enhanced NAT gateway. During the upgrade process, the NAT gateway may be disconnected for 1 to 2 seconds. The service resumes after your workloads are reconnected.

    ![Check the upgrade state of the NAT gateway](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6618369951/p147358.png)


