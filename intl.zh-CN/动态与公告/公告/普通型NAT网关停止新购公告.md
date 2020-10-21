# 普通型NAT网关停止新购公告

阿里云将停止新购普通型NAT网关。

## 停止新购时间

2020年11月20日起，阿里云将在所有地域停止新购普通型NAT网关。给您带来不便，敬请谅解。

## 停止新购影响

停止新购普通型NAT网关后，您可以使用增强型NAT网关实现公网访问能力。通过以下方式使用增强型NAT网关：

-   [创建增强型NAT网关](#section_0ix_ti4_tkw)
-   [将普通型NAT网关升级至增强型NAT网关](#section_tzu_ypj_t15)

## 创建增强型NAT网关

增强型NAT网关在普通型NAT网关的技术架构上作了升级，具有高性能、自动弹性、灵活计费、精细化运维等特性。详细信息，请参见[增强型NAT网关发布公告](/intl.zh-CN/动态与公告/公告/增强型NAT网关发布公告.md)。

您可以通过控制台和API创建增强型NAT网关。

-   在控制台创建增强型NAT网关时，您需要为增强型NAT网关指定所属的交换机。详细信息，请参见[创建NAT网关](/intl.zh-CN/NAT网关实例/创建NAT网关.md)。
-   使用API创建增强型NAT网关时，您需要指定**NatType**为**Enhanced**，并为增强型NAT网关指定所属的**VSwitchId**。详细信息，请参见[CreateNatGateway](/intl.zh-CN/API参考/NAT网关/CreateNatGateway.md)。

## 将普通型NAT网关升级至增强型NAT网关

您可以继续使用存量普通型NAT网关，但建议您将普通型NAT网关升级至增强型NAT网关，以帮助您更好的管理公网访问流量。详细信息，请参见[普通型NAT网关升级至增强型NAT网关](/intl.zh-CN/NAT网关实例/普通型NAT网关切换至增强型NAT网关.md)。

