# 购买NAT网关

本文以创建增强型NAT网关为例，说明购买NAT网关的操作步骤。

## 前提条件

您已经创建了专有网络VPC和交换机。具体操作，请参见[创建专有网络](/intl.zh-CN/专有网络和交换机/管理专有网络/创建专有网络.md)。

## 云资源访问授权

如果您是第一次创建增强型NAT网关，请先使用阿里云账号完成RAM角色的授权。

1.  登录[NAT网关管理控制台](https://vpc.console.aliyun.com/nat)。

2.  打开[云资源访问授权](https://ram.console.aliyun.com/role/authorization?request=%7B%22Services%22%3A%5B%7B%22Service%22%3A%22NAT%22%2C%22Roles%22%3A%5B%7B%22RoleName%22%3A%22AliyunNATAccessingNetworkInterfaceRole%22%2C%22TemplateId%22%3A%22ENIRole%22%7D%5D%7D%5D%2C%22ReturnUrl%22%3A%22https%3A%2F%2Fvpc.console.aliyun.com%2Fnat%22%7D)页面。

3.  在**云资源访问授权**页面单击**同意授权**。

    ![NAT增强型实例访问授权](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7237607061/p188048.png)


## 创建NAT网关

1.  登录[NAT网关管理控制台](https://vpc.console.aliyun.com/nat)。

2.  在**NAT网关**页面，单击**创建NAT网关**。

3.  在**创建NAT网关**页面，配置以下购买信息，然后单击**立即购买**。

    -   **地域和可用区**：选择需要创建NAT网关的地域。
    -   **可用区**：选择NAT网关实例所属的可用区。
    -   **VPC ID**：选择NAT网关所属的VPC。创建NAT网关后，不能修改NAT网关所属的VPC。

        **说明：** 如果在VPC列表中，找不到目标VPC，请排查是否有以下情况：

        -   所选择地域内没有VPC。
        -   查看该VPC中是否存在目标网段为0.0.0.0/0的自定义路由。如果存在，请删除该路由条目。
        -   RAM账号不具备读取访问VPC的权限，请联系主账号进行授权。
    -   **交换机ID**：选择NAT网关实例所属的交换机。
    -   **网关类型**：默认选择为**增强型**。

        增强型NAT网关在普通型NAT网关的技术架构上作了升级，具有更优的弹性和更强的稳定性，帮助您更好的管理公网访问流量。

    -   **计费类型**
        -   **按使用量计费**：按NAT网关实际使用量收费，更多信息，请参见[t16029.md\#section\_v5g\_sue\_5bj](/intl.zh-CN/购买指南/按量付费.md)。
        -   **按固定规格计费**：每个计费周期的费用固定，不会因NAT网关的使用量发生变化。选择该计费类型后，需要选择**规格**。更多信息，请参见[按固定规格计费](/intl.zh-CN/购买指南/按量付费.md)。
    -   **计费类型**：选择NAT网关实例的计费类型。

        目前，仅支持按固定规格计费。

    -   **计费周期**：显示NAT网关实例的计费周期。
4.  在支付订单页面确认支付金额，然后单击**支付**完成购买。

    当出现**恭喜，支付成功！**的提示后，说明您购买成功。


## 结果验证

创建成功后，您可以在**NAT网关**页面查看已创建的NAT网关实例。

**相关文档**  


[CreateNatGateway](/intl.zh-CN/API参考/NAT网关/CreateNatGateway.md)

