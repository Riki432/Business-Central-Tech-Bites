---
title: "Configuring Data Director Part 1"
date: 2021-10-01T21:09:27+05:30
draft: false
tags: ['LS Central']
categories: ['Technical']
summary: 'How to configure Data Director for LS 16 Part - 1'
featured_image: '/content/images/ls-central/configure-data-director-part-1/Image5.png'
---

# Introduction

Data Director is one of the applications from LS Retail and it is essential to keep the data between the POS, Stores and HO in sync.

Data Director is used to move data between databases, generally used with MS SQL Server but it is not limited to it and can be used with databases like MySQL as well. 

A rule of thumb is that If the database supports ODBC then the Data Director should be able to use it.

Read the "Data Director User Guide" for more information.


## Pre-requisites
- Microsoft Dynamics 365 Business Central 
- LS Central
- Data Director V3.02

## References
[Data Director User Guide](https://implementation.ls-one.com/Content/Documents/InstallGuides/LS%20Data%20Director%20User%20Guide.pdf)

## Configuration
### Data Director Installation
- Open the data director installation package.

<!-- ![Image](https://i.ibb.co/8dpZ21Z/image.png) -->
![Image](/content/images/ls-central/configure-data-director-part-1/Image1.png)

- Select or deselect the components as you need, if you're setting up Data Director for a new system the following are sufficient.

<!-- ![Image](https://i.ibb.co/YB0cR1G/image.png) -->
![Image](/content/images/ls-central/configure-data-director-part-1/Image2.png)

- If you have not changed the "Default Web Site" name in IIS, then you can leave this step unchanged.

<!-- ![Image](https://i.ibb.co/kBJ2dts/image.png) -->
![Image](/content/images/ls-central/configure-data-director-part-1/Image3.png)

- Click install and wait for a few seconds.

<!-- ![Image](https://i.ibb.co/3MCJrj6/image.png) -->
![Image](/content/images/ls-central/configure-data-director-part-1/Image4.png)

- To test if the Data Director service is running properly, go to "http://localhost/DDWebService/DDJson.svc/Ping" and if the returned response looks like this then it is properly installed.

<!-- ![Image](https://i.ibb.co/P5Y8b26/image.png) -->
![Image](/content/images/ls-central/configure-data-director-part-1/Image5.png)

- In some cases, I have found that there are issues when we try to run the job we get this error;

<!-- ![Image](https://i.ibb.co/5cNs6rg/image.png) -->
![Image](/content/images/ls-central/configure-data-director-part-1/Image6.png)

- Go to - **"C:\Program Files (x86)\LS Retail\Data Director 3\bin"**, set a filter on "Type" and choose "Application Extension" and copy all the files there, then go to **"C:\Program Files\Microsoft Dynamics 365 Business Central\160\Service\Add-ins\LSRetail\DD\Control"**  if this path does not exist, then create it and paste all the files there, this should resolve that issue.

<!-- ![Image](https://i.ibb.co/QjCJdHR/image.png) -->
![Image](/content/images/ls-central/configure-data-director-part-1/Image7.png)

<!-- ![Image](https://i.ibb.co/J7vSgpc/image.png) -->
![Image](/content/images/ls-central/configure-data-director-part-1/Image8.png)

### Network Configuration

- Go to the Networking tab in your azure portal and create "Inbound" and "Outbound" port rules allowing the following ports.
    - **16860** - TCPS - For secured Data Director
    - **16850** - TCP - For Data Director
    - **16803** - If your Data Director is using Cfront processing then this port is required, otherwise you can skip it.
    - **80** - It is useful in debugging and testing data director connections.

<!-- ![Image](https://i.ibb.co/Thkp8Cd/image.png) -->
![Image](/content/images/ls-central/configure-data-director-part-1/Image9.png)

- Similarly, go to "Windows Defender Firewall with Advanced Security" and create Firewall rules, both inbound and outbound for the same ports.

<!-- ![Image](https://i.ibb.co/cJhyynj/image.png) -->
![Image](/content/images/ls-central/configure-data-director-part-1/Image10.png)

- Host File
    - Go to **"C:\Windows\System32\drivers\etc\"**
    - Modify the "hosts" file and add the IP Host-name like the below example.
    - Do note that, you need admin privileges, to modify this file. 

<!-- ![Image](https://i.ibb.co/LdDV0s2/image.png) -->
![Image](/content/images/ls-central/configure-data-director-part-1/Image11.png)

## Conclusion

Thus, we saw how to install Data Director, configure Network connections and modify Host file. 

In the [next part](/posts/ls-central/configure-data-director-part-2/) we will configure SQL Server and Business Central so that we can finally use Data Director. 

Happy Coding!