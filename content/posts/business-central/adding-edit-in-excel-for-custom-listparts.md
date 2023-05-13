---
title: "Adding Edit in Excel for Custom Listparts"
date: 2022-10-16T23:57:22+05:30
draft: false
tags: ['Business Central']
categories: ['Technical']
summary: 'How to add Edit in Excel functionality for custom list parts'
featured_image: '/content/images/business-central/adding-edit-in-excel-for-custom-listparts/Image2.png'
---

# Introduction
Business Central provides us an easy method of modifying our data from within Excel using Web Services commonly found in the Edit in Excel action. 

This can be seen in the commonly used List Pages for example Payment Terms. 

However this functionality can be missing for certain pages or you might want to have additional logic or filtering before executing this. 

For this I'll be demonstrating how to add the "Edit in Excel" action in Business Central pages.

![Image](/content/images/business-central/adding-edit-in-excel-for-custom-listparts/Image1.png)

## Pre-requisites
Business Central Cloud

## References

[Viewing and Editting in Excel - Microsoft Docs](https://docs.microsoft.com/en-us/dynamics-nav/using-filter-expressions-in-odata-uris)

## Configuration

![Image](/content/images/business-central/adding-edit-in-excel-for-custom-listparts/Image2.png)

In the above piece of code, I've added the "Edit in Excel" action onto the Blanket Sales Order SubForm to allow for easily adding lines using Excel.

Firstly, we define the filters that we will be using on the page that we will be passing in the "EditWorksheetInExcel" procedure of the "OdataUtility" codeunit.

Note that these filters are defined as Odata expressions as the "Edit in Excel" functionality uses Excel behind the scenes.

In the next lines, we see that we pass the Page Caption, the page ID and the filters to be set on the page.

Under the hood, the procedure creates a Published Web Service using the provided Page ID and uses that for the data manipulation.

We had to prepend the additional "00000" as the procedure has been hardcoded to use "COPYSTR("00000" + {PageID}, 5)" meaning it starts reading after the 5th character. 

## Conclusion
Thus we saw how to configure Edit in Excel for pages that do not have built in Excel functionality.

Also note that Microsoft has expanding the Edit in Excel functionality to many pages in Business Central since v19 Wave 2 but this can still be handy. 

Happy Coding!
