---
keyword: [NAT网关, 常见问题, DNAT, 提供公网服务]
---

# DNAT功能FAQ

本文介绍目的网络地址转换DNAT（Destination Network Address Translation）功能相关的常见问题。

-   [一个NAT网关支持创建多少条DNAT条目？](#section_wk1_9rh_68u)
-   [创建DNAT条目时，为什么在公网IP地址列表中找不到已创建的EIP？](#section_pq2_99h_dt6)
-   [如果ECS实例绑定了EIP，是否支持为该ECS实例创建DNAT条目？](#section_ade_vnf_0a0)

## 一个NAT网关支持创建多少条DNAT条目？

一个NAT网关默认支持创建100条DNAT条目。

您可以通过以下任一方式自助提升配额：

-   前往[配额管理页面](https://vpc.console.aliyun.com/quota)提升配额，具体操作，请参见[管理配额](/cn.zh-CN/通用配置/管理配额.md)。
-   前往[配额中心](https://quotas.console.aliyun.com)提升配额。具体操作，请参见[创建配额提升申请]()。

## 创建DNAT条目时，为什么在公网IP地址列表中找不到已创建的EIP？

创建DNAT条目前，请确保您已经创建了NAT网关并绑定了弹性公网IP（EIP）。具体操作，请参见[创建DNAT提供公网服务](/cn.zh-CN/基本功能操作/创建DNAT提供公网服务.md)。

## 如果ECS实例绑定了EIP，是否支持为该ECS实例创建DNAT条目？

不支持。

如需为该ECS实例创建DNAT条目，请先将ECS实例与EIP解绑，然后再为该ECS实例创建DNAT条目。具体操作，请参见[解绑EIP](/cn.zh-CN/用户指南/解绑EIP.md)和[创建DNAT提供公网服务](/cn.zh-CN/基本功能操作/创建DNAT提供公网服务.md)。

**说明：** 如果存量ECS实例绑定了EIP，且处于NAT网关的DNAT条目中，则ECS实例优先通过绑定的EIP进行公网通信。

