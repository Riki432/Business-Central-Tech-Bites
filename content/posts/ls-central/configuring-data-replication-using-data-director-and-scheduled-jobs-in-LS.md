---
title: "Configuring Data Replication Using Data Director and Scheduled Jobs in LS"
date: 2022-03-02T22:17:01+05:30
draft: false
tags: ['LS Central']
categories: ['Technical']
summary: 'How toc configure data replication in LS v16 using Data Director and Scheduled Jobs'
featured_image: ''
---

# Introduction
In this blog, we will be seeing Scheduled Job configuration for Data Replication using Data Director.

Scheduled Jobs comprise of two parts: the Job Header and Sub-jobs.

In the Job Header, we define different parameters for the Jobs like, Error Handling methodology, To and From Locations, Compression Types, Scheduling details and the sub-jobs.

In the Sub Jobs, we define where to get the schemas of the table, the tables to replicate, methods of replication, filters on the data to be replicated, linked tables, etc.

## Pre-requisites
- Microsoft Dynamics 365 Business Central 
- LS Central

## References
- [LS Data Director User Guide](https://implementation.ls-one.com/Content/Documents/InstallGuides/LS%20Data%20Director%20User%20Guide.pdf)
- [Isolation levels in SQL Server](https://www.sqlservercentral.com/articles/isolation-levels-in-sql-server)
- [Distribution Sub-Locations](https://help.lscentral.lsretail.com/Content/Fields/T_99001586_93.htm)
- [Distribution Restrictions](https://help.lscentral.lsretail.com/Content/Fields/T_99001586_91.htm)

## Configuration

### General

![Image](https://i.ibb.co/hcSfRMH/image.png)

1. **Job ID** :- A unique Identifier for this Scheduled Job.
2. **Scheduler Job Type Code**:- It is a kind of category for this Job, we can use this category as a filter when we configure NAS Services.
3. **Subjobs Defined By Job**:- Specifies where system is supposed to fetch sub-jobs from for this Job. Generally it is the same as "Job ID" but LS allows you to create a job with its sub-jobs defined in another job.

### Location Settings

![Image](https://i.ibb.co/VQhBgbc/image.png)

In this tab, we specify where the Data is supposed to come from and where the data is supposed to go.
There are multiple ways to configure this,

1. From Multiple Locations to Single Location
- Set the "From Dist. Restrictions to "Include List".
- Click on Navigate -> Jobs -> Sender Location List.

![Image](https://i.ibb.co/F5P1R85/image.png)

- Add all the locations that you want to pull the data from.

![Image](https://i.ibb.co/1QWK622/image.png)

- Set "Distribution Restrictions" to "Single Location"
- Set the Location in "To-Location Code" field.

![Image](https://i.ibb.co/2tGLbN6/image.png)

2. From Single Location to Multiple Locations - This is the similar to the previous one simply reversing where we set the values.

- Set "From Dist. Restrictions" to Single Location and set the location.
- Set "Distribution Sublocations" to "Included in Replic.", this field is used to specify whether Data should be sent to sublocations(POS Terminals) or not.
- Set "Distribution Restrictions" to "Include List" and Go to Navigate > Jobs > "Receiver Locations Include/Exclude."

![Image](https://i.ibb.co/nkb5k95/image.png)

- Add all the locations you want to send the Data to.

![Image](https://i.ibb.co/f0cms4H/image.png)

3. From Multiple Locations to Multiple Locations
- Simply set Include List on both sides and add all the locations that the data is supposed to come from and where it is supposed to go.

### Schedule Details

![Image](https://i.ibb.co/MMXv3gw/image.png)

Here we specify how often this Job is supposed to run.

You can schedule the Job to run every day, hour, minute or second as per your needs. 

In the above example, I have scheduled the Job to run every 15 minutes, every day.

Do note that you need to have NAS Services configured for the jobs to run automatically.

### Data Replication

![Image](https://i.ibb.co/s28Nnd6/image.png)

Here we have to define the "Subjobs", which are in essence, tables which are to be replicated. 

## Conclusion

Thus, we saw how to create a Scheduled Job Header, there are a lot more things that can be done with this like, using different codeunits for Data Replication, Object Replication
Or simply running Codeunits for automating tasks. 

You can find the second part [here](/posts/ls-central/configuring-data-replication-using-data-director-and-scheduled-jobs-in-ls-part-2/).

Happy Coding!