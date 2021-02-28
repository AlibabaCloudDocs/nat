# Differences in API operations between enhanced NAT gateways and standard NAT gateways

This topic describes the differences in APIs operations between enhanced NAT gateways and standard NAT gateways.

## CreateNatGateway

Before you call the [CreateNatGateway](/intl.en-US/API reference/NAT Gateway/CreateNatGateway.md) operation to create a NAT gateway, you must call the [ListEnhanhcedNatGatewayAvailableZones](/intl.en-US/API reference/NAT Gateway/ListEnhanhcedNatGatewayAvailableZones.md) operation to query the zones that support enhanced NAT gateways in a specified region. Then, create a vSwitch or select a vSwitch that has idle IP addresses in the zone.

|Item|Enhanced NAT gateway|Standard NAT gateway|
|----|--------------------|--------------------|
|How the API operation is called|The operation is asynchronous.CreateNatGateway is an asynchronous operation. After you make a request, the ID of an enhanced NAT gateway is returned but the specified NAT gateway is not created. The system creates the NAT gateway in the background. You can call the [DescribeNatGateways](/intl.en-US/API reference/NAT Gateway/DescribeNatGateways.md) operation to query the state of the enhanced NAT gateway.

-   **Creating**: indicates that the system is creating the enhanced NAT gateway. You can only query the state of the NAT gateway. You cannot perform other operations on the NAT gateway.
-   **Available**: indicates that the enhanced NAT gateway is created.

|The operation is synchronous.|
|Request parameters|The following parameters are added:-   **VswitchId**: required.
-   **NatType**: required.
-   **InternetChargeType**: optional.

|N/A|

## DescribeNatGateways

The following table describes the differences in response parameters of the [DescribeNatGateways](/intl.en-US/API reference/NAT Gateway/DescribeNatGateways.md) operation between enhanced NAT gateways and standard NAT gateways.

|Parameter|Enhanced NAT gateway|Standard NAT gateway|
|---------|--------------------|--------------------|
|NatGatewayPrivateInfo|The information about the private network of the enhanced NAT gateway. Valid values:-   **EniInstanceId**: the ID of the elastic network interface \(ENI\). This parameter is of the STRING type, for example, eni-xaskc\*\*\*\*.
-   **PrivateIpAddress**: the private IP address of the enhanced NAT gateway. This parameter is of the STRING type, for example, 192.XX.XX.1.
-   **VswitchId**: the ID of the vSwitch to which the enhanced NAT gateway belongs. This parameter is of the STRING type, for example, vsw-bp1s2laxhdf9ayjbo\*\*\*\*.
-   **MaxBandwidth**: the maximum bandwidth of the enhanced NAT gateway. Unit: Mbit/s. This parameter is of the INTEGER type, for example, 5120.
-   **IzNo**: the zone where the enhanced NAT gateway is created. This parameter is of the STRING type, for example, cn-hangzhou-b.

|N/A|
|Status|The state of the enhanced NAT gateway. Valid values:-   **Creating**: After you send a request to create an enhanced NAT gateway, the system creates the NAT gateway in the background. The NAT gateway remains in the **Creating** state until the operation is complete.
-   **Modifying**: After you send a request to modify an enhanced NAT gateway, the system modifies the NAT gateway in the background. The NAT gateway remains in the **Modifying** state until the operation is complete.
-   **Deleting**: After you send a request to delete an enhanced NAT gateway, the system deletes the NAT gateway in the background. The NAT gateway remains in the **Deleting** state until the operation is complete.

|**Available**: After the enhanced NAT gateway is created, the state of the enhanced NAT gateway changes to Available.|
|NatType|**Enhanced**: an enhanced NAT gateway.|**Normal**: a standard NAT gateway.|
|InternetChargeType|-   **PayBySpec**: billed on a pay-by-specification basis.
-   **PayByLcu**: billed on a pay-by-LCU basis.

|N/A|

## ModifyNatGatewaySpec

The following table describes the differences in the [ModifyNatGatewaySpec](/intl.en-US/API reference/NAT Gateway/ModifyNatGatewaySpec.md) operation between enhanced NAT gateways and standard NAT gateways.

|Enhanced NAT gateway|Standard NAT gateway|
|--------------------|--------------------|
|The operation is asynchronous.ModifyNatGatewaySpec is an asynchronous operation. After you make a request, the ID of the request is returned but the enhanced NAT gateway is not modified. The system modifies the NAT gateway in the background. You can call the [DescribeNatGateways](/intl.en-US/API reference/NAT Gateway/DescribeNatGateways.md) operation to query the state of the enhanced NAT gateway.

-   **Modifying**: indicates that the system is modifying the enhanced NAT gateway. You can only query the state of the NAT gateway, but cannot perform other operations.
-   **Available**: indicates that the enhanced NAT gateway is modified.

|The operation is synchronous.|

## DeleteNatGateway

The following table describes the differences in the [DeleteNatGateway](/intl.en-US/API reference/NAT Gateway/DeleteNatGateway.md) operation between enhanced NAT gateways and standard NAT gateways.

|Enhanced NAT gateway|Standard NAT gateway|
|--------------------|--------------------|
|The operation is asynchronous.DeleteNatGateway is an asynchronous operation. After you make a request, the ID of the request is returned but the enhanced NAT gateway is not deleted. The system deletes the NAT gateway in the background. You can call the [DescribeNatGateways](/intl.en-US/API reference/NAT Gateway/DescribeNatGateways.md) operation to query the state of the enhanced NAT gateway.

-   **Deleting**: indicates that the system is deleting the enhanced NAT gateway. You can only query the state of the NAT gateway, but cannot perform other operations.
-   If the returned NAT gateway list is empty in the response, the enhanced NAT gateway is deleted.

|The operation is synchronous.|

## New API operations for enhanced NAT gateways

|API|Description|
|---|-----------|
|[ListEnhanhcedNatGatewayAvailableZones](/intl.en-US/API reference/NAT Gateway/ListEnhanhcedNatGatewayAvailableZones.md)|Queries the zones that support enhanced NAT gateways in a specified region.|
|[UpdateNatGatewayNatType](/intl.en-US/API reference/NAT Gateway/UpdateNatGatewayNatType.md)|Upgrades a standard NAT gateway to an enhanced NAT gateway.|
|[GetNatGatewayConvertStatus](/intl.en-US/API reference/NAT Gateway/GetNatGatewayConvertStatus.md)|Queries the upgrade state of an enhanced NAT gateway.|
|[EnableNatGatewayEcsMetric](/intl.en-US/API reference/NAT Gateway/EnableNatGatewayEcsMetric.md)|Enables the traffic monitoring feature for an enhanced NAT gateway.|
|[ListNatGatewayEcsMetric](/intl.en-US/API reference/NAT Gateway/ListNatGatewayEcsMetric.md)|Queries the traffic monitoring data that is collected by an enhanced NAT gateway.|

