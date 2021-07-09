---
keyword: [VPC NAT网关, 私网, 网络地址转换, SNAT]
---

# 创建SNAT实现源私网IP地址转换

您可以使用VPC NAT网关的SNAT功能，使VPC中的ECS实例可以通过NAT IP访问外部网络。

## 前提条件

创建SNAT条目前，请确保满足以下条件：

-   您已经创建了VPC NAT网关。具体操作，请参见[创建VPC NAT网关实例](/cn.zh-CN/VPC NAT网关基本功能操作/创建VPC NAT网关实例.md)。
-   如果要创建以交换机为粒度的SNAT条目，请确保VPC NAT网关所关联的VPC中已经创建了交换机。具体操作，请参见[使用交换机](/cn.zh-CN/专有网络和交换机/使用交换机.md)。
-   如果要创建以ECS为粒度的SNAT条目，请确保VPC NAT网关所关联的VPC中已经创建了ECS实例。具体操作，请参见[使用向导创建实例](/cn.zh-CN/实例/创建实例/使用向导创建实例.md)。

## 创建SNAT条目

1.  登录[NAT网关管理控制台](https://vpc.console.aliyun.com/nat)。

2.  在**创建SNAT条目**页面，配置以下参数信息，然后单击**确定创建**。

    |参数|说明|
    |:-|:-|
    |**SNAT条目粒度**|选择SNAT条目的粒度。    -   **VPC粒度**：VPC NAT网关所属VPC下的所有地址段可以通过配置的SNAT规则访问外部网络。
    -   **交换机粒度**：指定交换机下的ECS实例通过配置的SNAT规则访问外部网络。
        -   **选择交换机**：在下拉列表中选择交换机。

**说明：**

            -   如果下拉列表中没有可选的交换机，可在下拉列表单击**创建交换机**跳转到VPC控制台创建交换机。
            -   如您选择多个交换机，将会为您创建多条SNAT条目，使用相同的NAT IP地址。
        -   **交换机网段**：显示所选交换机的网段。
    -   **ECS粒度**：指定的ECS实例通过配置的SNAT规则访问外部网络。
        -   **选择ECS**：在下拉列表中选择ECS。该ECS实例将通过配置的SNAT规则访问外部网络。请确保ECS实例处于正常运行中。

**说明：**

            -   如果下拉列表中没有可选的ECS，可在下拉列表单击**创建ECS**跳转到ECS控制台进行创建。
            -   如您选择多个ECS，将会为您创建多条SNAT条目，使用相同的NAT IP地址。
        -   **ECS网段**：显示所选ECS实例的网段。
    -   **自定义网段粒度**：您可以配置任意网段。任意网段内的ECS实例都可以通过配置的SNAT规则访问外部网络。 |
    |**选择NAT IP地址**|在下拉列表中选择用来访问外部网络的NAT IP地址。**说明：** 您也可以在下拉列表单击**新建NAT IP**，在**添加NAT IP**对话框中完成操作。 |
    |**NAT IP 地址**|当**SNAT条目粒度**选择**自定义网段粒度**时，需要自定义NAT IP地址。|
    |**条目名称**|SNAT条目的名称。 名称长度为2~128个字符，以大小写字母或中文开头， 可包含数字、下划线（\_）和短划线（-）。 |


## 编辑SNAT条目

创建SNAT条目后，您可以修改SNAT条目的NAT IP地址和名称，但您不能修改SNAT条目的VPC、交换机和ECS实例。

1.  登录[NAT网关管理控制台](https://vpc.console.aliyun.com/nat)。

2.  在**SNAT条目列表**区域，找到目标SNAT条目，然后在**操作**列单击**编辑**。

3.  在**编辑SNAT条目**页面，修改SNAT条目的NAT IP地址或名称，然后单击**确定修改**。


## 删除SNAT条目

如果您VPC内的ECS实例不需要通过源私网IP地址转换访问外部网络，您可以删除SNAT条目。

1.  登录[NAT网关管理控制台](https://vpc.console.aliyun.com/nat)。

2.  在**SNAT条目列表**区域，找到目标SNAT条目，然后在**操作**列单击**删除**。

3.  在**删除SNAT条目**对话框，单击**确定**。


**相关文档**  


[CreateSnatEntry](/cn.zh-CN/API参考/NAT网关/CreateSnatEntry.md)

[ModifySnatEntry](/cn.zh-CN/API参考/NAT网关/ModifySnatEntry.md)

[DeleteSnatEntry](/cn.zh-CN/API参考/NAT网关/DeleteSnatEntry.md)

