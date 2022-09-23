---
title: "Changed Date Now Unable to Login to BC"
date: 2022-09-05T13:52:09+05:30
draft: false
tags: ['Business Central','Technical', 'Functional']
summary: 'How to resolve the error where changing date on the host sever causes lock out of Business Central'
featured_image: 'https://i.ibb.co/mJ4K1zk/image.png'
---

# Introduction
While doing some customization testing, which revolved around using different dates, I realized that once the date is switched back to the correct date, I was unable to connect to Business Central.
I restarted the server instance, IIS, SQL Server services to no avail. 


## Pre-requisites
- Business Central OnPrem with SSL Setup


## References
- [Server Fault](https://serverfault.com/questions/217343/date-header-returned-by-iis7-is-wrong)
- [Microsoft Support](https://support.microsoft.com/en-us/topic/using-net-stop-and-net-start-commands-to-force-iis-services-to-re-read-the-registry-c6fe0d0b-9893-36d0-cc3c-47d03f9ccdde)

## Verification
Logging into Business Central gave no errors, there were no errors in the Event Viewer that explicitly mention that it is a Date related issue.

The way I stumbled across it being a date related issue is that in the Response that the Business Central server sent to the Login Request, was carrying the wrong date in it. 

When I switched the System Date back to the date mentioned in the Response headers, everything seemed to be working again.

![Problem Verified](https://i.ibb.co/Y7bLcPX/image.png)

## Solution
This issue is caused because when the system date is changed, the same is changed in IIS but when you change it back IIS does not refresh it and we have to manually reset it. 

Restarting it does not work, trust me, **I tried**.

One way to do this is to execute the following commands on the Server:
1. net http stop
2. net http start

These commands took a lot of time so be sure to have available down time before you run them.

The other way, which is much simpler in my opinion, is to simply **restart the Server**.

This stops all the services and restarts them which forces the IIS to reset as well.

![Solution](https://i.ibb.co/mJ4K1zk/image.png)

## Conclusion
Thus in this blog, we saw how to resolve the issue of being unable to login after change Server Date in Business Central.
Hope this helps!
