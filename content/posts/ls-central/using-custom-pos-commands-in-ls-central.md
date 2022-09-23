---
title: "Using Custom Pos Commands in Ls Central"
date: 2022-09-05T14:05:57+05:30
draft: false
tags: ['LS Central', 'Technical']
summary: ''
featured_image: 'https://i.ibb.co/RckWhh5/image.png'
summary: 'How to add Custom functionality through the use of POS External Commands'
---

# Introduction
LS Central provides an easy way to add Custom functionality through the use of POS External Commands.

These commands are executed on the POS and let me know you how to create them.

For this example, we will create a POS Command, to remove all the lines from the current transaction.

## Pre-requisites
- Microsoft Dynamics 365 Business Central On Premise
- LS Central V16

## Configuration
You will need a Codeunit in which we define all the custom commands, all your Custom commands can be added in a single Codeunit.

Make sure to set the *"TableNo"* property to *"POS Menu Line"* table.

In the OnRun trigger, we have to handle two cases:
1. Registering the module and other commands
2. Procedure to execute when command is called.

For handling the first case, we create a procedure *"Register"* which takes a *"POS Menu Line"* as a parameter.

In this procedure we use the *"POS Command Registration"* codeunit to register this module and all the associated commands.

![Image 1](https://i.ibb.co/wYgY1GH/image.png)

I prefer to use Global Labels to store the Module Code/ Module Description and Command Code/Command Description, as this change in once place need not be replicated everywhere this way but it is not necessary.

![Image 2](https://i.ibb.co/HHLVDFn/image.png)

Once this is done, the next step is to register the POS Module, this can be done in two ways

**Using Retail Modules:**
1. Search for Retail Modules in BC Search
2. Click on *"Process"* and then on *"Register"*

![Image 3](https://i.ibb.co/z7mTvJX/image.png)

3. Search for your Codeunit and click on OK.

![Image 4](https://i.ibb.co/Syszq8T/image.png)

**Using "POS External Commands":**
1. Search for *Retail Modules* in BC Search.
2. Click on *"Process"* and then on *"Register"*

![Image 5](https://i.ibb.co/wy63gf3/image.png)

3. Search for your Codeunit and click on OK.

![Image 6](https://i.ibb.co/w6HRPLX/image.png)

4. You can confirm that your commands are visible by checking the list of POS External Commands.

![Image 7](https://i.ibb.co/2cGMzTX/image.png)

Now on the POS, we right-click on a button and click on *"Button Properties"*

![Image 8](https://i.ibb.co/SXdMqCX/image.png)

Then set your custom command,

![Image 9](https://i.ibb.co/hK5ykBV/image.png)

Now we add multiple Items.

![Image 10](https://i.ibb.co/RckWhh5/image.png)

And when we press the button, this is the result, as expected.

![Image 11](https://i.ibb.co/LC5J5tn/image.png)

## Conclusion

Thus, in this blog, we saw how to create Custom commands which can be used on POS. 
Thanks for reading!