# Getting started

After you have activated your trial account for SAP BTP with access to the BTP Cockpit and the SAP Cloud Identity (SCI) trial with access to the SAP Cloud Identity administrative console you are set for the next steps.

We expect that you have created a **trial subaccount** in your SAP BTP trial account cockpit.

We also expect that you have enabled the **Cloud Foundry Environment**.

Finally, you have installed on your mobile device a time-based one-time password (TOTP) authentication application (such as Google Authenticator or Microsoft Authenticator).

Following the blog to setup the **SAP Cloud Identity Services (SCI) trial** you have already established the trust configuration in your BTP trial subaccount, which adds the trial identity provider for applications to enable users from your trial identity provider to log on to applications consumed in this subaccount.

## Result of the preparation

1. Logon to your personal SAP BTP trial account cockpit with the user you used to activate the account. Go to the [**SAP BTP Trial page**](https://account.hanatrial.ondemand.com/trial/#/home/trial) and click **Log On**.

2. You will see one main button on the welcome screen of the SAP BTP cockpit. Click on **Go To Your Trial Account** to navigate to your global account.  
   **Bookmark** the link for fast and quick access to the **BTP cockpit**.

3. Navigate to the subaccount by clicking on the tile.

  <br><img src="/exercises/ex0/images/GlobalAccount.png" width="70%">

  Note: If the tile is disabled then you may have to add yourself as subaccount administrator.

  <br><img src="/exercises/ex0/images/AddMeAsAdmin.png" width="70%">

4. Check if the Cloud Foundry runtime is enabled in the subaccount. If it is **not** enabled, click on **Enable Cloud Foundry**. This may take some seconds. This page displays the current state of the subaccount. You can manage your subscriptions and jump into the different runtime environments. It also shows you fundamental information of the Cloud Foundry environment, such as the API endpoint and the available spaces.

  <br><img src="/exercises/ex0/images/SubAccount2.png" width="70%">

5. Check the trust configuration for application users.

   Navigate in the  BTP Cockpit to **Trial HOME -> your initial subaccount (e.g. trial) -> Security -> Trust Configuration**

   Check if the Custom Identity Provider for applications is configured. If not, then go back to the preparations and follow the blog [SAP Cloud Identity Services offered as Trial Version](https://blogs.sap.com/2023/04/13/sap-cloud-identity-services-offered-as-trial-version/) on how to configure it.

  <br><img src="/exercises/ex0/images/TrustConfig.png" width="70%">

6. To logon to your personal identity provider, navigate in your subaccount to **Instance and Subscriptions**. Click on the tile next to the subscribed application **Cloud Identity Services**, which says **Go to Application** when you hover over it. A new window opens with your SAP Cloud Identity Services trial account cockpit. 

  <br><img src="/exercises/ex0/images/CIS_Link3.png" width="70%">

7. **Bookmark** the link for fast and quick access to the **SCI cockpit**.
   
  <br><img src="/exercises/ex0/images/SCI_Cockpit.png" width="70%"> 

8. In the **SCI administration console -> Applications & Resources -> Applications** you will see the trust configuration that was established by your BTP trial account. It is called **SAP BTP subaccount trial**.

  <br><img src="/exercises/ex0/images/TrialSubaccountApp3.png" width="70%"> 

  Applications you deploy in your BTP subaccount can now delegate authentication to the SCI tenant you just created. And in the **SCI admin console** you may configure the various options for authentication and multi-factor authentication.

 9.  Log out of the **SCI administrative console**.

  <br><img src="/exercises/ex0/images/SCI_Logout.png" width="70%"> 

## Summary

Now that you have checked all the prerequisites and have access to both administrative cockpits, SAP BTP cockpit and the SCI cockpit,  
Continue to - [Exercise 1 - Enable Multi-Factor Authentication for applications](../ex1/README.md)
