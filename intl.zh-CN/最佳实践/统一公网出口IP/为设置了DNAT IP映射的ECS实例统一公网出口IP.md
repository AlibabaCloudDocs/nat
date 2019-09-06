# 为设置了DNAT IP映射的ECS实例统一公网出口IP {#concept_711329 .concept}

统一ECS实例的公网出口IP，有利于您更高效的管理互联网业务。本文为您介绍如何为设置了DNAT IP映射的ECS实例统一公网出口IP。

## 前提条件 {#section_guz_qq7_inj .section}

设置了DNAT IP映射的ECS实例所在的VPC已经配置了SNAT功能。详细信息，请参见[创建SNAT条目](../intl.zh-CN/快速入门/创建SNAT条目.md#)。

## 背景信息 {#section_uvy_nls_sa5 .section}

NAT网关提供SNAT功能，为VPC内无公网IP的ECS实例提供访问互联网的代理服务。如果VPC内某些ECS实例已经设置了DNAT IP映射（IP映射即所有端口映射），这些ECS实例会优先通过DNAT条目中的公网IP访问互联网，而VPC内的其他ECS实例通过NAT网关的SNAT功能代理访问互联网，造成VPC内ECS实例的公网出口IP不一致，不利于统一管理业务。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/570564/156144624549565_zh-CN.png)

您可以通过为ECS实例绑定弹性网卡来解决ECS实例公网出口IP不统一的问题。

如下图，您可以为ECS实例单独分配一块弹性网卡，然后移除NAT网关中的DNAT IP映射条目并创建新的DNAT条目，建立NAT网关上的公网IP与弹性网卡的映射关系，这样来自互联网的访问流量会经过弹性网卡到达ECS实例，当ECS实例需要访问互联网时会通过NAT网关进行转发。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/570109/156144624549551_zh-CN.png)

## 步骤一 创建弹性网卡 {#section_on9_ddc_6rg .section}

完成以下操作，为ECS实例创建弹性网卡。

1.  登录[云服务器ECS管理控制台](https://ecs.console.aliyun.com/#/home)。
2.  在左侧导航栏，单击**网络与安全** \> **弹性网卡**。
3.  选择弹性网卡的地域。

    **说明：** 弹性网卡的地域必须与ECS实例的地域相同。

4.  在网卡列表页面，单击**创建弹性网卡**。
5.  在创建弹性网卡页面，根据以下信息配置弹性网卡，然后单击**确定**。
    -    **网卡名称**：输入弹性网卡的名称。
    -    **专有网络**：选择ECS实例所在的专有网络。
    -    **交换机**：选择ECS实例所在可用区的交换机。
    -    **主私网IP**（可选）：输入弹性网卡的主私网IPv4地址。此IPv4地址必须属于交换机的CIDR网段中的空闲地址。如果您没有指定，创建弹性网卡时将自动为您分配一个空闲的私网IPv4地址。
    -    **安全组**：选择当前专有网络的一个安全组。
    -    **描述**（可选）：输入对弹性网卡的描述。

## 步骤二 将弹性网卡绑定到ECS实例 {#section_5b2_9sh_9rm .section}

完成以下操作，将弹性网卡绑定到ECS实例。

1.  登录[云服务器ECS管理控制台](https://ecs.console.aliyun.com/#/home)。
2.  在左侧导航栏中，选择**网络与安全** \> **弹性网卡**。
3.  选择弹性网卡的地域。
4.  在网卡列表页面，找到目标弹性网卡，单击**操作**列下的**绑定实例**。
5.  在弹出的对话框中，选择要绑定的ECS实例，然后单击**确定**。

## 步骤三 移除DNAT IP映射 {#section_miz_l1c_xmx .section}

完成以下操作，移除NAT网关中的DNAT IP映射条目。

1.  登录[专有网络管理控制台](https://vpcnext.console.aliyun.com) 
2.  在左侧导航栏，单击**NAT网关**。
3.  选择NAT网关的地域。
4.  在NAT网关页面，找到目标NAT网关实例，单击**操作**列下的**设置DNAT**。
5.  在DNAT表页面，找到目标DNAT条目，单击**操作**列下的**移除**。
6.  在弹出的对话框中，单击**确定**。

## 步骤四 创建DNAT条目 {#section_9gh_p20_u4c .section}

完成以下操作，创建DNAT条目，建立NAT网关上的公网IP与弹性网卡的映射关系。

1.  登录[专有网络管理控制台](https://vpcnext.console.aliyun.com) 
2.  在左侧导航栏，单击**NAT网关**。
3.  在NAT网关页面，找到目标NAT网关实例，单击**操作**列下的**设置DNAT**。
4.  在DNAT表页面，单击**创建DNAT条目** 
5.  在创建DNAT条目页面，根据以下信息配置DNAT条目，然后单击**确定**。
    -    **公网IP地址**：选择一个可用的公网IP。用于创建SNAT条目的公网IP不能再用来创建DNAT条目。
    -    **私网IP地址**：选择弹性网卡实例。
    -    **端口设置**：选择所有端口。
    -    **条目名称**：输入DNAT条目的名称。

## 步骤五 测试网络连通性 {#section_v6f_yti_doa .section}

完成以下操作，测试互联网是否可以通过弹性网卡绑定的EIP访问ECS实例。本操作以本地Linux设备远程连接Linux实例为例。

**说明：** 远程连接Linux实例，Linux实例的安全组必须放行SSH（22）端口。详细信息，请参见[添加安全组规则](../../intl.zh-CN/安全/安全组/添加安全组规则.md#)。

1.  登录本地Linux设备。
2.  执行`ssh root@公网IP`命令，然后输入Linux实例的登录密码，查看是否可以远程连接到实例。

    若界面上出现Welcome to Alibaba Cloud Elastic Compute Service!时，表示您已经成功连接到实例。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/570109/156144624549595_zh-CN.png)


完成以下操作，测试ECS实例是否可以通过NAT网关的SNAT功能主动访问互联网。本操作以在linux实例上查看公网出口IP为例。

1.  登录ECS实例。
2.  执行`curl https://myip.ipip.net`查看公网出口IP。

    若公网出口IP与NAT网关SNAT条目中的IP一致，即ECS实例优先通过NAT网关的SNAT功能主动访问互联网。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/570109/156144624549596_zh-CN.png)


