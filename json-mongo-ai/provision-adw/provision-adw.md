# Provision an Autonomous Database

## Introduction
<Lab 1 - Load and update MovieStream data in Oracle Autonomous Data Warehouse using Data Studio>

This lab walks you through the steps to get started using the Oracle Autonomous Database (Autonomous Data Warehouse [ADW]) on Oracle Cloud. In this lab, you provision a new ADW instance.

Watch our short video that explains how to provision your Autonomous Database instance:

[](youtube:IfWJhnodAxk)

Estimated Lab Time: 10 minutes

### Objectives 
- Create an Autonomous Database with the latest features of Oracle Databases

## Task 1: Create a new Autonomous Data Warehouse Database

1. Click on the hamburger **MENU** link at the upper left corner of the page.

    This will produce a drop-down menu, where you should select **Autonomous Data Warehouse**.

    ![Oracle Cloud Web Console](https://oracle-livelabs.github.io/common/images/console/database-adw.png " ")

    This will take you to the management console page.

    To learn more about comparments, see [Managing Compartments](https://docs.cloud.oracle.com/en-us/iaas/Content/Identity/Tasks/managingcompartments.htm).
    
2. To create a new instance, click the blue **Create Autonomous Database** button.

    ![Create ADB](./images/create-adb.png)

    Enter the required information and click the **Create Autonomous Database** button at the bottom of the form. For the purposes of this workshop, use the information below:

    - **Compartment:** Verify that a compartment (&lt;tenancy_name&gt;) is selected.

    By default, any OCI tenancy has a default ***root*** compartment, named after the tenancy itself. The tenancy administrator (default root compartment administrator) is any user who is a member of the default Administrators group. For the workshop purpose, you can use ***root***.
    By default, any OCI tenancy has a default ***root*** compartment, named after the tenancy itself. The tenancy administrator (default root compartment administrator) is any user who is a member of the default Administrators group. For the workshop purpose, you can use ***root***.

    - **Display Name:** Enter the display name for your ADW Instance. For this demo purpose, I have called my database `ADW_OAC`.
        ```
        <copy>ADW_OAC</copy>
        ```
    
    - **Database Name:** Enter any database name you choose that fits the requirements for ADW. The database name must consist of letters and numbers only, starting with a letter. The maximum length is 14 characters. You can leave the name provided. That field is not a mandatory one.
    - **Workload Type:** Autonomous Data Warehouse  
    
    - **Deployment Type:** Shared Infrastructure
    
    - **Always Free:** On

    You can select Always Free configuration to start enjoying your Free Autonomous Database. You will have see the Always Free logo next to the name of your database:

    ![Always Free Logo](./images/always-free-logo.png)

    We have selected 'Always Free Tier On'. 

    To learn more about Always Free check the following [link](https://www.oracle.com/uk/cloud/free/#always-free).

    ![ADB Creation Details](./images/adw-creation-details.png)

    - **Choose Database version:** 23ai
    
    - **CPU Count:** 1
    
    - **Storage Capacity (TB):** 1

    - **CPU Count and Storage Capacity (TB)** are defined by default for the Always Free Tier.
    
    - **OCPU Auto scaling:** Off
    
    - **Storage Auto scaling:** Off

    ![ADB Creation Storage](./images/adw-db-version-23ai.png)

3. Under **Create administration credentials** section:

    - **Administrator Password:** Enter any password you wish to use noting the specific requirements imposed by ADW.
    
    - **Reminder:** Note your password in a safe location as this cannot be easily reset.

    Under **Choose network access** section:

    - Select **'Secure access from everywhere'**: *On*
    
    ![ADB Creation Password](./images/adw-db-password-new.png)

4. Under **Choose a license type** section, choose **License Type: Licence Included**.

    When you have completed the required fields, scroll down and click on the blue **Create Autonomous Database** button at the bottom of the form:

    ![ADB Creation](./images/adw-db-license-type.png)

5. The Autonomous Database **Details** page will show information about your new instance. You should notice the various menu buttons that help you manage your new instance - because the instance is currently being provisioned all the management buttons are greyed out.

    ![ADB Creation Provisioning](./images/adw-provisioning.png)

6. A summary of your instance status is shown in the large box on the left. In this example, the color is amber and the status is **Provisioning**.

    ![ADB Creation Provisioning Amber](./images/provisioning.png)

7. After a short while, the status will change to **Available** and the "ADW" box will change color to green:

    ![ADB Creation Provisioning Green](./images/available.png)

8. Once the Lifecycle Status is **Available**, additional summary information about your instance is populated, including workload type and other details.

    The provisioning process should take **under 5 minutes**.

9. After having the Autonomous Database instance **created** and **available**, you can get a message window asking you to upgrade from 19c to 23ai if you have selected 19c as a database version during the provisioning. **Upgrade** the database release to 23ai if you have not already. If your database version precedes 23ai, the ONNX model example in Lab 6 will be unsuccessful.

    This page is known as the **Autonomous Database Details Page**. It provides you with status information about your database, and its configuration. Get **familiar** with the buttons and tabs on this page.

    ![ADB Creation Details](./images/adw-ready.png)

    Remember: You will have visible the Always Free logo next to the name of your database:

    ![Always Free Logo](./images/always-free-logo.png)

You have just created an Autonomous Database with the latest features of Oracle Databases.

## **Acknowledgements**

- **Author** - Priscila Iruela - Technology Product Strategy Director, Juan Antonio Martin Pedro - Analytics Business Development
- **Contributors** - Victor Martin, Melanie Ashworth-March, Andrea Zengin
- **Last Updated By/Date** - Deshan de Mel, July 2025

## Need Help?
Please submit feedback or ask for help using our [LiveLabs Support Forum](https://community.oracle.com/tech/developers/categories/livelabsdiscussions). Please click the **Log In** button and login using your Oracle Account. Click the **Ask A Question** button to the left to start a *New Discussion* or *Ask a Question*.  Please include your workshop name and lab name.  You can also include screenshots and attach files.  Engage directly with the author of the workshop.

If you do not have an Oracle Account, click [here](https://profile.oracle.com/myprofile/account/create-account.jspx) to create one.