---
title: Description of Methodology
deprecated: false
hidden: false
metadata:
  robots: index
---
Description of MethodologyThis Description of Methodology (DOM) is a summary of the impression measurement processes employed, including a general description of our measurement methodology, filtration processes, and reporting procedures.What’s included:
Protected Media provides a cyber-security layer to ensure that every online ad – display, mobile, or video – is properly located, visible, and seen by real people. Protected Media’s Anti-Fraud solution is targeted to advertisers, agencies, ad networks, and ad servers, and is designed to integrate and co-exist with existing advertising campaigns, collecting ad-impression data and providing near-real-time information about ad interactions.
The MRC certification will incise the below metrics as well as the processes related to the logging filtration and reporting related to them. (please see the full list in page 19 - below)
\*Link to Protected Viewability DOM
\*Link to Protected Brand Safety DOMWhat’s not included:
Not included in the scope of this MRC audit (and therefore not disclosed in this DOM) are the different Fraudulent and Suspicious category metrics available to Protected Media’s clients and provide them with the different suspicious behavior detected, for example,
Advertising bots simulating human traffic
Hostile tools masking the user
Tunneled traffic masking IP/geolocation
View fraud occurs when an ad is deliberately displayed in a manner that is invisible to humans
Publisher fraud occurs when an ad is displayed on a website/application different from the one reported to the advertiser
Traffic from known fraudulent IPsAlso not included are the different Visibility metrics available to Protected Media’s clients  which provide insightful data based on additional continuous visibility checks which are performed at multiple intervals in addition to those required by the MRC standards.
There are several reasons for non-visible ads, including view fraud, zero-size ad, ad behind the ad, ad at the end of the webpage, or ad that wasn't rendered.
Protected Media indicates to the client if an ad was visible and if the ad was on the website and had not closed or crashed (time on site).Out of scope  Metrics
Fraudulent
Bot/Virus
Hostile Tools
Tunneled Traffic
Non-Malicious Bots
View Fraud
Publisher Fraud
Reputation
Suspicious
Bot/Virus
Hostile Tools
Tunneled Traffic
Non-Malicious Bots
View Fraud
Publisher Fraud
Reputation
Visibility
1
2
5
10
15
20
25
Time On-Site
1
2
5
10
15
20
25Clarification regarding Metrics naming convention
“Fraud” / equates to the MRC’s definition of IVT and does not imply fraudulent behavior or intent.Measurement Methodology
By default, Protected Media reports on a client-initiate, census basis and does not sample impressions. In line with the IAB guidelines, PM utilizes the HTTP cache-control response headers 'cache-control,  and 'expiry’.
Metrics reported by Protected Media are based on all impression activity, subject to the filtration procedures described below.
a valid ad impression may only be counted when an ad counter receives and responds to an HTTP request for a tracking asset from a client (browser). (i.e. client-initiated approach)
The count must happen after the initiation of retrieval of underlying page content and only when ad content has been loaded and at minimum begins to render.Data logging
Protected Media uses a JavaScript URL integrated as a tracking pixel within a customer’s application or creative. A user browser fetches and executes this JavaScript code, with each call representing one impression.
Tracking data is sent back to Protected Media databases currently hosted on Google Cloud. Summary data is returned hourly to either a customer dashboard or raw log files.
Cache-Busting
Each call to the Protected Media’s JS contains cache-busters including timestamps and random strings that prevent the caching of the requests by the user's browser and ensure each call is sent successfully to the PM's servers.
Tracked Parameters
The following parameters are tracked with each callParameter Name
Description
Remarks
pid
Your partner ID.
Fixed value.
Provided by Protected Media
tid
Your traffic ID.
Fixed value per traffic source.High level report organization such as platform name, department. traffic type is required to be labeled using one or more of the following labels
\_InAPP
\_MW
\_Desktop
\_Video
l1-l6
Your main grouping for data to collect and analyze.
These parameters are used to further break down the reports and can be viewed in your aggregated reportsThe level (l1-l6)  parameters determine the report’s hierarchy.
It is recommended and most common to include two or three such parameter values, but up to six can be used.If you want to add more (the example code shows the default l1 and l2), simply add \&l3=value, for examplepub\_app
Mobile app name where your ad is displayed, including the package name/bundle name (e.g., com.facebook.katana)
Applicable for mobile application ads onlyParameter Name
Description
Remarks
pub\_domain
Domain name in which the ad is displayed (e.g., cnn.com)
Applicable for ads viewed via browser (mobile or web)
only
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
cb
Cachebuster
A unique string that verifies your users are served by Protected Media serversauto\_refresh
Auto Refresh Indicator
Value of ‘1’ indicates that this placement will be periodically refreshed by default
continuous\_play
Continuous Play Indicator
Value of ‘1’ indicates that content will play automatically after the end of previous content without user interaction.creative\_typeCreative IndicatorValues of “display”, “click-to-play-video”, “autoplay-video”, “forced-duration-video”, “audio” to indicate the type of creativetraffic\_source\_type
Traffic Source Type
Values of “organic”, “affiliate”, “referral”, “search” and “purchased”\*Explanation for each value is mentioned below.“Traffic source type” Limitations:

