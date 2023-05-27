---
title: "Automated Detached Media Cleanup"
date: 2023-05-27T11:50:44+05:30
draft: false
tags: ['Business Central']
categories: ['Technical']
summary: 'How to automate Detached Media Cleanup in Business Central'
featured_image: '/content/images/business-central/automated-detached-media-cleanup/Picture4.png'
---

# Introduction
In Business Central, there are two ways to store files. 

Either as Blobs or as Media types. 

In Media types, we store the files in the database (**Tenant Media ID - 2000000184**) and then we refer this record in other tables. 

Whenever there are no records referring a Media, it is deleted from the database. 

Media types are much more performant as they support caching whereas BLOBs needs to be fetched from the SQL Server every time they are used. 

Microsoft has moved most of the fields from using Blobs to Media types. 

However, in scenarios with a high load of writes and deletes, it is possible that there may end up orphaned media records i.e. Media records that are not referenced anywhere.  

In order to tackle such cases, Microsoft has recently announced the *FindOrphans* procedure which would return a list of GUIDs of such orphaned Media Types which could then we dealt with as needed. 

There's also another tool that has been provided by Microsoft which uses this newly added procedures and helps us in reduce storage usage needlessly, which is what are going to discuss today. 

## Pre-requisites

Business Central Cloud/On Prem 

## References
[Media Data Type - Microsoft Learn ](https://learn.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/media/media-data-type)

[Media.FindOrphans() Method - Microsoft Learn ](https://learn.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/media/media-findorphans-method)

## Configuration

You can access the "Detached Media Cleanup" from the "Data Administration" tool in Business Central.

[![Picture 1](/content/images/business-central/automated-detached-media-cleanup/Picture1.png)](/content/images/business-central/automated-detached-media-cleanup/Picture1.png)

Under "Data Cleanup -> Miscellaneous".

[![Picture 2](/content/images/business-central/automated-detached-media-cleanup/Picture2.png)](/content/images/business-central/automated-detached-media-cleanup/Picture2.png)

Here, we have the actions to Load any detached Media and then delete them individually.
I tried many ways to recreating the scenario where detached media exist but I couldn't get it to work, so if any of you know how to re-create this do let me know!

[![Picture 3](/content/images/business-central/automated-detached-media-cleanup/Picture3.png)](/content/images/business-central/automated-detached-media-cleanup/Picture3.png)

Finally there's also an option to run it automatically periodically to prevent buildup of detached media taking up storage space.

[![Picture 4](/content/images/business-central/automated-detached-media-cleanup/Picture4.png)](/content/images/business-central/automated-detached-media-cleanup/Picture4.png)

## Conclusion

Thus we saw how we can use the inbuild tool "Detached Media Clean up" to free up database space. 

Happy Coding!
