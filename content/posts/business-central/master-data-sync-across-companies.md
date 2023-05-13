---
title: "Master Data Sync Across Companies"
date: 2023-05-10T22:38:56+05:30
draft: false
tags: ['Business Central']
categories: ['Functional']
summary: 'How to sync master data across multiple companies in Business Central.'
featured_image: '/content/images/business-central/master-data-sync-across-companies/Picture10.png'
---

# Introduction
In many business scenarios we have two or more companies which work with the same Customers or Vendors or has same data that is to be shared with multiple legal entities. 

For such cases, manually making sure everything is in sync becomes difficult as the number of entities increases. 

For this, Business Central now comes with the functionality to sync master data across multiple companies. 

This can also be used by consultants for one time syncs if they simply need the setups from one company in another instead of going through the Configuration Package route. 

## Pre-requisites
- Business Central Cloud/OnPrem

## References
- [Set up and sync master data across companies](https://learn.microsoft.com/en-us/dynamics365/release-plan/2023wave1/smb/dynamics365-business-central/set-up-sync-master-data-across-companies)
- [Set Up Companies to Synchronize Master Data - Business Central](https://learn.microsoft.com/en-us/dynamics365/business-central/admin-set-up-data-sync#use-match-based-coupling)
 

## Configuration
First, I've created two companies in a Sandbox Box which are going to have a uni-directional sync between them. 

It is possible to have a bi-directional sync however it may cause issues and may cause over-write of data if it isn't configured properly. 

[![Picture 1](/content/images/business-central/master-data-sync-across-companies/Picture1.png)](/content/images/business-central/master-data-sync-across-companies/Picture1.png)

Here the data is going to flow from CRONUS USA, Inc. -> Zeus Ltd. 

As such, we go to the Master Data Management Setup in the "Zeus Ltd." company. 

[![Picture 2](/content/images/business-central/master-data-sync-across-companies/Picture2.png)](/content/images/business-central/master-data-sync-across-companies/Picture2.png)

Here we can specify which company the data is going to be pulled from and whether we want to enable the synchronization or not. 

So, I'll select "CRONUS USA Inc." as the Source Company and then I'll click on the "Synchronization Tables" action to show the list of the tables that I want to synchronize.   

[![Picture 3](/content/images/business-central/master-data-sync-across-companies/Picture3.png)](/content/images/business-central/master-data-sync-across-companies/Picture3.png)

Here by default, all the tables are enabled, I've disabled most of them and only selected a few. 

You can add your custom tables as well. 

Further, there's also the option to add filters so if we only want data that fulfils a certain criteria to be pulled into this company that can be managed from here. 

An example of this would be, a Parent company which has Customers globally which has a local company in a particular country and only wants customers from the said country. 

[![Picture 4](/content/images/business-central/master-data-sync-across-companies/Picture4.png)](/content/images/business-central/master-data-sync-across-companies/Picture4.png)

Further, we can also specify which exact fields we want to sync and whether we want to over-write the data if, there is any present in the current company, during the sync. 

[![Picture 5](/content/images/business-central/master-data-sync-across-companies/Picture5.png)](/content/images/business-central/master-data-sync-across-companies/Picture5.png)

After that, we go to the "Master Data Initial Sync." action on the "Master Data Management Setup" and we see the list of the tables that are to be synced along with the "Sync. Mode". 

We can change the Sync modes using the action at the top ("Use Full Sync" or "Use Match Based Coupling") 
1. In case of Full Sync, all the records that exist in Parent Company but don't exist in the child company are created. 
2. In case of Match Based Coupling, we can define a set of fields which will be used to match the data between the parent company and the child company and if we do not find a match, we have the option to create a new record. 

[![Picture 6](/content/images/business-central/master-data-sync-across-companies/Picture6.png)](/content/images/business-central/master-data-sync-across-companies/Picture6.png)

In either case, if we want the data in the Parent Company to over-ride the data in the child company we have to set the "Overwrite Local Change" field either at the field level or a the table level. 

[![Picture 7](/content/images/business-central/master-data-sync-across-companies/Picture7.png)](/content/images/business-central/master-data-sync-across-companies/Picture7.png)

If it is set to false then the change fails and we can see the same in the Synchronization Log. 

[![Picture 8](/content/images/business-central/master-data-sync-across-companies/Picture8.png)](/content/images/business-central/master-data-sync-across-companies/Picture8.png)

Once this is done, we can click on "Start All" which will start the synchronization process. It is only meant to be run once, as after this the synchronization jobs will take over. 

[![Picture 9](/content/images/business-central/master-data-sync-across-companies/Picture9.png)](/content/images/business-central/master-data-sync-across-companies/Picture9.png)

Once, everything is done syncing, we get the results as well. 

![Picture 10](/content/images/business-central/master-data-sync-across-companies/Picture10.png)

After this, as long as the "Enable Synchronization" is set to true on the "Master Data Management Setup" the jobs will keep the data in sync between the two companies. 

As an example I've created a Customer in the parent company and the same gets created into the child company directly within a few seconds.  

[![Picture 11](/content/images/business-central/master-data-sync-across-companies/Picture11.png)](/content/images/business-central/master-data-sync-across-companies/Picture11.png)

[![Picture 12](/content/images/business-central/master-data-sync-across-companies/Picture12.png)](/content/images/business-central/master-data-sync-across-companies/Picture12.png)

## Conclusion
Thus we saw how we can enable the native functionalty of Business Central to sync data across companies.

Happy Coding!
