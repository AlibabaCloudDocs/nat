---
keyword: [NAT网关, 公网访问, SNAT, DNAT]
---

# 什么是NAT网关

NAT网关（NAT Gateway）是一款企业级的公网网关，提供NAT代理（SNAT和DNAT）功能，具有10 Gbps级别的转发能力和跨可用区的容灾能力。

![NAT网关图解](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/1283214061/p4440.png)

## 功能简介

NAT网关作为一个网关设备，需要绑定公网IP才能正常工作。创建NAT网关后，您可以为NAT网关绑定弹性公网IP（Elastic IP Address，简称EIP）。

**说明：** 2017年11月3日之前，如果您的阿里云账号存在NAT带宽包，您仍需使用NAT带宽包为NAT网关提供公网IP。如需使用EIP为NAT网关提供公网IP的功能，请将NAT带宽包转换为共享带宽。具体操作，请参见[NAT网关带宽包转换为共享带宽](/cn.zh-CN/NAT网关带宽包 （停止新购）/NAT网关带宽包转换为共享带宽.md)。

NAT网关支持SNAT和DNAT功能，功能说明如下：

|功能|说明|相关文档|
|--|--|----|
|SNAT功能|为专有网络（VPC）内无公网IP的ECS实例提供访问公网的代理服务。|[使用SNAT访问公网](/cn.zh-CN/快速入门/使用SNAT访问公网.md)|
|DNAT功能|将NAT网关上绑定的EIP映射给VPC内的ECS实例使用，使ECS实例可以面向公网提供服务。|[通过DNAT实现主机面向公网提供服务](/cn.zh-CN/快速入门/通过DNAT实现主机面向公网提供服务.md)|

## 联系我们

如果您对NAT网关产品有任何疑问，请打开钉钉扫描下方二维码加入钉钉群咨询。

群名：NAT网关客户交流群

群号：34756416

![用户群二维码](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4082659951/p161032.png)

