---
title: "Configuring NAS for Scheduled Jobs in LS Central"
date: 2023-06-18T15:06:01+05:30
draft: false
tags: ['LS Central']
categories: ['Technical']
summary: 'How to configure NAS to run Scheduled Jobs in LS Central.'
featured_image: '/content/images/ls-central/configuring-nas-for-scheduled-jobs/Picture5.png'
---

# Introduction
LS Central Scheduler Jobs are used for automatic background processing. 

These jobs use the NAS Service under the hood. 

We are going to see how to configure the NAS Service for LS Central.

## Pre-requisites
- LS Central
- Data Director

## References
[tehttps://help.lscentral.lsretail.com/Content/LS-Insight/Setup/LS-Central-In-Cloud-LS-Insight-In-Azure/3-Machine-Or-VM.htmxt](https://help.lscentral.lsretail.com/Content/LS-Insight/Setup/LS-Central-In-Cloud-LS-Insight-In-Azure/3-Machine-Or-VM.htm)

## Configuration
Create a new Server Instance and name it appropriately.

[![Picture 1](/content/images/ls-central/configuring-nas-for-scheduled-jobs/Picture1.png)](/content/images/ls-central/configuring-nas-for-scheduled-jobs/Picture1.png)

Ensure that the account for this new Server Instance is set to User and the User has Administrator privileges.

[![Picture 2](/content/images/ls-central/configuring-nas-for-scheduled-jobs/Picture2.png)](/content/images/ls-central/configuring-nas-for-scheduled-jobs/Picture2.png)

In the General tab, update the "Service Default Company" and "Service Default Time Zone."

[![Picture 3](/content/images/ls-central/configuring-nas-for-scheduled-jobs/Picture3.png)](/content/images/ls-central/configuring-nas-for-scheduled-jobs/Picture3.png)

In the NAS Services tab, set the following fields:

- **Run NAS Services with Admin Rights** : True
- **Startup Argument** : NASID,TYPEFILTER=,LOG=1,REPEAT=1
- **Startup Codeunit** : 99001468
- **Startup Method** : LSRSCHEDULER

[![Picture 4](/content/images/ls-central/configuring-nas-for-scheduled-jobs/Picture4.png)](/content/images/ls-central/configuring-nas-for-scheduled-jobs/Picture4.png)

Restart the Server Instance.

Open the Scheduler Setup in LS Central and set the "Enable NAS Scheduler" to true.

[![Picture 5](/content/images/ls-central/configuring-nas-for-scheduled-jobs/Picture5.png)](/content/images/ls-central/configuring-nas-for-scheduled-jobs/Picture5.png)

Refresh the page.

## Conclusion
Thus, we saw how to configure NAS Services in LS Central for running scheduled jobs.

Happy Coding!