---
title: "Apply Multiple Entries to Each Other"
date: 2022-10-01T19:56:11+05:30
draft: false
tags: ['Business Central']
categories: ['Technical']
summary: 'How to apply multiple posted entries to each other in Business Central using AL'
featured_image: '/content/images/business-central/apply-multiple-entries-to-each-other/Image6.png'
---

# Introduction

While trying to implement a functionality of automatically applying any open invoices for a Customer with the open Payments for the said customer; I observed that there was no quick and easy method to post the application directly.

This can be very useful in environments where Payment Entries are created via Integrations without specifying the invoice it needs to be applied to. 

I read around online but couldn't find any blogs with the latest method of doing so in Business Central.

As such, I spent a good portion of my day debugging the process of applying entries, from start to end as written by Microsoft and to save your time I'm going to jot down my findings here.

## Pre-requisites
Business Central OnPrem/Cloud

## Configuration
<!-- ![Image](https://i.ibb.co/yF5KwVd/image.png) -->
![Image](/content/images/business-central/apply-multiple-entries-to-each-other/Image1.png)

Here as an example I'm using a processing report to iterate over all the open Payments in the system and the indented dataitem will iterate over all the open Invoices of the same Customer. 

The method of iteration and validations may vary however the general logic will remain the same.

<!-- ![Image](https://i.ibb.co/nR8TRDx/image.png) -->
![Image](/content/images/business-central/apply-multiple-entries-to-each-other/Image2.png)

This is what happens in the background when we click the "Apply Entries" action on a Customer Ledger Entry (I'm using Payment entry in this instance) in the background.


```
Payments."Applying Entry" := true;
Payments."Applies-to ID" := UserId;
Payments."Amount to Apply" := Payments."Remaining Amount";

Codeunit.Run(Codeunit::"Cust. Entry-Edit", Payments);
Commit();
```

Here, after this we set the selected Customer Ledger Entry on the Apply Customer Entries Worksheet and display all the open entries which can be applied against it.

<!-- ![Image](https://i.ibb.co/GvXfdH7/image.png) -->
![Image](/content/images/business-central/apply-multiple-entries-to-each-other/Image3.png)

This is what happens, when we select an entry and click on the "Set Applies-To-ID" action.

```
CU_CustSetApplyID.SetApplId(Invoices, Payments, UserId);
Commit();
```

It calls the *SetApplId* procedure of the **Cust. Entry-SetAppl.ID"** Codeunit [ID - 101], which mainly updates the following fields, in the Applying Entry:
- "Applies to ID"
- "Amount to Apply" 


<!-- ![Image](https://i.ibb.co/PwqwfVw/image.png) -->
![Image](/content/images/business-central/apply-multiple-entries-to-each-other/Image4.png)

Then, after we click on the "Post Application" action, standard Business Central allows us to change some parameters regarding the posting by using the "Post Application" page.

```
PostApplication.SetParameters(ApplyUnapplyParameters);
if ACTION::OK = PostApplication.RunModal() then begin
    PostApplication.GetParameters(NewApplyUnapplyParameters);
    if NewApplyUnapplyParameters."Posting Date" < ApplicationDate then
        Error(ApplicationDateErr, Rec.FieldCaption("Posting Date"), Rec.TableCaption());
    end else
        Error(ApplicationProcessCanceledErr);
```
<!-- ![Image](https://i.ibb.co/yPyxjRG/image.png) -->
![Image](/content/images/business-central/apply-multiple-entries-to-each-other/Image5.png)

Since, we are going this programatically, we'll set the values we need directly.

```
ApplicationDate := CustEntryApplyPostedEntries.GetApplicationDate(Invoices);

Rec_ApplyUnapplyParameters.CopyFromCustLedgEntry(Invoices);
Rec_ApplyUnapplyParameters."Posting Date" := ApplicationDate;

Rec_GLSetup.GetRecordOnce();

if Rec_GLSetup."Journal Templ. Name Mandatory" then begin
    Rec_GLSetup.TestField("Apply Jnl. Template Name");
    Rec_GLSetup.TestField("Apply Jnl. Batch Name");
    Rec_ApplyUnapplyParameters."Journal Template Name" := Rec_GLSetup."Apply Jnl. Template Name";
    Rec_ApplyUnapplyParameters."Journal Batch Name" := Rec_GLSetup."Apply Jnl. Batch Name";
end;

CustEntryApplyPostedEntries.Apply(Invoices, Rec_ApplyUnapplyParameters);
```

<!-- ![Image](https://i.ibb.co/Nsc27Bd/image.png) -->
![Image](/content/images/business-central/apply-multiple-entries-to-each-other/Image6.png)

You can find the entire source code [here](https://pastebin.com/wr8jHsXf).

## Conclusion
Thus we saw how we can write our custom code to apply customer ledger entries against each other.

I hope this helps save your time!

Happy Coding!
