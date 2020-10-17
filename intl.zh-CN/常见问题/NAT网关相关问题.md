# NAT网关相关问题

-   [一个公网IP可以同时用于DNAT和SNAT条目吗？](#section_vlv_m2f_2bf)
-   [一个阿里云账号可以创建多少个NAT网关？](#section_0wp_8zk_c6u)
-   [一个NAT网关可以创建多少条DNAT条目？](#section_igf_d4c_mui)
-   [一个NAT网关可以创建多少条SNAT条目？](#section_rsx_1cu_8cd)
-   [一个SNAT条目支持关联多少个公网IP？](#section_oyo_bvw_tt3)
-   [NAT网关支持查看每个交换机的流量吗？](#section_vcs_0wp_vsg)
-   [ECS实例分配了固定公网IP且创建了SNAT条目，如何实现ECS实例优先通过SNAT的公网IP访问互联网？](#section_534_7dp_bs8)
-   [ECS实例绑定了EIP且创建了SNAT条目，如何实现ECS实例优先通过SNAT的公网IP访问互联网？](#section_u9j_9ts_jo0)
-   [ECS实例设置了DNAT IP映射且创建了SNAT条目，如何实现ECS实例优先通过SNAT的公网IP访问互联网？](#section_0wq_838_rp7)

## 一个公网IP可以同时用于DNAT和SNAT条目吗？

NAT网关类型不同，对一个公网IP是否可以同时用于DNAT和SNAT条目的支持情况不同，具体如下：

-   普通型NAT网关不支持将一个公网IP同时用于DNAT条目和SNAT条目。
-   增强型NAT网关白名单支持将一个公网IP同时用于DNAT条目和SNAT条目。如需使用，请[提交工单](https://workorder-intl.console.aliyun.com/#/ticket/createIndex)。

## 一个阿里云账号可以创建多少个NAT网关？

每个VPC仅能创建1个NAT网关。不针对阿里云账号限制NAT网关的数量。

## 一个NAT网关可以创建多少条DNAT条目？

一个NAT网关最多可添加100条DNAT条目。

您可以在配额管理页面，找到配额名称natgw\_quota\_dnat\_entry\_num，然后申请调整。

## 一个NAT网关可以创建多少条SNAT条目？

一个NAT网关最多可添加40条SNAT条目。

您可以在配额管理页面，找到配额名称natgw\_quota\_snat\_entry\_num，然后申请调整。

## 一个SNAT条目支持关联多少个公网IP？

默认64个，不支持调整。

## NAT网关支持查看每个交换机的流量吗？

不支持。

您可以为每个交换机绑定一个EIP，然后通过查看EIP获取交换机的流量。

## ECS实例分配了固定公网IP且创建了SNAT条目，如何实现ECS实例优先通过SNAT的公网IP访问互联网？

您可以为ECS实例单独分配一块弹性网卡，并将固定公网IP转为EIP，然后将EIP绑定到弹性网卡，以实现ECS实例优先通过SNAT的公网IP访问互联网，互联网通过弹性网卡主动访问ECS实例。详细信息，请参见[为已分配固定公网IP的ECS实例统一公网出口IP](/intl.zh-CN/最佳实践/统一公网出口IP/为已分配固定公网IP的ECS实例统一公网出口IP.md)。

## ECS实例绑定了EIP且创建了SNAT条目，如何实现ECS实例优先通过SNAT的公网IP访问互联网？

您可以为ECS实例单独分配一块弹性网卡，然后将EIP与ECS实例解绑并将EIP绑定到弹性网卡，以实现ECS实例优先通过SNAT的公网IP访问互联网，互联网通过弹性网卡主动访问ECS实例。详细信息，请参见[为已绑定EIP的ECS实例统一公网出口IP](/intl.zh-CN/最佳实践/统一公网出口IP/为已绑定EIP的ECS实例统一公网出口IP.md)。

## ECS实例设置了DNAT IP映射且创建了SNAT条目，如何实现ECS实例优先通过SNAT的公网IP访问互联网？

您可以为ECS实例单独分配一块弹性网卡，然后移除NAT网关中的DNAT IP映射条目并创建新的DNAT条目，建立NAT网关上的公网IP与弹性网卡的映射关系，以实现ECS实例优先通过SNAT的公网IP访问互联网，互联网通过弹性网卡主动访问ECS实例。详细信息，请参见[为设置了DNAT IP映射的ECS实例统一公网出口IP](/intl.zh-CN/最佳实践/统一公网出口IP/为设置了DNAT IP映射的ECS实例统一公网出口IP.md)。

