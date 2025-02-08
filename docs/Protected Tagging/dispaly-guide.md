---
title: Display Creatives
deprecated: false
hidden: false
metadata:
  robots: index
---
## General Overview

The Protected Media solution is designed to integrate and co-exist with your existing advertising campaigns, collecting ad-impression data.\
By integrating the Protected Media solution, you will be able to get near-real-time information about interactions with your ad. This data can be formed into actionable items to help increase the value of your ads.

## Implementation

The below steps outline the process of modifying and implementing Protected Media’s JS code within your system.
Please review the guide carefully while giving special attention to the various parameters.

Copy the JS code (located below in the Code Example section) into a simple text editor (i.e. Notepad).\
Replace the various parameters with your own values.
Send the modified JS code to your Sales Engineer or Technical Account Manager at Protected Media for QA .
Once approved you’ll be provided with a final version of the JS code which includes your unique PID .
Implement the final version of the JS code in the desired location (landing page, ad server, or third-party platform).
Shortly after implantation, the data will be available on the Protected Media’s dashboard.

## Parameter Details

Parameter values are used to configure the report’s dimensions available on the Protected Media dashboard and allow further data analysis when needed.\
The actual fraud detection decisions are always performed by Protected Media’s algorithm, regardless of the mandatory parameter settings in the JS.

## Mandatory Parameters

The below parameters will be used as the report’s dimensions in the Protected Media dashboard and CSV reports and therefore, replacing them with your own values is mandatory.

<br />

| Parameter Name            | Description                                           | Remarks                                                                                                                                                                                                        |
| ------------------------- | ----------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ref**                   | **Referrer URL**                                      | **The webpage that referred the user to your advertisement**                                                                                                                                                   |
| **utid**                  | **Unique Transaction ID**                             | **An ID that enables both Protected Media and you to locate the relevant impression or transaction for investigation purposes**                                                                                |
| **uid**                   | **Unique User ID**                                    | **An ID that enables you to identify and track your users**                                                                                                                                                    |
| **uip**                   | **User IP**                                           | **User IP address**                                                                                                                                                                                            |
| **pub\_ua**               | **User Agent**                                        | **The user agent of the device**                                                                                                                                                                               |
| **cb**                    | **Cachebuster**                                       | **A unique string that verifies your users are served by Protected Media servers**                                                                                                                             |
| **adid**                  | **\*explanation below! Unique id for the ad element** | **\*explanation below! if you are running on the top page add the element’s html ID attribute so we will only check the viewability of this specific element and also track adclick function if you used it.** |
| **auto\_refresh**         | **Auto Refresh Indicator**                            | **Value of ‘1’ indicates that this placement will be periodically refreshed by default**                                                                                                                       |
| **continuous\_play**      | **Continuous Play Indicator**                         | **Value of ‘1’ indicates that content will play automatically after the end of previous content without user interaction.**                                                                                    |
| **creative\_type**        | **Creative Indicator**                                | **Values of “display”, “click-to-play-video”, “autoplay-video”, “forced-duration-video”, “audio” to indicate the type of creative**                                                                            |
| **pub\_ts**               | **Epoch UTC Timestamp of the transaction**            | **1602296413**                                                                                                                                                                                                 |
| **traffic\_source\_type** | **Traffic Source Type**                               | **Values of “organic”, “affiliate”, “referral”, “search” and “purchased” \*Description of Traffic Source values is below.**                                                                                    |