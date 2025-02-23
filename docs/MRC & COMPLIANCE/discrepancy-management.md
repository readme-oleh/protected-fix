---
title: Discrepancy management
deprecated: false
hidden: false
metadata:
  robots: index
---
The purpose of this document is to (1) raise awareness to perform Discrepancy checks, while (2) emphasize the importance of performing them accurately. At Protected Media, we view Discrepancy as an indicator of your data’s health, which must trigger an immediate analysis and drill down.

## Process Overview

The purpose of this document is to suggest a clear and practical method to analyze \*discrepancies between different platforms.

\*Discrepancy = the difference in analytical/reporting data between two parties, or more. Discrepancies can occur due to various reasons (elaborated below in the “Main causes” section).

## Why do discrepancies happen? What does it mean?

The nature of digital media, alongside the ecosystem’s structure of various players in the supply chain creates a scenario where discrepancies between different dashboards are extremely common. The discrepancy is an indicator of your data’s health, which must trigger an immediate analysis and drill down.

Nonetheless, we highly recommend monitoring and assessing the discrepancy between your different vendors proactively.

## How does it impact me?

Your actions and decisions are based on your data. For this basic reason, you must verify that your data is reliable and accurate. Otherwise, you’ll be basing your decisions on the wrong data, which can translate to significant losses.

The recommended tolerance for discrepancies is up to 10% as the industry standard. (For the IAB standards, click here).

## Important to know!

PM has no visibility into its clients’ ad server side. It is the client’s responsibility to monitor. Based on our experience, we recommend our clients take proactive steps on a biweekly basis to identify discrepancy issues between the ad server records and PM records.

## Main causes:

* Human Error - Pixel / Macro Implementation, HTML5 Creatives, Incorrect Settings (targeting, UTC, media type, etc.)
* Ad Serving Sequence - Internet Connectivity Issues/Latency, Short Session Times, Caching, Difference in Counting Methodology
* Reporting - Time Zone, Traffic Validation/Report Filtration (User Agents, Behavior Validation), No Referral URL, Server Side vs. Client Side Counting, Differences in Terminology/Definitions
* Targeting - Targeting by Device Characteristics, Geo/Location Based Targeting
* Fraudulent activity - There are instances where a supply source is intentionally preventing 3rd party JS verification pixels like PM from running and detecting foul play

## Detecting and eliminating discrepancies (basic & advanced)

You’ve noticed there’s a discrepancy between different reports? Different dashboards?

## OR

You’re running your scheduled discrepancy check and found gaps in the data?

Below, you’ll find a recommended method to approach in order to gain deeper insights regarding the cause of the discrepancy.The suggested steps below are labeled as “basic” and “advanced”. We recommend approaching this research in a systematic manner, thus assuring the reliability of its outcome.

## Basic Checklist:

1. Confirm that your PM 3rd party tags were implemented properly on your end. Typos are the most common source of integration errors (we’re all humans). Please double-check and ensure the integration is set correctly.
2. If the discrepancy is across all your supply partners, it’s more likely to be an integration issue. Remember point 1 :)

## Done the above, but still have discrepancies with some partners? Let’s get actionable!

## Basic Actions:

Access the PM dashboard and perform the following: select the desired time frame (i.e “last 7 days”), choose your desired time zone, and keep the high-level parameters in place: Integration, Traffic ID, and Level 1. Remember! Your goal is to identify the disc proportion for each Supply partner. Please see the screenshot below.

<br />

Next, \*export a supply-side report from your ad server/platform of choice using the same parameters, time zone, and time frame. It’s crucial to double check and ensure the time frame and time zone are aligned across all reports! Otherwise, you won’t be able to compare reports correctly!

\*export = the export option in our dashboard (highlighted in the image above) will be ideal for these actions. Make sure that you export the parameters you actually utilize, and remove the fields without data. Unlike the dashboard, our CSV isn’t “lines limited”.

## Remember, a clean data set is a good one :)

<br />

compare the number of impressions on your ad server to the number of total transactions on the PM report. We highly recommend using the following Excel functions (VLOOKUP and MERGE) to create the best view of your data.

Make sure you use the same data on both reports (For example a specific Pub ID on a specific day). In most cases (over 90%) the discrepancy will be present on specific publisher/s. Your goal is to identify the specific partner (supply source) who generates the discrepancy. Once done, we recommend reaching out to said partners and sharing the analysis information with them in order to resolve this. With these partners, we highly recommend executing the Advanced step!
Advanced (Deep dive into the data, per partner!)

After identifying the specific partners/supply sources/pubs who generate the discrepancy, you’ll want to add additional layers of data like Environment (Inapp, Desktop, etc.) / Type (VAST, VPAID etc.) / Devices / UA / OS / SITE / PLACEMENT as well as any other data you think could assist eliminating it (For example, remove a specific Domain, Bundle, UA etc.).

The goal here is to identify a shared root cause of the discrepancy per partner.For example, we discovered cases where a discrepancy would occur only on a specific OS on Android devices. Once aware of it, the targeting for the said campaign was updated and the discrepancy was solved.

Difficulties resolving this issue? please contact your CS Manager at Protected Media for additional assistance: [support@protected.media](mailto:support@protected.media)