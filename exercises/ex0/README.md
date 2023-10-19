# Getting started

After you did activate your Trial Account for SAP BTP with access to the BTP Cockpit and the SAP Cloud Identity (SCI) Trial with access to the SAP Cloud Identity administrative console you are set for the next steps.

We can expect that you did create a **Trial subaccount** in your SAP BTP Trial Account cockpit.

We also expect that you did enable the **Cloud Foundry Environment**.

Finally you have installed on your mobile device a time-based authentication application (such as SAP Authenticator, Google Authenticator or Microsoft Authenticator).

Following the blog to setup the **SAP Cloud Identity Services (SCI) Trial** you did already establish the Trust configration in your BTP Trial Subaccount, which adds the Trial Identity Provider for applications to enable users from your Trial Identity Provider to log on to applications consumed in this subaccount.

## Result of the preparation

1. Logon to your personal SAP BTP Trial account cockpit with the user you used to activate the Account. Go to the [**SAP BTP Trial page**](https://account.hanatrial.ondemand.com/trial/#/home/trial) and click **Log On**.

2. You will see one main button on the welcome screen of the SAP BTP Cockpit. Click on **Go To Your Trial Account** to navigate to your global account.  
   **Bookmark** the link for fast and quick access to the **BTP cockpit**.

3. Navigate to the subaccount and check if the Cloud Foundry runtime is enabled. If it is **not** enabled, click on **Enable Cloud Foundry**. This may take some seconds. This page displays the current state of the subaccount. You can manage your subscriptions and jump into the different runtime environments. It also shows you fundamental information of the Cloud Foundry environment, such as the API endpoint and the available spaces.

<br>![](/exercises/ex0/images/audit0.png)

<br>![](/exercises/ex0/images/Subaccount%20Overview.png)

4. Check the Trust Configuration for application users

   Navigate in the  BTP Cockpit to **Trial HOME -> your initial subaccount (e.g. Trial Subaccount 1 ) -> Security -> Trust Configuration**

   Check if the Custom Identity Provider for applications is configured. If not go back to the preparations and follow the blog [SAP Cloud Identity Services offered as Trial Version](https://blogs.sap.com/2023/04/13/sap-cloud-identity-services-offered-as-trial-version/) on how to configure it.

<br>![](/exercises/ex0/images/Subaccoount1_TrustConfiguration.png)

5. Logon to your personal Identity Provider - SCI Cockpit (SCI - SAP Cloud Identity service).

   Navigate in your Subaccoount to **Instance and Subscriptions**. Click on the tile next to the subscribt application **Cloud Identity Services** which says **Go to Application** when you hover over it. A new window opens with your SAP Cloud Identity Services Trial Account Cockpit. **Bookmark** the link for fast and quick access to the **SCI cockpit**.

    <br>![](/exercises/ex0/images/SubaccountInstanceandSubscriptions.png)
   
     <br>![](/exercises/ex0/images/SCICockpit.png)

7. In the **SCI administration console -> Applications & Resources -> Applications** you will see the trust configuration that was established by your BTP trial account. It is called **XSUAA_trial**.

<br>![](/exercises/ex0/images/SCI_XSUAA_trial.png")

   Applications you deploy in your BTP subaccount can now delegate authentication to the SCI tenant you just created. And in the **SCI admin console** you may configure the various options for authentication and multi-factor authentication.

 8.  Logout at the **SCI administrative console**.

<br><img src="/exercises/ex1/images/SCI_logout.png" width="70%"> 

## Summary

Now that you have checked all the prerequisites and have access to both administrative cockpits, SAP BTP Cockpit and the SCI Cockpit,  
Continue to - [Exercise 1 - Enable Multi-Factor Authentication for applications](../ex1/README.md)
