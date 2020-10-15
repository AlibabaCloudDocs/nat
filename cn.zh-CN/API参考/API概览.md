# API概览

NAT网关提供如下API供您使用。NAT网关的API服务地址为vpc.aliyuncs.com，请参见VPC API文档调用NAT网关API。

## NAT网关

|API|说明|
|---|--|
|[t2533.md\#](/cn.zh-CN/API参考/NAT网关/CreateNatGateway.md)|创建NAT网关。|
|[ModifyNatGatewayAttribute](/cn.zh-CN/API参考/NAT网关/ModifyNatGatewayAttribute.md)|修改NAT网关的名称和描述。|
|[t2535.md\#](/cn.zh-CN/API参考/NAT网关/ModifyNatGatewaySpec.md)|修改NAT网关的规格。|
|[ListEnhanhcedNatGatewayAvailableZones](/cn.zh-CN/API参考/NAT网关/ListEnhanhcedNatGatewayAvailableZones.md)|查询增强型NAT网关的资源可用区。|
|[UpdateNatGatewayNatType](/cn.zh-CN/API参考/NAT网关/UpdateNatGatewayNatType.md)|将普通型NAT网关切换为增强型NAT网关。|
|[GetNatGatewayConvertStatus](/cn.zh-CN/API参考/NAT网关/GetNatGatewayConvertStatus.md)|查看NAT网关转换状态列表。|
|[t2534.md\#](/cn.zh-CN/API参考/NAT网关/DescribeNatGateways.md)|查询已创建的NAT网关。|
|[t2537.md\#](/cn.zh-CN/API参考/NAT网关/DeleteNatGateway.md)|删除NAT网关。|
|[EnableNatGatewayEcsMetric](/cn.zh-CN/API参考/NAT网关/EnableNatGatewayEcsMetric.md)|开启ECS流量监控。|
|[ListNatGatewayEcsMetric](/cn.zh-CN/API参考/NAT网关/ListNatGatewayEcsMetric.md)|查看NAT网关的流量监控数据。|
|[DisableNatGatewayEcsMetric](/cn.zh-CN/API参考/NAT网关/DisableNatGatewayEcsMetric.md)|关闭ECS流量监控。|

## DNAT表

|API|说明|
|---|--|
|[CreateForwardEntry](/cn.zh-CN/API参考/NAT网关/CreateForwardEntry.md)|创建DNAT条目。|
|[t2549.md\#](/cn.zh-CN/API参考/NAT网关/ModifyForwardEntry.md)|修改DNAT条目。|
|[t2548.md\#](/cn.zh-CN/API参考/NAT网关/DescribeForwardTableEntries.md)|查询已创建的DNAT条目。|
|[t2550.md\#](/cn.zh-CN/API参考/NAT网关/DeleteForwardEntry.md)|删除DNAT条目。|

## SNAT表

|API|说明|
|---|--|
|[CreateSnatEntry](/cn.zh-CN/API参考/NAT网关/CreateSnatEntry.md)|创建SNAT条目。|
|[t2553.md\#](/cn.zh-CN/API参考/NAT网关/ModifySnatEntry.md)|修改SNAT条目。|
|[t2552.md\#](/cn.zh-CN/API参考/NAT网关/DescribeSnatTableEntries.md)|查询已创建的SNAT条目。|
|[t2554.md\#](/cn.zh-CN/API参考/NAT网关/DeleteSnatEntry.md)|删除SNAT条目。|

## NAT带宽包

|API|说明|
|---|--|
|[t2540.md\#](/cn.zh-CN/API参考/NAT网关/CreateBandwidthPackage.md)|创建NAT带宽包。|
|[DescribeBandwidthPackages](/cn.zh-CN/API参考/NAT网关/DescribeBandwidthPackages.md)|查询NAT带宽包。|
|[ModifyBandwidthPackageSpec](/cn.zh-CN/API参考/NAT网关/ModifyBandwidthPackageSpec.md)|修改指定NAT带宽包的带宽。|
|[ModifyBandwidthPackageAttribute](/cn.zh-CN/API参考/NAT网关/ModifyBandwidthPackageAttribute.md)|修改指定NAT带宽包的名称和描述。|
|[AddBandwidthPackageIps](/cn.zh-CN/API参考/NAT网关/AddBandwidthPackageIps.md)|添加公网IP到NAT带宽包中。|
|[RemoveBandwidthPackageIps](/cn.zh-CN/API参考/NAT网关/RemoveBandwidthPackageIps.md)|删除NAT带宽包中的公网IP。|
|[DeleteBandwidthPackage](/cn.zh-CN/API参考/NAT网关/DeleteBandwidthPackage.md)|删除NAT带宽包。|

**说明：** NAT带宽包相关接口CreateBandwidthPackage、DescribeBandwidthPackages、ModifyBandwidthPackageSpec、ModifyBandwidthPackageAttribute、AddBandwidthPackageIps、RemoveBandwidthPackageIps和DeleteBandwidthPackage仅供在2017年11月3日 23:59之前账户下存在NAT带宽包的用户调用。对于在2017年11月3日23:59之前账户下不存在NAT带宽包的用户请使用弹性公网IP（EIP）。

