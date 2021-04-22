---
keyword: [NAT网关, 增强型, 网络地址转换, 提供公网服务, 访问公网]
---

# 什么是NAT网关

NAT网关（NAT Gateway）是一款企业级的针对公网访问的安全网关，提供NAT代理（SNAT和DNAT）功能，具有100 Gbps级别的转发能力及跨可用区的容灾能力。

-   如果您的云上网络只希望主动访问公网上的业务，而不希望您云上的业务直接暴露在公网上从而有被攻击的风险，您可以选用NAT网关为您的业务提供安全防护能力。
-   如果您的业务具有突增的访问公网的流量需求，您可以选用NAT网关为您提供的灵活和弹性的扩容能力，并且只需要按使用量付费，节省企业成本。
-   如果您有大量访问公网的机器，您可以通过NAT网关统一公网出口并通过NAT网关提供准确和精细化的运维监控能力管理企业访问公网的流量。

![NAT网关图解](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1283214061/p4440.png)

## 产品功能

NAT网关支持SNAT和DNAT功能，功能说明如下：

|功能|说明|相关文档|
|--|--|----|
|SNAT功能|为VPC内无公网IP的ECS实例提供访问公网的代理服务。|[使用SNAT访问公网](/cn.zh-CN/快速入门/使用SNAT访问公网.md)|
|DNAT功能|将NAT网关上绑定的EIP映射给VPC内的ECS实例使用，使ECS实例可以面向公网提供服务。|[通过DNAT实现主机面向公网提供服务](/cn.zh-CN/快速入门/通过DNAT实现主机面向公网提供服务.md)|

## 产品优势

NAT网关拥有以下优势：

-   **安全防护**

    NAT网关的SNAT功能具有安全防护的能力，只有当VPC内的ECS实例主动访问外部才可以建立连接进行通信，而外部无法主动访问VPC内的ECS实例。SNAT功能会屏蔽VPC内ECS实例对外的端口，保护VPC内的ECS实例免受外部的入侵和攻击。

-   **高性能**

    NAT网关是基于阿里云自研分布式网关，使用SDN技术推出的一款虚拟网络硬件。NAT网关支持10 Gbps级别的转发能力，为大规模公网应用提供支撑。

-   **节约成本**

    NAT网关的规格、EIP的规格和个数，均可以随时升降，轻松应对业务变化，同时还可以按使用量计费。

-   **区域高可用性**

    NAT网关跨可用区部署，可用性高。单个可用区的故障都不会影响NAT网关的业务连续性。


## 使用规则

