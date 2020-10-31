---
keyword: [NAT网关, DNAT, 提供公网服务]
---

# DNAT概述

NAT网关支持DNAT（Destination Network Address Translation，目的网络地址转换）功能，可以实现专有网络（VPC）类型的ECS实例面向公网提供服务。

![DNAT架构图](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/8322314061/p178170.png)

## DNAT功能简介

DNAT指目的网络地址转换，即可以将DNAT IP（DNAT条目中设置的EIP）映射给VPC内的ECS实例使用。配置DNAT功能后，DNAT IP收到的请求将按照自定义的映射规则，转发给VPC内的ECS实例，使ECS实例可以面向公网提供服务。

## 设置DNAT功能

您可以通过端口映射和IP映射两种方式设置DNAT功能：

-   端口映射

    配置端口映射后，NAT网关会将以指定协议和端口访问DNAT IP的请求转发到目标ECS实例的指定协议和端口上。例如下表中的DNAT条目。

    |转发条目|公网IP|公网端口|私网IP|私网端口|协议|
    |:---|:---|:---|:---|:---|:-|
    |条目1|1.x.x.1|80|192.168.1.1|80|TCP|
    |条目2|2.x.x.2|8080|192.168.1.2|8000|UDP|

    -   条目1：NAT网关会将访问1.x.x.1的TCP 80端口的请求转发到192.168.1.1的TCP 80端口上。
    -   条目2：NAT网关会将访问2.x.x.2的UDP 8080端口的请求转发到192.168.1.2的UDP 8000端口上。
-   IP映射

    配置IP映射后，NAT网关会将任何访问DNAT IP的请求都将转发到目标ECS实例上。例如下表中的DNAT条目。

    |转发条目|公网IP|公网端口|私网IP|私网端口|协议|
    |:---|:---|:---|:---|:---|:-|
    |条目3|3.x.x.3|Any|192.168.1.3|Any|Any|

    条目3：NAT网关会将任何访问3.x.x.3的请求转发到192.168.1.3实例上。


如何设置DNAT功能，请参见[创建DNAT条目](/cn.zh-CN/用户指南/DNAT（提供公网服务）/创建DNAT条目.md)。

