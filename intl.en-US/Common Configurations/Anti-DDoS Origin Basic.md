# Anti-DDoS Origin Basic

A distributed denial-of-service \(DDoS\) attack is a malicious network attack against one or more systems, which can crash the targeted network. Alibaba Cloud provides up to 5 Gbit/s of basic anti-DDoS protection for a NAT gateway free of charge. Anti-DDoS Origin Basic can effectively prevent DDoS attacks.

## How Anti-DDoS Origin Basic works

After you enable Anti-DDoS Origin Basic, traffic from the Internet must pass through Alibaba Cloud Security before the traffic arrives at the NAT gateway. Anti-DDoS Origin Basic scrubs and filters common DDoS attacks at Alibaba Cloud Security. Anti-DDoS Origin Basic protects your services against attacks such as SYN floods, UDP floods, ACK floods, ICMP floods, and DNS Query floods.

Anti-DDoS Origin Basic specifies the traffic scrubbing and blackhole triggering thresholds based on the bandwidth limit of the elastic IP address \(EIP\) that is associated with the NAT gateway. When the inbound traffic reaches the threshold, traffic scrubbing or blackhole is triggered:

-   Traffic scrubbing: When the attack traffic from the Internet exceeds the scrubbing threshold or matches the attack traffic pattern, Alibaba Cloud Security starts to scrub the attack traffic. Traffic scrubbing includes packet filtering, bandwidth capping, and traffic throttling.
-   Blackhole: When the attack traffic from the Internet exceeds the blackhole triggering threshold, blackhole is triggered and all inbound traffic is dropped.

## Traffic scrubbing and blackhole triggering thresholds

The following table describes the methods that are used to calculate the traffic scrubbing and blackhole triggering thresholds on NAT gateways.

|Bandwidth limit of the EIP|Traffic scrubbing threshold \(bit/s\)|Traffic scrubbing threshold \(pps\)|Default blackhole triggering threshold|
|:-------------------------|:------------------------------------|:----------------------------------|:-------------------------------------|
|Lower than or equal to 800 Mbit/s|800 Mbit/s|120,000|1.5 Gbit/s|
|Higher than 800 Mbit/s|Predefined bandwidth|Predefined bandwidth × 150|Predefined bandwidth × 2|

If the bandwidth limit of the EIP is 1,000 Mbit/s, the traffic scrubbing threshold \(bit/s\) is 1,000 Mbit/s, the traffic scrubbing threshold \(pps\) is 150,000, and the default blackhole triggering threshold is 2 Gbit/s.

