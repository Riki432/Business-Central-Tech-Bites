---
title: "Create a New Environment in LCS for D365 Finance and Operations"
date: 2024-01-25T15:40:28+05:30
draft: false
tags: ['D365 Finance and Operations']
categories: ['Functional']
summary: 'How to create a New Environment in LCS for D365 Finance and Operations'
featured_image: '/content/images/d365-finance-and-operations/create-a-new-environment-in-LCS-for-D365-Finance-and-Operations/image2.png'
---

# Introduction
In this blog, we'll be looking into creating a new environment for D365 Finance and Operations or D365 Commerce. 

## Pre-requisites
1. Microsoft Azure with a valid subscription 
2. Office 365 Account with Finance and Operations License 

## References
1. [Azure Resource Manager Overview](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/overview)
2. [Deploy a demo environment | Microsoft Learn](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/deployment/deploy-demo-environment)
3. [Deploy and access development environments - Microsoft Learn](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/dev-tools/access-instances#deploying-cloud-development-environments)
4. [Complete the Azure Resource Manager onboarding process - Microsoft Learn](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/deployment/arm-onboarding)
5. [Finance and operations application architecture - Microsoft Learn](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/organization-administration/architecture-overview)

## Configuration
Go to [Microsoft Dynamics Lifecycle Services](https://lcs.dynamics.com/v2) and log in with your account. 

![Image](/content/images/d365-finance-and-operations/create-a-new-environment-in-LCS-for-D365-Finance-and-Operations/image1.png)
![Image](/content/images/d365-finance-and-operations/create-a-new-environment-in-LCS-for-D365-Finance-and-Operations/image2.png)

If you select D365 Commerce, you get the following screen. 
If you select D365 Finance and Operations, you get another screen where you have to specify whether the project is an actual implementation or just for evaluation after which you get the same screen as below. 

![Image](/content/images/d365-finance-and-operations/create-a-new-environment-in-LCS-for-D365-Finance-and-Operations/image3.png)

Once the Project is created, we get the following screen. 

![Image](/content/images/d365-finance-and-operations/create-a-new-environment-in-LCS-for-D365-Finance-and-Operations/image4.png)

From here, we click on the hamburger menu at the top and then click on Cloud Hosted Environments. 

![Image](/content/images/d365-finance-and-operations/create-a-new-environment-in-LCS-for-D365-Finance-and-Operations/image5.png)

Click on __Add__ to create a new environment. 

![Image](/content/images/d365-finance-and-operations/create-a-new-environment-in-LCS-for-D365-Finance-and-Operations/image6.png)

If you get the below pop-up asking to configure an Azure Connector, please refer to my blog [here](/posts/d365-finance-and-operations/configure-an-azure-connector-in-lcs/).

![Image](/content/images/d365-finance-and-operations/create-a-new-environment-in-LCS-for-D365-Finance-and-Operations/image7.png)

Once, you have an Azure Connector configured, you can click on __Add__ again and get the following pop-up. 
![Image](/content/images/d365-finance-and-operations/create-a-new-environment-in-LCS-for-D365-Finance-and-Operations/image8.png)

After selecting the __Application__ and __Platform__ version, you'll get the option to select the environment topology. 

__DEMO__ - A demo environment includes only Microsoft demo data. You can use a demo environment to explore default features and functionality. 
__DEVTEST__ - A DevTest environment is for development or build.  You can use this environment for development or build. 

![Image](/content/images/d365-finance-and-operations/create-a-new-environment-in-LCS-for-D365-Finance-and-Operations/image8.png)

Then we get another pop-up to select the environment topology.  
![Image](/content/images/d365-finance-and-operations/create-a-new-environment-in-LCS-for-D365-Finance-and-Operations/image9.png)

After that is selected, we decide the environment name and the size of the VM that is to be used for this environment. 
You can read more about VM sizes here - [VM sizes - Azure Virtual Machines | Microsoft Learn](https://learn.microsoft.com/en-us/azure/virtual-machines/sizes)

![Image](/content/images/d365-finance-and-operations/create-a-new-environment-in-LCS-for-D365-Finance-and-Operations/image10.png)

Once we click on __Next__ we get the last pop-up after which the environment gets deployed. 
![Image](/content/images/d365-finance-and-operations/create-a-new-environment-in-LCS-for-D365-Finance-and-Operations/image11.png)

Once we click on deploy, it takes about 6-8 hours to deploy the environment after which it'll be available in the cloud-hosted environments section. 
If, for some reason, you try to create an environment with the latest platform and application version and that deployment fails, you can try to create an environment one platform/application version below that.

## Conclusion
Thus we saw how to create an environment in LCS for either D365 Finance and Operations. 

Happy Coding!