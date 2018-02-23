---
title: "Creación de una entidad de servicio de Azure con Azure PowerShell"
description: "Aprenda a crear una entidad de servicio para cualquier aplicación o servicio con Azure PowerShell."
keywords: Azure PowerShell, Azure Active Directory, Azure Active directory, AD, RBAC
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 05/15/2017
ms.openlocfilehash: 6eda2d2a729331b212938aa2681d0188a25b734a
ms.sourcegitcommit: 7e77fe7ecd2112d6b4515517509c5c723e750e27
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2018
---
# <a name="create-an-azure-service-principal-with-azure-powershell"></a><span data-ttu-id="19196-104">Creación de una entidad de servicio de Azure con Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="19196-104">Create an Azure service principal with Azure PowerShell</span></span>

<span data-ttu-id="19196-105">Si planea administrar una aplicación o servicio con Azure PowerShell, debe ejecutarla en una entidad de servicio de Azure Active Directory (AAD), en lugar de con sus propias credenciales.</span><span class="sxs-lookup"><span data-stu-id="19196-105">If you plan to manage your app or service with Azure PowerShell, you should run it under an Azure Active Directory (AAD) service principal, rather than your own credentials.</span></span> <span data-ttu-id="19196-106">En este tema le ayudará a crear a una entidad de seguridad con Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="19196-106">This topic steps you through creating a security principal with Azure PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="19196-107">Las entidades de servicio también se pueden crear desde Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="19196-107">You can also create a service principal through the Azure portal.</span></span> <span data-ttu-id="19196-108">Para más información, lea [Uso del portal para crear una aplicación de Azure Active Directory y una entidad de servicio con acceso a los recursos](/azure/azure-resource-manager/resource-group-create-service-principal-portal).</span><span class="sxs-lookup"><span data-stu-id="19196-108">Read [Use portal to create Active Directory application and service principal that can access resources](/azure/azure-resource-manager/resource-group-create-service-principal-portal) for more details.</span></span>

## <a name="what-is-a-service-principal"></a><span data-ttu-id="19196-109">¿Qué es una "entidad de servicio"?</span><span class="sxs-lookup"><span data-stu-id="19196-109">What is a 'service principal'?</span></span>

<span data-ttu-id="19196-110">Una entidad de servicio de Azure es una identidad de seguridad que usan las aplicaciones, los servicios y las herramientas de automatización creadas por el usuario para acceder a recursos específicos de Azure.</span><span class="sxs-lookup"><span data-stu-id="19196-110">An Azure service principal is a security identity used by user-created apps, services, and automation tools to access specific Azure resources.</span></span> <span data-ttu-id="19196-111">Se puede considerar una "identidad de usuario" (nombre de usuario y una contraseña o certificado) con un rol específico y permisos estrechamente controlados.</span><span class="sxs-lookup"><span data-stu-id="19196-111">Think of it as a 'user identity' (username and password or certificate) with a specific role, and tightly controlled permissions.</span></span> <span data-ttu-id="19196-112">A diferencia de una identidad de usuario general, solo necesita poder realizar acciones específicas.</span><span class="sxs-lookup"><span data-stu-id="19196-112">It only needs to be able to do specific things, unlike a general user identity.</span></span> <span data-ttu-id="19196-113">Mejora la seguridad si solo se le concede el nivel de permiso mínimo necesario para realizar sus tareas de administración.</span><span class="sxs-lookup"><span data-stu-id="19196-113">It improves security if you only grant it the minimum permissions level needed to perform its management tasks.</span></span>

## <a name="verify-your-own-permission-level"></a><span data-ttu-id="19196-114">Comprobación del nivel de permiso</span><span class="sxs-lookup"><span data-stu-id="19196-114">Verify your own permission level</span></span>

<span data-ttu-id="19196-115">En primer lugar, debe tener permisos suficientes tanto en su suscripción de Azure como en Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="19196-115">First, you must have sufficient permissions in both your Azure Active Directory and your Azure subscription.</span></span> <span data-ttu-id="19196-116">En concreto, debe poder crear una aplicación en Active Directory y asignar un rol a la entidad de servicio.</span><span class="sxs-lookup"><span data-stu-id="19196-116">Specifically, you must be able to create an app in the Active Directory, and assign a role to the service principal.</span></span>

