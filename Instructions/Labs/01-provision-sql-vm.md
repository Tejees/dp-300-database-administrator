# Lab 01: Provision a SQL Server on an Azure Virtual Machine

## Estimated Time: 30 minutes

## Lab scenario
Students will explore the Azure Portal and use it to create an Azure VM with SQL Server 2019 installed. Then they will connect to the virtual machine through Remote Desktop Protocol.

You are a database administrator for AdventureWorks. You need to create a test environment for use in a proof of concept. The proof of concept will use SQL Server on an Azure Virtual Machine and a backup of the AdventureWorksDW database. You need to set up the Virtual Machine, restore the database, and query it to ensure it is available.

## Lab objectives

In this lab, you will complete the following tasks:

- Task 1: Deploy a SQL Server on an Azure Virtual Machine
- Task 2: Connect to SQL Server on an Azure Virtual Machine

## Architecture 
In Task 1, you will deploy a SQL Server on an Azure Virtual Machine using the Azure portal. Then, in Task 2, you connect to that SQL Server from a client machine using tools like SSMS by enabling necessary network configurations. This setup allows you to run and manage SQL Server in the cloud.

## Architecture diagram

![](../images/preview(01).png)

### Task 1 - Deploy a SQL Server on an Azure Virtual Machine

In this task you will be deploying a SQL Server on an Azure Virtual Machine allows you to run SQL Server in the cloud which provides flexibility for customization, backups, and scaling as per workload needs.

1. On the Azure portal locate the search bar at the top of the page. Search for **Azure SQL (1)**. Select the search result for **Azure SQL (2)** that appears in the results under **Services**.

    ![Picture 9](../images/dp-300-lab1-1.png)

1. On the **Azure SQL** blade, select **Create**.

    ![Picture 10](../images/dp-300-lab1-2.png)

1. On the **Select SQL deployment option** blade, click on the drop-down box under **SQL virtual machines(1)**. Select the option labeled **Free SQL Server License: SQL 2019 Developer on Windows Server 2022(2)**. Then select **Create**.

    ![Picture 11](../images/dp-300-lab1-3.png)

1. On the **Create a virtual machine** page, enter the following information and click **Next:Disks>**

    - **Subscription(1):** Use existing subscription 
    - **Resource group(2):** contoso-rg-<inject key="DeploymentID" enableCopy="false"/>
    - **Virtual machine name(3):**  azureSQLServerVM
    - **Region(4):** <inject key="location" enableCopy="false" />
    - **Availability Options(5):** No infrastructure redundancy required
    - **Security Type(6)**: Standard
    - **Image(7):** Free SQL Server License: SQL 2019 Developer on Windows Server 2022 - Gen1
    - **Run with Azure spot instance(8):** No (unchecked)
    - **Size(9):** Standard *D2s_v3* (2 vCPUs, 8 GiB memory). You may need to select the **"See all sizes"** link to see this option)
    - **Administrator account username(10):** sqladmin
    - **Administrator account password(11):** pwd!DP300lab01
    - **Confirm password(12):** pwd!DP300lab01
    - **Select inbound ports:** RDP (3389)
    - **Would you like to use an existing Windows Server license?:** No (unchecked)

    Make note of the username and password for later use.

    ![Picture 12](../images/infra.png)

1. Review the configuration on **Disks** tab, **Networking** tab  and navigate to  **Next:Management>** 

1. On the **Management (1)** tab and review the configuration and Verify that **Enable auto-shutdown (2)** is unchecked, click **Next:Monitoring> (3)**

    ![Picture 15](../images/dp-300-lab1-6.png)
    
1. Review the configuration on  **Monitoring** tab, **Advanced** tab and  **SQL Server settings** tab 
 
    >**Note**: you can also configure the storage for your SQL Server VM on this screen. By default, the SQL Server Azure VM templates create one premium disk with read caching for data, one premium disk without caching for transaction log, and uses the local SSD (D:\ on Windows) for tempdb.

1. Select the **Review + create** button. Then select **Create**.

1. On the deployment blade, wait until the deployment is complete. The VM will take approximate 5-10 minutes to deploy. After the deployment is complete, select  **Go to resource**.

    >**Note:** Your deployment may take 5-10 minutes to complete.

    ![Picture 19](../images/up1.png)
    
 1. On the **Overview** page for the virtual machine, explore the menu options for this resource to review what is available.

    ![Picture 20](../images/dp-300-lab1-9.png)
    
> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
- Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
- If not, carefully read the error message and retry the step, following the instructions in the lab guide.
- If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.

  <validation step="577c1452-0678-4fb0-9302-18ecc9944a6c" />

### Task 2 - Connect to SQL Server on an Azure Virtual Machine

In this task you will be connecting to SQL Server on an Azure Virtual Machine which involves accessing the VM using its public IP and SQL credentials via tools like SSMS.

1. On the **Overview** page for the virtual machine, select the **Connect** pulldown and select **Connect**.

1. On the RDP tab, select the **Download RDP File** button.

    ![Picture 22](../images/sqlconnect.png)

    >**Note**: If you see the error **Port prerequisite not met**. Make sure to select the link to add an inbound network security group rule with the destination port mentioned in the *Port number* field.

    ![Picture 22_1](../images/dp-300-lab1-11.png)

1. Open the RDP file that was just downloaded. When a dialog appears asking if you want to connect, select **Connect**.

    ![Picture 23](../images/dp-300-lab1-12.png)

1. Enter the username: **sqladmin(1)** and password : **pwd!DP300lab01 (2)** selected during the virtual machine provisioning process. Then select **OK(3)**.

    ![Picture 24](../images/dp-300-lab1-13.png)

1. When the **Remote Desktop Connection** dialog appears asking if you want to connect, select **Yes**.

    ![Picture 26](../images/dp-300-lab1-14.png)

1. Inside the Virtual Machine, Select the search bar besides the Windows Start button and type **SSMS(1)**. Select **SQL Server Management Studio 20(2)** from the list.  

   ![Picture 34](../images/dp-300-lab1-15.png)

1. When SSMS opens, notice that the Connect to Server dialog will be pre-populated with the default instance name. Check the option **Trust server certificate** and then select Connect.

    ![Picture 35](../images/up2.png)

>**Note**: Make sure Encryption is selected as Mandatory.

>**Results:** In this exercise, you've seen how the Azure portal gives you powerful tools to manage a SQL Server hosted in a virtual machine. These tools include control over automated patching, automated backups, and giving you an easy way to setup high availability.

### Review

In this lab, you have completed:

- Deployed a SQL Server on an Azure Virtual Machine
- Connected to SQL Server on an Azure Virtual Machine

### You have successfully completed the lab.
