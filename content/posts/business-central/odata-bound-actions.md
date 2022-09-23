---
title: "Working with Odata Bound Actions"
date: 2022-09-04T17:33:31+05:30
draft: false
tags: ['Business Central']
categories: ['Technical']
summary: 'How to interact with and use OData bound actions'
featured_image: 'https://i.ibb.co/vVq7XGf/image.png'
---
# Introduction
OData Bound Actions allows us to perform logic in Business Central by hitting specific end points.

We can also pass in parameters and get results in response. It’s very similar to using Azure Functions but is natively built into Business Central at no extra cost!

In this example, we’ll be returns the Base64 version of an Image of a Customer, we will also see how to get the Image for any other customer as well.

## Pre-requisites
1. Business Central OnPrem/OnCloud

## References
[WebServiceActionContext ](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/webserviceactioncontext/webserviceactioncontext-data-type)
[Interacting with Odatav4 bound actions](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/devenv-creating-and-interacting-with-odatav4-bound-action)

## Configuration
OData Bound Actions are written on Pages or API – Pages that you are declaring as Web Services.
In this example below, I’ve created a simple Customer Page with a few fields and kept the OData key field as the “No.” field. I’ve also defined this as a Web Service in Business Central.

![Image 1](https://i.ibb.co/BPKLYVD/image-8.png)

To create a OData Bound Action, we create a Global Procedure with the Service Enabled decorator.
In this procedure, we have to create a WebServiceActionContext variable and set the “ObjectType”, “ObjectID” and Keys that we are using for this Web Service, which is “No.” in this case, after our processing is done we also need to set the “Result Code” for this request.
 
![Image 2](https://i.ibb.co/nP8yNFB/image-7.png)

In the above piece of code, I’ve written simple logic which converts the content of a Media Data Type (Image field) to Base64 Text and returns it.
In Post-Man if you check of the metadata, you’ll be able to see this action defined in the metadata.

![Image 3](https://i.ibb.co/b7wyY7t/image-11-1024x551.png)

Now, it’s time to test out OData Bound Action!
To call the OData Bound Action, we need to be working with a single record. So we specify the “No.” field to identify a single record.

![Image 4](https://i.ibb.co/8X35sCN/image-12-1024x522.png)

Now, we append our procedure name as “NAV.[Procedure Name]” and make a POST request.

![Image 5](https://i.ibb.co/BBKcskV/image.png)

If we put this Base64 through a Base64 to File Converter, we can see that the original data is recovered.

![Image 6](https://i.ibb.co/vVq7XGf/image.png)

Now, we create a new procedure, which will take the System ID as a parameter and return the Image data for that Customer Record.

![Image 7](https://i.ibb.co/yW52MLW/image.png)
![Image 8](https://i.ibb.co/xsMBNPB/image.png)

If you want to pass the parameters to the OData Bound Actions, you have to do it as the Body of the Request.

![Image 9](https://i.ibb.co/B3NzmBk/image.png)

## Conclusion

*P.S. I’ve tried but it seems polymorphism doesn’t work with this.*

I hope this was insightful and a quick start on how to write OData Bound Actions.

Happy coding! 

