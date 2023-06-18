---
title: "Navigation in Business Central APIs"
date: 2023-06-18T14:14:43+05:30
draft: false
tags: ['Business Central']
categories: ['Technical']
summary: 'How to use navigation in Business Central APIs to get sub-records for a parent record.'
featured_image: '/content/images/business-central/navigation-in-business-central-APIs/Picture3.png'
---

# Introduction
Business Central provides us a standard set of API pages which we can use for performing CRUD Operations on records. 

In addition to this it also provides us with "Containments" feature, which lets us fetch records related to a certain record.

## Pre-requisites
- Business Central onCloud or On-Premise.
- Postman (For Testing)

## References
[Using Containments and Associations - Business Central | Microsoft Docs](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/webservices/use-containments-associations)


## Usage
Go to Web Services.

Click on Actions and download the Metadata for that Web Services.

[![Picture 1](/content/images/business-central/navigation-in-business-central-APIs/Picture1.png)](/content/images/business-central/navigation-in-business-central-APIs/Picture1.png)

In case of the "Sales Order API", the actual sub-page is named *salesOrderLines*, so the endpoint for Navigation would be *{ParentServiceName}{SubPageName}* which in this case would be *salesOrderssalesOrderLines*.

[![Picture 2](/content/images/business-central/navigation-in-business-central-APIs/Picture4.png)](/content/images/business-central/navigation-in-business-central-APIs/Picture4.png)

We can see the same in the Metadata document as well.

[![Picture 3](/content/images/business-central/navigation-in-business-central-APIs/Picture2.png)](/content/images/business-central/navigation-in-business-central-APIs/Picture2.png)

Use the following format for calling the Containment endpoint - salesOrders(Document ID)/salesOrderssalesOrderLines.

[![Picture 3](/content/images/business-central/navigation-in-business-central-APIs/Picture3.png)](/content/images/business-central/navigation-in-business-central-APIs/Picture3.png)

This returns an array, which contains the list of that particular Sales Order's Lines.

You can create these associations in your own APIs as well by adding a subpage to your API page or Web Service.

## Conclusion
Thus we saw how we can use Navigation in Business Central APIs to directly access sub-page data in APIs.

Happy Coding!
