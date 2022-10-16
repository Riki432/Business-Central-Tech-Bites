---
title: "Using Security Filters in Business Central"
date: 2021-07-15T16:50:24+05:30
draft: false
tags: ['Business Central']
categories: ['Technical', 'Functional']
summary: 'How to use Security Filters in Business Central'
featured_image: '/content/images/business-central/using-security-filters-in-business-central/Image7.png'
---

# Introduction
Business Central allows various levels of security that can be used to restrict User access to different features or objects.

We can use Permission Sets to prevent User access to specific objects like reports or pages.

For more refined, row-level authorization we can use Security Filters to restrict access to individual record based on some filters.

## Pre-requisites
- Business Central OnCloud or OnPremise.

## References
[Security Filters - Microsoft Documentation](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/security/security-filters)

## Configuration
Suppose, you want the User to only be able to access a specific set of Customers.

You can either create your own Permission Set from scratch, in which you will describe all the objects that the User will have access to or you can copy one of the existing ones by clicking on "Copy Permission Set" 
and then entering a new name for the permission set. 

Do note that you require proper permissions to make changes to Permission Sets as well.

Open the Permission Set, by clicking on the "Permissions" action and Scroll to the Right.

<!-- ![Image](https://i.ibb.co/jMRb8yv/image.png) -->
![Image](/content/images/business-central/using-security-filters-in-business-central/Image1.png)

Click on the three dots next to the Security Filter field.

<!-- ![Image](https://i.ibb.co/jGpLSrc/image.png) -->
![Image](/content/images/business-central/using-security-filters-in-business-central/Image2.png)

Select the field(s) which you want to filter by clicking on the three dots next to the Field Number and then click on OK.

<!-- ![Image](https://i.ibb.co/mStDJXN/image.png) -->
![Image](/content/images/business-central/using-security-filters-in-business-central/Image3.png)

<!-- ![Image](https://i.ibb.co/dQpxt2H/image.png) -->
![Image](/content/images/business-central/using-security-filters-in-business-central/Image4.png)

Set a value for the filter in the "Field Filter" field. You can add as many filters as required and any Business Central filter is valid in this field (Except for wildcard characters). 

Once you are done, click on Close.

<!-- ![Image](https://i.ibb.co/qrsZhnF/image.png) -->
![Image](/content/images/business-central/using-security-filters-in-business-central/Image5.png)

Click on OK and add (in case there are no other permission sets and you have created your own) or replace (in case you have copied the permission set) the new permission set onto the User in the "User Permission Sets" tab of the User card.

<!-- ![Image](https://i.ibb.co/VmszBGz/image.png) -->
![Image](/content/images/business-central/using-security-filters-in-business-central/Image6.png)

Login to the User Account and verify that only the records that match the mentioned filters are visible to the Users.

<!-- ![Image](https://i.ibb.co/ySPtnH0/image.png) -->
![Image](/content/images/business-central/using-security-filters-in-business-central/Image7.png)

## Conclusion

Thus we saw how to create and configure security filters in Business Central for maintaining record level security.

As a side note, I would like to highlight that in Business Central, in case a User has multiple Permission Sets containing different levels of permissions for the same object then Business Central combines these Permission Sets and uses the least restrictive group of Permissions. 

As such if you apply a Permission Set with a Security Filter and another Permission Set without the filter on the same object, Business Central will use the one without the Security Filter as it is least restrictive. 

Happy Coding!
