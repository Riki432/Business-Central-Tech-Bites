---
title: "Report Does Not Have a Layout Type None"
date: 2022-09-04T16:08:29+05:30
draft: false
tags: ['Business Central', 'Technical']
summary: 'How to resolve “Report ___ does not have a layout of type None.” error'
description: 'How to resolve “Report ___ does not have a layout of type None.” error'
featured_image : 'https://i.ibb.co/6RV4Lw7/image.png'
---
# Introduction

Have you ever faced the error: “Report ___ does not have a layout of type None.”

![Error Message](https://i.ibb.co/6RV4Lw7/image.png)

Here’s how you can resolve it.

## Pre-requisites
1. Business Central OnCloud/OnPrem

## References
[Community Question](https://community.dynamics.com/business/b/think-about-it/posts/how-do-i-fix-error-report-x-does-not-have-a-layout-of-type-none)

## Configuration
With the earlier versions of Business Central, you were allowed to run a report without specifying a layout, even if it was not a processing only report.

However with the recent version of Business Central it is mandatory to specify both the DefaultLayout and the path to the layout via the **RDLCLayout** or **WordLayout** or **ExcelLayout** properties.

Once these properties are the defined the error is resolved.

Furthermore you can also resolve this error by using the report rendering section which has been made available since runtime 9.0.

However be sure to define the **DefaultRenderingLayout** property for the report to specify which of the layouts defined should be considered as default.

![Code Snippet](https://i.ibb.co/vkgQfCD/image.png)

---

## Conclusion

Thus we saw how we can resolve the error: “Report ___ does not have a layout of type None.”

Happy Coding!


