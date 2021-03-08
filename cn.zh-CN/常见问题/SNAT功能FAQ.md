---
keyword: [NAT网关, SNAT, 常见问题, 访问公网]
---

# SNAT功能FAQ

本文介绍源网络地址转换SNAT（Source Network Address Translation）功能相关的常见问题。

-   [一个NAT网关支持创建多少条SNAT条目？](#section_1ca_x5e_789)
-   [一个SNAT条目支持关联多少个EIP？](#section_h4h_468_si4)
-   [SNAT条目支持创建SNAT IP地址池吗？](#section_pq1_mx8_13k)
-   [如何统一ECS实例的公网出口IP？](#section_nr6_yu9_rjy)
-   [创建SNAT条目时，为什么在公网IP地址列表找不到已创建的EIP？](#section_khm_d8g_c21)
-   [ECS实例分配了固定公网IP且创建了SNAT条目，如何实现ECS实例优先通过SNAT条目的公网IP访问互联网？](#section_uap_mm1_v62)
-   [ECS实例绑定了EIP且创建了SNAT条目，如何实现ECS实例优先通过SNAT条目的公网IP访问互联网？](#section_0kw_7t6_1or)
-   [ECS实例设置了DNAT IP映射且创建了SNAT条目，如何实现ECS实例优先通过SNAT条目的公网IP访问互联网？](#section_t8x_nbi_kjc)

## 一个NAT网关支持创建多少条SNAT条目？

一个NAT网关默认支持创建40条SNAT条目。

您可以通过以下任意方式自助提升配额：

-   前往[配额管理页面](https://vpc.console.aliyun.com/quota)提升配额。具体操作，请参见[管理配额](/cn.zh-CN/通用配置/管理配额.md)。
-   前往[配额中心](https://quotas.console.aliyun.com)提升配额。具体操作，请参见[创建配额提升申请]()。

## 一个SNAT条目支持关联多少个EIP？

一个SNAT条目默认支持关联64个弹性公网IP（EIP），且不支持提升配额。

## SNAT条目支持创建SNAT IP地址池吗？

SNAT条目支持创建SNAT IP地址池。具体操作，请参见[创建SNAT IP地址池](/cn.zh-CN/最佳实践/创建SNAT IP地址池.md)。

## 如何统一ECS实例的公网出口IP？

为ECS实例配置SNAT规则后，ECS实例会通过SNAT IP访问互联网。但如果该ECS实例持有了公网IP（例如分配了固定公网IP、绑定了EIP或设置了DNAT IP映射），当该ECS实例发起互联网访问时，会优先通过持有的公网IP访问互联网，而不会使用SNAT IP访问互联网。如需统一公网出口IP，请参见[为已分配固定公网IP的ECS实例统一公网出口IP](/cn.zh-CN/最佳实践/统一公网出口IP/为已分配固定公网IP的ECS实例统一公网出口IP.md)、[为已绑定EIP的ECS实例统一公网出口IP](/cn.zh-CN/最佳实践/统一公网出口IP/为已绑定EIP的ECS实例统一公网出口IP.md)和[为设置了DNAT IP映射的ECS实例统一公网出口IP](/cn.zh-CN/最佳实践/统一公网出口IP/为设置了DNAT IP映射的ECS实例统一公网出口IP.md)。

## 创建SNAT条目时，为什么在公网IP地址列表找不到已创建的EIP？

创建SNAT条目前，请确保您已经创建了NAT网关实例并绑定了EIP。具体操作，请参见[创建SNAT实现访问公网服务](/cn.zh-CN/基本功能操作/创建SNAT实现访问公网服务.md)。

## ECS实例分配了固定公网IP且创建了SNAT条目，如何实现ECS实例优先通过SNAT条目的公网IP访问互联网？

您可以为ECS实例单独分配一块弹性网卡，并将固定公网IP转换为EIP，然后将EIP绑定到弹性网卡，以实现ECS实例优先通过SNAT条目的公网IP访问互联网，以及互联网通过弹性网卡主动访问ECS实例。具体操作，请参见[为已分配固定公网IP的ECS实例统一公网出口IP](/cn.zh-CN/最佳实践/统一公网出口IP/为已分配固定公网IP的ECS实例统一公网出口IP.md)。

## ECS实例绑定了EIP且创建了SNAT条目，如何实现ECS实例优先通过SNAT条目的公网IP访问互联网？

您可以为ECS实例单独分配一块弹性网卡，然后将EIP与ECS实例解绑并将EIP绑定到弹性网卡，以实现ECS实例优先通过SNAT条目的公网IP访问互联网，以及互联网通过弹性网卡主动访问ECS实例。具体操作，请参见[为已绑定EIP的ECS实例统一公网出口IP](/cn.zh-CN/最佳实践/统一公网出口IP/为已绑定EIP的ECS实例统一公网出口IP.md)。

## ECS实例设置了DNAT IP映射且创建了SNAT条目，如何实现ECS实例优先通过SNAT条目的公网IP访问互联网？

您可以为ECS实例单独分配一块弹性网卡，然后移除NAT网关中的DNAT IP映射条目并创建新的DNAT条目，建立NAT网关上的公网IP与弹性网卡的映射关系，以实现ECS实例优先通过SNAT条目的公网IP访问互联网，以及互联网通过弹性网卡主动访问ECS实例。具体操作，请参见[为设置了DNAT IP映射的ECS实例统一公网出口IP](/cn.zh-CN/最佳实践/统一公网出口IP/为设置了DNAT IP映射的ECS实例统一公网出口IP.md)。

