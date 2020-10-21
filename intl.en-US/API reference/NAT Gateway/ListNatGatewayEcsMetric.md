# ListNatGatewayEcsMetric

View the traffic monitoring data of a NAT gateway.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates a sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Vpc&api=ListNatGatewayEcsMetric&type=RPC&version=2016-04-28)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ListNatGatewayEcsMetric|The operation that you want to perform. Set the value to **ListNatGatewayEcsMetric**. |
|NatGatewayId|String|Yes|ngw-2vc53wynunp35lw1y\*\*\*\*|The ID of the NAT gateway whose traffic monitoring data you want to view.

**Note:** You can query only a single NAT gateway. |
|RegionId|String|Yes|cn-chengdu|The ID of the region to which the NAT gateway belongs. You can call the [DescribeRegions](~~36063~~) operation to query the region ID. |
|TimePoint|Long|Yes|1602653760|The timestamp of the traffic monitoring data that is accurate to the minute.

For example, to view the traffic monitoring data from 17:22:00 on 2020-07-13 to 17:23:00 on 2020-07-13, specify the timestamp at 17:22:00 on 2020-07-13. |
|DryRun|Boolean|No|false|Specifies whether to precheck only the current request. Valid values:

**true**: sends a precheck request and does not view the traffic monitoring data. The system checks whether your AccessKey pair is valid, RAM user is authorized, and required parameter values are specified. If the request fails to meet the requirements in the check items, an error message is returned. If the request passes the precheck, the `DryRunOperation` error message is returned.

**false** \(default\): checks the API request. After the request passes the check, the 2XX HTTP status code is returned, and service resources are automatically added to the endpoint service. |
|OrderKey|String|No|ActiveSessionNum|The field by which traffic monitoring data is sorted. Default value: ActiveSessionNum. |
|OrderType|String|No|desc|The sorting rule of traffic monitoring data. Valid values:

-   **desc** \(default\): The data is sorted in descending order.
-   **asc**: The data is sorted in ascending order. |
|PrivateIpAddress|String|No|192.168.0.12|The IP address of the ECS instance whose traffic monitoring data you want to view. |
|NextToken|String|No|caeba0bbb2be03f84eb48b699f0a4883|The query token. Set this parameter to the NextToken value that is returned in the last API call. If no subsequent request is sent, you do not need to set this parameter. |
|MaxResults|String|No|20|The number of entries to return on each page. Valid values:**10** to **20**. Default value: **20**. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|MaxResults|Integer|1|The number of entries to return on each page. |
|MetricDataList|Array of MetricData| |The list of traffic monitoring data. |
|ActiveSessionNum|Long|6|The number of concurrent connections per minute. Unit: connections |
|NatGatewayId|String|ngw-2vc53wynunp35lw1y\*\*\*\*|The ID of the NAT gateway whose traffic monitoring data you want to view. |
|NewSessionRate|Long|0|The new session rate. Unit: sessions/s |
|PrivateIpAddress|String|192.168.0.12|The IP address of the ECS instance whose traffic monitoring data you want to view. |
|RxBps|Long|125|Outbound bandwidth. Unit: bit/s. |
|RxPps|Long|2|Outbound data packets transferred per second. |
|Timestamp|Long|1602653760|The timestamp of the traffic monitoring data that is accurate to the minute. |
|TxBps|Long|125|Inbound bandwidth. Unit: bit/s. |
|TxPps|Long|2|Inbound data packet. Unit: count/s. |
|NextToken|String|caeba0bbb2be03f84eb48b699f0a4883|The token that is required for the next query. If the NextToken parameter is empty, no subsequent query will be sent. |
|RequestId|String|0ED8D006-F706-4D23-88ED-E11ED28DCAC0|The ID of the request. |

## Examples

Sample requests

```
https://vpc.aliyuncs.com/?Action=ListNatGatewayEcsMetric
&NatGatewayId=ngw-2vc53wynunp35lw1y****
&RegionId=cn-chengdu
&TimePoint=1602653760
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ListNatGatewayEcsMetricResponse>
  <RequestId>F3C9E92A-0BAA-4444-ABD9-4E41BADBBD3E</RequestId>
  <NextToken></NextToken>
  <MetricDataList>
        <PrivateIpAddress>192.168.0.48</PrivateIpAddress>
        <RxBps>1178</RxBps>
        <TxBps>45593</TxBps>
        <RxPps>2</RxPps>
        <TxPps>4</TxPps>
        <ActiveSessionNum>6</ActiveSessionNum>
        <NewSessionRate>0</NewSessionRate>
        <NatGatewayId>ngw-2vc53wynunp35lw1y****</NatGatewayId>
        <Timestamp>1602653760</Timestamp>
  </MetricDataList>
  <MaxResults>1</MaxResults>
</ListNatGatewayEcsMetricResponse>
```

`JSON` format

```
{
  "RequestId": "F3C9E92A-0BAA-4444-ABD9-4E41BADBBD3E",
  "NextToken": "",
  "MetricDataList": [
    {
      "PrivateIpAddress": "192.168.0.48",
      "RxBps": 1178,
      "TxBps": 45593,
      "RxPps": 2,
      "TxPps": 4,
      "ActiveSessionNum": 6,
      "NewSessionRate": 0,
      "NatGatewayId": "ngw-2vc53wynunp35lw1y****",
      "Timestamp": 1602653760
    }
  ],
  "MaxResults": 1
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Vpc).

