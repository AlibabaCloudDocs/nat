---
keyword: [NAT网关, 增强型, 网络地址转换, 提供公网服务, 访问公网]
---

# 同VPC内多NAT网关部署方案

同一个VPC内支持创建多个增强型NAT网关，您可以通过不同的NAT网关来转发去往不同目的地址的流量，并可以针对不同的NAT网关做不同的安全防护，实现更精细化的部署公网访问网络。

## 同VPC内部署多NAT网关的场景说明

本部署方案将根据以下目标场景，利用增强型NAT产品在同一个VPC内构建独立的公网出入口的网络环境。

![同VPC多NAT网关方案架构图](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1805619061/p206992.png)

上述场景方案中的交换机对应的场景说明如下：

-   VSwitch1：属于默认安全域，关联系统路由表。

    独立公网IP，50 Mbps带宽；不主动对外暴露公网IP，只允许内部主机主动对外访问，并要求独立环境。

-   VSwitch2：属于特殊安全域，关联VPC子网路由表。

    共享特殊安全域内的统一公网出口1 Gbps；既能被外网访问，同时需要主动访问公网。

-   VSwitch3：属于特殊安全域，关联VPC子网路由表。

    共享特殊安全域内的统一公网出口1 Gbps；既能被外网访问，同时需要主动访问公网。


## 同VPC内部署多NAT网关的解决方案说明

针对上述场景，您需要创建的资源和对应的解决方案罗列如下：

-   创建一个VPC来部署3个VSwitch，其中默认安全域内部署一套NAT网关（NATGW-1），VSwitch使用该套网关；独立安全域内部署另一套NAT网关（NATGW-2），VSwitch2和VSwitch3共享这套网关。
-   创建一个50 Mbps的EIP，用于绑定NATGW-1的SNAT。
-   申请一个1 Gbps的共享带宽，用于NATGW-2，再申请3个EIP加入到该共享带宽中，2个EIP分别用于VSwitch2和VSwitch3的DNAT使用，第三个EIP用于两个VSwitch的SNAT访问。
-   配置NAT网关的监控，针对NATGW-2下不同VSwitch的SNAT流量进行监控，监控VSwitch的使用情况。

## 同VPC内部署多NAT网关的配置汇总

|云资源|配置|数量|
|---|--|--|
|VPC|呼和浩特地域|1个|
|VSwitch|分布于两个可用区|3 个|
|增强型NAT网关|部署在同一个VPC中|2 个|

|云资源|配置|数量|
|---|--|--|
|增强型NAT实例|按量计费-小型|1个|
|EIP|按量付费-50 Mbps|1个|
|ECS|ecs.g6e.large|1 台|

|云资源|配置|数量|
|---|--|--|
|增强型NAT实例|按量计费-中型|1个|
|EIP|按量付费-5 Mbps|3个|
|共享带宽|按量付费-1 Gbps|1个|
|ECS|ecs.g6e.large|2台|

## 部署流程

![同VPC内多NAT网关部署流程](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/0805619061/p206994.png)

