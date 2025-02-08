---
title: Display guide
deprecated: false
hidden: false
metadata:
  robots: index
---
JS Code Implementation Guide

<br />

<br />

<br />

1 - General Overview	2\
2 - Implementation Workflow	2
3 - Parameter Details	3
3.1 - Mandatory Parameters	4
3.2 - Highly Recommended Parameters	5
3.3 - Level Parameters — Detailed Explanation	6
3.3.a - Level Parameters — Adding Additional Parameters	7
3.3.b - Level Parameters — Exceptions	9
4 - JS Code Implementation	10
4.1 - SDK Implementation	11
4.2 - Top-Page Implementation	11
4.3 - Server/Platform Implementation	11
5 - JS Code Basic Example	12

<br />

<br />

<br />

1 - General Overview\
The Protected Media solution is designed to integrate and co-exist with your existing advertising campaigns, collecting ad-impression data.
By integrating the Protected Media solution, you will be able to get near-real-time information about interactions with your ad. This data can be formed into actionable items to help increase the value of your ads.

<br />

<br />

2 - Implementation Workflow\
The below steps outline the process of modifying and implementing Protected Media’s JS code within your system.
Please review the guide carefully while giving special attention to the various parameters.

<br />

Copy the JS code (located below in the Code Example section) into a simple text editor (i.e. Notepad).\
Replace the various parameters with your own values.
Send the modified JS code to your Sales Engineer or Technical Account Manager at Protected Media for QA .
Once approved you’ll be provided with a final version of the JS code which includes your unique PID .
Implement the final version of the JS code in the desired location (landing page, ad server, or third-party platform).
Shortly after implantation, the data will be available on the Protected Media’s dashboard.

<br />

<br />

3 - Parameter Details

<br />

Parameter values are used to configure the report’s dimensions available on the Protected Media dashboard and allow further data analysis when needed.\
The actual fraud detection decisions are always performed by Protected Media’s algorithm, regardless of the mandatory parameter settings in the JS.

<br />

<br />

<br />

<br />

3.1 - Mandatory Parameters\
The below parameters will be used as the report’s dimensions in the Protected Media dashboard and CSV reports and therefore, replacing them with your own values is mandatory.

<br />

Parameter Name\
Description
Remarks
pid
Your partner ID.
Fixed value.
Provided by Protected Media
tid
Your traffic ID.
Fixed value per traffic source.

<br />

High level report organization such as platform name, department. traffic type is required to be labeled using one or more of the following labels:
\_InAPP
\_MW
\_Desktop
\_Video
\_Video\_Auto\_Play
\_Video\_Click\_To\_Play
l1-l6
Your main grouping for data to collect and analyze.
These parameters are used to further break down the reports and can be viewed in your aggregated reports

<br />

<br />

The level (l1-l6)  parameters determine the report’s hierarchy.\
It is recommended and most common to include two or three such parameter values, but up to six can be used.
If you want to add more (the example code shows the default l1 and l2), simply add \&l3=value, for example
pub\_app
Mobile app name where your ad is displayed, including the package name/bundle name (e.g., com.facebook.katana)
Applicable for mobile application ads only

<br />

<br />

pub\_domain\
Domain name in which the ad is displayed (e.g., cnn.com)
Applicable for ads viewed via browser (mobile or web)
only

<br />

<br />

3.2 - Highly Recommended Parameters
The below parameters are highly recommended as they increase Protected Media’s detection capabilities (ref, pub\_app, and pub\_domain) and allow further data analysis when needed (utid, uid, uip, and cb).

<br />

Parameter Name\
Description
Remarks
ref
Referrer URL
The webpage that referred the user to your advertisement
utid
Unique Transaction ID
An ID that enables both Protected Media and you to locate the relevant impression or transaction for investigation purposes
uid
Unique User ID
An ID that enables you to identify and track your users
uip
User IP
User IP address
pub\_ua
User Agent
The user agent of the device
cb
Cachebuster
A unique string that verifies your users are served by Protected Media servers
adid

