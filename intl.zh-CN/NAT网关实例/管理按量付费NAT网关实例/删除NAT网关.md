# 删除NAT网关

您可以删除按量付费模式的NAT网关，包年包月模式的NAT网关不支持删除操作。

删除NAT网关前，请确保满足以下条件：

-   NAT网关没有绑定EIP，如有绑定请解绑。详细信息，请参见[解绑EIP](/intl.zh-CN/NAT网关实例/管理EIP/解绑EIP.md)。
-   DNAT列表中没有DNAT条目，如有请删除。详细信息，请参见[删除DNAT条目](/intl.zh-CN/DNAT/删除DNAT条目.md)。
-   SNAT列表中没有SNAT条目，如有请删除。详细信息，请参见[删除SNAT条目](/intl.zh-CN/SNAT/删除SNAT条目.md)。

1.  登录[NAT网关管理控制台](https://vpc.console.aliyun.com/nat)。

2.  在顶部菜单栏处，选择NAT网关的地域。

3.  在**NAT网关**页面，找到目标NAT网关，单击**操作**列下的**![更多操作](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/2081359951/p103337.png)** \> **删除**。

4.  在弹出的对话框中，单击**确定**。

    **说明：** 您可以在弹出的对话框中选择**强制删除**，在删除NAT网关后自动删除NAT网关中的DNAT和SNAT条目，并解绑EIP。


**相关文档**  


[DeleteNatGateway](/intl.zh-CN/API参考/NAT网关/DeleteNatGateway.md)

