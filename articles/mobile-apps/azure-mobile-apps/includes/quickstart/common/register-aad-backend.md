---
ms.topic: include
ms.date: 06/11/2022
author: adrianhall
ms.author: adhal
ms.prod: azure-mobile-apps
---

## Add authentication to your backend service

Your backend service is a standard ASP.NET 6 service.  Any tutorial that shows you how to enable authentication for an ASP.NET 6 service will work with Azure Mobile Apps.

To enable Azure Active Directory authentication for your backend service, you need to:

* Register an application with Azure Active Directory.
* Add authentication checking to the ASP.NET 6 backend project.

### Register the application

First, register the web API in your Azure Active Directory tenant and add a scope by following these steps:

1. Sign in to the [Azure portal](https://portal.azure.com).
2. If you have access to multiple tenants, use the **Directories + subscriptions** filter in the top menu to switch to the tenant in which you want to register the application.
3. Search for and select **Azure Active Directory**.
4. Under **Manage**, select **App registrations** > **New registration**.

   * **Name**: enter a name for your application; for example, **TodoApp Quickstart**.  Users of your app will see this name.  You can change it later.
   * **Supported account types**: **Accounts in any organizational directory (Any Azure AD directory - Multitenant) and personal Microsoft accounts (e.g. Skype, Xbox)**

5. Select **Register**.
6. Under **Manage**, select **Expose an API** > **Add a scope**.
7. For **Application ID URI**, accept the default by selecting **Save and continue**.
8. Enter the following details:

   * **Scope name**: `access_as_user`
   * **Who can consent?**: **Admins and users**
   * **Admin consent display name**: `Access TodoApp`
   * **Admin consent description**: `Allows the app to access TodoApp as the signed-in user.`
   * **User consent display name**: `Access TodoApp`
   * **User consent description**: `Allow the app to access TodoApp on your behalf.`
   * **State**: **Enabled**

9. Select **Add scope** to complete the scope addition.
10. Note the value of the scope.  It will be `api://<client-id>/access_as_user`.  You'll need the scope when configuring the client.  This will be referred to as the _Web API Scope_.
11. Select **Overview**.
12. Note the **Application (client) ID** in the **Essentials** section as you'll need this value to configure the backend service later on.  This will be referred to as the _Web API Application ID_.
