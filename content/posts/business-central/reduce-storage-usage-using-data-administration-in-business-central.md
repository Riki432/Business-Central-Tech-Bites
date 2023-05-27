---
title: "Reduce Storage Usage Using Data Administration in Business Central"
date: 2023-05-27T11:33:57+05:30
draft: false
tags: ['Business Central']
categories: ['Technical]
summary: 'How to Reduce Storage Usage Using Data Administration in Business Central'
featured_image: '/content/images/business-central/reduce-storage-usage-using-data-administration-in-business-central/Picture13.png'
---

# Introduction

By default, Business Central comes with 80GB of storage capacity across three sandbox environments and 1 Production Environment with an additional 3GB/Premium License, 2GB/Essential License, 1GB/Device license. 

These storage limits depending on your business volume may run out if the data is not managed properly. 

Business Central now comes with a one stop view where you can manage (compress or delete) the entries to reduce storage usage - "Data Administration." 

## Pre-requisites

Business Central Cloud/On Prem 

## References
[Manage Storage by Deleting Documents or Compressing Data - Business Central | Microsoft Learn ](https://learn.microsoft.com/en-us/dynamics365/business-central/admin-manage-documents?wt.mc_id=d365bc_inproduct_page)

## Configuration

[![Picture 1](/content/images/business-central/reduce-storage-usage-using-data-administration-in-business-central/Picture1.png)](/content/images/business-central/reduce-storage-usage-using-data-administration-in-business-central/Picture1.png)

In Business Central, we have had the option to view the capacity usage from the Admin Center for a while now. 

Recently, they've also added a one stop view to check and manage the capacity usage - Data Administration. 

It can be found directly from the global search. 

[![Picture 2](/content/images/business-central/reduce-storage-usage-using-data-administration-in-business-central/Picture2.png)](/content/images/business-central/reduce-storage-usage-using-data-administration-in-business-central/Picture2.png)

The first time we open this we are greeted with an empty view, the data is loaded after we click on refresh to load the latest data.  

[![Picture 3](/content/images/business-central/reduce-storage-usage-using-data-administration-in-business-central/Picture3.png)](/content/images/business-central/reduce-storage-usage-using-data-administration-in-business-central/Picture3.png)

You can also configure it so that the data is loaded automatically in the background every so often. 

[![Picture 4](/content/images/business-central/reduce-storage-usage-using-data-administration-in-business-central/Picture4.png)](/content/images/business-central/reduce-storage-usage-using-data-administration-in-business-central/Picture4.png)

Here, we get the options for Data Clean up where we can delete data that isn't required anymore. 

All of the below options, open a similar processing report where you can set filters which are used to delete the records as needed. 

[![Picture 5](/content/images/business-central/reduce-storage-usage-using-data-administration-in-business-central/Picture5.png)](/content/images/business-central/reduce-storage-usage-using-data-administration-in-business-central/Picture5.png)

[![Picture 6](/content/images/business-central/reduce-storage-usage-using-data-administration-in-business-central/Picture6.png)](/content/images/business-central/reduce-storage-usage-using-data-administration-in-business-central/Picture6.png)

[![Picture 7](/content/images/business-central/reduce-storage-usage-using-data-administration-in-business-central/Picture7.png)](/content/images/business-central/reduce-storage-usage-using-data-administration-in-business-central/Picture7.png)

[![Picture 8](/content/images/business-central/reduce-storage-usage-using-data-administration-in-business-central/Picture8.png)](/content/images/business-central/reduce-storage-usage-using-data-administration-in-business-central/Picture8.png)

[![Picture 9](/content/images/business-central/reduce-storage-usage-using-data-administration-in-business-central/Picture9.png)](/content/images/business-central/reduce-storage-usage-using-data-administration-in-business-central/Picture9.png)

[![Picture 10](/content/images/business-central/reduce-storage-usage-using-data-administration-in-business-central/Picture10.png)](/content/images/business-central/reduce-storage-usage-using-data-administration-in-business-central/Picture10.png)

The "Delete Detached Media" opens another page which I've discussed in depth in another [blog](/posts/business-central/automated-detached-media-cleanup/). 
 
The second action groups hold actions which are meant to compress the ledger entries which can drastically reduce the storage space used. 

It is important to note that you can only compress entries which are older than 5 years by yourself which belong to Fiscal years that are closed and the entries themselves are closed (Open is set to false). 

You can configure the compression such that there is one entry per day, one entry per week, one entry per month, one entry per quarter, one entry per year or one entry for the period that is defined for compression. 

[![Picture 11](/content/images/business-central/reduce-storage-usage-using-data-administration-in-business-central/Picture11.png)](/content/images/business-central/reduce-storage-usage-using-data-administration-in-business-central/Picture11.png)

You also have the functionality to delete empty registers from here. 

[![Picture 12](/content/images/business-central/reduce-storage-usage-using-data-administration-in-business-central/Picture12.png)](/content/images/business-central/reduce-storage-usage-using-data-administration-in-business-central/Picture12.png)

If these individual actions seem to be overwhelming, Microsoft also provides for a Data Administration wizard which simplifies this process and allows you to manage the capacity via a wizard. 

[![Picture 13](/content/images/business-central/reduce-storage-usage-using-data-administration-in-business-central/Picture13.png)](/content/images/business-central/reduce-storage-usage-using-data-administration-in-business-central/Picture13.png)
 
[![Picture 14](/content/images/business-central/reduce-storage-usage-using-data-administration-in-business-central/Picture14.png)](/content/images/business-central/reduce-storage-usage-using-data-administration-in-business-central/Picture14.png)

[![Picture 15](/content/images/business-central/reduce-storage-usage-using-data-administration-in-business-central/Picture15.png)](/content/images/business-central/reduce-storage-usage-using-data-administration-in-business-central/Picture15.png)


## Conclusion
Thus, we saw how we can use the standard data administration tools to manage capacity of Business Central environment which can help the system run much more efficiently in terms of both performance and costs. 

Happy Coding!
