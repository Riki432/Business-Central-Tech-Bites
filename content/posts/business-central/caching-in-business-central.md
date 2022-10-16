---
title: "Caching in Business Central"
date: 2022-10-16T16:35:58+05:30
draft: false
tags: ['Business Central']
categories: ['Technical']
summary: 'A general idea about caching in business Central'
featured_image: '/content/images/business-central/caching-in-business-central/Image2.png'

---

## References
- [Data Access - Microsoft Docs](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/administration/optimize-sql-data-access)
- [Select Latest Version - Microsoft Docs](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/database/database-selectlatestversion-method)

## Explanation

Caching is one of the methods which systems use to improve performance and respond to requests rapidly.
In a Business Central system, caching is done at two levels:
1. Business Central Server Instance Data Cache
2. SQL Server Data Cache.

Whenever a User requests data from Business Central, it firsts check whether 
1. The data is available in the Server Instance's cache, 
2. If not, then it checks the SQL Server Data Cache,
3. And if not here then it fetches the data from the database.

The Business Central Server Instance's Cache is accessible to all the Users connected to that Server Instance.
There are two types of cache stored here, 
1. Global Cache
2. Private Cache

Global cache is the one which is accessible to all the Users connected to the SQL Server.
Private cache is only accessible over a transaction, for a particular User, for a particular company. This cache is cleared as soon as the transaction is completed.

Which cache is to be used for which User depends on whether the Table from which the User is requesting data is locked or not. In case it is locked, Private Cache is queried else Global Cache is queried.

The following procedures in Business Central support using Cache:
1. GET
2. GETBYSYSTEMID
3. FIND
4. FINDFIRST
5. FINDLAST
6. FINDSET
7. COUNT
8. ISEMPTY
9. CALCFIELDS

Whenever we make a call to the "FIND" functions, 1024 records are cached. The Data Cache size in Business Central can be changed using the "Data Cache Size" setting of the Business Central Server Configuration file. The default value is set to 9 which is equivalent to 500mb. Increasing the value by 1 doubles the cache size.

![Image](/content/images/business-central/caching-in-business-central/Image1.png)

If we want to latest data from the database to be fetched, i.e. if we want to bypass the cache, we can use the "SelectLatestVersion" procedure. 

![Image](/content/images/business-central/caching-in-business-central/Image2.png)

Just another note the results from Query objects in Business Central are not cached.

If there are multiple Server Instances over a single database, Business Central synchronizes the cache every 30 seconds by default. We can change this by using the "CacheSynchronizationPeriod" parameter in the CustomSettings.config file.

## Conclusion

Thus we saw how to Caching works in Business Central and how we can optimize it usage for maximum performance in Business Central.
Happy Coding!
