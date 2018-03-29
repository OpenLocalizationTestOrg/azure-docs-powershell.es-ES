---
title: Creación de una entidad de servicio de Azure con Azure PowerShell
description: Aprenda a crear una entidad de servicio para cualquier aplicación o servicio con Azure PowerShell.
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
ms.sourcegitcommit: 15bf69bf95eceb936b3a429e741add95c308826a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/28/2018
---
# <a name="create-an-azure-service-principal-with-azure-powershell"></a>Creación de una entidad de servicio de Azure con Azure PowerShell

Si planea administrar una aplicación o servicio con Azure PowerShell, debe ejecutarla en una entidad de servicio de Azure Active Directory (AAD), en lugar de con sus propias credenciales. En este tema le ayudará a crear a una entidad de seguridad con Azure PowerShell.

> [!NOTE]
> Las entidades de servicio también se pueden crear desde Azure Portal. Para más información, lea [Uso del portal para crear una aplicación de Azure Active Directory y una entidad de servicio con acceso a los recursos](/azure/azure-resource-manager/resource-group-create-service-principal-portal).

## <a name="what-is-a-service-principal"></a>¿Qué es una "entidad de servicio"?

Una entidad de servicio de Azure es una identidad de seguridad que usan las aplicaciones, los servicios y las herramientas de automatización creadas por el usuario para acceder a recursos específicos de Azure. Se puede considerar una "identidad de usuario" (nombre de usuario y una contraseña o certificado) con un rol específico y permisos estrechamente controlados. A diferencia de una identidad de usuario general, solo necesita poder realizar acciones específicas. Mejora la seguridad si solo se le concede el nivel de permiso mínimo necesario para realizar sus tareas de administración.

## <a name="verify-your-own-permission-level"></a>Comprobación del nivel de permiso

En primer lugar, debe tener permisos suficientes tanto en su suscripción de Azure como en Azure Active Directory. En concreto, debe poder crear una aplicación en Active Directory y asignar un rol a la entidad de servicio.

El portal representa la forma más sencilla de comprobar si su cuenta tiene los permisos adecuados. Consulte [Comprobación de los permisos necesarios en el portal](/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions).

## <a name="create-a-service-principal-for-your-app"></a>Creación de una entidad de servicio para la aplicación

Una vez que haya iniciado sesión en su cuenta de Azure puede crear la entidad de servicio. Debe realizar alguno de los siguientes métodos para identificar la aplicación implementada:

* El nombre único de la aplicación implementada (como "MyDemoWebApp" en los ejemplos siguientes), o bien
* el identificador de la aplicación, el GUID único asociado a la aplicación, el servicio o el objeto implementados

### <a name="get-information-about-your-application"></a>Obtención de información acerca de una aplicación

El cmdlet `Get-AzureRmADApplication` puede usarse para detectar información acerca de la aplicación.

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

### <a name="create-a-service-principal-for-your-application"></a>Creación de una entidad de servicio para la aplicación

El cmdlet `New-AzureRmADServicePrincipal` se usa para crear la entidad de servicio.

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

### <a name="get-information-about-the-service-principal"></a>Obtención de información acerca de la entidad de servicio

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

### <a name="sign-in-using-the-service-principal"></a>Inicio de sesión mediante la entidad de servicio

Ya puede iniciar sesión como la nueva entidad de servicio en la aplicación mediante los valores de *appId* y *password* que proporcionó. Debe proporcionar el identificador del inquilino de su cuenta. El identificador de inquilino aparece al iniciar sesión en Azure con sus credenciales personales.

```powershell
$cred = Get-Credential -UserName $svcprincipal.ApplicationId -Message "Enter Password"
Login-AzureRmAccount -Credential $cred -ServicePrincipal -TenantId XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
```

Ejecute este comando desde una nueva sesión de PowerShell. Después de un inicio de sesión correcto, obtendrá un resultado parecido al siguiente:

```
Environment           : AzureCloud
Account               : 00c01aaa-1603-49fc-b6df-b78c4e5138b4
TenantId              : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
SubscriptionId        :
SubscriptionName      :
CurrentStorageAccount :
```

Felicidades. Puede usar estas credenciales para ejecutar la aplicación. A continuación, debe ajustar los permisos de la entidad de servicio.

## <a name="managing-roles"></a>Administración de roles