<br />

<br />

\*explanation below!\
Unique id for the ad element

<br />

\*explanation below!\
if you are running on the top page add the element’s html ID attribute so we will only check the viewability of this specific element and also track adclick function if you used it.

<br />

auto\_refresh
Auto Refresh Indicator
Value of ‘1’ indicates that this placement will be periodically refreshed by default
continuous\_play
Continuous Play Indicator
Value of ‘1’ indicates that content will play automatically after the end of previous content without user interaction.
creative\_type

<br />

Creative Indicator

<br />

Values of “display”, “click-to-play-video”, “autoplay-video”, “forced-duration-video”, “audio” to indicate the type of creative

<br />

<br />

pub\_ts\
Epoch UTC Timestamp of the transaction
1602296413
traffic\_source\_type
Traffic Source Type
Values of “organic”, “affiliate”, “referral”, “search” and “purchased”
\*Description of Traffic Source values is below.
\*\*\*     tt=g
Traffic type = Google
Passing the value “g” represents Google’s traffic, assuring no cookie is dropped (per TCF guidelines)

<br />

\*Description of Traffic Source values:

<br />

<br />

\*\*\* Privacy Supporting Feature: Protected Media has adopted the IAB Transparency and Consent Framework v2.0 (TCF Document), which supports and facilitates GDPR and ePrivacy compliance in the digital advertising chain.\
In order to support you in your compliance with applicable data protection laws and regulations, Protected Media offers you an option to run Protected scan without cookies and local storage usage by adding 'tt=g'  to your Protected integration, if required by applicable data protection laws and regulations.

<br />

3.3 - Level Parameters — Detailed Explanation
As different companies have different data grouping needs, Protected Media enables you to determine what will be your reporting dimensions within the Protected Media dashboard and the CSV reports. This is done by utilizing the level parameters within the JS code.
Up to six dimensions can be used in this manner in addition to the pid parameter.
For example, many orginaztions use the l1, l2, and l3 level parameters to pass their publisherID, campaignID, and domain and use them as report dimensions.
In such a case, the level (l) section in the pixel will resemble the following:
l1=PublisherID\&l2=CampaignID\&l3=DOMAIN
Or when populated with data:
l1=129501\&l2=1234\&l3=abc.com

<br />

3.3.a - Level Parameters — Adding Additional Parameters\
The basic example JS code contains l1,l2 and parameters by default (highlighted):

\<script type="text/javascript" src="https\://js.ad-score.com/score.min.js?pid=\[YOUR\_PID]\&tt=g#tid=display-ad\&l1=group1\&l2=group2\&ref=referrer\&pub\_app=app-bundle\&pub\_domain=domain\&utid=uniquetransaction\_id\&uid=user\_id\&uip=user\_ip\&pub\_ua=user\_agent\&cb=cachebuster\&auto\_refresh=0\&continuous\_play=0\&creative\_type=display" async=1  >\</script> \<noscript>\<img src="https\://data.ad-score.com/img?s=ns\&pid=\[YOUR\_PID]\&tt=g\&tid=display-ad\&l1=group1\&l2=group2\&ref=referrer\&pub\_app=app-bundle\&pub\_domain=domain\&utid=uniquetransaction\_id\&uid=user\_id\&uip=user\_ip\&pub\_ua=user\_agent\&cb=cachebuster\&auto\_refresh=0\&continuous\_play=0\&creative\_type=display" width="1" height="1" >\</noscript>


If you would like to add l3 as an additional reporting dimension simply add \&l3=group3, as shown below (highlighted):

