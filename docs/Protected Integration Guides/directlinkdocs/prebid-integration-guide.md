---
title: Prebid Integration Guide
deprecated: false
hidden: true
metadata:
  robots: index
---
## Intro and Overview

Protected Media will provide you with the executable. It is highly recommended that the executable will run on an environment that has a low latency between it and the bidder environment, in order to minimize latency. Our Prebid solution doesn't have to run on the same machine as your internal processes as we understand the security concerns involved, but simply close enough to your machines to lower the latency.You will be able to query the executable server-proxy using HTTP1.1 requests and receive a score on the request. It is recommended that purchased impressions are verified using our post-bid JS pixel in order to continuously update our pre-bid cache with scoring on purchased users. In case this is a fraudulent user the pre-bid will be immediately updated to prevent subsequent fraudulent impressions.A trace amount of requests will be logged for reporting under the ‘PREBID\_SAMPLE’ integration in the UI - this will provide you with detailed data on the reasons specific traffic channels were flagged, and will help you evaluate your sources.

<br />

## System Requirements

The below configuration will support 60K QPS. Additional nodes and a load-balancing mechanism should be utilized to scale above this

●  OS (minimum): CentOS 7+ / Ubuntu 16+ / Debian 8+ With at least a 4 core CPU, 8GB RAM, and 64-Bit (for maximum network throughput)

● 	Outbound (not inbound) ports required to be opened: 80, 9898, 9888

● 	200 concurrent connections to the machine with the same open HTTP 1.1 connection.Connections should be kept alive for as long as the pre-bid client is active.

● 	Pre-bid nodes should not be spawned or killed dynamically (e.g., set up as a
Docker container). This allows the nodes to maximize usage of the pre-bid cache.

● 	SSH access to the machine (for troubleshooting - recommended but not required)

## Post bid & Pre Bid

<br />

As mentioned in previous sections, the Prebid proxy is basically a cache of sampled Postbid data.Since the Prebid proxy is updated using Protected Media’s global data, it is required to run the Protected Media post-bid JS tag or IMG pixel on at least 10% of the impressions that are checked via Prebid in order to immediately update the Prebid cache. This is done by syncing the post and Prebid data using the same data structure in pre-bid requests and post-bid impressions. In order for the data to sync successfully, you should simply use the same macros and their values per session both on the Prebid and on the Postbid.

## Implementation & constraints

<br />

**Step 1 - Adjust machine limits**1.a. Append the below towards the end of `/etc/security/limits.conf`

```
* hard nofile 1048576 
* soft nofile 1048576 
root hard nofile 1048576 
root soft nofile 1048576 
```

1.b. Create the following file /etc/sysctl.d/prebid-sysctl.conf and the below

```
fs.file-max = 1048576
```

1.c. reboot

**Step 2  - Install the Pre-bid Proxy**

```
curl "http://CUSTOMER_PID.s2s.ad-score.com/archive/proxy/install.sh?k=CUSTOMER_KEY&pid=CUSTOMER_PID" | bash 
```

CUSTOMER\_PID and CUSTOMER\_KEY will be provided by Protected Media.

<br />

## Structure of Requests and Responses

### Requests

Constraints:

* The full request must not exceed 8kb of size.
* <br />

The URL and all parameters \*\*must \*\*be in lower case (i.e, tid and not TID)

* The following characters are \*\*forbidden \*\*as parameter values: #, @, =, ;. All other characters are allowed, including upper and lower case characters.
* Each parameter value in this example \*\*must \*\*be replaced with your own value. These values are most commonly macros that populate the value per impression. The third-party platform of your choice should have a list of corresponding parameters.

### Request Parameters

All parameters must be encoded. Can be done via curl:

```
curl -G "http://127.0.0.1:9898/v2/s2s" --data-urlencode "pid=CUSTOMER_PID" --data-urlencode "k=CUSTOMER_KEY" --data-urlencode "otherparam=VALUE"
```

**Data passed within pre-bid request parameters should match the data used for post-bid.**