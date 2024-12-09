# Exercise 4 - Managing administrative authorizations in SAP Cloud Identity

SAP Cloud Identity offers a wealth of functionality in the space of Identity and Access Management (IAM). Especially in larger organizations, it may not be possible for any individual to manage all IAM processes available in the cockpit, or be responsible for the IAM-related configuration of all end users in the organization. A solution for this problem is to share the work among multiple persons. However, by default, everybody working as an administrator in the SAP Cloud Identity cockpit has very broad authorizations. It may be a security risk if individuals that are meant to perform limited administrative tasks have full administrative access way beyond their area of responsibility. 
In this execise you will learn how to implement fine grained administrative authorizations that allow you to give limited access when delgating administrative tasks to others.  

## Exercise 4.1 Enable policy-based authorizations in SAP Cloud Identity

1. Open the **SAP BTP Cockpit**.

  <br><img src="/exercises/ex3/IMAGES/audit0.png" width="70%">

2. Navigate to your **trial subaccount** by clicking on the tile. Go to **Tenant Settings** in the **Applications & Resources** section.

  <br><img src="/exercises/ex4/images/TenantSettings.png" width="70%">

3. 
