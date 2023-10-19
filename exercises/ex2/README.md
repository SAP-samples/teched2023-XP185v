# Exercise 2 - Security Recommendations regarding user access and authentication

In this exercise you will learn about further security recommendations that help protect your accounts from risks related to access and authentication

# Relevant Security Recommendations
- BTP-IAS-0002
- BTP-IAS-0003
- BTP-IAS-0005
- BTP-IAS-0017


## Exercise 2.1 Identify obsolete users

It makes sense to review on a regular basis whether the users actually need access to adminsitrative tasks and cockpits. After all, an abandoned account with high privileges could become an attack target. We have two administrative cockpits we deal with in this excercise. One is the **SAP BTP cockpit** and the other one is the **administrative console for Cloud Identity Services**. In the Trial BTP cockpit we don´t have access to the global account user management and security functionalities. In the administrative console for Cloud Identity Services we have access. In this excercise we will check for the users in the administrative console for Cloud Identity Services. SAP Cloud Identity services play a critical role in the access to SAP cloud applications. Because the central role of the services, it's required to reduce the number of administrators with full access. SAP Cloud Identity services permissions are based on the internal user store and its permission concept.

1. Open the **administrative console for Cloud Identity Services** from your bookmarks or like describt in the fist excercise. 

<br><img src="/exercises/ex2/images/SCICockpit.png" width="70%">

2. First we will add a new test user. Navigate to **User & Authorizations -> User Management**
3. Click on the **+ Add**-button

<br><img src="/exercises/ex2/images/ex200user1.png" width="70%">

4. A pop-Up window will allow to enter the relevant test user information. You are free to choose the name and email adress. Set the status to active. Click on the **+ Add**-button.

<br><img src="/exercises/ex2/images/ex200user2.png" width="70%">

5. Now we add the newly created user to the Administrators. Choose the menu item **Users & Authorizations --> Administrators**.

<br><img src="/exercises/ex2/images/ex22.png" width="70%">

6. Click on **Add -> User**

<br><img src="/exercises/ex2/images/ex20add.png" width="70%">

7. Add the **Identifier** information (Email adress) of the new test user in the Add Administrator window and click on the **Save**-button.

<br><img src="/exercises/ex2/images/ex200user3.png" width="70%">
   
7. Now we can check the User and his authorizations. The assignment of the following authorizations is critical.
You will manage them ideally as part of your identity lifecycle process.
- Manage Corporate Identity Providers
- Manage Tenant Configuration
- Manage Users
  
<br><img src="/exercises/ex2/images/ex200user4.png" width="70%">

8. Remove the authorizations, which are not needed anymore. If you remove all of them the user will no longer be an administrator, and the name will be removed from the list on the left. We will do this now. Uncheck all Radio-buttons. Then click on the **Save**-button.

<br><img src="/exercises/ex2/images/ex200user5.png" width="70%">

9. Now you have to confirm your changes. Click on the **Okay**-button. 

<br><img src="/exercises/ex2/images/ex200user6.png" width="70%">

The only administrator left will be your trial account user.
You cannot remove the authorizations of this user completely, as he is the only one left. 
For this reason the authorization
- Manage Tenant Configuration
- Manage tenant configuration and authorization assignment to users 

is greyed out. 

<br><img src="/exercises/ex2/images/ex2_MTC.png" width="70%">


## Exercise 2.2 Defining a custom password policy

By default, SAP Cloud Identity services come with 2 password policies, Standard and Enterprise. In this exercise you will learn how to define your own password policy, based on your company's requirements.

1. Open the **administration console for Cloud Identity Services**. 

<br><img src="/exercises/ex2/images/SCICockpit.png" width="70%">

2. Choose the menu item **Applications & Resources --> Password Policies**

<br><img src="/exercises/ex2/images/ex2pp1.png" width="70%">

3. Click on the button **Add Custom Policy**. 

<br><img src="/exercises/ex2/images/ex2pp2.png" width="70%">

4. The dialog **Custom Password Policy** is displayed

<br><img src="/exercises/ex2/images/ex2pp3.png" width="70%">

5. Set the policy strength to **3**. This implies that this policy has a higher priority than the existing policies "Standard" and "Enterprise". This becomes relevant when a user accesses applications with different password policy requirements. A password policy with strength 3 will also be accepted by applications that require strength 1 or 2.

