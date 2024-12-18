# Exercise 4 - Managing administrative authorizations in SAP Cloud Identity

SAP Cloud Identity offers a wealth of functionality in the space of Identity and Access Management (IAM). Especially in larger organizations, it may not be possible for any individual to manage all IAM processes available in the cockpit, or be responsible for the IAM-related configuration of all end users in the organization. A solution for this problem is to share the work among multiple persons. However, by default, everybody working as an administrator in the SAP Cloud Identity cockpit has very broad authorizations. It may be a security risk if individuals that are meant to perform limited administrative tasks have full administrative access way beyond their area of responsibility. 
In this execise you will learn how to implement fine grained administrative authorizations that allow you to give limited access when delgating administrative tasks to others.  

## Exercise 4.1 Enable policy-based authorizations in SAP Cloud Identity

1. Open the administrative console for SAP Cloud Identity services from your bookmarks or like described in the first exercise.

  <br><img src="/exercises/ex2/images/SCICockpit.png" width="70%">

2. Go to **Tenant Settings** in the **Applications & Resources** section.

  <br><img src="/exercises/ex4/images/TenantSettings.png" width="70%">

3. Open the tab **Policy-Based Authorizations**

  <br><img src="/exercises/ex4/images/PolicyBasedAuthZMenu.png" width="70%">

4. Enable policy-based authorizations

  <br><img src="/exercises/ex4/images/EnablePolicyBasedAuthZ.png" width="70%">

## Exercise 4.2 Create an authorizations policy for reading users

1. Open the menu and go to the **Applications** user interface

  <br><img src="/exercises/ex4/images/ApplicationsMenu.png" width="70%">

2. Select the system application **Administration Console** , which represents the administration console of SAP Cloud Identity services.

  <br><img src="/exercises/ex4/images/Applications.png" width="70%">

3. Open the tab **Authorization Policies**
  
  <br><img src="/exercises/ex4/images/AdminConsoleApp.png" width="70%">

4. A list of authorization policies is displayed, which can be used to manage access to the administration console. Click on the **Create** dropdown menu and select the menu item **Create Restriction**

  <br><img src="/exercises/ex4/images/AdminConsoleAppPolicies.png" width="70%">
  
5. In the popup dialog, enter the policy name **READ_USERS_BESTRUN** and choose the base policy **users.READ_USERS**. Then click on **Create**.

  <br><img src="/exercises/ex4/images/CreatePolicy.png" width="70%">

6. Save the newly created policy

  <br><img src="/exercises/ex4/images/SavePolicyWithoutRestriction.png" width="70%">

7. Go to the **Assignments** tab of the policy, click the button with the 3 dots and choose **Add**

  <br><img src="/exercises/ex4/images/AssignPolicyToUser.png" width="70%">

8. Select your user and click the **Add** button.

  <br><img src="/exercises/ex4/images/AssignPolicyToSelectedUser.png" width="70%">

You have now created an authorization policy that gives READ access to user accounts, and assigned this policy to your administrator user.

## Exercise 4.4 Create another user account to be used for testing

1. Go to the User Management page

  <br><img src="/exercises/ex4/images/StartUserManagement.png" width="70%">

2. Click the **Add** button and enter the details for a new user. Then click the **Add** button on the popup dialog.

  <br><img src="/exercises/ex4/images/AddUser.png" width="70%">

3. Click on the new user account in the list and then click on the **Edit** button

  <br><img src="/exercises/ex4/images/EditUser.png" width="70%">

4. Scroll down to the **Company Information** section and enter the company name **Bestrun**. Then click the **Save** button. 

  <br><img src="/exercises/ex4/images/AddCompany.png" width="70%">

## Exercise 4.5 Remove classic authorization for reading users

5. Go to **Users & Authorizations** --> **Administrators**

  <br><img src="/exercises/ex4/images/AdministratorsConfigFromUsers.png" width="70%">

6. Select your administrator user and disable the authorizations **Manage Users** and **Read Users**. Then click the **Save** button.

  <br><img src="/exercises/ex4/images/RemoveReadManageUsersAuthZ.png" width="70%">

7. Go to the **Home** tab

  <br><img src="/exercises/ex4/images/Home.png" width="70%">

## Exercise 4.6 Validate that you can still see all user records

1. The **User Management** tile shows that there are 2 users that you can see. Click on the tile to see the list of users. 

  <br><img src="/exercises/ex4/images/UserManagementTile_Unrestricted.png" width="70%">

## Exercise 4.7 Restrict the authorization policy

1. Go to **Applications & Resources** --> **Applications**

  <br><img src="/exercises/ex4/images/ApplicationsFromUserManagement.png" width="70%">

2. Select the system application **Administration Console** , which represents the administration console of SAP Cloud Identity services.

  <br><img src="/exercises/ex4/images/Applications.png" width="70%">

3. Open the tab **Authorization Policies**
  
  <br><img src="/exercises/ex4/images/AdminConsoleApp.png" width="70%">

4. In the list of policies, click on the policy **READ_USERS_BESTRUN**

  <br><img src="/exercises/ex4/images/ChooseBestrunPolicy.png" width="70%">

5. Open the **Rules** tab for the policy and then click the **Edit** button

  <br><img src="/exercises/ex4/images/BestrunPolicyEdit.png" width="70%">
  
6. Click on the **+** icon to add a new restriction

  <br><img src="/exercises/ex4/images/AddNewRestriction.png" width="70%">

7. Click on the **+** icon and select **Value**

  <br><img src="/exercises/ex4/images/ConfigureNewRestriction.png" width="70%">

8. Enter the restriction attribute **user.organization**, the operator **=** and the value **Bestrun**. Then click on **Save**.

  <br><img src="/exercises/ex4/images/SetRestrictionValue.png" width="70%">

## Exercise 4.8 Validate that you can only see the allowed user accounts
