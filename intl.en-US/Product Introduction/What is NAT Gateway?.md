---
keyword: [NAT Gateway, Internet access, SNAT, DNAT]
---

# What is NAT Gateway?

NAT gateways are enterprise-class gateways that provide the Source Network Address Translation \(SNAT\) and Destination Network Address Translation \(DNAT\) features. Each NAT gateway provides a throughput capacity of up to 100 Gbit/s. NAT gateways also support cross-zone disaster recovery.

![Diagram](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8604485061/p4440.png)

## Features

You must associate public IP addresses with NAT gateways so that the NAT gateways can function as expected. After you create a NAT gateway, you can associate elastic IP addresses \(EIPs\) with the NAT gateway.

**Note:** If you purchased a NAT service plan before January 26, 2018, you can associate only the public IP addresses in the NAT service plan with your NAT gateway to enable Internet access. To associate EIPs with your NAT gateway, you must convert the NAT service plan to an EIP bandwidth plan. For more information, see [Convert a NAT service plan to an EIP bandwidth plan](/intl.en-US/Bandwidth Package (Archive)/Convert a NAT service plan to an EIP bandwidth plan.md).

NAT gateways provide the SNAT and DNAT features.

|Feature|Description|Reference|
|-------|-----------|---------|
|SNAT|SNAT allows Elastic Compute Service \(ECS\) instances that are deployed in a virtual private cloud \(VPC\) to access the Internet when no public IP address is associated with these ECS instances.|[Use SNAT to enable Internet access](/intl.en-US/Quick Start/Use SNAT to enable Internet access.md)|
|DNAT|DNAT maps the EIPs of a NAT gateway to ECS instances. This way, the ECS instances can receive requests from the Internet.|[Allow ECS instances to provide Internet-facing services by using DNAT](/intl.en-US/Quick Start/Allow ECS instances to provide Internet-facing services by using DNAT.md)|

