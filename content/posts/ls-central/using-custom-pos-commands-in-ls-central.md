---
title: "Using Custom POS Commands in LS Central"
date: 2022-09-05T14:05:57+05:30
draft: false
tags: ['LS Central']
categories: ['Technical']
summary: ''
featured_image: '/content/images/ls-central/using-custom-pos-commands-in-ls-central/Image10.png'
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

![Image 1](/content/images/ls-central/using-custom-pos-commands-in-ls-central/Image1.png)

I prefer to use Global Labels to store the Module Code/ Module Description and Command Code/Command Description, as this change in once place need not be replicated everywhere this way but it is not necessary.

![Image 2](/content/images/ls-central/using-custom-pos-commands-in-ls-central/Image2.png)

Once this is done, the next step is to register the POS Module, this can be done in two ways

**Using Retail Modules:**
1. Search for Retail Modules in BC Search
2. Click on *"Process"* and then on *"Register"*

![Image 3](/content/images/ls-central/using-custom-pos-commands-in-ls-central/Image3.png)

3. Search for your Codeunit and click on OK.

![Image 4](/content/images/ls-central/using-custom-pos-commands-in-ls-central/Image4.png)

**Using "POS External Commands":**
1. Search for *Retail Modules* in BC Search.
2. Click on *"Process"* and then on *"Register"*

![Image 5](/content/images/ls-central/using-custom-pos-commands-in-ls-central/Image5.png)

3. Search for your Codeunit and click on OK.

![Image 6](/content/images/ls-central/using-custom-pos-commands-in-ls-central/Image6.png)

4. You can confirm that your commands are visible by checking the list of POS External Commands.

![Image 7](/content/images/ls-central/using-custom-pos-commands-in-ls-central/Image7.png)

Now on the POS, we right-click on a button and click on *"Button Properties"*

![Image 8](/content/images/ls-central/using-custom-pos-commands-in-ls-central/Image8.png)

Then set your custom command,

![Image 9](/content/images/ls-central/using-custom-pos-commands-in-ls-central/Image9.png)

Now we add multiple Items.

![Image 10](/content/images/ls-central/using-custom-pos-commands-in-ls-central/Image10.png)

And when we press the button, this is the result, as expected.

![Image 11](/content/images/ls-central/using-custom-pos-commands-in-ls-central/Image11.png)

## Conclusion

Thus, in this blog, we saw how to create Custom commands which can be used on POS. 
Thanks for reading!