---
title: "Block Items on POS"
date: 2022-09-23T19:33:57+05:30
draft: false
tags: ['LS Central']
categories: ['Functional']
summary: 'How to block Items on POS in LS Central'
featured_image: 'https://i.ibb.co/jrNQcX1/image.png'
---

# Introduction
LS Central has its own unique way of preventing Items from being sold which is different from the standard "Blocked" option field we get on the Item Card.
It also comes with detailed and refined permissions which can fit most business needs.
All of this is done using another related table known as "Item Status" 

## Pre-requisites
- Business Central OnCloud/OnPrem
- LS Central v16

## References
1. [LS Retail Documentation](https://help.lscentral.lsretail.com/Content/Fields/T_10001403.htm)
2. [How to block Items from POS](https://www.navisiontech.com/how-to-block-items-from-sale-at-the-pos/)

## Configuration
1. Open the Retail Item Card for the Item you want to block.

![Image](https://i.ibb.co/8BH9CWm/image.png)

2. Open the "Item Status" for that Item.

![Image](https://i.ibb.co/Hgytc0T/image.png)

3. Click on the "Status Code" and Click on "Select from full list"

![Image](https://i.ibb.co/pfVH1KH/image.png)

![Image](https://i.ibb.co/k3yb1D1/image.png)

4. Create a new record with code "BLOCKED" and enable all the fields.

5. Here, you can see all the detailed controls available.

![Image](https://i.ibb.co/vX0K71T/image.png)

![Image](https://i.ibb.co/jrNQcX1/image.png)

## Conclusion
Thus, we saw how we can Block Items on POS in LS Central and other finer controls available at our disposal in LS Central.

Happy Coding!