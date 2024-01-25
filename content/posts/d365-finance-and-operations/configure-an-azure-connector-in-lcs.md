---
title: "Configure an Azure Connector in LCS"
date: 2024-01-25T15:42:43+05:30
draft: false
tags: ['D365 Finance and Operations']
categories: ['Functional']
summary: 'How to configure an Azure Connector in LCS'
featured_image: '/content/images/d365-finance-and-operations/configure-an-azure-connector-in-LCS/image2.png'
---

# Introduction
In this blog, we'll be looking into configuring the Azure Connector in LCS with the Azure Resource Manager so that LCS can deploy your resources to Azure. 

## Pre-requisites
An Azure subscription that you are a co-administrator in. 

## References
1. [Azure Resource Manager overview - Microsoft Learn](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/overview)
2. [Deploy a demo environment - Microsoft Learn](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/deployment/deploy-demo-environment)
3. [Deploy and access development environments - Microsoft Learn](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/dev-tools/access-instances#deploying-cloud-development-environments)
4. [Complete the Azure Resource Manager onboarding process - Microsoft Learn](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/deployment/arm-onboarding)

## Configuration
Go to [Microsoft Dynamics Lifecycle Services](https://lcs.dynamics.com/v2) and log in with your account. 

In LCS, when we try to create a cloud hosted environment for the first time, it prompts us to create an Azure Connector first. 

You can also access this by going to your Project Settings and the "Azure Connectors."

![Image](/content/images/d365-finance-and-operations/configure-an-azure-connector-in-LCS/image2.png)

![Image](/content/images/d365-finance-and-operations/configure-an-azure-connector-in-LCS/image1.png)

![Image](/content/images/d365-finance-and-operations/configure-an-azure-connector-in-LCS/image3.png)

Once, we reach this screen, we have to click on __Authorize__ in the organization where we want to authorize. 

![Image](/content/images/d365-finance-and-operations/configure-an-azure-connector-in-LCS/image4.png)

Please do ensure your account has the necessary permissions for these actions. 
Once, this is done click on __Microsoft Azure Portal__ as there are a few configurations we need to do in the Azure Portal. 

![Image](/content/images/d365-finance-and-operations/configure-an-azure-connector-in-LCS/image5.png)

Click on _Subscriptions_. 

![Image](/content/images/d365-finance-and-operations/configure-an-azure-connector-in-LCS/image6.png)

From the Subscriptions list, we can note down the Subscription ID as we will need it while creating the Azure Connector. 

![Image](/content/images/d365-finance-and-operations/configure-an-azure-connector-in-LCS/image7.png)

The "Subscription ID" is also available in the Overview section of the Subscription. 

Then go to the _Access Control (IAM)_ tab and click on __Add__ and then __Add Role Assignment.__

![Image](/content/images/d365-finance-and-operations/configure-an-azure-connector-in-LCS/image8.png)

Then go to _Role_ -> _Privileged Administrator Roles_ and then search for "Contributor". 

Click on it and then click on Next. 

![Image](/content/images/d365-finance-and-operations/configure-an-azure-connector-in-LCS/image9.png)

In the members tab, click on _User, group or Service Principal_ and click on __Select Members.__ 

![Image](/content/images/d365-finance-and-operations/configure-an-azure-connector-in-LCS/image10.png)

After that search for and add "Dynamics Deployment Services [wsfed-enabled]" and your own user to this role assignment. 

![Image](/content/images/d365-finance-and-operations/configure-an-azure-connector-in-LCS/image11.png)

![Image](/content/images/d365-finance-and-operations/configure-an-azure-connector-in-LCS/image12.png)

Once that is done, we'll get a confirmation message.

After that, we can move back to the LCS for configuring the Azure Connector. 

We click on __Add__ to create a new Azure Connector and get the following pop-up. 

Here we add a name for the connector, Azure Subscription ID and the Domain Name. 

Name can be anything that you want, the Domain Name in most cases is the part of your email address after the @. For e.g. it'd be "microsoft.com" in case of rbansode@microsoft.com. 

For the Azure Subscription ID, we have already stored that from the previous steps.  

![Image](/content/images/d365-finance-and-operations/configure-an-azure-connector-in-LCS/image13.png)

Once we add the necessary values and click on next we get the following pop-up. 

We've already completed the necessary steps in the Azure Portal so we can simply click on Next. 

![Image](/content/images/d365-finance-and-operations/configure-an-azure-connector-in-LCS/image14.png)

After that, we get the following pop-up. 

We've completed the steps mentioned in the _Ensure you are a subscription user_ section. 

If for some reason you are facing any difficulties in that you can also try the steps from the _Apply a Subscription Tag_ section. 

![Image](/content/images/d365-finance-and-operations/configure-an-azure-connector-in-LCS/image15.png)

### Apply a subscription tag 
When you click on __Get a Code__ you'll get the following pop-up which includes a unique verification code. 
We copy this and head on to the Azure Portal. 

![Image](/content/images/d365-finance-and-operations/configure-an-azure-connector-in-LCS/image16.png)

Then go to your subscription in Azure Portal. 

Head to the _Tags_ section and create a new entry with name as "LifecycleServicesAuthCode" and the value as unique verification code from LCS.

![Image](/content/images/d365-finance-and-operations/configure-an-azure-connector-in-LCS/image17.png)

If neither of those methods work, there is a soon to be deprecated method mentioned as well where you upload the certificate downloaded from LCS into the "Management Certificates" of your Azure Subscription. 

![Image](/content/images/d365-finance-and-operations/configure-an-azure-connector-in-LCS/image18.png)

![Image](/content/images/d365-finance-and-operations/configure-an-azure-connector-in-LCS/image19.png)

Hopefully, one of these three methods work out for you and you'll get the following pop-up.

![Image](/content/images/d365-finance-and-operations/configure-an-azure-connector-in-LCS/image20.png)


Once you click on connect you'll see an entry created in your Azure Connectors. 

This indicates that your Azure Account has been linked and now LCS can utilize it to create resources in Azure on your behalf. 

![Image](/content/images/d365-finance-and-operations/configure-an-azure-connector-in-LCS/image21.png)

### Side Note

If you see the following error message then that means there was an error with one of the three suggested approaches you choose. 
You can try with another approach and start over. 

![Image](/content/images/d365-finance-and-operations/configure-an-azure-connector-in-LCS/image22.png)

## Conclusion
Thus we saw how to configure the Azure Connector in LCS. 

Happy Coding!