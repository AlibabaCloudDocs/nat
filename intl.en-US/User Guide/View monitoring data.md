# View monitoring data

Cloud Monitor allows you to manage NAT gateways in a more efficient way by collecting and analyzing monitoring data of NAT gateways.

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is created.

3.  On the NAT Gateway page, find the NAT gateway that you want to manage, and click ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6894140061/p41324.png) in the **Monitoring** column.

    The following table lists the monitoring metrics that can be collected based on the gateway type.

    ![Enhanced NAT gateway](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5216645951/p101525.png)

    |Gateway type|Monitoring metric|Description|
    |------------|-----------------|-----------|
    |Enhanced NAT gateway|Concurrent connections|The maximum number of concurrent TCP or UDP connections that a NAT gateway supports.|
    |Dropped connections|The number of connections dropped due to the concurrent connection limit of a NAT gateway.|
    |Rate of new connections|The maximum number of TCP or UDP connections that can be established to a NAT gateway per second.|
    |Dropped new connections|The number of new connections dropped due to the rate limit of new connections of a NAT gateway.|
    |Ratio of concurrent connections to the upper limit|The ratio of established connections to the upper limit of total connections.|
    |Ratio of new connections to the upper limit|The ratio of established new connections to the upper limit of total new connections.|
    |Inbound traffic rate|The amount of inbound traffic per second:    -   Rate of traffic from the Internet.
    -   Rate of traffic to a VPC network. |
    |Inbound traffic|The total amount of inbound traffic:    -   Traffic from the Internet.
    -   Traffic to a VPC network. |
    |Inbound packet rate|The number of inbound packets per second:    -   The rate of packets from the Internet.
    -   The rate of packets to a VPC network. |
    |Inbound packets|The total number of inbound packets:    -   Packets from the Internet.
    -   Packets to a VPC network. |
    |Outbound traffic rate|The amount of outbound traffic per second:    -   The rate of traffic from the Internet.
    -   The rate of traffic to a VPC network. |
    |Outbound traffic|The total amount of outbound traffic:    -   Traffic to the Internet.
    -   Traffic from a VPC network. |
    |Outbound packet rate|The number of outbound packets per second:    -   The rate of packets to the Internet.
    -   The rate of packets from a VPC network. |
    |Outbound packets|The number of outbound packets:    -   Packets to the Internet.
    -   Packets from a VPC network. |
    |Standard NAT gateway|SNAT connections|The number of SNAT connections of the NAT gateway.|
    |Cumulative connections discarded due to the SNAT connection limit|The specification of a NAT gateway determines the maximum number of SNAT connections supported by the NAT gateway. This metric displays the number of discarded SNAT connections when the number of SNAT connections exceeds the upper limit. **Note:** The cumulative metric cannot be cleared.

    -   If the value of this metric continues to increase for a period of time, we recommend that you upgrade your NAT gateway.
    -   If the value of this metric remains unchanged for a period of time, no SNAT connection is discarded during that period of time. |
    |Cumulative connections discarded due to the new SNAT connection limit|The specification of the NAT gateway determines the maximum number of new SNAT connections that can be created per second. This metric displays the number of discarded new SNAT connections when the number of new SNAT connections per second exceeds the upper limit. **Note:** This metric is a cumulative metric and the collected statistics cannot be cleared.

    -   If the value of this metric continues to increase for a period of time, we recommend that you upgrade your NAT gateway.
    -   If the value of this metric remains unchanged for a period of time, no new SNAT connection is discarded during that period of time. |