<span data-ttu-id="19196-117">El portal representa la forma más sencilla de comprobar si su cuenta tiene los permisos adecuados.</span><span class="sxs-lookup"><span data-stu-id="19196-117">The easiest way to check whether your account has adequate permissions is through the portal.</span></span> <span data-ttu-id="19196-118">Consulte [Comprobación de los permisos necesarios en el portal](/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions).</span><span class="sxs-lookup"><span data-stu-id="19196-118">See [Check required permission in portal](/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions).</span></span>

## <a name="create-a-service-principal-for-your-app"></a><span data-ttu-id="19196-119">Creación de una entidad de servicio para la aplicación</span><span class="sxs-lookup"><span data-stu-id="19196-119">Create a service principal for your app</span></span>

<span data-ttu-id="19196-120">Una vez que haya iniciado sesión en su cuenta de Azure puede crear la entidad de servicio.</span><span class="sxs-lookup"><span data-stu-id="19196-120">Once you are signed into your Azure account, you can create the service principal.</span></span> <span data-ttu-id="19196-121">Debe realizar alguno de los siguientes métodos para identificar la aplicación implementada:</span><span class="sxs-lookup"><span data-stu-id="19196-121">You must have one of the following ways to identify your deployed app:</span></span>

* <span data-ttu-id="19196-122">El nombre único de la aplicación implementada (como "MyDemoWebApp" en los ejemplos siguientes), o bien</span><span class="sxs-lookup"><span data-stu-id="19196-122">The unique name of your deployed app, such as "MyDemoWebApp" in the following examples, or</span></span>
* <span data-ttu-id="19196-123">el identificador de la aplicación, el GUID único asociado a la aplicación, el servicio o el objeto implementados</span><span class="sxs-lookup"><span data-stu-id="19196-123">the Application ID, the unique GUID associated with your deployed app, service, or object</span></span>

### <a name="get-information-about-your-application"></a><span data-ttu-id="19196-124">Obtención de información acerca de una aplicación</span><span class="sxs-lookup"><span data-stu-id="19196-124">Get information about your application</span></span>

<span data-ttu-id="19196-125">El cmdlet `Get-AzureRmADApplication` puede usarse para detectar información acerca de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="19196-125">The `Get-AzureRmADApplication` cmdlet can be used to discover information about your application.</span></span>

```powershell
Get-AzureRmADApplication -DisplayNameStartWith MyDemoWebApp
```

```
DisplayName             : MyDemoWebApp
ObjectId                : 775f64cd-0ec8-4b9b-b69a-8b8946022d9f
IdentifierUris          : {http://MyDemoWebApp}
HomePage                : http://www.contoso.com
Type                    : Application
ApplicationId           : 00c01aaa-1603-49fc-b6df-b78c4e5138b4
AvailableToOtherTenants : False
AppPermissions          :
ReplyUrls               : {}
```

### <a name="create-a-service-principal-for-your-application"></a><span data-ttu-id="19196-126">Creación de una entidad de servicio para la aplicación</span><span class="sxs-lookup"><span data-stu-id="19196-126">Create a service principal for your application</span></span>

<span data-ttu-id="19196-127">El cmdlet `New-AzureRmADServicePrincipal` se usa para crear la entidad de servicio.</span><span class="sxs-lookup"><span data-stu-id="19196-127">The `New-AzureRmADServicePrincipal` cmdlet is used to create the service principal.</span></span>

```powershell
Add-Type -Assembly System.Web
$password = [System.Web.Security.Membership]::GeneratePassword(16,3)
New-AzureRmADServicePrincipal -ApplicationId 00c01aaa-1603-49fc-b6df-b78c4e5138b4 -Password $password
```

```
DisplayName                    Type                           ObjectId
-----------                    ----                           --------
MyDemoWebApp                   ServicePrincipal               698138e7-d7b6-4738-a866-b4e3081a69e4
```

### <a name="get-information-about-the-service-principal"></a><span data-ttu-id="19196-128">Obtención de información acerca de la entidad de servicio</span><span class="sxs-lookup"><span data-stu-id="19196-128">Get information about the service principal</span></span>

```powershell
$svcprincipal = Get-AzureRmADServicePrincipal -ObjectId 698138e7-d7b6-4738-a866-b4e3081a69e4
$svcprincipal | Select-Object *
```

```
ServicePrincipalNames : {http://MyDemoWebApp, 00c01aaa-1603-49fc-b6df-b78c4e5138b4}
ApplicationId         : 00c01aaa-1603-49fc-b6df-b78c4e5138b4
DisplayName           : MyDemoWebApp
Id                    : 698138e7-d7b6-4738-a866-b4e3081a69e4
Type                  : ServicePrincipal
```