1. This logic requires JS in order to function in full.
   2. Affiliate/Organic are self-reported only (no detection).
      3. IMG/pixel-based monitoring limits the amount of data we are able to collect, and so it limits the number of cases where we detect and report on a traffic source type. This has the greatest impact on web-served video.
         4. Creative Sandboxes (such as those used by Amazon, Xandr, and Google) limit the data we are able to collect about the user and the source of the traffic, and our ability to determine the traffic source type
            5. AMP Project pages also limit our ability to detect the traffic source type, as this type of content serving mechanism overwrites data that would otherwise be available without AMP
               6. Content that is served in a paginated “slideshow” format naturally will obscure the source of the traffic and our ability to determine the source past page 2.\*How does it work?
                  let `V` be a value and `V'` be a different value:
                  * If the user's declaration is `V` and our detection is `V` => V
                    * If the user's declaration is `null` and our detection is `V` => V
                      * If the user's declaration is `V` and our detection is `null` => (V)
                        * If the user's declaration is `V` and our detection is `V'`=> V' (V)
                          * If the user's declaration is `null` and our detection is `null` => UndeterminedNote:The \&tt=g definition is used for Google traffic and can be removed if not relevant for your implementation. If relevant, please read more about the TCF here.Data logging processThe JavaScript from the ad sends all calculated data to the server (Argus core servers)
                            In the server, the data is processed and all logic is executed to determine a fraudulent or legitimate transaction
                            The server also checks the AeroSpike server to determine if the IP, URL, and app name are known to be fraudulent
                            The server also checks the AeroSpike server to determine if the client user ID or cookie is known to be fraudulent from a previous transaction or if a certain amount of calls from the same IP is exceeded
                            The results are saved to log files in Google Storage
                            Another machine (the feeder - bqAgent process) continuously checks Google Storage for new files and streams them to the BigQuery Footprints table. It deletes the files when finished
                            The data that is saved there is the raw data and the detection results (fraud, clean, etc.)
                            Every hour the hourly\_csv\_report process queries all the rows from the last hour and aggregates them by user fields (Traffic Type, L1- L6, Integration Type, pm\_ct, etc.). The result is the total fraud grouped by these fields
                            For each customer, the results are saved in Google Storage as CSV files on an hourly basis
                            For each customer, on a daily, weekly, and monthly basis, PM aggregates those files into one daily, weekly, and monthly summary CSV file
                            The process impression.py takes the CSV files and creates UI tables (Impression table) that contain the aggregated data for the Dashboard UI for quick customer access to the aggregated data\*Data storage disclaimer - PM stores the IMP level data for a period of 12 months before permanently erasing the data. This data is stored in full compliance with GDPR.Server-initiated (SSAI) video ad counting methods\
                            As described Protected Media utilizes a client-initiate, census basis approach to count impressions
                            Clients who are utilizing SSAI (a configuration in which ad impressions are counted at the same time the underlying page content is served) to count impressions are instructed in Protected Media’s integration guide to using a specific parameter to identify such traffic within Protected Media’s DB and these impressions would not be included under the metrics accredited by MRC.
                            Measurement Limitation of SSAI Traffic and PM Method of Identification
                            Protected Media utilizes the IAB VAST 4.1 guidelines to identify SSAI traffic (at a minimum, the presence of x-device-ip and x-device-user-agent headers). If SSAI traffic is not passing along the IAB VAST 4.1 required headers, then the traffic is deemed invalid.
                            Besides reviewing SSAI traffic for these headers, Protected Media applies pattern analysis to generate a daily report of suspected SSAI traffic and servers for manual review.
                            Valid impressions from apps verified to utilize SSAI are reported under the Non-Malicious Bot category in the Protected Media UI.
                            Measurement Limitations between OTT IntegrationsDisplay in Off State
                            User Inactivity
                            Continuous Play
                            VAST (IMG, no SDK)
                            Unable to Measure
                            Able to Measure
                            \*\*Unable to Measure
                            SSAI (IMG, no SDK)
                            Unable to Measure
                            \*Able to Measure
                            \*\*Unable to Measure
                            SDK
                            Able to Measure
                            Able to Measure
                            Able to Measure\*pending MRC accreditation.
                            \*\*PM is able to indicate when this is reported by the Client (User reported “Continuous Play).Auto-Play Video
                            Protected Media utilizes its JS capabilities in order to automatically identify the measured creative type including Auto-Play Video creatives and segregate it within the Protected Media’s reports.
                            As for now, Protected Media has not detected any material amount of Auto-Play Video traffic within its DB.
                            \*If the "refresh" property of the ad element is true, we are detecting the ad as “autorefresh”.
                            \*When available, “autorefresh” can be detected via NavigationAPI (since Chrome 102, only on top-page).
                            \*Auto-play traffic consists represents around 3% of total traffic scanned.Measurement Limitation of Continuous play
                            (also referred to as Post-Play and analogous to Auto-Play) refers to an OTT configuration that will play the next episode in a series or related content automatically after the end of previous content without user interaction. The implementation of Continuous Play may vary in terms of time between content, the number of pieces of content that play automatically, capping, and user interaction prompts. However, when video content itself (inclusive of advertising) is played without user interaction (Continuous Play) this should be disclosed.Measurement Limitation of Firefox Browser
                            Any Firefox browser above version 68 will currently block PM’s code. This matter is currently under review.
                            Measurement limitation - Rendering off in Safari
                            Rendering off in Safari is applicable 1 second after the page loading.
                            Cases where the Safari is opened and closed within 1 second will not be measured.
                            Safari desktop limitation (Top hits function)
                            Safari's "top hits" function triggers a scenario where PM detects and reports these Impressions as "Rendered" when they are Preloaded only. This scenario exists in less than 4.7% of the JS clean traffic on Safari desktop. PM monitors this quarterly.
                            Inactivity Rules
                            Protected Media utilize thresholds based on timestamp signals such as interactions performed by the user on the device and other signals to determine user inactivity in accordance with the IAB’s Video Impression Guidelines.
                            User sessions that reach the predetermined level of consecutive inactivity will be terminated and excluded from additional contributions.
                            PM’s inactivity threshold was last updated in November 2024 and is currently set to 16 inactive impressions per hour.
                            In addition to the above stated, PM also measures Inactivity via the UID parameter with specific thresholds for each environment.
                            Lastly, PM measures various User Interaction signals with different thresholds per environment.
                            The threshold mentioned above is expected to be modified in the future based on evidence from an empirical study of the evolution of users’ browsing habits.
                            \*For additional information regarding the Inactivity functionality please write to [support@protected.media](mailto:support@protected.media)Limitations
                            It is recognized that there are some situations, out of Protected Media’s control, that may result in differences in the number of impressions counted by Protected Media and the number of impressions (or any other pixel triggering event) counted on the client's ad server, this could be as a result of
                            Human Error
                            Pixel Implementation
                            Macro Implementation
                            HTML5 Creatives
                            Incorrect Settings
                            Ad Serving Sequence
                            Internet Connectivity Issues/Latency
                            Short Session Times (Abandonment)
                            Caching
                            Difference in Counting Methodology
                            Use of Ad-blocking software
                            Image Rendering disabled
                            Reporting
                            Time Zone
                            Traffic Validation/Report Filtration (User Agents, Behavior Validation)
                            No Referral URL
                            Server-Side vs. Client-Side Counting
                            Differences in Terminology/Definitions
                            Targeting
                            Targeting by Device Characteristics
                            Geo/Location Based Targeting
                            Fraudulent activity
                            There are instances where a supply source is intentionally preventing 3rd party JS verification pixels like PM from running and detecting foul play
                            When the ad is inside an iFrame and the PM tag is fired from outside of the ad iFrame, Protected Media might not be able to detect the ad creative type, Auto-refresh, and Continuous Play.Environments
                            The measurement process is generally similar for both desktop and mobile environments. For mobile apps, the pub\_app parameter specifies the app name where the ad is being displayed. For ads viewed in mobile or desktop browsers, the pub\_domain parameter specifies the domain name in which the ad is displayed.
                            Protected Media can detect mobile or desktop environments using the user agent and other parameters of the extracted page using JavaScript. Common logic in JavaScript detects fraud, but Protected Media also uses environment-specific logic for mobile and desktop browsers. In general, contradictions between what the browser says it is and its actual behavior or abnormal browser parameters indicate that it is not a real user.\
                            \*In order to segregate by environment use the “Environment” dimension available directly through the UI (added in September 2022).Filtration Methodology
                            Protected Media employs both GIVT and SIVT filtration techniques based on identifiers, activity, and patterns from data in the log files to detect and remove the invalid activity.
                            Because user identification and intent cannot always be known or discerned by the publisher, advertiser, or their respective agents, it is unlikely that all invalid activity can be identified and excluded from report results.Removal of Internal “Unnatural” Activity
                            In order to segregate all internally generated activity that does not represent legitimate advertising consumption or otherwise valid internet traffic.
                            These activities are considered invalid traffic for advertising commerce purposes if material, but are allowed to be removed prior to impression
                            counting (prior to invalid traffic measurement and reporting) with appropriate support.
                            In order to filter/segregate these "Unnatural" transactions from Gross measurement, please perform the following:
                            1. Contact your dedicated CS manager with this request.
                               2. For these "Unnatural" transactions, add in L6 the following value: "test".
                                  3. Verify with your CS manager that the setup is correct.                                     &#x20;&#x20;




                                     General Invalid Traffic Filtration

                                     Protected Media filters GIVT traffic identified through routine means of filtration executed through the application of lists or with other standardized parameter checks. For example:

                                     Robot Instruction Files
                                     Prefetch and Prerender impressions and requests
                                     Internally generated traffic
                                     Known data center sourced traffic
                                     Bots and Spiders or other crawlers (Based on Protected Media’s proprietary lists)
                                     Activity-based filtration data
                                     Frequency Capping - users who exceed a set number of impressions from the same IP / Cookie / UID
                                     Non-browser user-agent headers / Unknown browsers
                                     Clients that lack the support of HTTPS protocol
                                     Non-rendering capabilities; sessions or traffic without the capability to render or display images (other than cases of disabled image rendering) or other activity may be associated with them such as headless browsers or component devices without a display component.
                                     Invalid placements (specific to ads); small, barely visible or invisible ad delivery or illogical (non-industry standard) ad size of: 0x0 and 1x1 as delivered on the client side.


                                     \*Decision rate for GIVT is 100%.
                                     Robot Instruction Files
                                     Protected Media uses robots.txt files to instruct robots that they should not follow or index any links within the domain from which the robots.txt file was retrieved.

                                     Prefetch and Prerender call
                                     When applying prefetch or prerender ad serving techniques clients are guided to use specific parameters to distinguish rendered calls.
                                     By default Protected Media blocks prefetch ad requests by using a 403 denied return code and no impressions will be recorded.
                                     Internally generated traffic
                                     Internally generated traffic is being assigned to a specific PID and therefore is not affecting system-wide impressions counting
                                     Auto-Refresh&#x20;
                                     Automatically refreshing pages use HTML programming code to automatically reload the user's browser with an updated web page after a specified time interval, including new ad impressions.&#x20;
                                     Protected Media does not have direct control over the client's site-initiated auto-refresh, and does not have the ability to ensure clients are fully reporting and disclosing the use of auto-refresh.
                                     If the ad is auto-refreshed, a new request is sent to Protected and a new impression will be counted.
                                     However, Protected Media guides clients to use a specific parameter to disclose the presence of auto-refresh traffic and settings (how often the ad refreshes)
                                     The removal of suspicious auto-page refresh is done during processing time.&#x20;
                                     Protected Media also utilizes a manual process to review and segment auto-refresh traffic for internal review proactively
                                     Protected Media proprietary list robotic user agents
                                     Protected Media utilizes a single-pass specific identification approach for the filtration of robotic activity and unknown user agents whereby user agents are compared to a proprietary list of robotic user agent strings.
                                     Protected Media’s proprietary list of robotic user agents is updated by the R\&D team in a manual process where unclassified user agents are added to the list on a weekly basis.

                                     Sophisticated Invalid Traffic Filtration
                                     In addition to the GIVT traffic filtration techniques, Protected Media also employs SIVT filtration techniques in order to detect and filter sophisticated inventory that requires advanced analytics, multi-point corroboration/coordination, and significant human intervention. For example,

                                     Advertising bots simulating human traffic
                                     Hostile tools masking the user&#x20;
                                     Traffic masking IP / Geolocation
                                     Ads that are deliberately displayed in a manner that is invisible to humans
                                     Ads are displayed on a website/application different from the one reported to the advertiser
                                     Traffic from known fraudulent IPs
                                     Client identified as a host (e.g., server from a cloud hosting provider)
                                     Reputation - Clients previously identified as IVT not only by IP but by cookies or user ID















                                     Data reporting
                                     Protected Media provides clients with a web-based reporting interface which offers several metrics on Several tabs, each individual reporting tab presents total transaction counts as well as the count and percentage of Fraudulent, Suspicious and Total IVT transactions for a selected date range (By default the previous 24 hours are displayed).
                                     Within each reporting tab, users can view the reported metrics using various time-based filters, such as date range, today, yesterday, month-to-date, year-to-date, etc.
                                     Users can also generate filter reports by defining the campaign or advertiser’s Traffic ID, the six additional client-configurable reporting hierarchy parameters (L1-L6), and the integration type (i.e., JavaScript or \<IMG>; the image tag is excluded from the scope of this engagement)

                                     Reports in the dashboard are updated on an hourly basis a considered “Final” once available
                                     (unless otherwise noted via the dashboard notification pop up).


                                     Anti-Fraud
                                     Displays total transaction counts at the ad campaign or creative level along with the percentage of transactions falling into each of Protected Media’s seven defined IVT categories. (i.e. Bot Virus, Hostile, Tunnel, Non-malicious bots, View Fraud, Publisher Fraud, and Reputation)
                                     \*The metrics under this tab are out of the scope of the MRC accreditation


                                     Visibility
                                     Includes data tables displaying total transaction counts at the ad campaign or creative level and the percentage of impressions that were considered visible for predefined intervals of time.&#x20;
                                     (i.e. 1, 2, 5, 10, 15, 20 and 25 seconds)
                                     \*The metrics under this tab are out of the scope of the MRC accreditation


                                     MRC

                                     Under this tab clients can find all MRC accredited metrics as indicated on page 19 below.

                                     Time Zone reporting

                                     Protected Media’s measurement data is collected and reported in Coordinated Universal Time (UTC).&#x20;
                                     Protected Media’s reporting interface defaults to UTC reporting; however, users may select alternative time zone reporting within the reporting interface options.



                                     Business partner qualification&#x20;
                                     Protected Media conducts a Client Qualification Process on potential and existing clients to determine if a business relationship should be initiated or continued with the organization. The Client Qualification Process includes assessing the legitimacy of organizations and assessing available information around the organization’s intended use of fraudulent activity identified through Protected Media products.

                                     Log Files
                                     Activity log files can be downloaded in CSV format from the Dashboard. Additionally, raw and aggregate log files are stored in Google Cloud folders. Protected Media provides each client with the option of accessing the aggregate files stored in Google Cloud.
                                     log files are retained for one year and aggregated data is retained indefinitely

                                     Data reissue
                                     If Protected Media detects or becomes aware of issues that impact clients' data, there is a formal investigation process to determine the cause and impact of the issue.
                                     Decisions to regenerate reports are based on the level of impact on clients, if the material (more than 5%) Protected Media will regenerate reports up to 14 days prior to the date the issue was discovered. &#x20;
                                     The data change will be communicated to the clients using the reporting interface notification banner pop-ups








                                     Appendix A – Major Feeds
                                     The following table contains the type of partners with feeds into our measurement process.

                                     Category
                                     Use
                                     rbl
                                     DNS servers that get IP in a specific format and return data on that server; for example spam, malware, or Tor proxy.






                                     Brand
                                     Brand Protection site categories (Gambling, Tobacco, etc.)
                                     Proxies
                                     List of IPs that are known proxy servers.







                                     TOR
                                     Tor is free software for enabling anonymous communication by directing Internet traffic through an overlay network consisting of several thousand relays. PM gets known Tor proxies from 3rd parties.
                                     Spam and Attacks
                                     IPs of spam providers and attackers.
                                     Malware
                                     IPs of computers in which malware was detected.
                                     Whois
                                     Whois provides domain-related data. In particular, newer domains with large traffic are more suspicious.
                                     DNS
                                     Get IP and return name ptr. It helps us understand if it is dynamic or static IP and if it is an host name


                                     Appendix B – Metrics full breakdown
                                     Solution
                                     Protected Category
                                     Protected Metric Name
                                     Description
                                     MRC
                                     Tracked Ads
                                     Tracked Ads
                                     All transactions on MRC scope (mostly JS and IMG transactions that are not SSAI)
                                     Gross Impressions
                                     Gross Impressions\*
                                     All rendered and active impressions (Rendered impressions (from tracked ads) that weren't flagged by our inactivity rules)
                                     Net Impressions
                                     Net Impressions\*
                                     Gross Impressions - GIVT
                                     Viewable Impressions\*
                                     Ads contained in the viewable space of a browser window on an in-focus browser tab, based on pre-established criteria per the IAB guidelines regarding the percentage of ad pixels within the viewable space and the length of time the ad is in the viewable space of the browser
                                     Non-Viewable Impressions\*
                                     Ads which do not meet the MRC's definition of Viewable Impressions
                                     Undetermined Impressions\*
                                     Impressions which are of indeterminate viewability measurement
                                     Measured Rate\*
                                     The percentage of (Viewable Impressions + Non-Viewable Impressions) from Total Served Impressions
                                     Median Viewability time (ms)
                                     The median time that the net impressions (not GIVT) were viewable (ms)
                                     Total Net Impressions
                                     Total Net Impressions\*
                                     Gross Impressions - SIVT
                                     Viewable Impressions\*
                                     Ads contained in the viewable space of a browser window on an in-focus browser tab, based on pre-established criteria per the IAB guidelines regarding the percentage of ad pixels within the viewable space and the length of time the ad is in the viewable space of the browser
                                     Non-Viewable Impressions\*
                                     Ads which do not meet the MRC's definition of Viewable Impressions
                                     Undetermined Impressions\*
                                     Impressions which are of indeterminate viewability measurement
                                     Measured Rate\*
                                     The percentage of (Viewable Impressions + Non-Viewable Impressions) from Total Served Impressions
                                     Median Viewability time (ms)
                                     The median time that the clean impressions (not GIVT or SIVT) were viewable (ms)


                                     * Metrics accredited by the Media Ratings Council. What accreditation means?