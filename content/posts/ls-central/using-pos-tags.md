---
title: "Using POS Tags"
date: 2021-02-19T23:13:17+05:30
draft: false
tags: ['LS Central']
categories: ['Technical']
summary: 'How to use Tags in POS in LS Central for v16'
featured_image: 'https://i.ibb.co/Lk3S1sg/image.png'
---

# Introduction

Tags are small pieces of Information that we can display on the POS.

This information may be a field from a table or just some text.

If we are using a field from some table, it is necessary that, the table can be referenced using only the fields available in the current "POS Transaction" record.

There are multiple types of Tags available like:
1. **System** :- These Tags display system information.
2. **Transaction** :- These Tags display information regarding the current Transaction.
3. **Session**:- These Tags display information regarding the current Session.

## Pre-requisites
- Microsoft Dynamics 365 Business Central
- LS Central

## References
[LS Central - Tags](https://help.lscentral.lsretail.com/Content/LS%20Retail/POS/Data/Tags.htm)

## Configuration
In most cases, we are going to use "Transaction" type Tags so let take an example.

In this example, we are going to create a Tag which will display the manager of the Store.

#### To create a Tag:

Search for POS Tag in BC

![Image](https://i.ibb.co/6brkXty/image.png)

Create a new POS Tag, by convention the naming is <#TagName> so we are going to follow the same.

![Image](https://i.ibb.co/B6qN4VC/image.png)

Since the data we need is from the "Store" table we set the "Store" table's ID in the "Table No." field  and as we need the "Manager Name" from the "Store" record, we set the "Field No." accordingly. 

![Image](https://i.ibb.co/GMFDkKj/image.png)

In the "POS Trans. Key Field" we specify which field will be used to reference the table mentioned in the "Table No." field which, in our case, is Store. This list of fields is from the "POS Transaction" table.

In the "Expression" we can specify how the data should be presented, %1 is substituted for the data.

![Image](https://i.ibb.co/7kzjqvP/image.png)

On the POS, we can use this Tag in the "Description" field of any and all Menu Lines, for example, we can use this as the name of a button, thus the button will change depending on which Store it is being used on.  

In this example, I am going to set it on "Manager" button on POS.

Right Click on the "Manager" button and click on "Button Properties."

![Image](https://i.ibb.co/QXM5ZRQ/image.png)

Click on the three dots and choose the "Tag" that we just created and click on OK.

![Image](https://i.ibb.co/0Knv3Gm/image.png)

Click on OK again so that the "Button Properties" page closes.

![Image](https://i.ibb.co/Ks7bzZK/image.png)

The button now shows the "Manager Name" field of the Store, in the expression that we provided.

![Image](https://i.ibb.co/Lk3S1sg/image.png)

![Image](https://i.ibb.co/nLhs1zS/image.png)

## Conclusion
Thus, we saw how to configure and use "Tags" in POS, in LS Central.

Thanks for reading!

Happy Coding!