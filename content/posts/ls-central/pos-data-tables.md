---
title: "POS Data Tables"
date: 2022-09-05T14:29:37+05:30
draft: false
tags: ['LS Central']
categories: ['Technical']
summary: 'How to create custom Data Tables which can be used on POS to display or interact with Data.'
featured_image: '/content/images/ls-central/pos-data-tables/Image3.png'
---

# Introduction
POS Data Tables are used to display data from any table in POS. The default POS Screen that we see where we enter our items for sale also consists of a Data Table. 

Data Tables are also used with Lookups, Record Zooms and Data Grids.

In this blog, we are going to create our own POS Data Table using the Customer Table.

## Pre-requisites
- Microsoft Dynamics 365 Business Central
- LS Central

## References
1. [LS Documentation - POS Data Tables](https://help.lscentral.lsretail.com/Content/LS%20Retail/POS/Data/Data%20Tables.htm)
2. [LS Documentation - Fixed Filter, POS Data Table Columns](https://help.lscentral.lsretail.com/Content/Fields/T_99001565_11.htm)
3. [LS Documentation - Special Field Type, POS Data Table Columns](https://help.lscentral.lsretail.com/Content/Fields/T_99001565_14.htm)


## Configuration

The most important fields in the General Tab are:
| Field                    | Description |
| :-----------              |   :-----------    |
| Table No                  | Specify the ID of the Table, whose data this Data Table will be showing on POS.       |
| Table Columns             | Specifies the columns that will be visible in the Data Table.        |
| Table Rows                | Specifies how many rows should be visible by default, if there are more you can simply scroll.  |
| Key Value Fields          | Specifies the key fields of the select table. |
| Start Position            | Defines which record should be selected when this Data Table is opened. |
| Selection Mode            | This is useful when you are using your Data Table in a lookup, the options available are "MultiSelect", "SelectOne" or "NoSelect." |
| Default Search Type       | Specifies the search type, the options available are: "Any Part", "Beginning" or "Whole."     |
| Default Search Command    | You can specify different commands like  |
| Distribution Location     | Specifies where the POS Data Table should get the data from. Do note that Web Service configuration should be done for this to work and if the record you selected does not exist on your local system, you may get an error. |

<!-- ![Image 1](https://i.ibb.co/JsqLZvt/image.png) -->
![Image 1](/content/images/ls-central/pos-data-tables/Image1.png)

For Data Table Columns:
In this tab, we specify the columns we want in our Data Table and the properties of those columns.

| Field                     | Description |
| :-----------              |   :-----------    |
| Column No.                |	Specifies the order of the Columns |
| Field No.                 |	Specifies the Field No. to be used from the Table for the column. |
| Key No.	                |   Specify a value in this field if you want to search using this field. |
| Fixed Filter              |	Specify a value in this field for filtering the table. |
| Preferred Width           |	Specify the preferred width of the column. |
| Default Column            |	Setting this value to true, makes the current column be selected by default when opening the data table. |
| Sort Fixed                |	Setting this value to true, disables changing the sort order for that column. |
| Special Field Type        |	 It is used to identify that the current column is a special type of field, there are very limited options on this field and we usually                          do not need to use them. Read more at Reference #3. |
| Editable                  |	Makes the field modifiable when we use Record Zoom Controls. |
| Validate Input            |	Validates the input when we use Record Zoom Controls. |
| Filter Tags               |	Used to set a filter using "POS Tags" on that column. |
| POS Command Code          |	Used to specify a Command which is to be executed when user clicks on this column. A good example of this is the "Quantity" column of main POS Screen which executes the "Change Quantity" command when clicked on it. |

<!-- ![Image 2](https://i.ibb.co/5B1tfNq/image.png) -->
![Image 2](/content/images/ls-central/pos-data-tables/Image2.png)

<!-- ![Image 3](https://i.ibb.co/RzVyC97/image.png) -->
![Image 3](/content/images/ls-central/pos-data-tables/Image3.png)

## Conclusion
Thus, we saw how to create our own Data Table and the different properties associated with a Data Table.

Thanks for reading!