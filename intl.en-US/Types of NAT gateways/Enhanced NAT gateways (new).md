---
keyword: [NAT gateway, enhanced, network address translation, receive requests from the Internet, access the Internet]
---

# Enhanced NAT gateways \(new\)

Enhanced NAT gateways are upgraded from the technical architecture of standard NAT gateways. Compared with standard NAT gateways, enhanced NAT gateways offer higher elasticity and stability. This helps you manage data transfer in a more efficient way.

## Features

Enhanced NAT gateways are upgraded from the technical architecture of standard NAT gateways and have the following features: higher performance, higher elasticity, flexible billing, and fine-grained maintenance.

![Features](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0082659951/p147923.png)

## Benefits

Both enhanced NAT gateways and standard NAT gateways support basic features such as destination network address translation \(DNAT\) and source network address translation \(SNAT\) for Internet access. Enhanced NAT gateways provide new features in addition to the features of standard NAT gateways. The new features include:

-   More metrics for data transfer monitoring

    Up to 22 metrics are collected for you to monitor data transfer in real time. This helps you ensure system stability. For more information, see [Use Cloud Monitor to monitor NAT gateways](/intl.en-US/User Guide/Use Cloud Monitor to monitor NAT gateways.md).

-   Multiple NAT gateways for one virtual private cloud \(VPC\)

    You can create multiple enhanced NAT gateways for one VPC to forward traffic to different IP addresses. Then, you can better manage traffic destined for the Internet. You can also use different services to protect each gateway based on your requirements.

    You can create the same SNAT entry or DNAT entry on different NAT gateways and configure routes to forward outbound traffic from a specified NAT gateway.

    **Note:**

    -   To replace a standard NAT gateway with an enhanced NAT gateway, you must reconfigure the routes. This may cause transient connection errors. We recommend that you reconfigure the routes during off-peak hours.
    -   If you created both SNAT and DNAT entries on the enhanced NAT gateway, the Elastic Compute Service \(ECS\) instances cannot use SNAT to access services that use DNAT of the same enhanced NAT gateway to provide external access in the same VPC. If you want the ECS instances to access the services that use DNAT to provide external access in the same VPC, we recommend that you create another enhanced NAT gateway. Then, create DNAT entries on one NAT gateway and create SNAT entries on the other NAT gateway. For more information, see [t1997525.md\#]().

## Manage enhanced NAT gateways

Enhanced NAT gateways are used in the same way as standard NAT gateways. However, when you create an enhanced NAT gateway, you must specify the type of the gateway and configure the VPC and vSwitch to be associated with the enhanced NAT gateway. After the enhanced NAT gateway is created, the system assigns an idle private IP address from the vSwitch to the enhanced NAT gateway.

-   For more information about how to create an enhanced NAT gateway, see [t2003027.md\#]().
-   You can purchase a NAT gateway and EIPs at the same time. After you create a NAT gateway and EIPs, the system automatically associates the EIPs with the NAT gateway. For more information, see [Purchase a NAT gateway and EIPs at the same time]().

**Related topics**  


[t2005535.md\#]()

[t2005557.md\#]()