### <a name="sign-in-using-the-service-principal"></a><span data-ttu-id="19196-129">Inicio de sesión mediante la entidad de servicio</span><span class="sxs-lookup"><span data-stu-id="19196-129">Sign in using the service principal</span></span>

<span data-ttu-id="19196-130">Ya puede iniciar sesión como la nueva entidad de servicio en la aplicación mediante los valores de *appId* y *password* que proporcionó.</span><span class="sxs-lookup"><span data-stu-id="19196-130">You can now sign in as the new service principal for your app using the *appId* and *password* you provided.</span></span> <span data-ttu-id="19196-131">Debe proporcionar el identificador del inquilino de su cuenta.</span><span class="sxs-lookup"><span data-stu-id="19196-131">You need to supply the Tenant Id for your account.</span></span> <span data-ttu-id="19196-132">El identificador de inquilino aparece al iniciar sesión en Azure con sus credenciales personales.</span><span class="sxs-lookup"><span data-stu-id="19196-132">Your Tenant Id is displayed when you sign into Azure with your personal credentials.</span></span>

```powershell
$cred = Get-Credential -UserName $svcprincipal.ApplicationId -Message "Enter Password"
Login-AzureRmAccount -Credential $cred -ServicePrincipal -TenantId XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
```

<span data-ttu-id="19196-133">Ejecute este comando desde una nueva sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="19196-133">Run this command from a new PowerShell session.</span></span> <span data-ttu-id="19196-134">Después de un inicio de sesión correcto, obtendrá un resultado parecido al siguiente:</span><span class="sxs-lookup"><span data-stu-id="19196-134">After a successfully signing on you see output something like this:</span></span>

```
Environment           : AzureCloud
Account               : 00c01aaa-1603-49fc-b6df-b78c4e5138b4
TenantId              : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
SubscriptionId        :
SubscriptionName      :
CurrentStorageAccount :
```

<span data-ttu-id="19196-135">Felicidades.</span><span class="sxs-lookup"><span data-stu-id="19196-135">Congratulations!</span></span> <span data-ttu-id="19196-136">Puede usar estas credenciales para ejecutar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="19196-136">You can use these credentials to run your app.</span></span> <span data-ttu-id="19196-137">A continuación, debe ajustar los permisos de la entidad de servicio.</span><span class="sxs-lookup"><span data-stu-id="19196-137">Next, you need to adjust the permissions of the service principal.</span></span>

## <a name="managing-roles"></a><span data-ttu-id="19196-138">Administración de roles</span><span class="sxs-lookup"><span data-stu-id="19196-138">Managing roles</span></span>

> [!NOTE]
> <span data-ttu-id="19196-139">El control de acceso basado en roles (RBAC) de Azure es un modelo para definir y administrar roles tanto para usuario como para las entidades de servicio.</span><span class="sxs-lookup"><span data-stu-id="19196-139">Azure Role-Based Access Control (RBAC) is a model for defining and managing roles for user and service principals.</span></span> <span data-ttu-id="19196-140">Los roles conjuntos de permisos asociados a ellos, que son los que determinan los recursos que una entidad puede administrar o leer, a los que puede acceder o en los que puede escribir.</span><span class="sxs-lookup"><span data-stu-id="19196-140">Roles have sets of permissions associated with them, which determine the resources a principal can read, access, write, or manage.</span></span> <span data-ttu-id="19196-141">Para más información acerca de RBAC y roles, consulte [Roles integrados para el control de acceso basado en roles de Azure](/azure/active-directory/role-based-access-built-in-roles).</span><span class="sxs-lookup"><span data-stu-id="19196-141">For more information on RBAC and roles, see [RBAC: Built-in roles](/azure/active-directory/role-based-access-built-in-roles).</span></span>

<span data-ttu-id="19196-142">Azure PowerShell proporciona los siguientes cmdlets para administrar las asignaciones de roles:</span><span class="sxs-lookup"><span data-stu-id="19196-142">Azure PowerShell provides the following cmdlets to manage role assignments:</span></span>

* [<span data-ttu-id="19196-143">Get-AzureRmRoleAssignment</span><span class="sxs-lookup"><span data-stu-id="19196-143">Get-AzureRmRoleAssignment</span></span>](/powershell/module/azurerm.resources/get-azurermroleassignment)
* [<span data-ttu-id="19196-144">New-AzureRmRoleAssignment</span><span class="sxs-lookup"><span data-stu-id="19196-144">New-AzureRmRoleAssignment</span></span>](/powershell/module/azurerm.resources/new-azurermroleassignment)
* [<span data-ttu-id="19196-145">Remove-AzureRmRoleAssignment</span><span class="sxs-lookup"><span data-stu-id="19196-145">Remove-AzureRmRoleAssignment</span></span>](/powershell/module/azurerm.resources/remove-azurermroleassignment)

