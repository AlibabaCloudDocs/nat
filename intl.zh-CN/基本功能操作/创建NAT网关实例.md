# 创建NAT网关实例

本文介绍如何创建增强型NAT网关实例，为NAT网关添加EIP和标签，以及当不再需要NAT网关资源时，如何解绑EIP和删除NAT网关。

## 前提条件

您已经创建了专有网络VPC和交换机。具体操作，请参见[使用专有网络](/intl.zh-CN/专有网络和交换机/使用专有网络.md)。

## 创建NAT网关

1.  登录[NAT网关管理控制台](https://vpc.console.aliyun.com/nat)。

2.  在**NAT网关**页面，单击**创建NAT网关**。

3.  首次使用NAT网关时，在**创建NAT网关**页面最下方的关联角色创建须知区域，单击**创建**，创建服务关联角色。角色创建成功后即可创建NAT网关。

    ![创建角色](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9503170161/p225001.png)

4.  在**创建NAT网关**面板，配置以下购买信息，然后单击**立即购买**。

    -   **地域和可用区**：选择需要创建NAT网关的地域。
    -   **可用区**：选择NAT网关实例所属的可用区。
    -   **VPC ID**：选择NAT网关所属的VPC。创建NAT网关后，不能修改NAT网关所属的VPC。

        **说明：** 如果在VPC列表中，找不到目标VPC，请排查是否有以下情况：

        -   所选择地域内没有VPC。
        -   查看该VPC中是否存在目标网段为0.0.0.0/0的自定义路由。如果存在，请删除该路由条目。
        -   RAM账号不具备读取访问VPC的权限，请联系主账号进行授权。
    -   **交换机ID**：选择NAT网关实例所属的交换机。
    -   **网关类型**：默认选择为**增强型**。

        增强型NAT网关在普通型NAT网关的技术架构上作了升级，具有更优的弹性和更强的稳定性，帮助您更好地管理公网访问流量。

    -   **计费类型**：选择NAT网关实例的计费类型。

        目前，仅支持**按使用量计费**。

    -   **计费周期**：显示NAT网关实例的计费周期。
5.  在支付订单页面确认支付金额，然后单击**支付**完成购买。

    当出现**恭喜，支付成功！**的提示后，说明您购买成功。


## 绑定EIP

NAT网关需要绑定公网IP才能正常工作。一个NAT网关最多可绑定20个EIP，其中最多可绑定10个按流量计费的EIP，且每个按流量计费的EIP的最大带宽峰值不能超过200 Mbps。您可以通过配额管理申请更多配额。更多信息，请参见[管理配额](/intl.zh-CN/通用配置/管理配额.md)。



-   您已经创建了NAT网关和EIP。具体操作，请参见[购买NAT网关](/intl.zh-CN/购买指南/购买NAT网关.md)和[申请新EIP](/intl.zh-CN/用户指南/申请EIP/申请新EIP.md)。
-   您的账号在2018年01月26日23:59分之前没有NAT带宽包。

    2018年01月26日23:59分前，如果您的账号存在NAT带宽包，则仍需使用NAT带宽包为NAT网关提供公网IP。如需使用EIP绑定NAT网关，具体操作，请参见[为什么NAT网关控制台不能绑定EIP？]()。


1.  登录[NAT网关管理控制台](https://vpc.console.aliyun.com/nat)。

2.  在顶部菜单栏处，选择NAT网关的地域。

3.  在**NAT网关**页面，找到目标NAT网关实例，单击**弹性公网IP**列下的**立即绑定**。

4.  在绑定弹性公网IP对话框，配置以下参数，然后单击**确定**。

    |配置|说明|
    |--|--|
    |**所在资源组**|选择EIP所在的资源组。|
    |**选择弹性公网IP**|选择要绑定到NAT网关的EIP。    -   **从已有弹性公网IP中选择**：在下拉列表中选择已有的EIP实例。
    -   **新购弹性公网IP并绑定**：系统为您创建1个按使用流量计费的按量付费EIP，并绑定到NAT网关。 |

    绑定成功后，在NAT网关实例的**弹性公网IP**列将会显示出绑定的公网IP。


## 解绑EIP

如果您的NAT网关不需要与公网通信，您可以将NAT网关与EIP解绑。

确保要解绑的EIP没有被任何SNAT或DNAT条目占用。如有占用，请先删除SNAT条目和DNAT条目。具体操作，请参见[移除SNAT条目](/intl.zh-CN/基本功能操作/创建SNAT实现访问公网服务.md)和[删除DNAT条目](/intl.zh-CN/基本功能操作/创建DNAT提供公网服务.md)。

1.  登录[NAT网关管理控制台](https://vpc.console.aliyun.com/nat)。

2.  在顶部菜单栏处，选择NAT网关的地域。

3.  在**NAT网关**页面，找到目标NAT网关，单击**弹性公网IP**列下的公网IP。

4.  在**绑定的弹性公网IP**页签，选中要解绑的EIP，然后单击**操作**列的**解除绑定**。

5.  在弹出的对话框中单击**确定**。


## 编辑NAT网关

您可以修改NAT网关的名称和描述。

1.  登录[NAT网关管理控制台](https://vpc.console.aliyun.com/nat)。

2.  在顶部状态栏处，选择NAT网关的地域。

3.  在**NAT网关**页面，找到目标NAT网关，单击**操作**列下的**管理**。

4.  在**基本信息**页签，单击**实例名称**右侧的**编辑**，在弹出的对话框中输入NAT网关的名称，然后单击**确定**。

    名称长度为2~128个字符，以英文字母或中文开头，可包含数字、下划线（\_）和短划线（-）。

5.  单击描述右侧的**编辑**，在弹出的对话框中输入描述信息，然后单击**确定**。

    描述长度为2~256个字符，不能以`http://`和`https://`开头。


## 删除NAT网关

您可以删除按量付费模式的NAT网关，包年包月模式的NAT网关不支持删除操作。

**说明：** 您在NAT网关实例的**基本信息**页面开启了**删除保护**后，该NAT实例将不能被删除。请关闭了**删除保护**后再尝试删除。

-   NAT网关没有绑定EIP，如有绑定请解绑。
-   DNAT列表中没有DNAT条目，如有请删除。具体操作，请参见[删除DNAT条目](/intl.zh-CN/基本功能操作/创建DNAT提供公网服务.md)。
-   SNAT列表中没有SNAT条目，如有请删除。具体操作，请参见[移除SNAT条目](/intl.zh-CN/基本功能操作/创建SNAT实现访问公网服务.md)。

1.  登录[NAT网关管理控制台](https://vpc.console.aliyun.com/nat)。

2.  在顶部状态栏处，选择NAT网关的地域。

3.  在**NAT网关**页面，找到目标NAT网关，单击**操作**列下的**![更多操作](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2570920261/p103337.png)** \> **删除**。

4.  在**删除网关**对话框，选中**强制删除（删除NAT网关及其包含资源）**，然后单击**确认**。


## 相关文档

-   创建NAT网关实例：[CreateNatGateway](/intl.zh-CN/API参考/NAT网关/CreateNatGateway.md)。
-   绑定EIP：[AssociateEipAddress](/intl.zh-CN/API参考/弹性公网IP/AssociateEipAddress.md)。
-   解绑EIP：[UnassociateEipAddress](/intl.zh-CN/API参考/弹性公网IP/UnassociateEipAddress.md)。
-   为NAT网关添加标签：[TagResources](/intl.zh-CN/API参考/标签/TagResources.md)。
-   编辑NAT网关的基本信息：[ModifyNatGatewayAttribute](/intl.zh-CN/API参考/NAT网关/ModifyNatGatewayAttribute.md)。
-   删除NAT网关：[DeleteNatGateway](/intl.zh-CN/API参考/NAT网关/DeleteNatGateway.md)