💡 Identity Authentication service does not measure the strength of the policy that you define. It is up to you do decide, which properties are required for a password to be considered strong

6. Decide on the "Password Behavior". Should the user be able to reset an expired password with the old one, or should the user have to perform the password reset process?

7. Set the "Required character groups count" to 3. SAP Cloud Identity services supports 4 types of character groups, uppercase letters, lowercase letters, numbers, and symbols. With this setting you specific how many different groups need to be part of the password. 

8. Fill out the remaining fields of the "Custom Password Policy" dialog and click on the **"Add"**-button. Your new password policy is added to the top of the list as it has the highest strength.

<br><img src="/exercises/ex2/images/ex2pp4.png" width="70%">

Now you know how to create a custom password policy that you can use for additional protection of your applications. We now want to add the pasword policy to an application. 

9. Navigate to **Applications & Resources -> Applications**. Select one application on the left and choose on the right side **Authentication & Access -> Policies**.

<br><img src="/exercises/ex2/images/addpp1.png" width="70%">

10. Choose **Password Policy**

<br><img src="/exercises/ex2/images/addpp2.png" width="70%">

11. Select your custom password policy. Click on the **Save**-button.

Now the new password policy is active for the application. It sets the rules you defined for the password length and content as well as how users can update and unlock passwords. 

## Exercise 2.3 Keep public access to applications by self-registration disabled

For business-to-consumer (public) scenarios, self-registration may be required. By default, self-registration is disabled (value = internal) and can be configured per application.
Corporate identity lifecycle processes make self-registration undesirable in most business-to-employee (B2E) and business-to-business (B2B) scenarios. We recommend to keep self-registration disabled (value = internal). Actively manage use cases that require the function.

Procedure

1. Open the **administration console for Cloud Identity Services**.

<br><img src="/exercises/ex2/images/SCICockpit.png" width="70%">

2. Under **Applications & Resources**, choose the **Applications** tile.

<br><img src="/exercises/ex2/images/ex2selfreg1.png" width="70%">

3. Choose the **application** that you want to edit.
4. Choose the **Authentication and Access** tab.
5. Under **Authentication**, choose **User Application Access**.

<br><img src="/exercises/ex2/images/ex2selfreg2.png" width="70%">

6. Set the radio button for the users you want to allow to log on:
- Public
- Internal
- Private

<br><img src="/exercises/ex2/images/ex2selfreg3.png" width="70%">
  
7. Save your selection. The default setting is already **Internal**. Because of that you don´t need to change it.
8. If the application is updated, the system displays the message "Application - *name of application*" updated.

## Exercise 2.4 Keep Social Sign-On disabled

For business-to-consumer (public) scenarios, Social Sign-On may be required. If activated users are allowed to log on with their Apple, Google, Facebook, Twitter, or LinkedIn accounts. By default, Social Sign-On is disabled, set to Off, and can be configured per application.
Corporate identity lifecycle processes make social sign-on undesirable in most business-to-employee (B2E) and business-to-business (B2B) scenarios.

Procedure

1. Sign in to the **administration console for SAP Cloud Identity Services**.

<br><img src="/exercises/ex2/images/SCICockpit.png" width="70%">

2. Under **Applications & Resources**, choose the **Applications** tile.

<br><img src="/exercises/ex2/images/ex2selfreg1.png" width="70%">

3. Choose the **application** that you want to edit.
4. Choose the **Authentication and Access** tab.
5. Under **Authentication**, enable or disable **Social Sign-On** using the radio-button. Per default it should be disabled. Because of that you don´t need to change it.

<br><img src="/exercises/ex2/images/ex2sso1.png" width="70%">

6. Once the application has been updated, the system displays the message "Application - *name of application*" updated.

With Social Sign-On users can log on to the application via one of the social providers. They can see this option on the logon page. Which social identity providers logos appear on the logon page of the application depends on the configurations you have made.

7. Logout at the **SCI administrative console**.

<br><img src="/exercises/ex1/images/SCI_logout.png" width="70%">

## Summary

In this exercise you have learned how to identity potentially not needed user accounts. In addition, you have seen how you can define custom password policies, and how to check for several settings related to the authentication of users.



Continue to - [Exercise 3 - Security Recommendations regarding the Audit Log ](../ex3/README.md)
