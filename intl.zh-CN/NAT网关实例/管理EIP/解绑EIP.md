# 解绑EIP

如果您的NAT网关不需要与公网通信，您可以将NAT网关与弹性公网IP（EIP）解绑。

请确保要解绑的EIP没有被任何SNAT或DNAT条目占用。如有占用，请先删除SNAT条目和DNAT条目。详细信息，请参见[删除SNAT条目](/intl.zh-CN/SNAT/删除SNAT条目.md)和[删除DNAT条目](/intl.zh-CN/DNAT/删除DNAT条目.md)。

1.  登录[NAT网关管理控制台](https://vpc.console.aliyun.com/nat)。

2.  在顶部菜单栏处，选择NAT网关的地域。

3.  在**NAT网关**页面，找到目标NAT网关，单击**操作**列下的**![更多操作](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/2081359951/p103337.png)** \> **解绑弹性公网IP**。

4.  在解绑弹性公网IP对话框，选择要解绑的EIP，然后单击**确定**。


**相关文档**  


[UnassociateEipAddress](/intl.zh-CN/API参考/弹性公网IP/UnassociateEipAddress.md)