-   增强型NAT网关要求您在购买的时候选择VPC，并且需要指定VPC内的子网，建议您为NAT网关创建独立的子网，以便支持后续网络的规划。
-   增强型NAT网关会从您指定的子网中分配一个弹性网卡ENI（Elastic Network Interface），该ENI会关联创建一个安全组，此安全组您可以查看但是无法修改。更多信息，请参见[弹性网卡概述](/cn.zh-CN/网络/弹性网卡/弹性网卡概述.md)。
-   增强型NAT网关默认的带宽能力是5 Gbps，如果需要更大的带宽，请[提交工单](https://selfservice.console.aliyun.com/ticket/category/natgw/today)。
-   增强型NAT网关支持多可用区容灾，您购买时指定的子网是主可用区所在的子网，备可用区的子网无需您在购买时选择。

## 使用限制

|资源|默认限制|提升配额|
|--|----|----|
|一个专有网络（VPC）支持创建的增强型NAT网关的数量|5个|[提交工单](https://selfservice.console.aliyun.com/ticket/category/natgw/today)。|
|一个VPC支持创建的普通型NAT网关的数量|1个|无法提升配额。|
|一个NAT网关支持绑定的EIP的数量|20个，其中最多支持绑定10个按使用流量计费的EIP。|您可以通过以下任意方式自助提升配额：

-   前往[配额管理页面](https://vpc.console.aliyun.com/quota)提升配额，更多信息，请参见[管理配额](/cn.zh-CN/通用配置/管理配额.md)。
-   前往[配额中心](https://quotas.console.aliyun.com)提升配额。更多信息，请参见[创建配额提升申请]()。 |
|一个NAT网关支持绑定的按使用流量计费EIP的数量|10个|
|VPC中存在目标网段为0.0.0.0/0的自定义路由，是否支持在该VPC创建NAT网关|-   支持在该VPC中创建增强型NAT网关。
-   不支持在该VPC中创建普通型NAT网关。

**说明：** 如果需要在该VPC中创建普通型NAT网关，请先删除0.0.0.0/0的自定义路由，然后再在VPC中创建普通型NAT网关。


|无|

|资源|默认限制|提升配额|
|--|----|----|
|一个NAT网关支持创建的SNAT条目的数量|40个|您可以通过以下任意方式自助提升配额：

-   前往[配额管理页面](https://vpc.console.aliyun.com/quota)提升配额，更多信息，请参见[管理配额](/cn.zh-CN/通用配置/管理配额.md)。
-   前往[配额中心](https://quotas.console.aliyun.com)提升配额。更多信息，请参见[创建配额提升申请]()。 |
|一个SNAT条目支持可关联的EIP的数量|64个|无法提升配额。|
|以交换机粒度创建SNAT条目后，访问公网的带宽是否会受到EIP带宽峰值的限制|是。**说明：** 如果与NAT网关绑定的EIP加入到共享带宽中，则访问公网的带宽会受到共享带宽的带宽峰值的限制。

|无|
|一个EIP是否支持同时用于SNAT表和DNAT表|-   增强型NAT网关白名单支持将一个EIP同时用于SNAT表和DNAT表。如需申请白名单，请[提交工单](https://selfservice.console.aliyun.com/ticket/category/natgw/today)。
-   普通型NAT网关不支持将一个EIP同时用于SNAT表和DNAT表。 |
|SNAT IP数量对NAT网关最大并发连接数的限制|当VPC内无公网IP的ECS实例通过NAT网关访问公网上同一个目的IP和端口时，NAT网关SNAT条目配置的EIP数量会限制NAT网关的最大并发连接数。 -   当SNAT条目配置1个EIP时，NAT网关的最大并发连接数为55000。
-   当SNAT条目配置n个EIP时，NAT网关的最大并发连接数为n×55000。 |
|SNAT IP带宽限制|创建SNAT条目时，如果选择多个EIP配置SNAT IP地址池，需确保每个EIP都加入到同一个共享带宽中。-   增强型NAT网关的SNAT IP地址池中的EIP最大带宽没有限制。
-   普通型NAT网关的SNAT IP地址池中每个EIP的最大带宽限制为200 Mbps，为了使SNAT规则能充分利用共享带宽的带宽能力，及避免EIP过少导致端口冲突，建议您按照以下配比关系添加EIP到SNAT IP地址池：
    -   共享带宽的带宽峰值为1024 Mbps时，SNAT条目中的EIP数量应至少为5个。
    -   共享带宽的带宽峰值以1024 Mbps为基础每增加200 Mbps，SNAT条目中都应至少再新增1个EIP。

具体操作，请参见[创建SNAT IP地址池](/cn.zh-CN/最佳实践/创建SNAT IP地址池.md)。 |

|资源|默认限制|提升配额|
|--|----|----|
|一个NAT网关支持创建的DNAT条目的数量|100个|您可以通过以下任意方式自助提升配额：

-   前往[配额管理页面](https://vpc.console.aliyun.com/quota)提升配额，更多信息，请参见[管理配额](/cn.zh-CN/通用配置/管理配额.md)。
-   前往[配额中心](https://quotas.console.aliyun.com)提升配额。更多信息，请参见[创建配额提升申请]()。 |
|一个EIP是否支持同时用于SNAT表和DNAT表|-   增强型NAT网关白名单支持将一个EIP同时用于SNAT表和DNAT表。如需申请白名单，请[提交工单](https://selfservice.console.aliyun.com/ticket/category/natgw/today)。
-   普通型NAT网关不支持将一个EIP同时用于SNAT表和DNAT表。

|无|
|是否支持为绑定了EIP的ECS实例创建DNAT条目|不支持。如需为该ECS实例创建DNAT条目，请先将ECS实例与EIP解绑，然后再为该ECS实例创建DNAT条目。更多信息，请参见[解绑EIP](/cn.zh-CN/用户指南/解绑EIP.md)和[创建DNAT提供公网服务](/cn.zh-CN/基本功能操作/创建DNAT提供公网服务.md)。

**说明：** 如果存量ECS实例绑定了EIP，且处于NAT网关的DNAT条目中，则ECS实例优先通过绑定的EIP进行公网通信。 |

## 相关产品

-   [什么是专有网络](/cn.zh-CN/产品简介/什么是专有网络.md)
-   [什么是弹性公网IP](/cn.zh-CN/.md)
-   [什么是共享带宽](/cn.zh-CN/.md)