<span data-ttu-id="19196-146">El rol predeterminado de una entidad de servicio es **colaborador**.</span><span class="sxs-lookup"><span data-stu-id="19196-146">The default role for a service principal is **Contributor**.</span></span> <span data-ttu-id="19196-147">Dado su gran cantidad de permisos, es posible que no sea la mejor opción para las interacciones de una aplicación con los servicios de Azure.</span><span class="sxs-lookup"><span data-stu-id="19196-147">It may not be the best choice depending on the scope of your app's interactions with Azure services, given its broad permissions.</span></span>
<span data-ttu-id="19196-148">El rol de **lector** es más restrictivo y es una buena elección para el acceso de solo lectura.</span><span class="sxs-lookup"><span data-stu-id="19196-148">The **Reader** role is more restrictive and can be a good choice for read-only apps.</span></span> <span data-ttu-id="19196-149">En Azure Portal encontrará más información acerca de los permisos específicos de los roles o podrá crear permisos personalizados.</span><span class="sxs-lookup"><span data-stu-id="19196-149">You can view details on role-specific permissions or create custom ones through the Azure portal.</span></span>

<span data-ttu-id="19196-150">En este ejemplo, agregue el rol de **lector** al ejemplo anterior y elimine el de **colaborador**:</span><span class="sxs-lookup"><span data-stu-id="19196-150">In this example, we add the **Reader** role to our prior example, and delete the **Contributor** one:</span></span>

```powershell
New-AzureRmRoleAssignment -ResourceGroupName myRG -ObjectId 698138e7-d7b6-4738-a866-b4e3081a69e4 -RoleDefinitionName Reader
```

```
RoleAssignmentId   : /subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/myRG/providers/Microsoft.Authorization/roleAssignments/818892f2-d075-46a1-a3a2-3a4e1a12fcd5
Scope              : /subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/myRG
DisplayName        : MyDemoWebApp
SignInName         :
RoleDefinitionName : Reader
RoleDefinitionId   : b24988ac-6180-42a0-ab88-20f7382dd24c
ObjectId           : 698138e7-d7b6-4738-a866-b4e3081a69e4
ObjectType         : ServicePrincipal
```

```powershell
Remove-AzureRmRoleAssignment -ResourceGroupName myRG -ObjectId 698138e7-d7b6-4738-a866-b4e3081a69e4 -RoleDefinitionName Contributor
```

<span data-ttu-id="19196-151">Para ver los roles actuales asignados:</span><span class="sxs-lookup"><span data-stu-id="19196-151">To view the current roles assigned:</span></span>

```powershell
Get-AzureRmRoleAssignment -ResourceGroupName myRG -ObjectId 698138e7-d7b6-4738-a866-b4e3081a69e4
```

```
RoleAssignmentId   : /subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/myRG/providers/Microsoft.Authorization/roleAssignments/0906bbd8-9982-4c03-8dae-aeaae8b13f9e
Scope              : /subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/myRG
DisplayName        : MyDemoWebApp
SignInName         :
RoleDefinitionName : Reader
RoleDefinitionId   : acdd72a7-3385-48ef-bd42-f606fba81ae7
ObjectId           : 698138e7-d7b6-4738-a866-b4e3081a69e4
ObjectType         : ServicePrincipal
```

<span data-ttu-id="19196-152">Otros cmdlets de Azure PowerShell para administración de roles:</span><span class="sxs-lookup"><span data-stu-id="19196-152">Other Azure PowerShell cmdlets for role management:</span></span>

* [<span data-ttu-id="19196-153">Get-AzureRmRoleDefinition</span><span class="sxs-lookup"><span data-stu-id="19196-153">Get-AzureRmRoleDefinition</span></span>](/powershell/module/azurerm.resources/Get-AzureRmRoleDefinition)
* [<span data-ttu-id="19196-154">New-AzureRmRoleDefinition</span><span class="sxs-lookup"><span data-stu-id="19196-154">New-AzureRmRoleDefinition</span></span>](/powershell/module/azurerm.resources/New-AzureRmRoleDefinition)
* [<span data-ttu-id="19196-155">Remove-AzureRmRoleDefinition</span><span class="sxs-lookup"><span data-stu-id="19196-155">Remove-AzureRmRoleDefinition</span></span>](/powershell/module/azurerm.resources/Remove-AzureRmRoleDefinition)
* [<span data-ttu-id="19196-156">Set-AzureRmRoleDefinition</span><span class="sxs-lookup"><span data-stu-id="19196-156">Set-AzureRmRoleDefinition</span></span>](/powershell/module/azurerm.resources/Set-AzureRmRoleDefinition)

