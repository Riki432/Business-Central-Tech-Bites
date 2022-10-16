---
title: "Configuring Barcodes in LS Central"
date: 2021-05-12T16:40:58+05:30
draft: false
tags: ['LS Central']
categories: ['Technical', 'Functional']
summary: 'How to configure Barcode printing in LS Central v16'
featured_image: '/content/images/ls-central/configuring-barcodes-in-ls-central/Image4.png'
---

# Introduction
Refunding a transaction is an everyday occurrence in Retail. 

LS Central provides us with the functionality to initiate the refund of a transaction by simply scanning one barcode!

In this blog, we will be looking at how to configure this feature.

## Pre-requisites
- Business Central
- LS Central v16

## References
[Printing Receipt Barcodes - LS Central Documentation](https://help.lscentral.lsretail.com/Content/LS-Retail/POS/How-To/Printing-Receipt-Barcodes.htm)

## Configuration

From Business Central, open the POS Terminal for the current Store.

<!-- ![Image](https://i.ibb.co/SJwHnrj/image.png) -->
![Image](/content/images/ls-central/configuring-barcodes-in-ls-central/Image1.png)

In the "Printing" tab, 
1. Set the "Receipt Barcode" ID to 101.
2. Set the "Print Receipt BC Type" to "CODE39" or "CODE128_A".
3. You can optionally adjust the Barcode Height and Width but depending upon the POS Printer it may or may not be scannable as the resolution of the barcode suffers. 
    The default parameters which are applied if you leave the fields to 0 are width - 8 and height 40.
4. Set the "Receipt Barcode" to true.


<!-- ![Image](https://i.ibb.co/KwbnwD5/image.png) -->
![Image](/content/images/ls-central/configuring-barcodes-in-ls-central/Image2.png)

Once this is done, simply run the POS and generate a Receipt.

When the Barcode at the bottom of the Receipt is scanned it should directly take the User to the refund screen of the POS.

For instance, this is how it looks on the Virtual Printer.

<!-- ![Image](https://i.ibb.co/nmp8Mn5/image.png) -->
![Image](/content/images/ls-central/configuring-barcodes-in-ls-central/Image3.png)

While, this is how it looks when using a real printer.

<!-- ![Image](https://i.ibb.co/KxsFmT6/image.png) -->
![Image](/content/images/ls-central/configuring-barcodes-in-ls-central/Image4.png)

## Conclusion

Thus, in this blog we saw how to configure Barcodes on POS Receipt.

Happy Coding!