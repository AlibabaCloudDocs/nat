# NAT网关带宽包转换为共享带宽

您可以将留存的NAT网关带宽包转换为共享带宽。共享带宽提供地域级带宽共享和复用功能。您可以将同地域下的所有弹性公网IP EIP（Elastic IP Address）都添加到一个共享带宽实例中，复用共享带宽实例的带宽，节省公网带宽使用成本。

## 转换说明

将NAT带宽包转换为共享带宽过程中流量不会中断，不影响线上业务的运行。转换后：

-   NAT网关带宽包中的公网IP会转换为EIP。
-   NAT网关带宽包转换成共享带宽，更便于管理，节约成本。
-   转换失败对您的使用不会有影响，您可以继续使用网络产品。如果自行排查没有发现问题，可以[提交工单](https://selfservice.console.aliyun.com/ticket/category/natgw/today)反馈。提交工单时，需要提供以下信息：
    -   账号ID（UID）
    -   调用ConvertBandwidthPackage接口的Request ID
    -   转换的NAT网关带宽包实例ID
    -   转换失败的截图

## 准备工作

在开始转换前，请确保已完成以下准备工作：

-   确保要进行转换的账号有操作权限。

    推荐使用阿里云账号进行转换。如果使用RAM用户转换，在转换前阿里云账号需要在[访问控制台](https://ram.console.aliyun.com/users)为RAM用户添加以下权限：

    -   AliyunNATGatewayFullAccess
    -   AliyunEIPFullAccess
    -   AliyunCommonBandwidthPackageFullAccess

        ![授权](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5951400951/p96384.png)

-   确保您的账号下有足够的可用EIP。

    转换后，NAT网关带宽包中的公网IP会转换为EIP。确保EIP的数量不少于NAT网关带宽包中的公网IP数量。您可以在专有网络控制台的[配额管理](https://vpc.console.aliyun.com/quota)页面查看EIP数量。如果EIP数量不足，请在控制台进行申请。

    ![配额管理](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3649098161/p96382.png)

-   开通按流量计费NAT网关带宽包白名单

    如果待转换的NAT网关带宽包是按流量计费的，请[提交工单](https://selfservice.console.aliyun.com/ticket/category/natgw/today)申请转换。

-   备份实例信息

    在转换开始前，请根据以下表格存储一份NAT网关实例信息，方便跟踪和结果确认。

    |NAT网关带宽包实例ID|地域|带宽值|IP数量|转换状态|转换的共享带宽实例ID|
    |------------|--|---|----|----|-----------|
    |bwp-xxx1|杭州|200 Mbps|20|成功|cbwp-xxx1|
    |bwp-xxx2|上海|500 Mbps|50|待执行|无|


## 操作步骤

在完成所有准备工作后，请参考以下操作，转换NAT网关带宽包：

1.  调用ConvertBandwidthPackage接口完成转换。具体操作，请参见[ConvertBandwidthPackage](/cn.zh-CN/API参考/NAT网关/ConvertBandwidthPackage.md)。

2.  确认转换结果。

    您可以通过查看共享带宽实例ID判断是否转换成功。实例ID的转换规则为`${cbwpId}='c'+${bwpId}`。例如，转换的NAT网关带宽包实例ID是`${bwpId}=bwp-e8caejcj`，则转换后的共享带宽实例ID为`cbwp-e8caejcj`。

3.  完成所有NAT网关带宽包转换后，在NAT网关的配额申请页面，申请**natgw\_privilege\_allow\_bind\_eip**权限。

    该权限是自动审批，一分钟后刷新页面查看申请状态。

    **说明：** **natgw\_privilege\_allow\_bind\_eip**权限申请成功后，如果您要将其他EIP绑定到NAT网关，请先退出账号，重新登录NAT网关控制台，再将EIP绑定到NAT网关上。具体操作，请参见[绑定弹性公网IP](/cn.zh-CN/基本功能操作/创建NAT网关实例.md)。

    ![绑定eip权限](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3649098161/p96400.png)


