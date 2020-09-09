# Upgrade a standard NAT gateway to an enhanced NAT gateway

Enhanced NAT gateways support all features of standard NAT gateways. Compared with standard NAT gateways, enhanced NAT gateways use an upgraded technical architecture. Enhanced gateways provide higher elasticity and stability and enable you to better manage network traffic transmitted over the Internet. You can upgrade a standard NAT gateway to an enhanced NAT gateway.

From August 31, 2020 to September 30, 2020, you can upgrade standard NAT gateways to enhanced NAT gateways in the Virtual Private Cloud \(VPC\) console free of charge.

**Note:** Only selected users in the following regions can upgrade standard NAT gateways to enhanced NAT gateways: China \(Chengdu\), China \(Qingdao\), UK \(London\), Germany \(Frankfurt\), Malaysia \(Kuala Lumpur\), and India \(Mumbai\). If you need to upgrade your NAT gateways, [submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.11182172.nav-right.dticket.1e874882kUYyPy#/ticket/createIndex).

Before you upgrade a standard NAT gateway to an enhanced NAT gateway, read the considerations in the following figure.

![Considerations](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/0082659951/p147943.png)

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, click **Upgrade Now**.

    ![Upgrade Now](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/6618369951/p146934.png)

4.  In the **Upgrade to Enhanced NAT Gateway** dialog box, set the following parameters.

    ![The Upgrade to Enhanced NAT Gateway dialog box](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/6618369951/p148992.png)

    |Parameter|Description|
    |---------|-----------|
    |**NAT Gateway**|Select the standard NAT gateway that you want to upgrade to an enhanced NAT gateway.|
    |**Select a VSwitch for the enhanced NAT gateway**|Select a zone and a VSwitch to be used by the enhanced NAT gateway.**Note:** You must specify a VSwitch for the enhanced NAT gateway. After a VSwitch is specified, the system automatically selects an IP address from the CIDR block of the VSwitch for data transmission. Make sure that the CIDR block of the VSwitch has sufficient IP addresses. |

5.  Click **OK**.

6.  After the application is submitted, click **Back**.

7.  You can check the progress of the application on the **NAT Gateway** page. Find the NAT gateway and click **View Progress** in the **Status** column.

    It may take up to five minutes to upgrade a standard NAT gateway to an enhanced NAT gateway. During this process, transient disconnection errors may occur one or two times. The service resumes after your workloads are reconnected.

    ![Check the status of the application](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/6618369951/p147358.png)


