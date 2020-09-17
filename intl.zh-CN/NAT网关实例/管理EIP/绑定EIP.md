# 绑定EIP

NAT网关作为一个网关设备，需要绑定公网IP才能正常工作。创建NAT网关后，您可以为NAT网关绑定弹性公网IP（EIP）。

EIP绑定NAT网关前，请确保满足以下条件：

-   您的账号在2018年1月26日23:59分之前没有NAT带宽包。

    2018年1月26日23:59分前，如果您的账号存在NAT带宽包，则仍需使用NAT带宽包为NAT网关提供公网IP。如需使用EIP绑定NAT网关，请参见[为什么在NAT网关控制台不能绑定EIP](/intl.zh-CN/常见问题/EIP绑定NAT网关相关问题.md)中的操作步骤。

-   您已经创建了NAT网关和EIP。详细信息，请参见[创建NAT网关](/intl.zh-CN/NAT网关实例/创建NAT网关.md)和[申请新EIP](/intl.zh-CN/用户指南/申请EIP/申请新EIP.md)。

一个NAT网关最多可绑定20个EIP，其中最多可绑定10个按流量计费的EIP，且每个按流量计费的EIP的最大带宽峰值不能超过200Mbps。您可以通过配额管理申请更多配额。详细信息，请参见[管理配额](/intl.zh-CN/通用配置/管理配额.md)。

1.  登录[NAT网关管理控制台](https://vpc.console.aliyun.com/nat)。

2.  在顶部菜单栏处，选择NAT网关的地域。

3.  在**NAT网关**页面，找到目标NAT网关实例，单击**操作**列下的**![更多操作](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/2081359951/p103337.png)** \> **绑定弹性公网IP**。

4.  在绑定弹性公网IP对话框，完成以下操作，然后单击**确定**。

    |配置|说明|
    |--|--|
    |**从已有EIP列表选取**|
    |**可用EIP列表**|选择要绑定到NAT网关的EIP。|
    |**交换机**|选择要添加SNAT条目的交换机。 系统会自动添加SNAT条目使该交换机下的云资源可以主动访问互联网。您也可以不选择交换机，绑定EIP后手动添加SNAT条目。详细信息，请参见[创建SNAT条目](/intl.zh-CN/SNAT/创建SNAT条目.md)。

**说明：** 仅未绑定EIP的NAT网关显示该选项。 |
    |**新购EIP并绑定NAT网关**|
    |**购买EIP个数**|显示购买EIP的个数。默认为1个，不可修改。 系统为您创建1个按使用流量计费的按量付费EIP，并绑定到NAT网关。 |


**相关文档**  


[AssociateEipAddress](/intl.zh-CN/API参考/弹性公网IP/AssociateEipAddress.md)

