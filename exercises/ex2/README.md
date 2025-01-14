# Exercise 2 - Security Recommendations regarding user access and authentication

In this exercise you will learn about further security recommendations that help protect your accounts from risks related to access and authentication.

# Relevant Security Recommendations
- BTP-IAS-0002
- BTP-IAS-0003
- BTP-IAS-0005
- BTP-IAS-0017


## Exercise 2.1 Identify obsolete users

It makes sense to review on a regular basis whether the configured users really need access to administrative tasks and cockpits. After all, an abandoned account with high privileges could become a target for an attacker. We have two administration cockpits that are relevant for this exercise. One is the **SAP BTP cockpit**, and the other one is the **administration console for SAP Cloud Identity Services**. In the trial version of the BTP cockpit, we do not have access to the global account user management and security functionalities. On the other hand, we do have access to the administration console for SAP Cloud Identity Services. In this exercise we will therefore focus on the users in the administration console of the SAP Cloud Identity Services. SAP Cloud Identity Services play a critical role in the access to SAP cloud applications. That is why it's mandatory to monitor and limit the number of users that have administrative access. The permissions of the SAP Cloud Identity Services are based on the permission concept of the internal user store.

1. Open the **administration console for SAP Cloud Identity Services** from your bookmarks or like described in the first exercise. 

<br><img src="/exercises/ex2/images/SCI_Console.png" width="70%">

2. First, we will add a new test user. Navigate to **User & Authorizations --> User Management**
   
3. Click on the **+ Add**-button.

<br><img src="/exercises/ex2/images/Add_User.png" width="70%">

4. A pop-up window will allow you to enter the relevant test user information. You are free to choose the name and email address. Set the status to active. Click on the **+ Add**-button.

<br><img src="/exercises/ex2/images/Add_User_Doe.png" width="70%">

5. Now we add the newly created user to the Administrators. Choose the menu item **Users & Authorizations --> Administrators**.

<br><img src="/exercises/ex2/images/MenuItem_Admins.png" width="70%">

6. Click on **Add --> User**.

<br><img src="/exercises/ex2/images/Add_Admin_User.png" width="70%">

7. Add the **Identifier** information (Email address) of the new test user in the Add Administrator window.

<br><img src="/exercises/ex2/images/Enter_Doe_EMail.png" width="70%">

8. As a user record with this identifier is found in the identity directory, you do not need to enter additional user details. Click on the **OK** button.

<br><img src="/exercises/ex2/images/Enter_Doe_EMail_Confirm.png" width="70%">

9. Click the **Save** button to make the test user an administrator of SAP Cloud Identity Services.

<br><img src="/exercises/ex2/images/Save_Doe_Admin.png" width="70%">
   
10. Now we can check the user and his authorizations. The assignment of the following authorizations is especially critical.
- Manage Corporate Identity Providers
- Manage Tenant Configuration
- Manage Users
  
<br><img src="/exercises/ex2/images/Admin_Access.png" width="70%">

11. Remove the authorizations, which are not needed anymore by the user. If you remove all of them the user will no longer be an administrator, and the name will be removed from the list on the left. We will do this now. Disable all authorizations. Then click on the **Save**-button.

<br><img src="/exercises/ex2/images/Remove_Admin_Access.png" width="70%">

12. Now you have to confirm your changes. Click on the **OK** button. 

<br><img src="/exercises/ex2/images/Confirm_Remove_Admin_Access.png" width="70%">

13. The only administrator left will be your trial account user. You cannot remove the authorizations of this user completely, as you would otherwise lock yourself out of the administration console. For this reason, the authorization **Manage Tenant Configuration** is greyed out. 

<br><img src="/exercises/ex2/images/Own_User_Access.png" width="70%">

## Exercise 2.2 Defining a custom password policy

By default, SAP Cloud Identity Services come with 2 password policies, Standard and Enterprise. In this exercise you will learn how to define your own password policy, based on your company's requirements.

1. Open the **administration console for SAP Cloud Identity Services**. 

<br><img src="/exercises/ex2/images/SCI_Console.png" width="70%">

2. Choose the menu item **Applications & Resources --> Password Policies**

<br><img src="/exercises/ex2/images/MenuItem_PasswordPolicies.png" width="70%">

3. Click on the button **+ Create**. 

<br><img src="/exercises/ex2/images/Create_PasswordPolicy.png" width="70%">

4. The dialog **Create Custom Password Policy** is displayed.

