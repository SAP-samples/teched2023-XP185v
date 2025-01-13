# Exercise 4 - Managing administrative authorizations in SAP Cloud Identity Services (optional)

SAP Cloud Identity Services offer a wealth of functionality in the space of Identity and Access Management (IAM). Especially in larger organizations, it may not be possible for any individual to manage all IAM processes available in the cockpit or be responsible for the IAM-related configuration of all end users in the organization. A solution for this problem is to share the work among multiple persons. However, by default, everybody working as an administrator in the SAP Cloud Identity Services cockpit has very broad authorizations. It may be a security risk if individuals that are meant to perform limited administrative tasks have full administrative access way beyond their area of responsibility. 
In this exercise you will learn how to implement fine grained administrative authorizations that allow you to give limited access when delegating administrative tasks to others.  

## Exercise 4.1 Enable policy-based authorizations in SAP Cloud Identity Services

1. Open the administration console for SAP Cloud Identity Services from your bookmarks or like described in the first exercise.

  <br><img src="/exercises/ex0/images/SCI_Cockpit.png" width="70%">

2. Go to **Tenant Settings** in the **Applications & Resources** section.

  <br><img src="/exercises/ex4/images/TenantSettings.png" width="70%">

3. Open the tab **Policy-Based Authorizations**.

  <br><img src="/exercises/ex4/images/PolicyBasedAuthZMenu.png" width="70%">

4. Enable policy-based authorizations.

  <br><img src="/exercises/ex4/images/EnablePolicyBasedAuthZ.png" width="70%">

  SAP Cloud Identity Services now evaluate policy-based authorizations in addition to the role-based authorizations that are used by default.

## Exercise 4.2 Create an authorization policy for reading users

1. Open the **Applications & Resources** menu and go to the **Applications** user interface.

  <br><img src="/exercises/ex4/images/ApplicationsMenu.png" width="70%">

2. Select the system application **Administration Console**, which represents the administration console of SAP Cloud Identity Services.

  <br><img src="/exercises/ex4/images/Applications.png" width="70%">

3. Open the tab **Authorization Policies**.
  
  <br><img src="/exercises/ex4/images/AdminConsoleApp.png" width="70%">

4. A list of authorization policies is displayed, which can be used to manage access to the administration console. Click on the **Create** dropdown menu and select the menu item **Create Restriction**

  <br><img src="/exercises/ex4/images/AdminConsoleAppPolicies.png" width="70%">
  
5. In the popup dialog, enter the policy name **READ_USERS_BESTRUN** and choose the base policy **users.READ_USERS**. Then click on **Create**.

  <br><img src="/exercises/ex4/images/CreatePolicy.png" width="70%">

6. Save the newly created policy.

  <br><img src="/exercises/ex4/images/SavePolicyWithoutRestriction.png" width="70%">

7. Go to the **Assignments** tab of the policy, click the button with the 3 dots and choose **Add**.

  <br><img src="/exercises/ex4/images/AssignPolicyToUser.png" width="70%">

8. Select your user and click the **Add** button.

  <br><img src="/exercises/ex4/images/AssignPolicyToSelectedUser.png" width="70%">

You have now created an authorization policy that gives READ access to user accounts and assigned this policy to your administrator user.

## Exercise 4.3 Create another user account to be used for testing

1. Go to the User Management page.

  <br><img src="/exercises/ex4/images/StartUserManagement.png" width="70%">

2. Note: If you already created a test user in the previous exercise then you can continue with step 3 and edit the existing user account. If you did not create a test user, click the **Add** button and enter the details for a new user. Then click the **Add** button on the popup dialog.

  <br><img src="/exercises/ex4/images/AddUser.png" width="70%">

3. Click on the new user account in the list and then click on the **Edit** button.

  <br><img src="/exercises/ex4/images/EditUser.png" width="70%">

4. Scroll down to the **Company Information** section and enter the company name **Bestrun**. Then click the **Save** button. 

  <br><img src="/exercises/ex4/images/AddCompany.png" width="70%">

## Exercise 4.4 Remove classic authorization for reading users

5. Go to **Users & Authorizations** --> **Administrators**.

  <br><img src="/exercises/ex4/images/AdministratorsConfigFromUsers.png" width="70%">

6. Select your administrator user and disable the authorizations **Manage Users** and **Read Users**. Then click the **Save** button.

  <br><img src="/exercises/ex4/images/RemoveReadManageUsersAuthZ.png" width="70%">

7. Go to the **Home** tab.

  <br><img src="/exercises/ex4/images/Home2.png" width="70%">

## Exercise 4.5 Validate that you can still see all user records

1. The **User Management** tile shows that there are 2 users that you have access to. Click on the tile to display the list of users. 

  <br><img src="/exercises/ex4/images/UserManagementTile_Unrestricted.png" width="70%">

  As the **READ_USERS_BESTRUN** policy does not have any restrictions, you still have access to all user records.


## Exercise 4.6 Restrict the authorization policy

1. Go to **Applications & Resources** --> **Applications**.

  <br><img src="/exercises/ex4/images/ApplicationsFromUserManagement.png" width="70%">

2. Select the system application **Administration Console**, which represents the administration console of SAP Cloud Identity Services.

  <br><img src="/exercises/ex4/images/Applications.png" width="70%">

3. Open the tab **Authorization Policies**.
  
  <br><img src="/exercises/ex4/images/AdminConsoleApp.png" width="70%">

4. In the list of policies, click on the policy **READ_USERS_BESTRUN**.

  <br><img src="/exercises/ex4/images/ChooseBestrunPolicy.png" width="70%">

5. Open the **Rules** tab for the policy and then click the **Edit** button.

  <br><img src="/exercises/ex4/images/BestrunPolicyEdit.png" width="70%">
  
6. Click on the **+** icon to add a new restriction.

  <br><img src="/exercises/ex4/images/AddNewRestriction.png" width="70%">

7. Click on the **+** icon next to the label **RESTRICT** and select **Value**.

  <br><img src="/exercises/ex4/images/ConfigureNewRestriction.png" width="70%">

8. Enter the restriction attribute **user.organization**, the operator **=** and the value **Bestrun**. Then click on **Save**.

  <br><img src="/exercises/ex4/images/SetRestrictionValue.png" width="70%">

9. Go to the **Home** tab.

  <br><img src="/exercises/ex4/images/HomeFromPolicy.png" width="70%">

## Exercise 4.7 Validate that you can only see the allowed user accounts

1. The tile **User Management** shows the value 1. So out of the 2 users that are stored in the user management, you only have access to 1. Click on the tile.

 <br><img src="/exercises/ex4/images/UserManagementTile_Restricted.png" width="70%">

2. You can only see the user account with the company name **Bestrun**, due to the restriction that you applied to the access policy. 

<br><img src="/exercises/ex4/images/RestrictedListOfUsers.png" width="70%">

## Summary

In this exercise you learned how to switch from classic, role-based authorizations in SAP Cloud Identity Services to the new policy-based authorizations. You defined a new access policy and applied restrictions to it. When assigning this policy to the administrator user, you saw how the access of the administrator is reduced based on the restrictions in the policy definition. 