> [!NOTE]
> El control de acceso basado en roles (RBAC) de Azure es un modelo para definir y administrar roles tanto para usuario como para las entidades de servicio. Los roles conjuntos de permisos asociados a ellos, que son los que determinan los recursos que una entidad puede administrar o leer, a los que puede acceder o en los que puede escribir. Para más información acerca de RBAC y roles, consulte [Roles integrados para el control de acceso basado en roles de Azure](/azure/active-directory/role-based-access-built-in-roles).

Azure PowerShell proporciona los siguientes cmdlets para administrar las asignaciones de roles:

* [Get-AzureRmRoleAssignment](/powershell/module/azurerm.resources/get-azurermroleassignment)
* [New-AzureRmRoleAssignment](/powershell/module/azurerm.resources/new-azurermroleassignment)
* [Remove-AzureRmRoleAssignment](/powershell/module/azurerm.resources/remove-azurermroleassignment)

El rol predeterminado de una entidad de servicio es **colaborador**. Dado su gran cantidad de permisos, es posible que no sea la mejor opción para las interacciones de una aplicación con los servicios de Azure.
El rol de **lector** es más restrictivo y es una buena elección para el acceso de solo lectura. En Azure Portal encontrará más información acerca de los permisos específicos de los roles o podrá crear permisos personalizados.

En este ejemplo, agregue el rol de **lector** al ejemplo anterior y elimine el de **colaborador**:

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

Para ver los roles actuales asignados:

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

Otros cmdlets de Azure PowerShell para administración de roles:

* [Get-AzureRmRoleDefinition](/powershell/module/azurerm.resources/Get-AzureRmRoleDefinition)
* [New-AzureRmRoleDefinition](/powershell/module/azurerm.resources/New-AzureRmRoleDefinition)
* [Remove-AzureRmRoleDefinition](/powershell/module/azurerm.resources/Remove-AzureRmRoleDefinition)
* [Set-AzureRmRoleDefinition](/powershell/module/azurerm.resources/Set-AzureRmRoleDefinition)

## <a name="change-the-credentials-of-the-security-principal"></a>Cambio de las credenciales de la entidad de seguridad

A nivel de seguridad se recomienda revisar los permisos y actualizar las contraseñas periódicamente. Si lo desea, también puede administrar y modificar las credenciales de seguridad cuando la aplicación cambie. Por ejemplo, podemos cambiar la contraseña de la entidad de servicio mediante la creación de una contraseña nueva y la eliminación de la antigua.

### <a name="add-a-new-password-for-the-service-principal"></a>Adición de una nueva contraseña para la entidad de servicio

```powershell
$password = [System.Web.Security.Membership]::GeneratePassword(16,3)
New-AzureRmADSpCredential -ServicePrincipalName http://MyDemoWebApp -Password $password
```

```
StartDate           EndDate             KeyId                                Type
---------           -------             -----                                ----
3/8/2017 5:58:24 PM 3/8/2018 5:58:24 PM 6f801c3e-6fcd-42b9-be8e-320b17ba1d36 Password
```

### <a name="get-a-list-of-credentials-for-the-service-principal"></a>Obtención de una lista de credenciales para la entidad de servicio

```powershell
Get-AzureRmADSpCredential -ServicePrincipalName http://MyDemoWebApp
```

```
StartDate           EndDate             KeyId                                Type
---------           -------             -----                                ----
3/8/2017 5:58:24 PM 3/8/2018 5:58:24 PM 6f801c3e-6fcd-42b9-be8e-320b17ba1d36 Password
5/5/2016 4:55:27 PM 5/5/2017 4:55:27 PM ca9d4846-4972-4c70-b6f5-a4effa60b9bc Password
```

### <a name="remove-the-old-password-from-the-service-principal"></a>Eliminación de una contraseña antigua de la entidad de servicio

```powershell
Remove-AzureRmADSpCredential -ServicePrincipalName http://MyDemoWebApp -KeyId ca9d4846-4972-4c70-b6f5-a4effa60b9bc
```

```
Confirm
Are you sure you want to remove credential with keyId '6f801c3e-6fcd-42b9-be8e-320b17ba1d36' for
service principal objectId '698138e7-d7b6-4738-a866-b4e3081a69e4'.
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
```

### <a name="verify-the-list-of-credentials-for-the-service-principal"></a>Comprobación de la lista de credenciales para la entidad de servicio

```powershell
Get-AzureRmADSpCredential -ServicePrincipalName http://MyDemoWebApp
```

```
StartDate           EndDate             KeyId                                Type
---------           -------             -----                                ----
3/8/2017 5:58:24 PM 3/8/2018 5:58:24 PM 6f801c3e-6fcd-42b9-be8e-320b17ba1d36 Password
```
