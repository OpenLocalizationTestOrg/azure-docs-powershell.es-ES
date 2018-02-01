---
title: "Inicio de sesión con Azure PowerShell"
description: "Inicio de sesión con Azure PowerShell"
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 05/15/2017
ms.openlocfilehash: 1af5aeffb8e87e916df3e2440a84805935136c0f
ms.sourcegitcommit: c42c7176276ec4e1cc3360a93e6b15d32083bf9f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2017
---
# <a name="log-in-with-azure-powershell"></a>Inicio de sesión con Azure PowerShell

Azure PowerShell admite varios métodos de inicio de sesión. La manera más sencilla de empezar es iniciar sesión de forma interactiva en la línea de comandos.

## <a name="interactive-log-in"></a>Inicio de sesión interactivo

1. Escriba `Login-AzureRmAccount`. Aparecerá un cuadro de diálogo que le pide sus credenciales de Azure.

2. Escriba la dirección de correo electrónico y la contraseña asociadas a su cuenta. Azure autentica y guarda las credenciales y, luego, cierra la ventana.

## <a name="log-in-with-a-service-principal"></a>Inicio de sesión con una entidad de servicio

Las entidades de servicio proporcionan una manera de crear cuentas no interactivas que puede usar para manipular recursos. Las entidades de servicio son parecidas a las cuentas de usuario a las que puede aplicar reglas con Azure Active Directory. Mediante la concesión de los permisos mínimos necesarios a una entidad de servicio, puede asegurarse de que sus scripts de automatización son aún más seguros.

1. Si aún no tiene una entidad de servicio, [cree una](create-azure-service-principal-azureps.md).

2. Inicie sesión con la entidad de servicio.

    ```powershell
    Login-AzureRmAccount -ServicePrincipal -ApplicationId  "http://my-app" -Credential $pscredential -TenantId $tenantid
    ```

    Para obtener el valor de TenantId, inicie sesión de forma interactiva y, a continuación, obtenga este valor de su suscripción.

    ```powershell
    Get-AzureRmSubscription
    ```

    ```
    Environment           : AzureCloud
    Account               : username@contoso.com
    TenantId              : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    SubscriptionId        : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    SubscriptionName      : My Production Subscription
    CurrentStorageAccount :
    ```

### <a name="log-in-using-an-azure-vm-managed-service-identity"></a>Inicio de sesión con una identidad de servicio administrada de Azure VM

Managed Service Identity (MSI) es la versión preliminar de una característica de Azure Active Directory. Puede usar una entidad de servicio de MSI para iniciar sesión y adquirir un token de acceso solo para aplicaciones para tener acceso a otros recursos.

Para más información acerca de MSI, consulte [How to use an Azure VM Managed Service Identity (MSI) for sign-in and token acquisition](/azure/active-directory/msi-how-to-get-access-token-using-msi) (Uso de Managed Service Identity (MSI) para el inicio de sesión y la adquisición de tokens).

## <a name="log-in-to-another-cloud"></a>Inicio de sesión en otra nube

Azure Cloud Services proporciona distintos entornos que cumplen con las reglamentaciones sobre el control de datos de las distintas administraciones públicas. Si la cuenta de Azure está en una de las nubes de administración pública, debe especificar el entorno cuando inicie sesión. Por ejemplo, si la cuenta está en la nube de China, inicie sesión con el comando siguiente:

```powershell
Login-AzureRmAccount -EnvironmentName AzureChinaCloud
```

Use el comando siguiente para obtener una lista de los entornos disponibles:

```powershell
Get-AzureRmEnvironment | Select-Object Name
```

```
Name
----
AzureCloud
AzureChinaCloud
AzureUSGovernment
AzureGermanCloud
```

## <a name="learn-more-about-managing-azure-role-based-access"></a>Más información sobre la administración del acceso basado en rol de Azure

Para más información sobre la autenticación y la administración de la suscripción en Azure, consulte [Administrar cuentas, suscripciones y roles administrativos](/azure/active-directory/role-based-access-control-configure).

Cmdlets de Azure PowerShell para administración de roles

* [Get-AzureRmRoleAssignment](/powershell/module/AzureRM.Resources/Get-AzureRmRoleAssignment)
* [Get-AzureRmRoleDefinition](/powershell/module/AzureRM.Resources/Get-AzureRmRoleDefinition)
* [New-AzureRmRoleAssignment](/powershell/module/AzureRM.Resources/New-AzureRmRoleAssignment)
* [New-AzureRmRoleDefinition](/powershell/module/AzureRM.Resources/New-AzureRmRoleDefinition)
* [Remove-AzureRmRoleAssignment](/powershell/module/AzureRM.Resources/Remove-AzureRmRoleAssignment)
* [Remove-AzureRmRoleDefinition](/powershell/module/AzureRM.Resources/Remove-AzureRmRoleDefinition)
* [Set-AzureRmRoleDefinition](/powershell/moduel/AzureRM.Resources/Set-AzureRmRoleDefinition)
