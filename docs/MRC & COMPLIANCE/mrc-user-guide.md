---
title: MRC User Guide
excerpt: Protected Media’s journey to MRC accreditation & what it means
deprecated: false
hidden: false
metadata:
  robots: index
---
The introduction of the new interface components represents the final steps towards Protected Media joining a limited number of global traffic verification solutions providers, who are accredited by the Media Rating Council (MRC).

**What is the MRC and what does the accreditation mean?**

<br />

The Media Rating Council (MRC) is a United States-based nonprofit organization that manages accreditation for media research and rating purposes. By using a verification partner that is MRC accredited, your customers will be able to compare fraud and viewability rates using a standard metric, as defined by the industry and regulated by a centralized body - the MRC.

In this section, we’ll display measurements per the MRC requirements, including:\*Gross Impressions
(different from total transactions which we use to bill our clients and represent a call to our JS this metric represents a count of BTR - compliant impressions meaning impressions that began rendering on the user’s browser

<br />

**GIVT - ‘General Invalid Traffic,’ consist\[s] of traffic identified through routine means of filtration executed through the application of lists or with other standardized parameter checks.**

**SIVT – “Sophisticated Invalid Traffic,’ consists of more difficult to detect situations that require advanced analytics, multi-point corroboration/coordination, significant human intervention, etc., to analyze and identify.”**

Don’t be a stranger!

We hope that you enjoy using this version of the MRC accredited Fraud Detection solution - please make sure to send all of your feedback to your account manager \[email] and let us know what you think!

\*Please note that the MRC accredited measurement is only applicable to ads running our JavaScript/IMG and excludes any other implementations.

**Metrics**

**Tracked Ads**

Events which do not meet client-initiated, Begin-to-Render minimum requirements, are disclosed as Tracked Ads and disclaimed from accreditation.

* Tracked Ads- All transactions on MRC scope (mostly JS and IMG impressions that are not SSAI)
* GIVT (Tracked Ads)- Transactions in the MRC scope that are not flagged as GIVT
* SIVT (Tracked Ads)- Transactions in the MRC scope that are not flagged as GIVT or SIVT (Clean traffic, Not IVT)

**Gross Impressions**

* Gross Impressions- All rendered and active impressions (Tracked ads rendered impressions that weren't flagged by our inactivity rules)
* Net Impressions- Impressions that are flagged as gross impressions and not flagged as GIVT
* Total Net Impressions- Impressions that are flagged as gross impressions and not flagged as  GIVT or SIVT
* SIVT Decision Rate- Percentage of impressions that had the minimum required signals to determine SIVT decision from gross impressions.

**Viewability (Net Impressions)**

* Viewable Impressions\*- All viewable impressions from net impressions (viewable impressions that are flagged as gross impressions and not flagged as GIVT)
* Non-Viewable Impressions\*-  All non-viewable impressions from net impressions (non-viewable impressions that are flagged as gross impressions and not flagged as GIVT)
* Viewability Undetermined Impressions\*- The number of impressions that we couldn't collect enough information to decide regarding their viewability status from net impressions(Net impressions - (viewable impressions + non-viewable impressions))
* Measured Rate- The percentage of impressions that we had enough information to decide their viewability status (net impressions - undetermined impressions or viewable impressions + non-viewable impressions) from net impressions
* Median viewability (ms)- The median time that the net impressions (not GIVT) were viewable (ms)

% metrics are calculated as Distribution (from net impressions)

Viewability (Total Net Impressions)

* Viewable Impressions\*- All viewable impressions from total net impressions (viewable impressions that are flagged as gross impressions and not flagged as GIVT or SIVT)
* Non-Viewable Impressions\*- All non-viewable impressions from net impressions (non-viewable impressions that are flagged as gross impressions and not flagged as GIVT or SIVT)
* Viewability Undetermined Impressions\*- The number of impressions that we couldn't collect enough information to decide regarding their viewability status from total net impressions(total net impressions - (total net viewable impressions + total net undetermined impressions))
* Measured Rate- The percentage of impressions that we had enough information to decide their viewability status (total net impressions - total net undetermined impressions or total net viewable impressions + total net non-viewable impressions) from total net impressions
* Viewable rate- The percentage of the viewable impressions from measured impressions.
* Median viewability (ms)- The median time that the clean impressions (not GIVT or SIVT) were viewable (ms)

% metrics are calculated as Distribution (from total net impressions)