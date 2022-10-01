---
title: "Configuring Web Services for LS v16"
date: 2022-02-23T22:08:26+05:30
draft: false
tags: ['LS Central']
categories: ['Technical']
summary: 'How to configure WebServices in LS v16'
featured_image: 'https://i.ibb.co/DV7W3v8/image.png'
---

# Introduction

LS Central uses Business Central's inbuild Web Services to push or pull data from a remote database. 

LS Central provides are wide selection of Web Requests which are more than enough to handle most scenarios.

Advantages of using Web Services are that they are very simply to configure and they are almost instantaneous.

Disadvantage of using Web Services is that since they are inherently depending on having an active connection with the remote database as such these cannot be used in offline mode.

## Pre-requisites
- Microsoft Dynamics 365 Business Central 
- LS Central

## References
[LS Central - Documentation](https://help.lscentral.lsretail.com/Content/LS-Insight/Setup/LS-Central-In-Cloud-LS-Insight-In-Azure/2-WS-Setup-In-Cloud.htm)

## Configuration

Search for "Web Service Setup" in your Business Central system and Set the "Web Service is Active" to true.

![Image](https://i.ibb.co/chPmpXX/image.png)

Then in the "Server" tab, update the following fields:

Setting "Only Local Request" to true, ensure that the data Web Services pulls is from the local database.

Please note that if you're setting up "Web Service" to point to a remote database, as opposed to Local database shown in this blog, the parameters will differ accordingly.

![Image](https://i.ibb.co/J34vb46/image.png)

In case, there are any issues with the Web Services, we can use Logs to debug them. 

Do keep in mind that these Logs tend to become large in size rapidly which is why you should only use them for testing and debugging.

![Image](https://i.ibb.co/8xqhX1S/image.png)

As web services require credentials before they return data, we have to set these credentials in the "Client Credentials" tab.

![Image](https://i.ibb.co/qncP3V8/image.png)

If your system is using "NavUserPassword" authentication, then use those credentials and if it is "Windows" authentication then use the windows login credentials.

To verify if the credentials you have entered are valid, use the URL generated in "Web Service URI" field of "Server" tab and paste it in the browser. 

If, after entering credentials, you get some response then these credentials are valid.

The returned response may look something like this:

![Image](https://i.ibb.co/YfLBV2v/image.png)

Go to "Actions" then "Functions" and then click on all the "Insert **" actions consecutively.

![Image](https://i.ibb.co/K5rkpC6/image.png)

After the last action, "Insert Default Settings Store" you should get the following message.

![Image](https://i.ibb.co/d2qbFRM/image.png)

To confirm whether Web Service Setup is done successfully, you use the "Test Web Connection" action. 

If everything is configured properly this is the message you should get.

![Image](https://i.ibb.co/DV7W3v8/image.png)

## Conclusion

Thus, we saw how to configure "Web Services" in LS Central. 

Happy Coding!