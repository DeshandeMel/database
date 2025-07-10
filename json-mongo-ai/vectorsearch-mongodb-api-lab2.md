---
output: 
  pdf_document: default
  html_document: default
---

# Provisioning an Autonomous JSON Database

## Introduction
This lab walks you through the steps to get started using the Oracle Autonomous JSON Database [AJD] on Oracle Cloud. In this lab, you will provision a new AJD instance and connect to the Autonomous Database using JSON.

Estimated Time: 10 minutes

Watch the video below for a quick walk-through of the lab.
(Insert Video)

### Objectives
In this lab, you will:

* Learn how to provision a new Autonomous Database

* Connect to your Autonomous Database using JSON

### Prerequisites

* Logged into your Oracle Cloud Account


## Task 1: Choose AJD from the Services Menu

1. Login to the Oracle Cloud.

2. If you are using a Free Trial or Always Free account, and you want to use Always Free Resources, you need to be in the home region of the tenancy. Always Free Resources are only available in the home regions. You can see your current default \textbf{Region} in the top, right hand corner of the page.

    (Insert Image)

3. Click the navigation menu in the upper left to show top level navigation choices. Click on \textbf{Oracle Database} and choose \textbf{Autonomous JSON Database}.

    (Insert Image)

4. Use the \textbf{List Scope} drop-down menu on the left to select a compartment. Make sure your workload type is JSON Database.

    (Insert Image)
    (Insert Image)

\textbf{Note}: Avoid the use of the ManagedCompartmentforPaaS compartment as this is an Oracle default used for Oracle Platform Services.

## Task 2: Create the AJD Instance

1. Click \textbf{Create Autonomous Database} to start the instance creation process.

    (Insert Image)

2. This brings up the \textbf{Create Autonomous Database} screen where you will specify the configuration of the instance.

3. Provide basic information for the autonomous database:

    * \textbf{Choose a compartment} - Select a compartment for the database from the drop-down list.

    * \textbf{Display Name} - Enter a memorable name for the database for display purposes. For this lab, use \textbf{JSONDB}.

    * \textbf{Database Name} - Use letters and numbers only, starting with a letter. Maximum length is 14 characters. (Underscores not initially supported.) For this lab, use \textbf{JSONDB}.

    (Insert Image)

4. Choose a workload type: Select the workload type for your database from the choices:

    * \textbf{JSON} - For this lab, choose \textbf{JSON} as the workload type. Note that the MongoDB API is also available on Autonomous Transaction Processing and Autonomous Data Warehouse. However, Autonomous JSON database was purposely build, designed, and priced for JSON and document store workloads.

    (Insert Image)

5. Choose a deployment type: Select the deployment type for your database from the choices:

    * \textbf{Serverless} - For this lab, choose \textbf{Serverless} as the deployment type. (Autonomous JSON Database is only available on Serverless)

    (Insert Image)

6. Configure the database:

    * \textbf{Always Free} - If your Cloud Account is an Always Free account, you can select this option to create an always free autonomous database. An always free database comes with 1 CPU and 20 GB of storage. For this lab, we recommend you leave Always Free unchecked.

    * \textbf{Choose database version} - Select 19c from the database version. Note: This lab should work on 21c AJD database as well.

    * \textbf{ECPU count} - Number of ECPUs for your service. For this lab, leave the default \textbf{2 ECPU}. If you choose an Always Free database, it comes with preconfigured and fixed cpu capabilities.

    * \textbf{Storage} - Select your storage capacity in gigabytes. For this lab you can reduce the storage to the minimum of \textbf{20 GB} of storage. If you choose an Always Free database, it comes with 20 GB of storage by default.

    * \textbf{Auto Scaling} - For this lab, keep auto scaling enabled, to allow the system to automatically use up to three times more CPU and IO resources to meet workload demand. (While this will not happen as part of the workshop, we don't know what else you are going to experiment with.)

\textcolor{orange}{*Note: You cannot scale up/down an Always Free autonomous database.*}

If you are planning to use this autonomous database solely for the purpose of this workshop, you can reduce the backup retention also to the minimum of \textbf{1 day}.

    (Insert Image)

7. Create administrator credentials:

    * \textbf{Password and Confirm Password} - Specify the password for ADMIN user of the service instance and confirm the password.

The password must meet the following requirements:

    * The password must be between 12 and 30 characters long and must include at least one uppercase letter, one lowercase letter, and one numeric character.
    
    * The password cannot contain the username.
    
    * The password cannot contain the double quote (") character.
    
    * The password must be different from the last 4 passwords used.
    
    * The password must not be the same password that is set less than 24 hours ago.
    
    * Re-enter the password to confirm it. Make a note of this password.
    
Later stages of this LiveLab will be easier if you avoid any of the characters / : ? # [ ] and @ in your password.

    (Insert Image)

8. Set network access:

In order to use the Database API for MongoDB, you must set the database up with an access control rule. So choose \textbf{Secure access from allowed IPs and VCNs only}.

You can then click "Add My IP Address" to allow access from your current IP address. You should avoid any VPN or proxy server access which may mask or change your actual IP address.

If you are behind a proxy setup and have issues with access from your local IP address, you can set the CIDR block access to 0.0.0.0/0, which allows access from \textbf{everywhere}. This is not recommended for systems used in any production configuration, but sufficient for a workshop.

    (Insert Image)

9. Choose a license type:

For Autonomous JSON Database, only \textbf{License Included} is available. For other Autonomous Database workloads, you have these options:

    * \textbf{Bring Your Own License (BYOL)} - Select this type when your organization has existing database licenses.

    * \textbf{License Included} - Select this type when you want to subscribe to new database software licenses and the database cloud service.
    
    (Insert Image)

10. Click \textbf{Create Autonomous Database}.

    (Insert Image)

11. Your instance will begin provisioning. In a few minutes, the state will turn from Provisioning to Available. At this point, your Autonomous JSON database is ready to use! Have a look at your instance's details here including the Database Name, Database Version, OCPU Count, and Storage.
    
    (Insert Image)


## Task 3: Find MongoDB API Connection URL

These will be needed in later labs.

1. Go to Tool Configuration

On the Autonomous Database Information page, click on the \textbf{Tool configuration} tab.

    (Insert Image)

The Database Actions Console will open in a new browser tab.

2. Find MongoDB API

Scroll down the page until you find the section \textbf{MongoDB API}. For Autonomous JSON databases, it should be enabled by default. For Autonomous Transaction Processing or Autonomous Data Warehouse, it will be disabled by default and you will need to click \textbf{Edit Tool Configuration} at the top of the page to enable it. If you have not correctly set \textbf{Secure access from allowed IPs and VCNs only} in the previous Task, you will not be able to enable the MongoDB API.

    (Insert Image)

3. Save the URL for \textbf{Oracle Database API for MongoDB}

Click on the \textbf{Copy} button to copy the access URL, and save it to a text file for later use.

You may now \textbf{proceed to the next lab}.


## Learn More

[\textcolor{orange}{Provision Autonomous JSON Database}](https://docs.oracle.com/en/cloud/paas/autonomous-json-database/ajdug/autonomous-provision.html#GUID-0B230036-0A05-4CA3-AF9D-97A255AE0C08)


## Acknowledgements

* **Created By/Date** - Roger Ford, Principal Product Manager, Oracle Database
* **Contributors** - Kamryn Vinson, Andres Quintana
* **Last Updated By** - Hermann Baer, April 2024
