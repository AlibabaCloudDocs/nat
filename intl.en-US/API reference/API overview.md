# API overview

The following tables list the API operations available for use in NAT Gateway.

**Note:** The endpoint of the NAT Gateway API is vpc.aliyuncs.com. For more information, see the Make API calls topic in API Reference for Virtual Private Cloud \(VPC\).

## NAT gateways

|API|Description|
|---|-----------|
|[t2533.md\#](/intl.en-US/API reference/NAT Gateway/CreateNatGateway.md)|Creates a NAT gateway.|
|[ModifyNatGatewayAttribute](/intl.en-US/API reference/NAT Gateway/ModifyNatGatewayAttribute.md)|Modifies the name and description of a NAT gateway.|
|[t2535.md\#](/intl.en-US/API reference/NAT Gateway/ModifyNatGatewaySpec.md)|Changes the size of a NAT gateway.|
|[ListEnhanhcedNatGatewayAvailableZones](/intl.en-US/API reference/NAT Gateway/ListEnhanhcedNatGatewayAvailableZones.md)|Queries the zones that support enhanced NAT gateways in a specified region.|
|[UpdateNatGatewayNatType](/intl.en-US/API reference/NAT Gateway/UpdateNatGatewayNatType.md)|Upgrades a standard NAT gateway to an enhanced NAT gateway.|
|[GetNatGatewayConvertStatus](/intl.en-US/API reference/NAT Gateway/GetNatGatewayConvertStatus.md)|Queries the upgrade state of a NAT gateway.|
|[t2534.md\#](/intl.en-US/API reference/NAT Gateway/DescribeNatGateways.md)|Queries NAT gateways.|
|[t2537.md\#](/intl.en-US/API reference/NAT Gateway/DeleteNatGateway.md)|Deletes a NAT gateway.|
|[EnableNatGatewayEcsMetric](/intl.en-US/API reference/NAT Gateway/EnableNatGatewayEcsMetric.md)|Enables the traffic monitoring feature for a NAT gateway.|
|[ListNatGatewayEcsMetric](/intl.en-US/API reference/NAT Gateway/ListNatGatewayEcsMetric.md)|Views the traffic monitoring data that is collected by a NAT gateway.|
|[DisableNatGatewayEcsMetric](/intl.en-US/API reference/NAT Gateway/DisableNatGatewayEcsMetric.md)|Disables the traffic monitoring feature for a NAT gateway.|
|[ConvertBandwidthPackage](/intl.en-US/API reference/NAT Gateway/ConvertBandwidthPackage.md)|Converts a NAT service plan to an EIP bandwidth plan.|

## DNAT tables

|API|Description|
|---|-----------|
|[CreateForwardEntry](/intl.en-US/API reference/NAT Gateway/CreateForwardEntry.md)|Creates a Destination Network Address Translation \(DNAT\) entry.|
|[t2549.md\#](/intl.en-US/API reference/NAT Gateway/ModifyForwardEntry.md)|Modifies a DNAT entry.|
|[t2548.md\#](/intl.en-US/API reference/NAT Gateway/DescribeForwardTableEntries.md)|Queries DNAT entries in a DNAT table.|
|[t2550.md\#](/intl.en-US/API reference/NAT Gateway/DeleteForwardEntry.md)|Deletes a DNAT entry.|

## SNAT tables

|API|Description|
|---|-----------|
|[CreateSnatEntry](/intl.en-US/API reference/NAT Gateway/CreateSnatEntry.md)|Creates a Source Network Address Translation \(SNAT\) entry.|
|[t2553.md\#](/intl.en-US/API reference/NAT Gateway/ModifySnatEntry.md)|Modifies a SNAT entry.|
|[t2552.md\#](/intl.en-US/API reference/NAT Gateway/DescribeSnatTableEntries.md)|Queries SNAT entries in a SNAT table.|
|[t2554.md\#](/intl.en-US/API reference/NAT Gateway/DeleteSnatEntry.md)|Deletes a SNAT entry.|

