---
title: "Configuring Logo Printing on POS"
date: 2021-05-12T23:13:33+05:30
draft: false
tags: ['LS Central']
categories: ['Technical']
summary: 'How to configure Logo Printing on POS for LS v16'
featured_image: 'https://i.ibb.co/gVxwwsm/image.png'
---

# Introduction

Every Retail Store has a certain Logo to printing on their POS Receipt. 

LS Central provides build in support for this functionality and makes it a matter of minutes to change the Logo and/or it's properties. 

In this blog, we will be looking at how to configure this feature.

## Pre-requisites
- Microsoft Dynamics 365 Business Central 
- LS Central


## References

[LS Central Documentation](https://help.lscentral.lsretail.com/Content/LS-Retail/POS/How-To/How%20to%20Setup%20Receipt%20Logo.htm?TocPath=Retail%7CPoint%20of%20Sale%7CPOS%7CHow%20to%20...%7C_____17)


## Configuration

First, we need to make sure that the image we are passing is proper. 

Make sure that the Image is in Bitmap or .bmp. 

Other than this, unless your POS Printer supports it, make sure the image is gray scaled. 

I used [this](https://convertimage.net/online-photo-effects/black-and-white-photo-fx.asp) website for conversion.

Store the Image on the local system, make sure the folder and the image do not require any special permissions to access.

In Business Central, search for POS Printers and open the POS Receipt Printer which you are using. 

![Image](https://i.ibb.co/Nt3BD61/image.png)

In the Logo tab, add the location of the Image and set the other properties. 

Since, we are using the Image which is on our Local System, set the Logo Type as "Download".

![Image](https://i.ibb.co/gVxwwsm/image.png)

Open the POS and generate a POS Receipt. 

**Note**: In some cases Logo is not visible on the Virtual Printer, it is recommended to test the configuration on an actual POS printer. 

## Conclusion

Thus, in this blog we saw how to configure Logo on POS Receipt.

Happy Coding!