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

6. 
