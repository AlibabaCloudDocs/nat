# 创建DNAT实现目的私网IP地址转换

VPC NAT网关支持DNAT功能，将VPC NAT网关上的NAT IP地址映射给VPC内的ECS实例使用，使ECS实例能够对外部私网提供服务。DNAT功能支持端口映射和IP映射两种方式。

## 前提条件

您已经创建了VPC NAT网关。具体操作，请参见[创建VPC NAT网关实例](/intl.zh-CN/VPC NAT网关基本功能操作/创建VPC NAT网关实例.md)。

## 创建DNAT条目

1.  登录[NAT网关管理控制台](https://vpc.console.aliyun.com/nat)。

2.  在**创建DNAT条目**页面，配置以下参数，然后单击**确定创建**。

    |配置|说明|
    |:-|:-|
    |**选择NAT IP地址**|选择供外部网络访问的NAT IP地址。 **说明：** VPC NAT网关支持将一个NAT IP地址同时用于DNAT条目（端口映射方式）和SNAT条目。 |
    |**选择私网IP地址**|选择要通过DNAT规则进行通信的私网IP地址。您可以通过以下两种方式指定私网IP地址：     -   **通过ECS或弹性网卡进行选择**：从ECS实例或弹性网卡列表中选择。
    -   **通过手动输入**：输入目标私网IP地址。 |
    |**端口设置**|选择DNAT映射的方式：     -   **任意端口**：该方式属于IP映射，任何访问该NAT IP地址的请求都将转发到目标ECS实例上，目标ECS实例也可以使用该NAT IP地址主动访问外部网络。

**说明：**

        -   DNAT条目中配置了IP映射方式的NAT IP地址不能再被其他DNAT条目或SNAT条目使用。
        -   如果NAT网关既配置了DNAT IP映射方式，又配置了SNAT条目，则ECS实例会优先通过DNAT IP映射方式的NAT IP地址访问外部网络。
    -   **具体端口**：该方式属于端口映射，VPC NAT网关会将以指定协议和端口访问该NAT IP地址的请求转发到目标ECS实例的指定端口上。

选择具体端口后，请根据业务需求设置以下参数：

        -   **前端端口**：NAT IP地址被外部网络访问的端口。
        -   **后端端口**：映射的目标ECS实例端口。
        -   **协议类型**：转发端口的协议类型。 |
    |**条目名称**|输入DNAT条目的名称。 名称长度为2~128个字符，以大小写字母或中文开头， 可包含数字、下划线（\_）和短划线（-）。 |


## 编辑DNAT条目

创建DNAT条目后，您可以修改DNAT条目的NAT IP地址、私网IP地址、端口或名称。

1.  登录[NAT网关管理控制台](https://vpc.console.aliyun.com/nat)。

2.  在**DNAT条目列表**区域，找到目标DNAT条目，然后在**操作**列单击**编辑**。

3.  在**编辑DNAT条目**页面，修改DNAT条目的NAT IP地址、私网IP地址、端口或名称，然后单击**确定修改**。


## 删除DNAT条目

如果您不需要VPC内的ECS实例被外部私网访问，您可以删除DNAT条目。

1.  登录[NAT网关管理控制台](https://vpc.console.aliyun.com/nat)。

2.  在**DNAT条目列表**区域，找到目标DNAT条目，然后在**操作**列单击**删除**。

3.  在**删除DNAT条目**对话框，单击**确定**。


**相关文档**  


[CreateForwardEntry](/intl.zh-CN/API参考/NAT网关/CreateForwardEntry.md)

[ModifyForwardEntry](/intl.zh-CN/API参考/NAT网关/ModifyForwardEntry.md)

[DeleteForwardEntry](/intl.zh-CN/API参考/NAT网关/DeleteForwardEntry.md)

