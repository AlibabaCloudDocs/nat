---
keyword: [NAT网关, 常见问题, 计费]
---

# 计费FAQ

本文介绍NAT网关计费相关的常见问题。

-   [NAT网关服务如何计费？](#section_9x9_l8o_gxj)
-   [按量付费NAT网关支持哪些计费方式？](#section_3tw_bpc_d0o)
-   [EIP与NAT网关实例解绑后，为什么EIP和NAT网关仍在计费？](#section_k9h_r41_iol)

## NAT网关服务如何计费？

NAT网关不具备访问公网的能力，需要组合弹性公网IP（Elastic IP Address，简称EIP）才能正常使用。因此，您在使用NAT网关服务时，不仅要考虑NAT网关实例的计费，还要考虑EIP的计费。更多信息，请参见[计费概述](/intl.zh-CN/产品定价/计费概述.md)。

## 按量付费NAT网关支持哪些计费方式？

按量付费NAT网关支持按固定规格计费，每个计费周期的费用固定，费用不会因NAT网关的处理量发生变化。更多信息，请参见[按固定规格计费](/intl.zh-CN/产品定价/按量付费.md)。

## EIP与NAT网关实例解绑后，为什么EIP和NAT网关仍在计费？

EIP与NAT网关实例解绑仅是取消EIP与NAT网关的关联，并没有删除EIP和NAT网关，所以EIP和NAT网关仍在计费。如需停止计费，请删除EIP和NAT网关。具体操作，请参见[删除EIP](/intl.zh-CN/用户指南/管理按量计费实例/释放EIP.md)和[删除NAT网关](/intl.zh-CN/用户指南/NAT网关实例/管理按量付费NAT网关实例/删除NAT网关.md)。

**说明：** 仅按量付费EIP和按量付费NAT网关支持删除操作，包年包月EIP和包年包月NAT网关到期后自动停止服务。

