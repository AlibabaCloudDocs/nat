# 修改SNAT条目

创建SNAT条目后，您可以修改SNAT条目的公网IP和名称，但您不能修改SNAT条目的交换机和ECS实例。

1.  登录[NAT网关管理控制台](https://vpc.console.aliyun.com/nat)。

2.  在顶部菜单栏处，选择NAT网关的地域。

3.  在**NAT网关**页面，找到目标NAT网关实例，单击**操作**列下的**设置SNAT**。

4.  在**SNAT条目列表**区域，找到目标SNAT条目，单击**操作**列下的**编辑**。

5.  在**编辑SNAT条目**对话框，修改SNAT条目的公网IP和名称，然后单击**确定**。

    **说明：** 向存量SNAT条目添加或删除EIP会导致原有连接闪断，重连可以恢复，请谨慎操作。


**相关文档**  


[ModifySnatEntry](/intl.zh-CN/API参考/NAT网关/ModifySnatEntry.md)