5. Set the policy strength to **3**. This implies that this policy has a higher priority than the existing policies "Standard" and "Enterprise". This becomes relevant when a user accesses applications with different password policy requirements. A password policy with strength 3 will also be accepted by applications that require strength 1 or 2.

<br><img src="/exercises/ex2/images/PasswordPolicy_Details.png" width="70%">

💡 SAP Cloud Identity Services do not measure the strength of the policy that you define. It is up to you do decide, which properties are required for a password to be considered strong.

6. Decide on the "Password Behavior". If the password set by the user does not comply with the policy, should the user be able to set a new password by entering the old one, or should the password reset process be triggered?

7. Set the "Required character groups count" to 3. SAP Cloud Identity Services supports 4 types of character groups: uppercase letters, lowercase letters, numbers, and symbols. With this setting you specify how many different groups need to be part of the password. 

8. Fill out the remaining fields of the "Custom Password Policy" dialog and click on the **"+ Create"**-button. Your new password policy is added to the top of the list as it has the highest strength.

<br><img src="/exercises/ex2/images/PasswordPolicies_List.png" width="70%">

Now you know how to create a custom password policy that you can use for additional protection of your applications. We now want to add the password policy to an application. 

9. Navigate to **Applications & Resources --> Applications**. Select the **SAP Build Apps** application on the left and choose on the right side **Authentication & Access --> Policies**.

<br><img src="/exercises/ex2/images/Application_AuthNConfig.png" width="70%">

10. Choose **Password Policy**

<br><img src="/exercises/ex2/images/Application_PasswordPolicy.png" width="70%">

11. Select your custom password policy. Click on the **Save**-button.

<br><img src="/exercises/ex2/images/Application_Assign_PasswordPolicy.png" width="70%">

Now the new password policy is active for the application. It sets the rules you defined for the password length and content as well as how users need to update their password. 

## Exercise 2.3 Keep public access to applications by self-registration disabled

For business-to-consumer (public) scenarios, self-registration may be required. By default, self-registration is disabled (value = internal) and can be configured per application.
Corporate identity lifecycle processes make self-registration undesirable in most business-to-employee (B2E) and business-to-business (B2B) scenarios. We recommend keeping self-registration disabled. Actively manage use cases that require this functionality.

1. Open the **administration console for SAP Cloud Identity Services**.

<br><img src="/exercises/ex2/images/SCI_Console.png" width="70%">

2. Under **Applications & Resources**, choose the **Applications** menu item.

<br><img src="/exercises/ex1/images/SCIConsoleApps.png" width="70%">

3. Choose the application that you want to edit.
4. Choose the **Authentication and Access** tab.
5. Under **Authentication**, choose **User Application Access**.

<br><img src="/exercises/ex2/images/User_Application_Access.png" width="70%">

6. Set the radio button to define which set of users will be able to access the application: Public, Internal or Private.

<br><img src="/exercises/ex2/images/Set_User_Application_Access.png" width="70%">
  
7. The default setting is already **Internal**. Because of that you don't need to change it.

## Exercise 2.4 Keep Social Sign-On disabled

For business-to-consumer (public) scenarios, social sign-on may be required. When activated, users can log on with their Apple, Google, Facebook, Twitter, or LinkedIn accounts. By default, social sign-on is disabled and can be configured per application.
Corporate identity lifecycle processes make social sign-on undesirable in most business-to-employee (B2E) and business-to-business (B2B) scenarios.

1. Sign in to the **administration console for SAP Cloud Identity Services**.

<br><img src="/exercises/ex2/images/SCI_Console.png" width="70%">

2. Under **Applications & Resources**, choose the **Applications** menu item.

<br><img src="/exercises/ex1/images/SCIConsoleApps.png" width="70%">

3. Choose the application that you want to edit.
4. Choose the **Authentication and Access** tab.
5. Under **Authentication**, enable or disable **Social Sign-On** using the radio-button. Per default it should be disabled. Because of that you don't need to change it.

<br><img src="/exercises/ex2/images/SocialSignOn.png" width="70%">

With social sign-on, users can log on to the application via one of the social network providers. They can will the respective option on the logon page. Which social identity providers' logos appear on the logon page of the application depends on the configurations you have made.

7. Logout at the **SAP Cloud Identity Services administration console**.

<br><img src="/exercises/ex2/images/SCI_Logout.png" width="70%">

## Summary

In this exercise you have learned how to identify potentially not needed user accounts. In addition, you have seen how you can define custom password policies, and how to check several settings related to the authentication of users.



Continue to - [Exercise 3 - Security Recommendations regarding the Audit Log ](../ex3/README.md)
