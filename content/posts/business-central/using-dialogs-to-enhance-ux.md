---
title: "Use Dialogs to enhance User Experience"
date: 2022-09-23T18:13:16+05:30
draft: false
tags: ['Business Central']
categories: ['Technical']
summary: 'How to use Dialogs to enhance User Experience in Business Central'
featured_image: 'https://i.ibb.co/dKgRRjH/image.png'
---

# Introduction
We've all faced situations where we've had an operation take a long while which made the User wonder whether the system is stuck with something or is still processing.

We can use simple dialogs which can enhance the User experience by showing User the progress of the operation.

Some Business Central operations have out of the box dialogs which indicate progress like Posting documents or entries, Running reports with large data sets.

## Pre-requisites
- Business Central OnCloud/OnPrem

## References
[Dialog Data Type](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/dialog/dialog-data-type)

## Configuration
While using the Dialog for creating windows, there are 3 procedures that we are going to be using.
1. Open - It creates the window which we will be displaying the messages in.

2. Update - It updates the content of the window based on the values that we pass in it.

3. Close - It closes the window.

We can create a simple Progress Window using the below piece of code.

![Image](https://i.ibb.co/dm6wqCG/image.png)

![Image](https://i.ibb.co/6HhKNBz/image.png)

And this is the result for it.

Please note that because there were two # in the Label, system has broken them into two separate lines.

![Image](https://i.ibb.co/vYp2Wwj/image.png)

To avoid creating multiple lines within a single dialog box, we can use the StrSubstNo procedure which compresses the number of updates that we call to 1.

![Image](https://i.ibb.co/17gvZ47/image.png)

We can now see that the content is visible in a single line.

![Image](https://i.ibb.co/Ks4qbqs/image.png)

In Business Central 14 or previous versions of Business Central (which used windows client) it was possible to show the progress indicator in percentages using native APIs, however this functionality is not supported in Web Client.

However we can still simulate it using text and creating our own basic procedure which converts the values to a String which will be used to indicate the progress.

![Image](https://i.ibb.co/drTTdbm/image.png)

![Image](https://i.ibb.co/8mK0BDL/image.png)

![Image](https://i.ibb.co/5s7GCq9/image.png)

![Image](https://i.ibb.co/dKgRRjH/image.png)

## Conclusion
Thus we saw how we can use Dialogs to enhance User Experience and allow Users to visualize the processing of some long running task.

Happy coding!