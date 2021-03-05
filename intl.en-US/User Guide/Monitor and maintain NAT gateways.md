---
keyword: [NAT gateway, enhanced, network address translation, Internet-facing services, Internet access]
---

# Monitor and maintain NAT gateways

This topic describes how to use Cloud Monitor to monitor NAT gateways. You can use Cloud Monitor to monitor NAT gateways and collect monitoring data of NAT gateways in near real time. In the NAT Gateway console, you can troubleshoot issues that may occur on your NAT gateways based on the time sequence curves that are generated by Cloud Monitor.

![Enhanced NAT gateway](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5216645951/p101525.png)

## Query monitoring data

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to manage and click the ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6894140061/p41324.png) icon in the **Monitoring** column.

    The monitoring metrics vary based on the types of NAT gateways.

    |Metric category|Monitoring metric|Description|
    |---------------|-----------------|-----------|
    |SNAT session statistics|Concurrent connections|The maximum number of concurrent Transmission Control Protocol \(TCP\) or User Datagram Protocol \(UDP\) connections that are supported by a NAT gateway.|
    |Rate of concurrent connections dropped|The rate of concurrent connections that are dropped due to the limit of concurrent connections to a NAT gateway.|
    |Rate of new connections established and rate of new connections dropped|Rate of new connections established: the number of TCP or UDP connections that are established to a NAT gateway per second.Rate of new connections dropped: the number of new connections that are dropped per second due to the limit of new connections that can be established to a NAT gateway per second. |
    |Ratio of concurrent connections and ratio of new connections|Ratio of concurrent connections: the ratio of established connections to the upper limit of connections.Ratio of new connections: the ratio of established new connections to the upper limit of new connections. |
    |Inbound traffic statistics|Inbound traffic rate|The amount of inbound traffic per second:    -   Rate of traffic from the Internet.
    -   Rate of traffic to a virtual private cloud \(VPC\). |
    |Inbound traffic|The total amount of inbound traffic:    -   Traffic from the Internet.
    -   Traffic to a VPC. |
    |Inbound packet rate|The number of inbound packets per second:    -   Rate of packets from the Internet.
    -   Rate of packets to a VPC. |
    |Inbound packets|The total number of inbound packets:    -   Packets from the Internet.
    -   Packets to a VPC. |
    |Outbound traffic statistics|Outbound traffic rate|The amount of outbound traffic per second:    -   Rate of traffic to the Internet.
    -   Rate of traffic from a VPC. |
    |Outbound traffic|The total amount of outbound traffic:    -   Traffic to the Internet.
    -   Traffic from a VPC. |
    |Outbound packet rate|The number of outbound packets per second:    -   Rate of packets to the Internet.
    -   Rate of packets from a VPC. |
    |Outbound packets|The number of outbound packets:    -   Packets to the Internet.
    -   Packets from a VPC. |

    |Monitoring metric|Description|
    |-----------------|-----------|
    |SNAT connections|The number of Source Network Address Translation \(SNAT\) connections to the NAT gateway per minute.|
    |Connections dropped due to the upper limit|The size of a NAT gateway determines the maximum number of SNAT connections supported by the NAT gateway. This metric displays the number of SNAT connections that are dropped when the upper limit of SNAT connections is reached. **Note:** This metric is cumulative and the collected statistics cannot be cleared.

    -   If the value of this metric continues to increase within a period of time, we recommend that you upgrade your NAT gateway.
    -   If the value of this metric remains unchanged within a period of time, the upper limit of SNAT connections is not reached. Therefore, no SNAT connection is dropped. |
    |Connections dropped due to the rate limit|The size of a NAT gateway determines the maximum number of new SNAT connections that can be established to the NAT gateway per second. This metric displays the number of new SNAT connections that are dropped when the upper limit of new SNAT connections per second is reached. **Note:** This metric is cumulative and the collected statistics cannot be cleared.

    -   If the value of this metric continues to increase within a period of time, we recommend that you upgrade your NAT gateway.
    -   If the value of this metric remains unchanged within a period of time, the upper limit of new SNAT connections per second is not reached. Therefore, no new SNAT connection is dropped. |


## Query the monitoring data of EIPs that are associated with NAT gateways

