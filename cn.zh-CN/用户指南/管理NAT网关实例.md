# 管理NAT网关实例 {#concept_ehq_cbz_ydb .concept}

NAT网关实例是一个运行的NAT网关服务。在使用SNAT和DNAT功能前，您必须先创建一个NAT网关实例。

## 创建NAT网关 {#section_iml_hbz_ydb .section}

1.  登录[VPC管理控制台](https://vpcnext.console.aliyun.com/nat/)。
2.  在左侧导航栏，单击**NAT网关**。
3.  单击**创建NAT网关**。
4.  根据以下信息，配置NAT网关。

    |配置|说明|
    |:-|:-|
    |**地域**|选择需要配置NAT网关的VPC所在的地域。|
    |**VPC ID**| 选择需要配置NAT网关的VPC。创建NAT网关后，将不能修改VPC。

 若在VPC列表中，找不到目标VPC，可从以下方面进行排查：

     -   查看该VPC是否已经配置NAT网关。一个VPC只能配置一个NAT网关。

    -   查看该VPC中是否存在目标网段为0.0.0.0/0的自定义路由。若存在，需要删除该路由条目。

 |
    |**规格**| 选择NAT网关的规格。NAT网关的规格会影响SNAT功能的最大连接数和每秒新建连接数，但不会影响数据吞吐量。

 **说明：** NAT网关的规格对DNAT功能的连接数和吞吐量没有限制。详情参考[NAT网关规格](cn.zh-CN/用户指南/NAT网关规格.md#)。

 |
    |**计费周期**|显示NAT网关的计费周期。|

5.  单击立即购买，并完成支付。NAT网关的创建过程一般需要1-5分钟。




## 更改NAT网关规格 {#section_jml_hbz_ydb .section}

您可以根据业务需要，修改NAT网关的规格。NAT网关的规格仅对SNAT的性能有影响，对DNAT性能没有影响。

1.  登录[VPC管理控制台](https://vpcnext.console.aliyun.com/nat/)。
2.  在左侧导航栏，单击**NAT网关**。
3.  选择NAT网关的地域。
4.  单击目标NAT网关的实例ID。
5.  在NAT网关的详细页面，单击**修改规格**。
6.  在**配置变更**区域，选择新的NAT网关规格，然后单击**去开通**完成变更。

## 编辑NAT网关 {#section_mml_hbz_ydb .section}

您可以编辑NAT网关的名称和描述信息，以便于后期维护。

1.  登录[VPC管理控制台](https://vpcnext.console.aliyun.com/nat/)。
2.  在左侧导航栏，单击**NAT网关**。
3.  选择NAT网关的地域。
4.  单击目标NAT网关的实例ID。
5.  在NAT网关的详细页面，分别单击名称和描述右侧的**编辑**，在弹出的对话框中分别输入NAT网关的名称和描述信息，然后单击**确定**完成修改。

## 删除NAT网关 {#section_rf4_2cz_ydb .section}

1.  登录[VPC管理控制台](https://vpcnext.console.aliyun.com/nat/)。
2.  在左侧导航栏，单击**NAT网关**。
3.  选择NAT网关的地域。
4.  找到目标NAT网关，确保NAT网关中已经没有SNAT、DNAT条目和绑定的EIP后，单击**删除**。在弹出的对话框中，单击**确定**。

    **说明：** 您也可以在弹出的对话框中选择**强制删除**，在删除NAT网关后自动删除NAT网关中的DNAT、SNAT条目，并解绑已绑定的EIP。


