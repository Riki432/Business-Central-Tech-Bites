---
title: "Using Web Content on POS"
date: 2021-03-03T23:13:47+05:30
draft: false
tags: ['LS Central']
categories: ['Technical', 'Functional']
summary: 'How to use Web Content on POS in LS v16'
featured_image: 'https://i.ibb.co/XxrG4Pz/image.png'
---

# Introduction

LS Central allows us to use HTML content on the POS which includes both Text and Images. 

Users can add extra information related to the Items here which can assist in the POS Users to make the sales much more efficiently.

In this blog, I'll be demonstrating how to configure the same.

## Pre-requisites

- Microsoft Dynamics 365 Business Central 
- LS Central v16

## References

[LS Central Documentation](https://help.lscentral.lsretail.com/Content/Fields/T_10001411.htm)

## Configuration

Open Business Central and search for POS Terminals.

![Image](https://i.ibb.co/9nNcwpn/image.png)

Open the POS Terminal for the current Store and set the "Item HTML" and "Item Image" property to true.

![Image](https://i.ibb.co/VL3jB3p/image.png)

Search for Retail Items and open the Item you want to add description and image for.

![Image](https://i.ibb.co/xXtRzxX/image.png)

Open the Item Card and Go to Navigate -> Master Data -> Item HTML. 

![Image](https://i.ibb.co/LgjH2RL/image.png)

Here you can specify the description for the Item that you want to be displayed on the POS and click on Save. 

For instance:

![Image](https://i.ibb.co/9TjgXq4/image.png)

After that go to Navigate -> Master Data -> Images and click on New.

![Image](https://i.ibb.co/hYJn7hv/image.png)

Click on Import and select the Image of that Item and then Click on OK.

![Image](https://i.ibb.co/1JBWnqY/image.png)

Go to POS and search for the Item.

![Image](https://i.ibb.co/10Kggp8/image.png)

Double Click on the description of that Item to see the Image and the HTML Content.

![Image](https://i.ibb.co/XxrG4Pz/image.png)

You can even embed Videos if required!

![Image](https://i.ibb.co/SyxrmCC/image.png)

## Conclusion

Thus, in this blog we saw how we can utilize HTML content on POS.

As an additional side note I'd like to mention even using Javascript is possible, to a certain extent, so for those who are curious you can even create basic games for it.

Happy Coding!