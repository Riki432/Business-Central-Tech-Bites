---
title: "Attach Debugger to an Active Session"
date: 2023-05-14T08:47:21+05:30
draft: false
tags: ['Business Central']
categories: ['Technical']
summary: 'How to attach a debugger to an active session'
featured_image: '/content/images/business-central/attach-debugger-to-active-session/Picture1.png'
---

# Introduction
Business Central has recently introduced the functionality to attach a debugger to an active User session. 

This was previously available in NAV however it has only recently become available for Business Central. 

## Pre-requisites
- Business Central OnCloud/OnPrem 
## References
[Attach AL Debugger - MS Docs](https://learn.microsoft.com/en-us/dynamics365/release-plan/2023wave1/smb/dynamics365-business-central/attach-al-debugger-active-session-or-next-session-specific-user)

## Configuration
To use this functionality, we simply need to create an entry in the launch.json file. 

[![Picture 1](/content/images/business-central/attach-debugger-to-active-session/Picture1.png)](/content/images/business-central/attach-debugger-to-active-session/Picture1.png)

The important properties here are the "sessionId" and the "request". 

This works much faster than the traditional deploy and debug and really makes your life easier as a developer. 

[![Picture 2](/content/images/business-central/attach-debugger-to-active-session/Picture2.png)](/content/images/business-central/attach-debugger-to-active-session/Picture2.png)
Also, I tried using it for a Production Environment and as expected it didn't work.
Snapshot debugging it is then!

## Conclusion

Thus, we saw how we can attach a debuger to an active user session in Business Central.
Happy Coding!
