---
title: "Customizing POS Receipt in LS Central"
date: 2022-03-31T22:46:14+05:30
draft: false
tags: ['LS Central']
categories: ['Technical']
summary: 'How to customize POS Receipt in LS Central with/without Customzation'
featured_image: '/content/images/ls-central/customizing-POS-receipt-in-ls-central/Image14.png'

---

# Introduction
POS Receipts are generated after every transaction that occurs on POS. The default receipt provided by LS Central is generally sufficient but as is in all things there are always exceptions.

There are two methods that we can modify the POS Receipts and we are going to see them both.

## Pre-requisites
- Microsoft Dynamics 365 Business Central 
- LS Central

## Configuration

<!-- ![Image](https://i.ibb.co/1bdhgCX/image.png) -->
![Image](/content/images/ls-central/customizing-POS-receipt-in-ls-central/Image1.png)

This is the default receipt provided by LS. I have marked division of sections using color.
**Red** - Header
**Green** - Body
**Blue** - Footer

Without going with customization, we can still make some degree of changes to the standard layouts

1. Using Receipt Printing from POS Terminal / Store Card

- We can add text directly into the Header or the Footer of the POS Receipts and also define some basic properties like bold, italic or wide for the text. It can be defined at POS Level or Store Level i.e. for individual POS Terminals or for all the POS Terminals in a Store.
- Go to POS Terminal Card.
- Go to Printing -> Receipt Printing

<!-- ![Image](https://i.ibb.co/4Tps7Y9/image.png) -->
![Image](/content/images/ls-central/customizing-POS-receipt-in-ls-central/Image2.png)

<!-- ![Image](https://i.ibb.co/g6GThbg/image.png) -->
![Image](/content/images/ls-central/customizing-POS-receipt-in-ls-central/Image3.png)

- Here you add static content, like Store Name, GST/VAT No, Store Address, etc in both header and footer.
- Here you can also define, if you want to specify the Item No. or Barcode in the POS Receipt.
- Similar, to this, we can also define for Store level, i.e. all the POS Terminals in a Store.

<!-- ![Image](https://i.ibb.co/2cqG1Q5/image.png) -->
![Image](/content/images/ls-central/customizing-POS-receipt-in-ls-central/Image4.png)

<!-- ![Image](https://i.ibb.co/C1Dpszp/image.png) -->
![Image](/content/images/ls-central/customizing-POS-receipt-in-ls-central/Image5.png)

2. Using the "POS Print Utility" procedure (Customization):

In this method, we will write actual code to modify the receipt. 

If you are using NAV, then this is pretty straight forward, but in case of Business Central, we only have access to Events which we can subscribe to, to change the behaviour of the procedure.

<!-- ![Image](https://i.ibb.co/pXdFCm6/image.png) -->
![Image](/content/images/ls-central/customizing-POS-receipt-in-ls-central/Image6.png)

The highlighted four procedures do the majority of the work done in printing.

*PrintHeader* -> Prints the content of the header defined in the Receipt Printing.

<!-- ![Image](https://i.ibb.co/4sWP1Pz/image.png) -->
![Image](/content/images/ls-central/customizing-POS-receipt-in-ls-central/Image7.png)

*PrintSubHeader*: It prints the Information related to the current Transaction.

<!-- ![Image](https://i.ibb.co/RpMYwmW/image.png) -->
![Image](/content/images/ls-central/customizing-POS-receipt-in-ls-central/Image8.png)

*PrintSalesInfo*: It prints the actual Items of the Transaction along with VAT and other details.

<!-- ![Image](https://i.ibb.co/0n2wf9p/image.png) -->
![Image](/content/images/ls-central/customizing-POS-receipt-in-ls-central/Image9.png)

*PrintFooter*: It prints the Footer Text defined in the Receipt Printing.

<!-- ![Image](https://i.ibb.co/mTbNgf5/image.png) -->
![Image](/content/images/ls-central/customizing-POS-receipt-in-ls-central/Image10.png)

Now that we know which procedure is responsible for which part of the Receipt, we can subscribe to that procedure's event.

For example, let's try me modify the "Sub Header" part of the Receipt.

As such we need to modify the "PrintSubHeader" procedure, so we subscribe to its event.

<!-- ![Image](https://i.ibb.co/pwZDy5z/image.png) -->
![Image](/content/images/ls-central/customizing-POS-receipt-in-ls-central/Image11.png)

The parameter, sender gives us a reference to the current instance of "POS Print Utility" which we can use to call all the procedures of that codeunit with the proper values.

TransactionHeader is the current "Transaction Header" record.

At the start of the procedure, we need to set the IsHandled variable to True so that once your procedure ends, the main "PrintSubHeader" procedure exits immediately.

<!-- ![Image](https://i.ibb.co/rMr7QNh/image.png) -->
![Image](/content/images/ls-central/customizing-POS-receipt-in-ls-central/Image12.png)

**DSTR** - It is the design String, here we define the design of the Line that will be printed. It is at max up to 40 characters. It follows the pattern "#(alignment)##...". The Design String is divided into sections, each section contains one piece of data.

**Value** - It is a text array, which defines the data which is to be printed in the sections. The number of values set in the Value should be equal to the sections in the design string.

**Node** - It is used as a Label for the data in the section. The number of values in this array should be the same as the values in Value array.

Next, the essential part is the "FormatStr" procedure, the 4 booleans at the end are used to specify whether the String is going to be Wide, Bold, High or Italic respectively.

After this, the final piece of the puzzle is the "AddPrintLine" procedure, the first argument is the "Section ID", it is related to which part of the receipt we are printing in, it is better to set it the same as the procedure that we are customizing.

Next argument, specifies the maximum number of Sections that will be in the design string, just make sure it is more than the values you have provided.

Next, we pass the Node and Value array, the Design String and specify whether the String is going to be Wide, Bold, High or Italic and the Tray at the end. The value for Tray can be taken directly from the Event's parameters.

Similar to this, we will add one more line and then we will check the results.

<!-- ![Image](https://i.ibb.co/yyPm3gf/image.png) -->
![Image](/content/images/ls-central/customizing-POS-receipt-in-ls-central/Image13.png)

The "PrintSeperator" procedure is used to draw a horizontal line across the receipt using dashes.

Here is the final result:

<!-- ![Image](https://i.ibb.co/dpkxhPs/image.png) -->
![Image](/content/images/ls-central/customizing-POS-receipt-in-ls-central/Image14.png)

## Conclusion

Thus we saw how to customize POS Receipts in LS Central either through POS/Store Receipt Printing or for advanced customizations through Event subscriptions.

Happy Coding!