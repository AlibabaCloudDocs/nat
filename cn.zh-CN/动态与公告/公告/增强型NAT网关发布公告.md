---
keyword: [NAT网关, 增强型, 网络地址转换, 提供公网服务, 访问公网]
---

# 增强型NAT网关发布公告

阿里云发布增强型NAT网关，增强型NAT网关在普通型NAT网关的技术架构上作了升级，具有更优的弹性和更强的稳定性，帮助您更好的管理公网访问流量。

## 增强型NAT网关简介

增强型NAT网关与普通型NAT网关都支持DNAT（提供公网服务）和SNAT（访问公网服务）等基础功能。增强型NAT网关在普通型NAT网关的基础上新增了部分功能。

-   更加丰富的监控指标

    增强型NAT网关支持查看22个监控指标，可以实时监控NAT网关实例的运行情况，保证业务的稳定。更多信息，请参见[NAT网关监控与运维](/cn.zh-CN/基本功能操作/NAT网关监控与运维.md)。

-   同VPC多NAT网关

    同一个VPC内支持创建多个增强型NAT网关，您可以通过不同的NAT网关来转发去往不同目的地址的流量，并可以针对不同的NAT网关做不同的安全防护，实现更精细化的部署公网访问网络。

    您也可以在不同的NAT网关上指定相同的SNAT（访问公网服务）或DNAT（提供公网服务）条目，然后通过配置路由来指定流量的网关出口。

    **说明：**

    -   新申请的增强型NAT网关如果要接管普通型NAT网关的流量，需要重新配置路由，在配置过程中会导致业务闪断，请注意在业务低峰时间做切换。
    -   当您在增强型NAT实例上同时创建了SNAT和DNAT，VPC内的ECS实例通过该增强型NAT实例的SNAT能力去访问同NAT实例内的DNAT服务时无法联通。如果您需要ECS实例去访问同一个VPC内的DNAT服务，建议您新建一个增强型NAT网关，然后将DNAT和SNAT分别创建在不同的NAT网关实例上。
