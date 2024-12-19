# Exercise 1 - Enable Multi-Factor Authentication for applications

In this exercise, we will show how to enable Multi-Factor Authentication (MFA) using Time-based one-time password (TOTP) for Application Users. In general we recommend to configure Risk-Based Authentication methods, such as Multi-Factor Authentication, for the access to the **SAP BTP Cockpit** and the **SCI administrative console**. In the trial version this is not possible, because there is no possibility to set up a trust configuration to your BTP account on Global account level. This would be necessary to configure the trust for [platform users](https://help.sap.com/docs/btp/best-practices/basic-platform-concepts). 
The configuration in the **SCI administrative console** is the same, only for a different application. You will use **SAP Build Apps** as application to configure the risk-based authentication.

:bulb: **What is Multi-Factor Authentication (MFA)?**

Multi-Factor Authentication can be described as “An authentication mechanism that requires more than one distinct authentication factor for successful authentication”.
When a user authenticates, the user must provide valid credentials consisting of either one or multiple factors. It uses variety of factors and information, to verify the user identity. Many earlier systems use one factor, like a username/ password also called as basic authentication.
Now to strengthen the authentication process we use MFA which acts as another layer of security for users and reduce the risk of unauthorized access.

:bulb:**What is Time-based One-Time Password (TOTP)?**

A Time-based One-Time Password (TOTP) is a numerical code which is generated with a standard algorithm that uses the current time and a key as input. It is user friendly and available offline in a generator application of the user’s choice- usually on a mobile device. It appears as six-digit numbers that regenerate every 30 seconds.


# Relevant Security Recommendations
- BTP-UAA-0001


## Exercise 1.1 - Setup SAP Build Apps and enter the application with your trial identity provider user


1. Open the **SAP BTP Cockpit** and navigate to your global account. You should have bookmarked the URL in the **Getting started** exercise.

2. Navigate to **Boosters**

<br><img src="/exercises/ex1/images/BoostersMenu.png" width="70%">

4. Enter SAP Build Apps in the search field. Click on **Get started with SAP Build Apps**.

<br><img src="/exercises/ex1/images/BoosterTileApps.png" width="70%">

5. Now a wizard opens and you follow the wizard and click next after each entry.

6. Check prerequisites

<br><img src="/exercises/ex1/images/booster2.png" width="70%">

7. Select Scenario - select your subaccount

<br><img src="/exercises/ex1/images/booster3.png" width="70%">

8. Configure subaccount - enter your trial subaccount

<br><img src="/exercises/ex1/images/Booster4.png" width="70%">

9. Add Users - enter your email address for Administrators and Developers

<br><img src="/exercises/ex1/images/Booster5.png" width="70%">

10. Review your entries - Finish

<br><img src="/exercises/ex1/images/booster6.png" width="70%">

11. Progressing - this takes a bit

<br><img src="/exercises/ex1/images/Booster 7.png" width="70%">

12. **Success** - Navigate to the Subaccount 

<br><img src="/exercises/ex1/images/Boostersuccess.png" width="70%">

13. Go to **Instance and Subscriptions** in your Subaccount - Click on the tile to open **SAP Build Apps**

<br><img src="/exercises/ex1/images/openSAPBulidApps.png" width="70%">

14. A Logon page opens. Use your **Trial Account Identity Provider** to logon. There is the Default Identity Provider ( SAP ID Service ) shown and your Trail Account Identity provider (SCI - SAP Cloud Identity).

<br><img src="/exercises/ex1/images/logonSAPBulidApp.png" width="70%">

15.  A Pop-Up will ask for **Email** and **Password**. Enter the Email of your SAP Cloud Identity User and his Password.

<br><img src="/exercises/ex1/images/logon_XSUAA_trial.png" width="50%"> 

15. The Authorization should be successful as your user is assigned to the role collections needed during the booster creation process. You will see the entry page of the **SAP Build App** application.

<br><img src="/exercises/ex1/images/SAP Build App.png" width="70%">

16. **Sign-out** from SAP Build Apps and close the browser window.

<br><img src="/exercises/ex1/images/SAPBUILDsignout.png" width="70%">


## Exercise 1.2 - Configure Multi Factor Authentication to access SAP Build Apps

In exercise 1.1 we enabled SAP Build Apps and the configured users are now able to authenticate with the custom identity provider when they try to access the application. However, we want to restrict the access to the application and only allow access with a second authentication factor.

1. Logout of the SAP Build application and close the Browser window, if you haven`t done already.

<br><img src="/exercises/ex1/images/Singoutsapbuild.png" width="70%">

2. Open the **SCI administrative console**, either from your bookmark or from the **BTP cockpit** (In the BTP Cockpit navigate to  -> **Instances and Subscriptions** -> click on the Tile next to Cloud Identity Services).

<br><img src="/exercises/ex1/images/openSCItenant.png" width="70%">

3. In the pop-up window Sign-In with your email and password to the **SCI administrative console**.
   
<br><img src="/exercises/ex1/images/SigninSCITRIAL.png" width="70%">

4. In the **SCI administrative console** navigate to **Applications & Resources -> Applications**

<br><img src="/exercises/ex1/images/SCItenantApplications.png" width="70%">

5. On the left side you see Bundled and System Applications. In Bundled Applications we see the Application **XSUAA_trial**. Click on it to see the configuration data of this application.

💡  **XSUAA** is a service broker for the OAuth authorization server provided by the Cloud Foundry UAA. It offers authentication and authorization services for micro service style applications. It is used by almost all applications running on SAP BTP in the cloud foundry environment. When we configure Two-factor authentication for this application, all applications running on SAP BTP in the cloud foundry environment, will have to provide a second factor for authentication. 
   
6. In the configuration screen of the XSUAA_trial application navigate to **Authentication & Access**
   
<br><img src="/exercises/ex1/images/SCItrailXSUAA_AuAcc.png" width="70%">

7. Now you can see the line where **Risk-Based Authentication** can be configured. Click on the little arrow on the right.

<br><img src="/exercises/ex1/images/XSUAA_trial_app_SCI.png" width="70%">

8. In the **Risk-Based Authentication** frame you have the possibility to create Authentication Rules and you can see the Default Authentication Rule, which is **Allow**.

 <br><img src="/exercises/ex1/images/SCI_XSUAA_trial_RBA_default.png" width="70%">

9. Change the Default Authentication Rule to **Default Action = Two-Factor Authentication** and **Two-Factor Method = TOTP**. Don´t forget to **save** at the top right of the page the new configuration. Now the access to all applications on your SAP BTP subaccount which use the XSUAAA for authentication require a Time-based One-time Password (TOTP) as second factor.

<br><img src="/exercises/ex1/images/SCI_XSUAA_trial_RBA_MFA.png" width="70%">

Once the configuration is complete, the system prompts the user to select any of the available options after the initial username and password are provided. Next step is to enable the users to use MFA.

## Exercise 1.3 - Enable MFA for your User

1. Navigate to your users profile page in **SAP Cloud Identity**.

2. The user profile shows you the authentication methods setup for a user. You can access it through the following link in the trial environment: 

**https://"trialtenant-ID".trial-accounts.ondemand.com/ui/protected/profilemanagement**

Add the **ui/protected/profilemanagement** in your browser after **https://"trialtenant-ID".trial-accounts.ondemand.com/**

Here you can add/remove your authentication method, like accessing using your fingerprint etc. The next steps need a device with a time-based authentication application installed (such as Google Authenticator or Microsoft Authenticator).

3. Open the Multi-Factor Authentication. Click on **Activate TOTP Two-Factor Authentication**.

<br><img src="/exercises/ex1/images/userprofile1.png" width="70%">

4. Scan the QR code using the authenticator app on your device or enter the key manually. Once you have scanned or entered the key, enter the passcode generated by the authenticator app on your device below and click **Activate**.

<br><img src="/exercises/ex1/images/userprofile2.png" width="70%">

5. Now you have a device configured for TOTP two-factor authentication.

<br><img src="/exercises/ex1/images/userprofile3.png" width="70%">

6. To get back to the **SCI administrative console** add **admin** in your browser after **https://"trialtenant-ID".trial-accounts.ondemand.com/** or use your bookmark.

7. Logout at the **SCI administrative console**.

<br><img src="/exercises/ex1/images/SCI_logout.png" width="70%">

8. Navigate to the **SAP BTP cockpit -> Instance and Subscriptions -> SAP Build Apps -> Open the Application**

<br><img src="/exercises/ex1/images/MFASAPBUILDAPPSOpen.png" width="70%">

9. Select our SCI tenant to logon.

<br><img src="/exercises/ex1/images/MFASAPBUILDAPPSLogon1.png" width="70%">

10. A Pop-Up will ask for **Email** and **Password**. Enter the Email of your SAP Cloud Identity User and his Password.

<br><img src="/exercises/ex1/images/logon_XSUAA_trial.png" width="50%"> 

11. The next Pop-Up will ask for a **passcode**. Open the **authenticator app** you are using on our mobile device. To proceed, please enter the time-based passcode generated by your mobile device for the application. Then continue.

<br><img src="/exercises/ex1/images/MFASAPBUILDAPPSPasscode.png" width="70%">

12. **Success!** The SAP Build App opens.

<br><img src="/exercises/ex1/images/SAP Build App.png" width="70%">


## Summary

In this exercise you learned how to setup SAP Build and how to enable Multi-Factor Authentication (MFA) using a Time-based One-Time Password (TOTP).



Continue to - [Exercise 2 - Security Recommendations regarding user access and authentication](../ex2/README.md)
