# 增强型NAT网关和普通型NAT网关API差异

本文概括了增强型NAT网关和普通型NAT网关在调用API时的差异。

## CreateNatGateway

在执行[CreateNatGateway](/cn.zh-CN/API参考/NAT网关/CreateNatGateway.md)创建增强型NAT网关前，您需要先执行[ListEnhanhcedNatGatewayAvailableZones](/cn.zh-CN/API参考/NAT网关/ListEnhanhcedNatGatewayAvailableZones.md)接口查询增强型NAT网关的资源可用区，然后查询到的资源可用区中创建或选择一个有可用IP的交换机。

|差异|增强型NAT网关|普通型NAT网关|
|--|--------|--------|
|接口调用方式|异步方式。CreateNatGateway接口属于异步接口，即系统会先返回一个增强型NAT网关实例ID，但该实例并未创建完成，系统后台的创建任务仍在进行。您可以调用[DescribeNatGateways](/cn.zh-CN/API参考/NAT网关/DescribeNatGateways.md)查询增强型NAT网关的状态：

-   当增强型NAT网关处于**Creating**状态时，表示增强型NAT网关正在创建中，您只能执行查询操作，不能执行其他操作。
-   当增强型NAT网关处于**Available**状态时，表示增强型NAT网关创建完成。

|同步方式|
|请求参数|新增以下参数：-   **VswitchId**：必选参数。
-   **NatType**：必选参数。
-   **InternetChargeType**：非必选参数。

|无|

## DescribeNatGateways

[DescribeNatGateways](/cn.zh-CN/API参考/NAT网关/DescribeNatGateways.md)接口返回参数的差异如下：

|参数名称|增强型NAT网关|普通型NAT网关|
|----|--------|--------|
|NatGatewayPrivateInfo|新增增强型NAT网关私网信息的结构体，具体返回值如下：-   **EniInstanceId**：弹性网卡实例ID，String类型，例如eni-xaskc\*\*\*\*。
-   **PrivateIpAddress**：私网IP地址，String类型，例如192.XX.XX.1。
-   **VswitchId**：增强型NAT网关所属的交换机ID，String类型，例如vsw-bp1s2laxhdf9ayjbo\*\*\*\*。
-   **MaxBandwidth**：最大带宽值，Integer类型，单位为Mbps，例如5120。
-   **IzNo**：增强型NAT网关所属的可用区，String类型，cn-hangzhou-b。

|无|
|Status|新增以下状态：-   **Creating**：创建增强型NAT网关是异步操作，在创建完成之前是**Creating**状态。
-   **Modifying**：变配增强型NAT网关是异步操作，在变配的过程中是**Modifying**状态。
-   **Deleting**：删除增强型NAT网关是异步操作，在删除的过程中是**Deleting**状态。

|**Available**：网关创建完成后的状态，是稳定状态。|
|NatType|**Enhanced**：增强型NAT网关。|**Normal**：普通型NAT网关。|
|InternetChargeType|-   **PayBySpec**：按固定规格计费。
-   **PayByLcu**：按使用量计费。

|无|

## ModifyNatGatewaySpec

[ModifyNatGatewaySpec](/cn.zh-CN/API参考/NAT网关/ModifyNatGatewaySpec.md)接口调用方式的差异如下：

|增强型NAT网关|普通型NAT网关|
|--------|--------|
|异步方式。ModifyNatGatewaySpec接口属于异步接口，即系统会先返回一个请求ID，但该增强型NAT网关实例的规格并未变配完成，系统后台的变配任务仍在进行。您可以调用[DescribeNatGateways](/cn.zh-CN/API参考/NAT网关/DescribeNatGateways.md)查询增强型NAT网关的状态：

-   当增强型NAT网关处于**Modifying**状态时，表示增强型NAT网关正在变配中，您只能执行查询操作，不能执行其他操作。
-   当增强型NAT网关处于**Available**状态时，表示增强型NAT网关变配完成。

|同步方式|

## DeleteNatGateway

[DeleteNatGateway](/cn.zh-CN/API参考/NAT网关/DeleteNatGateway.md)接口调用方式的差异如下：

|增强型NAT网关|普通型NAT网关|
|--------|--------|
|异步方式。DeleteNatGateway接口属于异步接口，即系统会先返回一个请求ID，但该增强型NAT网关实例并未删除完成，系统后台的删除任务仍在进行。您可以调用[DescribeNatGateways](/cn.zh-CN/API参考/NAT网关/DescribeNatGateways.md)查询增强型NAT网关的状态：

-   当增强型NAT网关处于**Deleting**状态时，表示增强型NAT网关正在删除中，您只能执行查询操作，不能执行其他操作。
-   当返回的实例列表为空时，表示增强型NAT网关删除完成。

|同步方式|

## 增强型NAT网关新增API

|API|说明|
|---|--|
|[ListEnhanhcedNatGatewayAvailableZones](/cn.zh-CN/API参考/NAT网关/ListEnhanhcedNatGatewayAvailableZones.md)|查询增强型NAT网关的资源可用区。|
|[UpdateNatGatewayNatType](/cn.zh-CN/API参考/NAT网关/UpdateNatGatewayNatType.md)|将普通型NAT网关升级为增强型NAT网关。|
|[GetNatGatewayConvertStatus](/cn.zh-CN/API参考/NAT网关/GetNatGatewayConvertStatus.md)|查看增强型NAT网关转换状态列表。|
|[EnableNatGatewayEcsMetric](/cn.zh-CN/API参考/NAT网关/EnableNatGatewayEcsMetric.md)|开启ECS流量监控。|
|[ListNatGatewayEcsMetric](/cn.zh-CN/API参考/NAT网关/ListNatGatewayEcsMetric.md)|查看增强型NAT网关的流量监控数据。|

