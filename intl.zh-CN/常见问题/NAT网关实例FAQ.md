---
keyword: [NAT网关, 常见问题, FAQ]
---

# NAT网关实例FAQ

本文介绍NAT网关实例相关的常见问题。

-   [为什么NAT网关控制台不能绑定EIP？](#section_dxn_v29_z2k)
-   [为什么NAT网关控制台不能购买NAT带宽包？](#section_g17_xi3_lt0)
-   [一个阿里云账号支持创建多少个NAT网关实例？](#section_ch5_lda_osh)
-   [一个VPC支持创建多少个NAT网关实例？](#section_8l9_cwy_02b)
-   [一个NAT网关实例支持绑定多少个EIP？](#section_9hb_4u4_f2e)
-   [一个EIP可以同时用于DNAT和SNAT条目吗？](#section_9qf_el8_09i)
-   [ECS实例可以通过增强型NAT实例中的SNAT访问同一个NAT实例上的DNAT服务么？](#section_wdq_wze_1yj)
-   [NAT网关绑定EIP后，为什么访问公网的流量达不到EIP的带宽峰值？](#section_i0c_yb8_sw1)

## 为什么NAT网关控制台不能绑定EIP？

如果您的账号在2018年01月26日之前存在NAT带宽包，您仍需使用NAT带宽包为该NAT网关提供公网IP。如需使用EIP绑定NAT网关功能，请根据以下信息操作。

-   如果您的NAT带宽包的计费方式为按固定带宽计费，您可以将NAT带宽包中的公网IP转换为EIP。具体操作，请参见[NAT网关带宽包转换为共享带宽](/intl.zh-CN/NAT网关带宽包 （停止新购）/NAT网关带宽包转换为共享带宽.md)。
-   如果您的NAT带宽包的计费方式为按使用流量计费，请申请将NAT带宽包中的公网IP转换为EIP的白名单，然后再将NAT带宽包中的公网IP会转换为EIP。具体操作，请参见[NAT网关带宽包转换为共享带宽](/intl.zh-CN/NAT网关带宽包 （停止新购）/NAT网关带宽包转换为共享带宽.md)。您可以使用钉钉扫描下方的二维码或者搜索钉钉群号35128151加入钉钉群提交申请。

    ![NAT网关带宽包钉群](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4446285261/p293192.png)


## 为什么NAT网关控制台不能购买NAT带宽包？

如果您的账号在2018年01月26日之前不存在NAT带宽包，您需要为NAT网关绑定EIP使其具备访问公网的能力。具体操作，请参见[绑定EIP](/intl.zh-CN/基本功能操作/创建NAT网关实例.md)。

## 一个阿里云账号支持创建多少个NAT网关实例？

不针对阿里云账号限制创建NAT网关的数量。

## 一个VPC支持创建多少个NAT网关实例？

一个专有网络VPC（Virtual Private Cloud）支持创建的NAT网关实例的数量与NAT网关的网关类型有关，具体如下：

-   一个VPC支持创建1个普通型NAT网关实例，且无法提升配额。
-   一个VPC支持创建5个增强型NAT网关实例。如需更多配额，请[提交工单](https://workorder-intl.console.aliyun.com/#/ticket/createIndex)申请。

## 一个NAT网关实例支持绑定多少个EIP？

一个NAT网关实例默认支持绑定20个弹性公网IP EIP（Elastic IP Address），其中默认支持绑定10个按使用流量计费的EIP。

您可以前往[配额管理页面](https://vpc.console.aliyun.com/quota)自助提升配额。具体操作，请参见[管理配额](/intl.zh-CN/通用配置/管理配额.md)。

## 一个EIP可以同时用于DNAT和SNAT条目吗？

一个EIP是否可以同时用于DNAT（提供公网服务）和SNAT（访问公网服务）条目与NAT网关的网关类型有关，具体如下：

-   普通型NAT网关不支持将一个EIP同时用于DNAT条目和SNAT条目。
-   增强型NAT网关支持将一个EIP同时用于DNAT条目和SNAT条目。

## ECS实例可以通过增强型NAT实例中的SNAT访问同一个NAT实例上的DNAT服务么？

不可以。

当您在增强型NAT实例上同时创建了SNAT和DNAT，VPC内的ECS实例通过该增强型NAT实例的SNAT能力去访问同NAT网关实例内的DNAT服务时无法联通。

如果您需要ECS实例去访问同一个VPC内的DNAT服务，建议您新建一个增强型NAT网关，然后将DNAT和SNAT分别创建在不同的NAT网关实例上。

## NAT网关绑定EIP后，为什么访问公网的流量达不到EIP的带宽峰值？

NAT网关绑定的EIP的数量，会限制NAT网关的最大并发连接数。当NAT网关绑定1个EIP时，NAT网关的最大并发连接数为55000。

如果ECS实例通过NAT网关访问公网上同一个目的IP和端口的带宽大于2 Gbps时，建议您为NAT网关绑定4~8个EIP并构建SNAT IP地址池，避免出现因单个EIP的并发连接数限制而产生的丢包问题。具体操作，请参见[创建SNAT IP地址池](/intl.zh-CN/最佳实践/创建SNAT IP地址池.md)。

