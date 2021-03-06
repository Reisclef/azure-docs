---
title: 'Tutorial: Configure ThousandEyes for automatic user provisioning with Azure Active Directory | Microsoft Docs'
description: Learn how to configure Azure Active Directory to automatically provision and de-provision user accounts to ThousandEyes.
services: active-directory
documentationcenter: ''
author: asmalser-msft
writer: asmalser-msft
manager: daveba

ms.assetid: d4ca2365-6729-48f7-bb7f-c0f5ffe740a3
ms.service: active-directory
ms.subservice: saas-app-tutorial
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 01/26/2018
ms.author: asmalser-msft

ms.collection: M365-identity-device-management
---

# Tutorial: Configure ThousandEyes for automatic user provisioning


The objective of this tutorial is to show you the steps you need to perform in ThousandEyes and Azure AD to automatically provision and de-provision user accounts from Azure AD to ThousandEyes. 

## Prerequisites

The scenario outlined in this tutorial assumes that you already have the following items:

*   An Azure Active directory tenant
*   An active [ThousandEyes account](https://www.thousandeyes.com/pricing)
*   A ThousandEyes user account that has been assigned a Role which includes the following 3 permissions:
    * view all users
    * edit user
    * API access permissions

> [!NOTE]
> The Azure AD provisioning integration relies on the [ThousandEyes SCIM API](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnWrCAK_ThousandEyes-support-for-SCIM). 

## Assigning users to ThousandEyes

Azure Active Directory uses a concept called "assignments" to determine which users should receive access to selected apps. In the context of automatic user account provisioning, only the users and groups that have been "assigned" to an application in Azure AD is synchronized. 

Before configuring and enabling the provisioning service, you need to decide what users and/or groups in Azure AD represent the users who need access to your ThousandEyes app. Once decided, you can assign these users to your ThousandEyes app by following the instructions here:

[Assign a user or group to an enterprise app](../manage-apps/assign-user-or-group-access-portal.md)

### Important tips for assigning users to ThousandEyes

*	It is recommended that a single Azure AD user is assigned to ThousandEyes to test the provisioning configuration. Additional users and/or groups may be assigned later.

*	When assigning a user to ThousandEyes, you must select either the **User** role or another valid application-specific role (if available) in the assignment dialogue. The **Default Access** role does not work for provisioning, and these users are skipped.

## Configure auto-provisioned user roles in ThousandEyes

For each account group, you are auto-provisioning users into you can configure a set of roles to be applied when the new user account is created. By default, auto-provisioning users are assigned the _Regular User_ role for all account groups unless configured otherwise.

1. To specify a new set of roles for auto-provisioned users log-into ThousandEyes and navigate to the SCIM Settings section **> your user icon in the top right corner > Account Settings > Organization > Security & Authentication.** 

   ![Navigate to SCIM API Settings](https://monosnap.com/file/kqY8Il7eysGFAiCLCQWFizzM27PiBG)

2. Add an entry for each account group, assign a set of roles then *save* your changes.

   ![Set default roles and account groups for users created via SCIM API](https://monosnap.com/file/16siam6U8xDQH1RTnaxnmIxvsZuNZG)


## Configuring user provisioning to ThousandEyes 

This section guides you through connecting your Azure AD to ThousandEyes's user account provisioning API, and configuring the provisioning service to create, update, and disable assigned user accounts in ThousandEyes based on user and group assignment in Azure AD.

> [!TIP]
> You may also choose to enabled SAML-based Single Sign-On (SSO) for ThousandEyes, following the [instructions provided in Azure knowledge base](https://docs.microsoft.com/azure/active-directory/saas-apps/thousandeyes-tutorial) to complete SSO. SSO can be configured independently of automatic provisioning, though these two features complement each other.


### Configure automatic user account provisioning to ThousandEyes in Azure AD


1. In the [Azure portal](https://portal.azure.com), browse to the **Azure Active Directory > Enterprise Apps > All applications**  section.

2. If you have already configured ThousandEyes for single sign-on, search for your instance of ThousandEyes using the search field. Otherwise, select **Add** and search for **ThousandEyes** in the application gallery. Select ThousandEyes from the search results, and add it to your list of applications.

3. Select your instance of ThousandEyes, then select the **Provisioning** tab.

4. Set the **Provisioning Mode** to **Automatic**.

	![ThousandEyes Provisioning](./media/thousandeyes-provisioning-tutorial/ThousandEyes1.png)

5. Under the **Admin Credentials**  section, input the **OAuth Bearer Token**
generated by your ThousandEyes' account (you can find and or generate a token under your ThousandEyes account **Profile** section).

	![ThousandEyes Provisioning](./media/thousandeyes-provisioning-tutorial/ThousandEyes2.png)

6. In the Azure portal, click **Test Connection** to ensure Azure AD can connect to your ThousandEyes app. If the connection fails, ensure your ThousandEyes account has Admin permissions and try step 5 again.

7. Enter the email address of a person or group who should receive provisioning error notifications in the **Notification Email** field, and check the checkbox "Send an email notification when a failure occurs."

8. Click **Save**. 

9. Under the Mappings section, select **Synchronize Azure Active Directory Users to ThousandEyes**.

10. In the **Attribute Mappings** section, review the user attributes that are synchronized from Azure AD to ThousandEyes. The attributes selected as **Matching** properties are used to match the user accounts in ThousandEyes for update operations. Select the Save button to commit any changes.

11. To enable the Azure AD provisioning service for ThousandEyes, change the **Provisioning Status** to **On** in the **Settings** section

12. Click **Save**. 

This operation starts the initial synchronization of any users and/or groups assigned to ThousandEyes in the Users and Groups section. The initial sync takes longer to perform than subsequent syncs, which occur approximately every 40 minutes as long as the service is running. You can use the **Synchronization Details** section to monitor progress and follow links to provisioning activity logs, which describe all actions performed by the provisioning service.

For more information on how to read the Azure AD provisioning logs, see [Reporting on automatic user account provisioning](../manage-apps/check-status-user-account-provisioning.md).


## Additional resources

* [Managing user account provisioning for Enterprise Apps](../manage-apps/configure-automatic-user-provisioning-portal.md)
* [What is application access and single sign-on with Azure Active Directory?](../manage-apps/what-is-single-sign-on.md)

## Next steps

* [Learn how to review logs and get reports on provisioning activity](../manage-apps/check-status-user-account-provisioning.md)
