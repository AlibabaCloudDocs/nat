---
keyword: [NAT网关, 常见问题, FAQ]
---

# NAT网关实例FAQ

本文介绍NAT网关实例相关的常见问题。

-   [一个阿里云账号支持创建多少个NAT网关实例？](#section_ch5_lda_osh)
-   [一个VPC支持创建多少个NAT网关实例？](#section_8l9_cwy_02b)
-   [一个NAT网关实例支持绑定多少个EIP？](#section_9hb_4u4_f2e)
-   [一个EIP可以同时用于DNAT和SNAT条目吗？](#section_9qf_el8_09i)
-   [\#section\_vrx\_7la\_ch1](#section_vrx_7la_ch1)
-   [\#section\_hm7\_2wq\_l9y](#section_hm7_2wq_l9y)
-   [NAT网关绑定EIP后，为什么访问公网的流量达不到EIP的带宽峰值？](#section_i0c_yb8_sw1)

## 一个阿里云账号支持创建多少个NAT网关实例？

不针对阿里云账号限制创建NAT网关的数量。

## 一个VPC支持创建多少个NAT网关实例？

一个专有网络（VPC）支持创建的NAT网关实例的数量与NAT网关的网关类型有关，具体如下：

-   一个VPC支持创建1个普通型NAT网关实例，且无法提升配额。
-   一个VPC支持创建5个增强型NAT网关实例。如需更多配额，请[提交工单](https://workorder-intl.console.aliyun.com/#/ticket/createIndex)申请。

## 一个NAT网关实例支持绑定多少个EIP？

一个NAT网关实例默认支持绑定20个弹性公网IP（EIP），其中默认支持绑定10个按使用流量计费的EIP。

您可以前往[配额管理页面](https://vpc.console.aliyun.com/quota)自助提升配额。具体操作，请参见[管理配额]()。

## 一个EIP可以同时用于DNAT和SNAT条目吗？

一个EIP是否可以同时用于DNAT（提供公网服务）和SNAT（访问公网服务）条目与NAT网关的网关类型有关，具体如下：

-   普通型NAT网关不支持将一个EIP同时用于DNAT条目和SNAT条目。
-   增强型NAT网关白名单支持将一个公网IP同时用于DNAT条目和SNAT条目。如需申请白名单，请[提交工单](https://workorder-intl.console.aliyun.com/#/ticket/createIndex)。

## NAT网关绑定EIP后，为什么访问公网的流量达不到EIP的带宽峰值？

NAT网关绑定的EIP的数量，会限制NAT网关的最大并发连接数。当NAT网关绑定1个EIP时，NAT网关的最大并发连接数为55000。

如果ECS实例通过NAT网关访问公网上同一个目的IP和端口的带宽大于2 Gbps时，建议您为NAT网关绑定4~8个EIP并构建SNAT IP地址池，避免出现因单个EIP的并发连接数限制而产生的丢包问题。具体操作，请参见[创建SNAT IP地址池](/intl.zh-CN/最佳实践/创建SNAT IP地址池.md)。

