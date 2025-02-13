---
title: Prebid Integration Guide
deprecated: false
hidden: true
metadata:
  robots: index
---
Intro and Overview

Protected Media will provide you with the executable. It is highly recommended that the executable will run on an environment that has a low latency between it and the bidder environment, in order to minimize latency. Our Prebid solution doesn't have to run on the same machine as your internal processes as we understand the security concerns involved, but simply close enough to your machines to lower the latency.You will be able to query the executable server-proxy using HTTP1.1 requests and receive a score on the request. It is recommended that purchased impressions are verified using our post-bid JS pixel in order to continuously update our pre-bid cache with scoring on purchased users. In case this is a fraudulent user the pre-bid will be immediately updated to prevent subsequent fraudulent impressions.
A trace amount of requests will be logged for reporting under the ‘PREBID\_SAMPLE’ integration in the UI - this will provide you with detailed data on the reasons specific traffic channels were flagged, and will help you evaluate your sources.

<br />

System Requirements

<br />

The below configuration will support 60K QPS. Additional nodes and a load-balancing mechanism should be utilized to scale above this● OS (minimum): CentOS 7+ / Ubuntu 16+ / Debian 8+ With at least a 4 core CPU, 8GB RAM, and 64-Bit (for maximum network throughput)
● 	Outbound (not inbound) ports required to be opened: 80, 9898, 9888
● 	200 concurrent connections to the machine with the same open HTTP 1.1 connection.
Connections should be kept alive for as long as the pre-bid client is active.
● 	Pre-bid nodes should not be spawned or killed dynamically (e.g., set up as a
Docker container). This allows the nodes to maximize usage of the pre-bid cache.
● 	SSH access to the machine (for troubleshooting - recommended but not required)