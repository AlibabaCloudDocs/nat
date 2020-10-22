# API概览

NAT网关提供如下API供您使用。

**说明：** NAT网关的API服务地址为vpc.aliyuncs.com，请参见VPC API文档调用NAT网关API。

## NAT网关

|API|说明|
|---|--|
|[t2533.md\#](/intl.zh-CN/API参考/NAT网关/CreateNatGateway.md)|创建NAT网关。|
|[ModifyNatGatewayAttribute](/intl.zh-CN/API参考/NAT网关/ModifyNatGatewayAttribute.md)|修改NAT网关的名称和描述。|
|[t2535.md\#](/intl.zh-CN/API参考/NAT网关/ModifyNatGatewaySpec.md)|修改NAT网关的规格。|
|[ListEnhanhcedNatGatewayAvailableZones]()|查询增强型NAT网关的资源可用区。|
|[UpdateNatGatewayNatType]()|将普通型NAT网关切换为增强型NAT网关。|
|[GetNatGatewayConvertStatus]()|查看NAT网关转换状态列表。|
|[t2534.md\#](/intl.zh-CN/API参考/NAT网关/DescribeNatGateways.md)|查询已创建的NAT网关。|
|[t2537.md\#](/intl.zh-CN/API参考/NAT网关/DeleteNatGateway.md)|删除NAT网关。|
|[EnableNatGatewayEcsMetric]()|开启ECS流量监控。|
|[ListNatGatewayEcsMetric](/intl.zh-CN/API参考/NAT网关/ListNatGatewayEcsMetric.md)|查看NAT网关的流量监控数据。|
|[DisableNatGatewayEcsMetric]()|关闭ECS流量监控。|
|[ConvertBandwidthPackage](/intl.zh-CN/API参考/NAT网关/ConvertBandwidthPackage.md)|将NAT带宽包转换为共享带宽。|

## DNAT表

|API|说明|
|---|--|
|[CreateForwardEntry](/intl.zh-CN/API参考/NAT网关/CreateForwardEntry.md)|创建DNAT条目。|
|[t2549.md\#](/intl.zh-CN/API参考/NAT网关/ModifyForwardEntry.md)|修改DNAT条目。|
|[t2548.md\#](/intl.zh-CN/API参考/NAT网关/DescribeForwardTableEntries.md)|查询已创建的DNAT条目。|
|[t2550.md\#](/intl.zh-CN/API参考/NAT网关/DeleteForwardEntry.md)|删除DNAT条目。|

## SNAT表

|API|说明|
|---|--|
|[CreateSnatEntry](/intl.zh-CN/API参考/NAT网关/CreateSnatEntry.md)|创建SNAT条目。|
|[t2553.md\#](/intl.zh-CN/API参考/NAT网关/ModifySnatEntry.md)|修改SNAT条目。|
|[t2552.md\#](/intl.zh-CN/API参考/NAT网关/DescribeSnatTableEntries.md)|查询已创建的SNAT条目。|
|[t2554.md\#](/intl.zh-CN/API参考/NAT网关/DeleteSnatEntry.md)|删除SNAT条目。|