1.  Log on to the [NAT Gateway console](https://vpc.console.aliyun.com/nat).

2.  In the top navigation bar, select the region where the NAT gateway is deployed.

3.  On the **NAT Gateway** page, find the NAT gateway that you want to manage and click **Manage** in the **Actions** column.

4.  Click the **Monitoring** tab.

5.  Click the **Associated EIP** tab to view the monitoring metrics.

    |Monitoring metric|Description|
    |-----------------|-----------|
    |Inbound bandwidth|The bandwidth for traffic from the Internet to an Elastic Compute Service \(ECS\) instance. Unit: bit/s.|
    |Outbound bandwidth|The bandwidth for traffic from an ECS instance to the Internet. Unit: bit/s.|
    |Inbound packet rate|The number of packets sent from the Internet to an ECS instance per second.|
    |Outbound packet rate|The number of packets sent from an ECS instance to the Internet per second.|
    |Packet loss rate due to the rate limit|The rate of packets that are dropped due to the upper limit of packets that can be transmitted per second.|
    |Inbound bandwidth usage|The bandwidth usage of inbound traffic from the Internet to an ECS instance.|
    |Outbound bandwidth usage|The bandwidth usage of outbound traffic from an ECS instance to the Internet.|


## Create an alert rule

You can create alert rules to monitor the usage and states of NAT gateways in real time. This ensures the stability of your workloads.

1.  Log on to the[Cloud Monitor console](https://cms-intl.console.aliyun.com).

2.  In the left-side navigation pane, choose **Alerts** \> **Alert Rules**.

3.  On the **Threshold Value Alarm** tab, click **Create Alarm Rule**.

4.  On the **Create Alert Rule** page, set the parameters for an alert rule.

    |Parameter|Description|
    |---------|-----------|
    |**Product**|The name of the service that can be monitored by Cloud Monitor. Example: enhanced\_nat\_gateway.|
    |**Resource Range**|The resources to which the alert rule is applied. Valid values:    -   **All Resources**: The alert rule is applied to all the instances of the specified service. For example, if you set the Resource Range parameter to All Resources and the alert threshold for CPU utilization to 80% for ApsaraDB for MongoDB, Cloud Monitor sends an alert when the CPU usage of an ApsaraDB for MongoDB instance exceeds 80%. If you set the **Resource Range** parameter to **All Resources**, the alert rule is applied to up to 1,000 instances. If the specified service has more than 1,000 instances, you may not receive alerts when the value of the specified metric reaches the threshold. We recommend that you add resources to application groups before you create alert rules.
    -   **Instances**: The alert rule is applied to a specific instance. For example, if you set the Resource Range parameter to Instances and the alert threshold of CPU usage to 80% for an ECS instance, Cloud Monitor sends an alert when the CPU usage of the ECS instance exceeds 80%. |
    |**Alert Rule**|The name of the alert rule.|
    |**Rule Description**|The content of the alert rule. This parameter defines the conditions that trigger an alert. For example, if the condition specifies that the average CPU utilization in 5 minutes is greater than or equal to 90% for three consecutive cycles, Cloud Monitor checks whether the condition is met for only three times every 5 minutes.|
    |**Mute for**|Specifies the mute period. If the alert is not cleared within the mute period, a new alert notification is sent when the mute period ends.|
    |**Effective Period**|The period when the alert rule takes effect. The system monitors the metrics and generates alerts only if the alert rule is effective.|
    |**Notification Contact**|The contacts or contact group to which an alert notification is sent.|
    |**Notification Methods**|Emails and DingTalk ChatBot. |
    |**Auto Scaling**|If you select **Auto Scaling**, the specified scaling rule is triggered when an alert is generated. You must set the **Region**, **ESS Group**, and **ESS Rule** parameters.    -   For more information about how to create a scaling group, see [Create a scaling group](/intl.en-US/Scaling Group/Scaling group/Create a scaling group.md).
    -   For more information about how to create a scaling rule, see [Create a scaling rule](/intl.en-US/Scaling Group/Scaling rule/Create a scaling rule.md). |
    |**Log Service**|If you select **Log Service**, the alert message is written to Log Service when an alert is generated. You must set the **Region**, **Project**, and **Logstore** parameters.For more information about how to create a project and a Logstore, see [Quick Start](/intl.en-US/.md). |
    |**Email Remark**|The custom remarks that you want to include in the alert notification email.|
    |**HTTP CallBack**|The callback URL that can be accessed over the Internet. Cloud Monitor sends a POST request to push an alert message to the specified callback URL. Only HTTP requests are supported.|

5.  Click **Confirm**.


**Related topics**  


[EnableNatGatewayEcsMetric](/intl.en-US/API reference/NAT Gateway/EnableNatGatewayEcsMetric.md)

[ListNatGatewayEcsMetric](/intl.en-US/API reference/NAT Gateway/ListNatGatewayEcsMetric.md)

[DisableNatGatewayEcsMetric](/intl.en-US/API reference/NAT Gateway/DisableNatGatewayEcsMetric.md)

[PutResourceMetricRule](/intl.en-US/API Reference/Alert service/Alert rules for time series metrics/PutResourceMetricRule.md)

[CreateGroupMetricRules](/intl.en-US/API Reference/Application groups/CreateGroupMetricRules.md)
