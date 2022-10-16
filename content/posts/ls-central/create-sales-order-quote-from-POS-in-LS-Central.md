---
title: "Create Sales Order Quote From POS in LS Central"
date: 2022-09-04T17:24:33+05:30
draft: false
tags: ['LS Central']
categories: ['Technical']
summary: 'How to create a Sales Order or Sales Quote directly from POS'
featured_image : '/content/images/ls-central/create-sales-order-quote-from-POS-in-LS-Central/Image2.png'
---
# Introduction

LS Central allows us to create a Sales Order or Sales Quote directly from POS.
I will be demonstrating the same below in this blog.

## Pre-requisites
1. LS Central v16+
2. Business Central OnPrem/OnCloud

## References

[LS Central Documentation](https://help.lscentral.lsretail.com/Content/Fields/T_10001439_17.htm)

## Configuration
Search for “Sales Type” in Business Central

<!-- ![Image 1](https://i.ibb.co/KqdsDhc/image.png) -->
![Image](/content/images/ls-central/create-sales-order-quote-from-POS-in-LS-Central/Image1.png)

Create a new record titled “SALES ORDER”  in it. Make sure to set the Suspend Type to Sales Order/Sales Quote as required. I am setting it to Sales Order for this example.

<!-- ![Image 2](https://i.ibb.co/XJx8mPz/image.png) -->
![Image](/content/images/ls-central/create-sales-order-quote-from-POS-in-LS-Central/Image2.png)

Log In to your POS with a POS Super User account and Right click on a button and go to button properties, I’m using the default “SUSPEND” button for example here.

<!-- ![Image 3](https://i.ibb.co/bNc66Tq/image.png) -->
![Image](/content/images/ls-central/create-sales-order-quote-from-POS-in-LS-Central/Image3.png)

Set the command to “SUSPEND” and the parameter to the “Sales Order” record you created a few moments ago.

<!-- ![Image 4](https://i.ibb.co/tbxv0P2/image.png) -->
![Image](/content/images/ls-central/create-sales-order-quote-from-POS-in-LS-Central/Image4.png)

Once this is done, create a new Transaction with a Customer and then click on the button. In the confirmation box, click on Yes.

<!-- ![Image 5](https://i.ibb.co/ssBJS74/image.png) -->
![Image](/content/images/ls-central/create-sales-order-quote-from-POS-in-LS-Central/Image5.png)

If you check in Business Central now, you can see that a new Sales Order has been created.

<!-- ![Image 6](https://i.ibb.co/gr8tFvR/image.png) -->
![Image](/content/images/ls-central/create-sales-order-quote-from-POS-in-LS-Central/Image6.png)

You can also see the same from POS itself if you click on the “Sales Order” button that we created just now.

<!-- ![Image 7](https://i.ibb.co/HVmjC7Q/image.png) -->
![Image](/content/images/ls-central/create-sales-order-quote-from-POS-in-LS-Central/Image7.png)

## Conclusion

Thus we saw how to create a Sales Order/Sales Quote directly from POS.

Happy Coding!

