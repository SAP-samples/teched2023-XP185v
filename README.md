[![REUSE status](https://api.reuse.software/badge/github.com/SAP-samples/teched2023-XP264)](https://api.reuse.software/info/github.com/SAP-samples/teched2023-XP264)

# Get Hands-On Security Recommendations for Your SAP BTP Environment

## Description

This repository contains the material for the **Get Hands-On Security Recommendations for Your SAP BTP Environment** session.  

## Overview

In this session attendees will learn about the security recommendations for BTP services and how to implement them. The [SAP BTP Security Recommendations](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations) are available in the SAP Help Portal in the sections for the SAP Business Technology Platform. These recommendations for the configuration of SAP BTP services help customers meet their compliance goals and secure their business.

## Requirements

The requirements to follow the exercises in this repository are active trial accounts for SAP BTP and for the SAP Cloud Identity Services. 

**First you have to get your SAP BTP trial account. Follow these instructions:** 
[Get a Free Account on SAP BTP Trial](https://developers.sap.com/tutorials/hcp-create-trial-account.html)

**Then activate your SAP Cloud Identity Services trial. Follow the instructions in this blog:** 
[SAP Cloud Identity Services offered as Trial Version](https://blogs.sap.com/2023/04/13/sap-cloud-identity-services-offered-as-trial-version/)

💡You should have access to your mailbox, which you used while registering for your BTP trial account in order to activate your SAP Cloud Identity Services trial account.

**Finally, install a Time-based One-Time-Password (TOTP) authentication application (such as Google Authenticator or Microsoft Authenticator) on your mobile device and familiarize yourself with the process to create accounts in the app.**

Now you are ready to start the exercises.

## Exercises

- [Getting Started](exercises/ex0/)
- [Exercise 1 - Enable Multi-Factor Authentication for applications](exercises/ex1/)
    - [Exercise 1.1 - Setup SAP Build Apps and enter the application with your trial identity provider user](exercises/ex1#exercise-11---Setup-SAP-Build-Apps-and-enter-the-application-with-your-trial-identity-provider-user)
    - [Exercise 1.2 - Configure Multi-Factor Authentication to access SAP Build Apps](exercises/ex1#exercise-12---Configure-Multi-Factor-Authentication-to-access-SAP-Build-Apps)
    - [Exercise 1.3 - Enable MFA for your User](exercises/ex1#exercise-13---Enable-MFA-for-your-User)
    
- [Exercise 2 - Security Recommendations regarding user access and authentication](exercises/ex2/)
    - [Exercise 2.1 - Manage obsolete administrators](exercises/ex2#exercise-21-identify-obsolete-users)
    - [Exercise 2.2 - Defining a custom password policy](exercises/ex2#exercise-22-defining-a-custom-password-policy)
    - [Exercise 2.3 - Keep public access to applications by self-registration disabled](exercises/ex2#exercise-23-keep-public-access-to-applications-by-self-registration-disabled)
    - [Exercise 2.4 - Keep Social Sign-On disabled](exercises/ex2#exercise-24-keep-social-sign-on-disabled)
- [Exercise 3 - Security Recommendations regarding the Audit Log](exercises/ex3/)
    - [Exercise 3.1 - Subscribe to the SAP Audit Log Viewer service](exercises/ex3#exercise-31-subscribe-to-the-sap-audit-log-viewer-service)
    - [Exercise 3.2 - Configure the SAP Audit Log Viewer service](exercises/ex3#exercise-32-configure-the-sap-audit-log-viewer-service)
    - [Exercise 3.3 - Check the audit logs and download audit log entries via the SAP Audit Log Viewer service](exercises/ex3#exercise-33-check-the-audit-logs-and-download-audit-log-entries-via-the-sap-audit-log-viewer-service)
- [Exercise 4 - Managing administrative authorizations in SAP Cloud Identity Services (optional)](exercises/ex4/)
    - [Exercise 4.1 - Enable policy-based authorizations in SAP Cloud Identity Services](exercises/ex4/README.md#exercise-41-enable-policy-based-authorizations-in-sap-cloud-identity-services)
    - [Exercise 4.2 - Create an authorization policy for reading users](exercises/ex4/README.md#exercise-42-create-an-authorization-policy-for-reading-users)
    - [Exercise 4.3 - Create another user account to be used for testing](exercises/ex4/README.md#exercise-43-create-another-user-account-to-be-used-for-testing)
    - [Exercise 4.4 - Remove classic authorization for reading users](exercises/ex4/README.md#exercise-44-remove-classic-authorization-for-reading-users)
    - [Exercise 4.5 - Validate that you can still see all user records](exercises/ex4/README.md#exercise-45-validate-that-you-can-still-see-all-user-records)
    - [Exercise 4.6 - Restrict the authorization policy](exercises/ex4/README.md#exercise-46-restrict-the-authorization-policy)
    - [Exercise 4.7 - Validate that you can only see the allowed user accounts](exercises/ex4/README.md#exercise-47-validate-that-you-can-only-see-the-allowed-user-accounts)


**IMPORTANT**

Your repo must contain the .reuse and LICENSES folder and the License section below. DO NOT REMOVE the section or folders/files. Also, remove all unused template assets (images, folders, etc) from the exercises folder. 

## Contributing
Please read the [CONTRIBUTING.md](./CONTRIBUTING.md) to understand the contribution guidelines.

## Code of Conduct
Please read the [SAP Open-Source Code of Conduct](https://github.com/SAP-samples/.github/blob/main/CODE_OF_CONDUCT.md).

## How to obtain support

Support for the content in this repository is available during the actual time of the online session for which this content has been designed. Otherwise, you may request support via the [Issues](../../issues) tab.

## License
Copyright (c) 2025 SAP SE or an SAP affiliate company. All rights reserved. This project is licensed under the Apache Software License, version 2.0 except as noted otherwise in the [LICENSE](LICENSES/Apache-2.0.txt) file.
