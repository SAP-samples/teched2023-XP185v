# Exercise 3 - Security Recommendations regarding the Audit Log

In this exercise you will learn about security recommendations that help protect your accounts from risks by using the audit log.
The SAP Audit Log service is a platform service that stores all the audit logs written on your behalf by other platform services that you use. It allows you to retrieve the audit logs for your subaccount via the [audit log retrieval API](https://help.sap.com/docs/btp/sap-business-technology-platform/audit-log-retrieval-api-usage-for-subaccounts-in-cloud-foundry-environment) or view them using the SAP Audit Log Viewer service. The default retention time is 90 days, after which the audit log data is deleted.
Because of that, we recommend downloading audit logs on a regular basis and save them, ideally in an existing and central audit log system or Security Information and Event Management (SIEM) system of your choice. This can be done via the audit log retrieval API or in the SAP Audit Log Viewer service. 

# Relevant Security Recommendations
- BTP-AUD-0001


## Exercise 3.1 Subscribe to the SAP Audit Log Viewer service

In this exercise you will subscribe to the **Audit Log Viewer Service**

1. Open the **SAP BTP Cockpit** and navigate to your **trial subaccount** by clicking on the tile.

  <br><img src="/exercises/ex0/images/GlobalAccount.png" width="70%">

2. Go to **Service Marketplace**.

 <br><img src="/exercises/ex3/IMAGES/ServiceMarketplace.png" width="70%">

3. Enter **audit** in the search field. Select the **Audit Log Viewer Service** and click on it.

<br><img src="/exercises/ex3/IMAGES/AuditLogServiceTile.png" width="70%">
  
4. Now subscribe to it. This is done by using the **Create**-button in the upper right corner. The **Audit Log Management Service** can later be used to configure the retention period and to retrieve the logfiles for your SIEM system. We don't need it in this exercise.

<br><img src="/exercises/ex3/IMAGES/CreateAuditLogService.png" width="70%">

5. A window pops up. Click on the **Create**-button.

<br><img src="/exercises/ex3/IMAGES/CreateAuditLogServiceDialog.png" width="70%">

6. Navigate to **View Subscription**
   
<br><img src="/exercises/ex3/IMAGES/AuditLogServiceViewSubscription.png" width="70%">

7. Under **Instances and Subscriptions**, you can now see the new Application **Audit Log Viewer Service** and the **Go to Application** button.
   
<br><img src="/exercises/ex3/IMAGES/AuditLogServiceSubscriptionDetails.png" width="70%">


## Exercise 3.2 Configure the SAP Audit Log Viewer service

 In this exercise you will configure the SAP Audit Log Viewer service to see audit relevant log entries.

1. Open the **SAP BTP Cockpit**. 

  <br><img src="/exercises/ex0/images/GlobalAccount.png" width="70%">

2. Go to the **trial subaccount** by clicking on the tile.

3. Choose the menu item **Security --> Role Collections** and click on the **"+"**-button to create a new role collection.

<br><img src="/exercises/ex3/IMAGES/CreateRoleCollection.png" width="70%">

4. In the pop-up window enter the role collection name **Audit Log Viewer**. In the description enter **View the audit relevant logs in the audit log viewer**.
Click on the **Create**-button.

<br><img src="/exercises/ex3/IMAGES/CreateViewerRoleCollection.png" width="70%">

5. Now you can see the **Audit Log Viewer** role collection together with the other role collections. Click on **">"** on the right side of the newly created role collection to open the details. 

6. In the extended window you can assign roles and users to the role collection. Start assigning the two roles of the audit log viewer service called **Auditlog_Auditor** to the role collection. To do so click on the **Edit**-button.

<br><img src="/exercises/ex3/IMAGES/EditViewerRoleCollection.png" width="70%">

7. Open the selection dialog for roles in **Roles** section.

<br><img src="/exercises/ex3/IMAGES/OpenRoleSelectionDialog.png" width="70%">

8. Mark the two roles called **Auditlog_Auditor** and click the "Add"-button. 

<br><img src="/exercises/ex3/IMAGES/AddRoles2.png" width="70%">

9. Go to the **Users** section and enter the email address of your **SAP Cloud Identity Services user**. Enter it in the **ID** field and select the entry from the list.

<br><img src="/exercises/ex3/IMAGES/SelectUser.png" width="70%">
 
10. Click the **Save** button to save your changes.

<br><img src="/exercises/ex3/IMAGES/RoleCollectionCreated.png" width="70%"> 
 
11. The result will be that the user with the assigned authorizations can use the **Audit Log Viewer service**. You need to be logged into the cockpit with this user to be able to see the Viewer in the next step.

 


## Exercise 3.3 Check the audit logs and download audit log entries via the SAP Audit Log Viewer service

You can download the audit logs via the audit log retrieval API to import them into your Security Information and Event Management (SIEM) system or you can download them via the Viewer User Interface to store them as backup on your file system.
Now you learn how to download them via the User Interface.

1. Open the **SAP BTP Cockpit**. 

  <br><img src="/exercises/ex0/images/GlobalAccount.png" width="70%">

2. Navigate to **Services > Instances and Subscriptions**. Under Subscriptions you will see the **Audit Log Viewer service**. Next to the text field there is a link to the user interface. Click on it.
 
  <br><img src="/exercises/ex3/IMAGES/LinkViewerUI.png" width="70%">

3. A logon page will appear. Select your **Trial SAP Cloud Identity Services** tenant.

4. A Pop-Up will ask for **Email** and **Password**. Enter the Email of your SAP Cloud Identity Services user and his password.

   <br><img src="/exercises/ex1/images/ViewerUILogon.png" width="50%"> 

5. As we enabled in the first exercise Multi-Factor Authentication (MFA) using Time-based one-time password (TOTP) for Applications on BTP,  the **Two-Factor Authentication** window will pop-up. Generate the passcode on your mobile device and enter it. After entering the time-based passcode generated by your mobile device,  the **Audit Log Viewer**-application will open.

  <br><img src="/exercises/ex1/images/ViewerUILogon2FA.png" width="70%">

6. In the newly opened **Audit Log Viewer UI** you can accept the default timeframe or select a specific one to see the latest audit log entries. On the right side there is button to retrieve the logs after the selection of the timeframe.

   <br><img src="/exercises/ex3/IMAGES/ViewerUI.png" width="70%">

7. Now you can see the log entries of the specific audit relevant changes, which have been performed lately. 

   <br><img src="/exercises/ex3/IMAGES/AuditLog.png" width="70%">

8. The retention period of the logs in the Cloud Foundry environment is 90 days. Therefore, it is recommended to backup the audit log files or import them via the audit log retrieval API into a SIEM system.  You can download the files from the user interface. To do so, click on the download button in the middle of the headline.

   <br><img src="/exercises/ex3/IMAGES/AuditLogDownload.png" width="70%">

9. In the pop-up window, select a place on your laptop to save the **viewLogs.json** file. Click on **Save**.

You now know how to download the audit relevant log files for backup.

## Summary

In this exercise you have configured the **SAP Audit Log Viewer service** to see the audit relevant log entries. In addition, you have seen how to download the audit.log files before the retention period ends.

