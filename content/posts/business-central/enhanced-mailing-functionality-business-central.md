---
title: "Using Enhanced Mailing Functionality in Business Central"
date: 2022-09-23T19:58:04+05:30
draft: false
tags: ['Business Central']
categories: ['Technical']
summary: 'How to send mails using enhanced Mailing Functionality in Business Central'
featured_image: 'https://i.ibb.co/7tZ6wtc/image.png'
---

# Introduction
With SMTP Mail being deprecated, Business Central now provides us with a new and enhanced way for writing custom logic to send emails. 
To use this new functionality you have to first configure Email Accounts in Business Central, which you can find [here](https://www.cloudfronts.com/blog/d365-business-central/how-to-use-multiple-email-account-to-send-different-documents-using-email-setup/).

## Pre-requisites
- Business Central v20

## References
[Developing with enhanced mail feature](https://dankinsella.blog/developing-with-the-new-enhanced-email-feature/)

## Configuration
The new method uses the **Email Message (ID: 8904)** and **Email (ID: 8901)** Codeunits. 
I've added multiple actions below and I'll be describing what the expected behaviour is.

![Image](https://i.ibb.co/jh9vcwV/image.png)

![Image](https://i.ibb.co/L1Zz3Kw/image.png)

This is the simple piece of code which sends an email with the specified Recipients, CCs and BCCs.

We can specify multiple recipients and dynamically as the lists are not bound by size.

We can also call a simpler version of this method, where we don't need to specify the CC and BCC.

![Image](https://i.ibb.co/x27qmj1/image.png)

![Image](https://i.ibb.co/7tZ6wtc/image.png)

Using the *OpenInEditor* procedure of **Email** codeunit causes a page to be opened up where you can edit the message before you send it. 

You can also add attachments or you can save the message draft.

![Image](https://i.ibb.co/dmXxQcm/image.png)

![Image](https://i.ibb.co/ydWzJR2/image.png)

Using the *OpenInEditorModally* procedure of **Email** codeunit causes a page to be opened up (as "RunModal") where you can edit the message before you send it. 

You can also add attachments or you can save the message draft.

![Image](https://i.ibb.co/KhpZPNT/image.png)

![Image](https://i.ibb.co/7yn6w5C/image.png)

![Image](https://i.ibb.co/d45nZMd/image.png)

*SaveAsDraft* procedure saves the email as a draft and you can view it in the "Email Outbox" where you can make any changes if necessary and send it directly from there.

![Image](https://i.ibb.co/RcTvfdH/image.png)

![Image](https://i.ibb.co/qRxXtgB/image.png)

![Image](https://i.ibb.co/FVDQ4xB/image.png)

You can also add attachments to the email directly from code.

![Image](https://i.ibb.co/8myVYq2/image.png)

![Image](https://i.ibb.co/FwyZ55Q/image.png)

![Image](https://i.ibb.co/Q8KbRjZ/image.png)

## Conclusion
Thus we saw how we can send emails in Business Central v20.

Happy Coding!