-   按使用量计费
    -   按使用量计费，使用费用更低。
    -   按使用量计费的NAT网关具有超强的突发性能。

        |规格|SNAT最大连接数|SNAT最大新建规格|吞吐量|
        |--|---------|----------|---|
        |默认规格|200万|10万|5 Gbps|
        |[提交工单](https://selfservice.console.aliyun.com/ticket/category/natgw/today)最大可提升的额度|1000万|100万|100 Gbps|


## 对比增强型与普通型NAT网关

增强型与普通型NAT网关在功能和使用限制上有共同点，但也存在差异，具体如下。

|功能项|增强型NAT网关|普通型NAT网关|相关文档|
|---|--------|--------|----|
|同VPC多NAT网关|支持|不支持|[同VPC内多NAT网关部署方案](/cn.zh-CN/最佳实践/同VPC内多NAT网关部署方案.md)|
|NAT网关关联交换机|支持|不支持|无|
|按使用量计费|支持|不支持|[按使用量计费](/cn.zh-CN/购买指南/按量付费.mdsection_v5g_sue_5bj)|
|按小时计费周期|支持|不支持|[按使用量计费](/cn.zh-CN/购买指南/按量付费.mdsection_v5g_sue_5bj)|
|包年包月计费|支持|支持|[包年包月](/cn.zh-CN/购买指南/包年包月.md)|
|按天的计费周期|不支持|支持|[按量付费](/cn.zh-CN/购买指南/按量付费.md)|
|处理TCP、UDP和ICMP分片包|支持|不支持|无|
|监控指标|22个|4个|[NAT网关监控与运维](/cn.zh-CN/基本功能操作/NAT网关监控与运维.md)|
|网关流量监控（TOP ECS）|支持|不支持|[查看网关流量监控](/cn.zh-CN/基本功能操作/NAT网关监控与运维.md)|
|NAT网关绑定多EIP|支持|支持|[绑定弹性公网IP](/cn.zh-CN/基本功能操作/创建NAT网关实例.md)|
|SNAT功能|支持|支持|[创建SNAT实现访问公网服务](/cn.zh-CN/基本功能操作/创建SNAT实现访问公网服务.md)|
|一个SNAT列表创建多条SNAT条目|支持|支持|[创建SNAT实现访问公网服务](/cn.zh-CN/基本功能操作/创建SNAT实现访问公网服务.md)|
|一个SNAT列表绑定多个EIP|支持|支持|
|DNAT功能|支持|支持|[创建DNAT提供公网服务](/cn.zh-CN/基本功能操作/创建DNAT提供公网服务.md)|
|DNAT支持端口映射|支持|支持|[创建DNAT提供公网服务](/cn.zh-CN/基本功能操作/创建DNAT提供公网服务.md)|
|DNAT支持IP映射|支持|支持|
|ECS实例通过SNAT访问同一个NAT实例上的DNAT服务|不支持|支持|[ECS实例通过增强型NAT网关SNAT功能访问同一VPC下DNAT服务](/cn.zh-CN/最佳实践/ECS实例通过增强型NAT网关SNAT功能访问同一VPC下DNAT服务.md)|

|限制项|增强型NAT网关|普通型NAT网关|
|---|--------|--------|
|一个VPC支持创建的NAT网关的数量|5个（可[提交工单](https://selfservice.console.aliyun.com/ticket/category/natgw/today)提升配额）|1个（无法调整）|
|一个公网IP是否支持同时用于SNAT表和DNAT表|白名单支持。如需使用，请[提交工单](https://selfservice.console.aliyun.com/ticket/category/natgw/today)|不支持（无法调整）|
|一个NAT网关支持添加的DNAT条目的数量|100个（可自助提升配额。具体操作，请参见[管理配额](/cn.zh-CN/通用配置/管理配额.md)）|100个（可自助提升配额。具体操作，请参见[管理配额](/cn.zh-CN/通用配置/管理配额.md)）|
|一个NAT网关支持添加的SNAT条目的数量|40个（可自助提升配额。具体操作，请参见[管理配额](/cn.zh-CN/通用配置/管理配额.md)）|40个（可自助提升配额。具体操作，请参见[管理配额](/cn.zh-CN/通用配置/管理配额.md)）|
|一个SNAT条目支持关联的公网IP的数量|64个（无法调整）|64个（无法调整）|
|VPC中存在目标网段为0.0.0.0/0的自定义路由，是否支持为该VPC创建NAT网关|支持|不支持（必须删除0.0.0.0/0的自定义路由后，才支持为该VPC创建NAT网关）|
|交换机添加SNAT条目后，是否会受到EIP带宽峰值的限制|是（如果EIP已加入到共享带宽中，则交换机会受到共享带宽的带宽峰值的限制）|是（如果EIP已加入到共享带宽中，则交换机会受到共享带宽的带宽峰值的限制）|
|一个NAT网关支持绑定的EIP的数量|20个（可自助提升配额。具体操作，请参见[管理配额](/cn.zh-CN/通用配置/管理配额.md)）|20个（可自助提升配额。具体操作，请参见[管理配额](/cn.zh-CN/通用配置/管理配额.md)）|
|一个NAT网关支持绑定的按流量计费EIP的数量|10个（可自助提升配额。具体操作，请参见[管理配额](/cn.zh-CN/通用配置/管理配额.md)）|10个（可自助提升配额。具体操作，请参见[管理配额](/cn.zh-CN/通用配置/管理配额.md)）|
|NAT网关绑定的按流量计费EIP的最大带宽峰值|无|200 Mbps（无法调整）|
|一个NAT网关实例的最大带宽限制|5 Gbps（如果绑定的EIP或者共享带宽的总带宽大于5 Gbps，请[提交工单](https://selfservice.console.aliyun.com/ticket/category/natgw/today)提升配额）|NAT网关实例本身没有带宽限制，带宽限制取决于绑定到SNAT或DNAT规则中的EIP及EIP加入的共享带宽的带宽限制 例如：一个NAT网关创建了一个SNAT规则，SNAT规则绑定了5个按流量计费的EIP和2个500 Mbps的按带宽计费EIP，则该NAT网关的带宽限制为5\*200 Mbps+2\*500 Mbps=2000 Mbps，如果这7个EIP加入到同一个共享带宽，共享带宽的带宽限制为1000 Mbps，则NAT网关的带宽限制为1000 Mbps。 |
|一个EIP的最大并发数为55000|是|是|
|共享带宽中的单个EIP的峰值限制为200 Mbps|否|是|
|NAT带宽包用户不能绑定EIP|是|是|
|变配NAT网关关联的共享带宽的带宽峰值时，导致业务闪断（变配包括小于1 Gbps带宽峰值变配到大于1 Gbps带宽峰值或大于1 Gbps带宽峰值变配到小于1 Gbps带宽峰值）|否|是|
|存量的SNAT条目中减少IP数量导致业务闪断|是|是|
|存量的SNAT条目中增加IP数量导致业务闪断|否|是|
|ECS实例配置多个ENI，流量从某一个配置了EIP的ENI流入，从其他ENI流出时的流量畅通情况|流量不畅通，您可以在配置了EIP的ENI设置同进同出策略，具体操作，请参见[配置网卡路由](/cn.zh-CN/网络/弹性网卡/配置弹性网卡.md)。|流量畅通|

## 使用流程

增强型NAT网关的使用流程与普通型NAT网关的使用流程一致，但在创建NAT网关时需要选择增强型NAT网关，并指定增强型NAT网关要关联的VPC和交换机。增强型NAT网关创建成功后，系统会为增强型NAT网关分配一个交换机内的空闲私网IP地址。

**说明：** 如果您使用RAM用户创建增强型NAT网关，请先使用阿里云账号进行授权。[授权入口](https://ram.console.aliyun.com/#/role/authorize?request=%7B%22Requests%22:%20%7B%22request1%22:%20%7B%22RoleName%22:%20%22AliyunNATAccessingNetworkInterfaceRole%22,%20%22TemplateId%22:%20%22ENIRole%22%7D%7D,%20%22ReturnUrl%22:%20%22https:%2F%2Fvpc.console.aliyun.com%2Fnat%22,%20%22Service%22:%20%22NAT%22%7D)。

![创建增强型NAT网关](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9773424161/p243557.png)

增强型NAT网关的使用流程如下。

![NAT2.0流程](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8633359951/p101647.png)