\<script type="text/javascript" src="https\://js.ad-score.com/score.min.js?pid=\[YOUR\_PID]\&tt=g#tid=display-ad\&l1=group1\&l2=group2\&l3=group3\&ref=referrer\&pub\_app=app-bundle\&pub\_domain=domain\&utid=uniquetransaction\_id\&uid=user\_id\&uip=user\_ip\&pub\_ua=user\_agent\&cb=cachebuster\&auto\_refresh=0\&continuous\_play=0\&creative\_type=display" async=1  >\</script> \<noscript>\<img src="https\://data.ad-score.com/img?s=ns\&pid=\[YOUR\_PID]\&tt=g\&tid=display-ad\&l1=group1\&l2=group2\&l3=group3\&ref=referrer\&pub\_app=app-bundle\&pub\_domain=domain\&utid=uniquetransaction\_id\&uid=user\_id\&uip=user\_ip\&pub\_ua=user\_agent\&cb=cachebuster\&auto\_refresh=0\&continuous\_play=0\&creative\_type=display" width="1" height="1" >\</noscript>



If you would like to add the tt=g parameter (highlighted):

\<script type="text/javascript" src="https\://js.ad-score.com/score.min.js?pid=\[YOUR\_PID]\&tt=g#tid=display-ad\&l1=group1\&l2=group2\&l3=group3\&ref=referrer\&pub\_app=app-bundle\&pub\_domain=domain\&utid=uniquetransaction\_id\&uid=user\_id\&uip=user\_ip\&pub\_ua=user\_agent\&cb=cachebuster\&auto\_refresh=0\&continuous\_play=0\&creative\_type=display" async=1  >\</script> \<noscript>\<img src="https\://data.ad-score.com/img?s=ns\&pid=\[YOUR\_PID]\&tt=g\&tid=display-ad\&l1=group1\&l2=group2\&l3=group3\&ref=referrer\&pub\_app=app-bundle\&pub\_domain=domain\&utid=uniquetransaction\_id\&uid=user\_id\&uip=user\_ip\&pub\_ua=user\_agent\&cb=cachebuster\&auto\_refresh=0\&continuous\_play=0\&creative\_type=display" width="1" height="1" >\</noscript>



\*\*\*Note:&#x20;
The \&tt=g parameter is used for Google traffic and must be used if you’re scanning Google. For further information, please read more about the TCF initiative here.




In case you would like to use all six levels as reporting dimensions:
\<script type="text/javascript" src="https\://js.ad-score.com/score.min.js?pid=\[YOUR\_PID]#tid=display-ad& l1=group1\&l2=group2\&l3=group3\&l4=group4\&l5=group5\&l6=group6\&ref=referrer\&pub\_app=app-bundle\&pub\_domain=domain\&utid=uniquetransaction\_id\&uid=user\_id\&uip=user\_ip\&pub\_ua=user\_agent\&cb=cachebuster" async=1  >\</script> \<noscript>\<img src="https\://data.ad-score.com/img?s=ns\&pid=\[YOUR\_PID]\&tid=display-ad\&l1=group1\&l2=group2\&l3=group3\&l4=group4\&l5=group5\&l6=group6\&ref=referrer\&pub\_app=app-bundle\&pub\_domain=domain\&utid=uniquetransaction\_id\&uid=user\_id\&uip=user\_ip\&pub\_ua=user\_agent\&cb=cachebuster\&auto\_refresh=0\&continuous\_play=0\&creative\_type=display"" width="1" height="1" >\</noscript>


3.3.b - Level Parameters — Exceptions
There are cases where one or more of the level parameters should be reserved and therefore can’t be used freely:

Client-generated internal activity - in case you'd like to run internal traffic, such as for your own internal quality checks it is recommended to flag it with a distinct parameter, such as adding 'QA' to the 'l6' parameter.
Set \&uid= param after the session already started
try\{
adScore('set','uid',\{},
\{
pid:'1000XXX',&#x20;
adid:'adid-is-must-for-multiple-ads-in-one-page' ,&#x20;
uid:'12345678'
});
}catch(e)\{}

