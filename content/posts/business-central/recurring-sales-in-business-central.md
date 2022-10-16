---
title: "Recurring Sales in Business Central"
date: 2022-10-16T16:56:14+05:30
draft: false
tags: ['Business Central']
categories: ['Functional']
summary: 'How to configure recurring sales for an individual Customer in Business Central'
featured_image: '/content/images/business-central/recurring-sales-in-business-central/Image6.png'
---

# Introduction
In this blog, we'll be looking at how to reduce manual work in creating Sales Line in Business Central. 
For this, we'll be using the Out of the Box feature of "Recurring Sales Lines."

## Pre-requisites
- Business Central OnPrem or Cloud

## References
[Standard Recurring Sales - Microsoft Docs](https://docs.microsoft.com/en-us/dynamics365/business-central/sales-how-work-standard-lines)

## Configuration
Search for Recurring Sales Lines in Business Central global search and then click on New.

Enter a Code for Identification, a short description and the Currency Code, if applicable.

In the Lines, enter the Sales Line which are to be re-created. You can also define a Quantity if you want, it can be easily over-written if necessary.

<!-- ![Image](https://i.ibb.co/ydNyRHX/image.png) -->
![Image](/content/images/business-central/recurring-sales-in-business-central/Image1.png)

Go to the Customer Card for whom the Recurring Sales Line we created is going to be applicable.

Then Go to Related > Sales > Recurring Sales Lines.

![Image](/content/images/business-central/recurring-sales-in-business-central/Image2.png)

Set the Code of the Recurring Sales Line, we just created and set the Valid From and Valid to Dates.

![Image](/content/images/business-central/recurring-sales-in-business-central/Image3.png)

The Insert Rec. Lines have the following options which have the following impact:
**Manual** - System allows you to add the lines as and when required. Using the "Get Recurring Sales Lines" action.

![Image](/content/images/business-central/recurring-sales-in-business-central/Image4.png)

**Automatic** - System adds the recurring lines automatically whenever the Document is created.

![Image](/content/images/business-central/recurring-sales-in-business-central/Image5.png)

**Always Ask** - System shows a notification above which allows you to fetch the Recurring Lines in one click.

![Image](/content/images/business-central/recurring-sales-in-business-central/Image6.png)

## Conclusion

Thus, we saw how to configure Recurring Sales Lines in Business Central which is a very useful tool in reducing manual work.

Happy Coding!