## <a name="change-the-credentials-of-the-security-principal"></a><span data-ttu-id="19196-157">Cambio de las credenciales de la entidad de seguridad</span><span class="sxs-lookup"><span data-stu-id="19196-157">Change the credentials of the security principal</span></span>

<span data-ttu-id="19196-158">A nivel de seguridad se recomienda revisar los permisos y actualizar las contraseñas periódicamente.</span><span class="sxs-lookup"><span data-stu-id="19196-158">It's a good security practice to review the permissions and update the password regularly.</span></span> <span data-ttu-id="19196-159">Si lo desea, también puede administrar y modificar las credenciales de seguridad cuando la aplicación cambie.</span><span class="sxs-lookup"><span data-stu-id="19196-159">You may also want to manage and modify the security credentials as your app changes.</span></span> <span data-ttu-id="19196-160">Por ejemplo, podemos cambiar la contraseña de la entidad de servicio mediante la creación de una contraseña nueva y la eliminación de la antigua.</span><span class="sxs-lookup"><span data-stu-id="19196-160">For example, we can change the password of the service principal by creating a new password and removing the old one.</span></span>

### <a name="add-a-new-password-for-the-service-principal"></a><span data-ttu-id="19196-161">Adición de una nueva contraseña para la entidad de servicio</span><span class="sxs-lookup"><span data-stu-id="19196-161">Add a new password for the service principal</span></span>

```powershell
$password = [System.Web.Security.Membership]::GeneratePassword(16,3)
New-AzureRmADSpCredential -ServicePrincipalName http://MyDemoWebApp -Password $password
```

```
StartDate           EndDate             KeyId                                Type
---------           -------             -----                                ----
3/8/2017 5:58:24 PM 3/8/2018 5:58:24 PM 6f801c3e-6fcd-42b9-be8e-320b17ba1d36 Password
```

### <a name="get-a-list-of-credentials-for-the-service-principal"></a><span data-ttu-id="19196-162">Obtención de una lista de credenciales para la entidad de servicio</span><span class="sxs-lookup"><span data-stu-id="19196-162">Get a list of credentials for the service principal</span></span>

```powershell
Get-AzureRmADSpCredential -ServicePrincipalName http://MyDemoWebApp
```

```
StartDate           EndDate             KeyId                                Type
---------           -------             -----                                ----
3/8/2017 5:58:24 PM 3/8/2018 5:58:24 PM 6f801c3e-6fcd-42b9-be8e-320b17ba1d36 Password
5/5/2016 4:55:27 PM 5/5/2017 4:55:27 PM ca9d4846-4972-4c70-b6f5-a4effa60b9bc Password
```

### <a name="remove-the-old-password-from-the-service-principal"></a><span data-ttu-id="19196-163">Eliminación de una contraseña antigua de la entidad de servicio</span><span class="sxs-lookup"><span data-stu-id="19196-163">Remove the old password from the service principal</span></span>

```powershell
Remove-AzureRmADSpCredential -ServicePrincipalName http://MyDemoWebApp -KeyId ca9d4846-4972-4c70-b6f5-a4effa60b9bc
```

```
Confirm
Are you sure you want to remove credential with keyId '6f801c3e-6fcd-42b9-be8e-320b17ba1d36' for
service principal objectId '698138e7-d7b6-4738-a866-b4e3081a69e4'.
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
```

### <a name="verify-the-list-of-credentials-for-the-service-principal"></a><span data-ttu-id="19196-164">Comprobación de la lista de credenciales para la entidad de servicio</span><span class="sxs-lookup"><span data-stu-id="19196-164">Verify the list of credentials for the service principal</span></span>

```powershell
Get-AzureRmADSpCredential -ServicePrincipalName http://MyDemoWebApp
```

```
StartDate           EndDate             KeyId                                Type
---------           -------             -----                                ----
3/8/2017 5:58:24 PM 3/8/2018 5:58:24 PM 6f801c3e-6fcd-42b9-be8e-320b17ba1d36 Password
```