When using the click\_tracking integration the l5 parameter should equal ‘click’ and l6 ‘install’.
In cases where Protected Media’s JS is used within an application loading screen, the l6 parameter should equal ASA (i.e.  \&l6=ASA).
Prefetch / Prerender - When applying Prefetch / Prerender techniques, l6 should equal ‘pm\_render’
It is encouraged, but not required, that the orientation (landscape or portrait) of mobile video ads should be disclosed as part of placement-level reporting by using one of the L parameters.
JS example for sending clicks as well (BOLD text, in this example to empty l6), please remember to add adid in the JavaScript parameters above ):
\<button>
\<a href="#" onclick="try\{adScore('send','adclick',\{},\{pid:'1009898', adid:'adid-is-must-for-multiple-ads-in-one-page' , l6:'clicked'});}catch(e)\{}">
Ad Click Emulation
\</a>
\</button>



4 - JS Code Implementation
Once you receive the final JS code from your Sales Engineer or Technical Account Manager, you are ready to implement the code within your system.
Protected Media impression measurement follows a client-initiated approach for compliance with the Desktop Display Impression Guidelines.
As Protected Media does not have direct control over the premise of client-initiated counting as a third-party measurement service, we recommend following the below steps when implementing our tags as well as consulting with your Sales Engineer or Technical Account Manager to confirm proper measurement tag implementation.









4.1 - SDK Implementation&#x20;
When implementing the Protected Media JS within an SDK, clients should place the JS code&#x20;
under the Body section located in the webview html code.

\*Due to the relative complexity of  SDK integrations, please work together with your Sales Engineer or Technical Account Manager to verify correct JS tag implementation and compliance with the Mobile Application Impression Guidelines.

4.2 - Top-Page Implementation &#x20;
When implementing the Protected Media JS within the source code of an HTML webpage clients should place the JS code at the end of the Body section.
For distinctive placement measurement and reporting an Ad ID is Required.


4.3 - Server/Platform Implementation&#x20;
Implementing Protected Media’s JS code within a server or a platform is likely to vary between different platforms, but the principal implementation should always be the same.
Please locate the section within the platform where it allows you to implement a third-party tracking pixel and set the event that will trigger the JS pixel to run.

Regardless of the implementation method chosen by the client, please note - a valid ad impression may only be counted when an ad counter receives and responds to an HTTP request for a tracking asset from a client (browser).
The count must happen after the initiation of retrieval of underlying page content and only when ad content has been loaded and at minimum begins to render.
Permissible implementation techniques include (but are not limited to) HTTP requests generated by \<IMG>, \<IFRAME>, or \<SCRIPT SRC>.
For client-side ad serving, the ad content itself could be treated as the tracking asset and the ad server itself could do the ad counting as long as counting does not occur until ad content has been loaded and at a minimum begins to render.
4.4 - Integrating JS within VAST with Open Measurement SDK
By adding our JS via the VAST Extensions node or the Verifications node, it is possible to use a JS verification script via VAST in situations where the publisher and player is enabled and has an Open Measurement SDK integrated. Please refer to this page for the complete implementation guide.


5 - JS Code Basic Example
\<script type="text/javascript" src="https\://js.ad-score.com/score.min.js?pid=\[YOUR\_PID]#tid=display-ad\&l1=group1\&l2=group2\&ref=referrer\&pub\_app=app-bundle\&pub\_domain=domain\&utid=uniquetransaction\_id\&uid=user\_id\&uip=user\_ip\&cb=cachebuster" async=1  >\</script> \<noscript>\<img src="https\://data.ad-score.com/img?s=ns\&pid=\[YOUR\_PID]\&tt=g\&tid=display-ad\&l1=group1\&l2=group2\&ref=referrer\&pub\_app=app-bundle\&pub\_domain=domain\&utid=uniquetransaction\_id\&uid=user\_id\&uip=user\_ip\&pub\_ua=user\_agent\&cb=cachebuster" width="1" height="1" >\</noscript>




For any additional assistance please contact your Sales Engineer or Technical Account Manager at Protected Media