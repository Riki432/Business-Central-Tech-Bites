---
title: "Configuring Data Director Part 2"
date: 2021-10-01T21:48:53+05:30
draft: false
tags: ['LS Central']
categories: ['Technical']
summary: 'How to configure Data Director for LS 16 Part - 2'
featured_image: '/content/images/ls-central/configure-data-director-part-2/Image12.png'
---

# Introduction
In the [last part](/posts/ls-central/configure-data-director-part-1/), we saw how to install Data Director, configure Network connections and modify Host file.

In this part, we will see the SQL Server and Business Central side of configurations and how to test if everything is configured properly.

## Pre-requisites
- Microsoft Dynamics 365 Business Central 
- LS Central
- Data Director V3.02

## References
[Data Director User Guide](https://implementation.ls-one.com/Content/Documents/InstallGuides/LS%20Data%20Director%20User%20Guide.pdf)

## Configuration
### SQL Server
- Set the Authentication Mode for the Server Instance to "SQL Server and Windows Authentication."

<!-- ![Image](https://i.ibb.co/WpKM6q8/image.png) -->
![Image](/content/images/ls-central/configure-data-director-part-2/Image1.png)

- Go to your Server Instance and create a new Login.

<!-- ![Image](https://i.ibb.co/GpYv70b/image.png) -->
![Image](/content/images/ls-central/configure-data-director-part-2/Image2.png)

- Make sure to set the User Mapping to your database.

<!-- ![Image](https://i.ibb.co/KKVYVz9/image.png) -->
![Image](/content/images/ls-central/configure-data-director-part-2/Image3.png)

- Go to your Database and create a new User.

<!-- ![Image](https://i.ibb.co/TWZRgzZ/image.png) -->
![Image](/content/images/ls-central/configure-data-director-part-2/Image4.png)

<!-- ![Image](https://i.ibb.co/kM3nnpy/image.png) -->
![Image](/content/images/ls-central/configure-data-director-part-2/Image5.png)

- Make sure to set the "Membership" to "db_owner"

<!-- ![Image](https://i.ibb.co/vHGfjKq/image.png) -->
![Image](/content/images/ls-central/configure-data-director-part-2/Image6.png)

- To confirm if the SQL User has been configured properly, 

<!-- ![Image](https://i.ibb.co/ykWZQqq/image.png) -->
![Image](/content/images/ls-central/configure-data-director-part-2/Image7.png)

- Set the Authentication Mode to SQL and try to login with the newly created User.

<!-- ![Image](https://i.ibb.co/mRTpMgT/image.png) -->
![Image](/content/images/ls-central/configure-data-director-part-2/Image8.png)

- If you are able to login successfully, then we move to the next part.

### Distribution Location
- Set the "Data Director Mode" to TCP and the "Distribution Server" to point to the current system. It is advisable to set this value as the IP of the current system or the host-name if you have defined it in the hosts file.

<!-- ![Image](https://i.ibb.co/T2wzq6X/image.png) -->
![Image](/content/images/ls-central/configure-data-director-part-2/Image9.png)

- Then set the "Distribution Server URL" in the following pattern https://<IP>/DDWebservice. Set the User ID and password of that system in the "Distribution Server User ID" and "Distribution Server Password" field.

<!-- ![Image](https://i.ibb.co/znR4MjM/image.png) -->
![Image](/content/images/ls-central/configure-data-director-part-2/Image10.png)

- Then set the values in the "Replication" tab as follows:
    - **Company Name**: Name of the Company
    - **User ID**: UserID of the SQL User we created previously.
    - **Password**: Password of the SQL user we created previously.
    - **Db. Server Name**: The server name and server instance in the <SERVER-NAME>\<SERVER-INSTANCE> format.
    - **Db. Path & Name**: Name of the SQL Database
    - **Version**: The version of the SQL Server you are using.
    - **Net Type**: Set it as "tcp"

<!-- ![Image](https://i.ibb.co/8NdHCCM/image.png) -->
![Image](/content/images/ls-central/configure-data-director-part-2/Image11.png)

- To check if this has been configured properly, click on "Test Connection" on the top left and a success message should pop-out.

<!-- ![Image](https://i.ibb.co/9VnhmLJ/image.png) -->
![Image](/content/images/ls-central/configure-data-director-part-2/Image12.png)

- Do the same configuration for both Head Office and Stores, make sure the modify the Distribution Locations accordingly.

- Now, search for "Scheduled Jobs" in BC, let say "Items" for instance, and make the following changes:

<!-- ![Image](https://i.ibb.co/dpKCFRc/image.png) -->
![Image](/content/images/ls-central/configure-data-director-part-2/Image13.png)

- Now, click on "Run Now" at the top left, you should get some message.

- Open "Job Monitor" to confirm if the job has run successfully.

<!-- ![Image](https://i.ibb.co/1dD0bYF/image.png) -->
![Image](/content/images/ls-central/configure-data-director-part-2/Image14.png)

## Conclusion
Thus, we saw how to configure Data Director and test if everything is configured properly. 

Happy Coding!