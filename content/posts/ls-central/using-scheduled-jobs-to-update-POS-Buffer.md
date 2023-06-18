---
title: "Using Scheduled Jobs to Update POS Buffer"
date: 2023-06-18T14:53:24+05:30
draft: false
tags: ['LS Central']
categories: ['Technical']
summary: 'How to configure scheduled jobs to update the POS Buffer which is used to search items on the POS.'
featured_image: '/content/images/ls-central/using-scheduled-jobs-to-update-POS-Buffer/Picture5.png'
---

# Introduction
POS Search Buffer is used to display the Items in the main POS Search Drop Down. 

The configuration for automatically updating the POS Search Buffer is located in the POS Functionality Profile, but it is limited in nature, only 2 options exist on the POS Functionality Profile, one which defines whether the buffer should be updated automatically and the other defines the frequency in which it should be updated.

We've faced some issues with this process running automatically such the Buffer not being updated as such we had to look for a work-around using Scheduled Jobs.

## Pre-requisites
- LS Central
- Business Central OnPrem or OnCloud

## References
[How to: Control When to Update Search Index and POS Buffer (lsretail.com)](https://help.lscentral.lsretail.com/Content/LS-Retail/Performance/Control-When-To-Update-Search-Index-And-POS-Buffer.htm?TocPath=Retail%7CPoint%20of%20Sale%7CPOS%7CHow%20to%20...%7C_____4)

## Configuration
Create a new scheduled job with an appropriate name and description.

[![Picture 1](/content/images/ls-central/using-scheduled-jobs-to-update-POS-Buffer/Picture1.png)](/content/images/ls-central/using-scheduled-jobs-to-update-POS-Buffer/Picture1.png)

In the Object Setup, define the "Object Type" as **Codeunit** and "Object ID" as **10000749**, set the "Code" field as **INDEX**. 

Also ensure that the "Uses Scheduler Job Record" is set to **true**.

[![Picture 2](/content/images/ls-central/using-scheduled-jobs-to-update-POS-Buffer/Picture2.png)](/content/images/ls-central/using-scheduled-jobs-to-update-POS-Buffer/Picture2.png)

In the Schedule Details configure the frequency in which you want to run the job. 

In the below screenshot the job is defined to run Every 10 seconds from 27-01-2022 starting from 10:14:00.

[![Picture 3](/content/images/ls-central/using-scheduled-jobs-to-update-POS-Buffer/Picture3.png)](/content/images/ls-central/using-scheduled-jobs-to-update-POS-Buffer/Picture3.png)

Click on Run Now to test whether the job is working as expected.

[![Picture 4](/content/images/ls-central/using-scheduled-jobs-to-update-POS-Buffer/Picture4.png)](/content/images/ls-central/using-scheduled-jobs-to-update-POS-Buffer/Picture4.png)

## Extra
The reason we set the "Code" to **INDEX** and "Uses Scheduler Job Record" is set to **true** is because in the Source Code of the Codeunit that we are trying to run we can see that the TableNo is defined as Scheduler Job Header which is a reference to the "Uses Scheduler Job Record" field and we can see that it uses the "Code" field to compare which action is to be performed. 

For instance, if instead of **INDEX** we set it to **UPDATE** then the processing of the POS Search Buffer would happen based on Actions instead of all the records being re-index as happens when we set the "Code" to **INDEX**, we can also see that we can specify which table we want to Index by setting the table name in the "Text" field.

[![Picture 5](/content/images/ls-central/using-scheduled-jobs-to-update-POS-Buffer/Picture5.png)](/content/images/ls-central/using-scheduled-jobs-to-update-POS-Buffer/Picture5.png)

## Conclusion
Thus we saw how we can use Scheduled Jobs to update the POS Search Buffer in the event that the standard automatic updating of POS Search Buffer isn't working as expected.

Happy Coding!