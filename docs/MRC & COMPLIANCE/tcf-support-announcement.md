---
title: TCF support announcement
deprecated: false
hidden: false
metadata:
  robots: index
---
# Protected Media Joins IAB Europe’s Transparency and Consent Framework

## What is TCF?

The framework, which was launched in April 2018, is designed to help all parties in the digital advertising chain ensure that they comply with the EU’s General Data Protection Regulation (GDPR) and ePrivacy Directive when processing personal data or accessing and/or storing information on a user’s device, such as cookies, advertising identifiers, device identifiers, and other tracking technologies.

## You need to take into account:

As Google will start supporting the TCF initiative (for further details from Google, [click here](https://support.google.com/admanager/answer/9461778)),We highly recommend that you perform the required adjustment: Adding a parameter that declares the traffic type is from Google, thus **indicating to stay away from cookies**.

Please add: `&tt=g` as presented below. This is relevant for every type of integration!

For example:

```html javascript
<script type="text/javascript"
        src="https://js.ad-score.com/score.min.js?pid=[YOUR_PID]&tt=g#
             tid=display-ad&l1=group1&l2=group2&ref=referrer&pub_app=app-bundle&
             pub_domain=domain&utid=uniquetransaction_id&uid=user_id&uip=user_ip&
             pub_ua=user_agent&cb=cachebuster&auto_refresh=0&continuous_play=0&
             creative_type=display" 
        async=1  >
</script> 
<noscript>
  <img src="https://data.ad-score.com/img?s=ns&pid=[YOUR_PID]&tt=g&tid=display-ad&
            l1=group1&l2=group2&ref=referrer&pub_app=app-bundle&pub_domain=domain&
            utid=uniquetransaction_id&uid=user_id&uip=user_ip&pub_ua=user_agent&
            cb=cachebuster&auto_refresh=0&continuous_play=0&creative_type=display" 
       width="1" height="1" >
  </img>
</noscript>
```

For more information regarding Google and IAB’s collaboration on TCF, please visit the following link: [https://support.google.com/admanager/answer/9461778?hl=en](https://support.google.com/admanager/answer/9461778?hl=en) .

For any additional questions please contact [support@protected.media](mailto:support@protected.media)