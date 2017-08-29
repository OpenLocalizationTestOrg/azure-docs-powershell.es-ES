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
ms.openlocfilehash: f6d249ca5bb09c4fe8445ba5b339ffa6012815ed
ms.sourcegitcommit: 226527be7cb647acfe2ea9ab151185053ab3c6db
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2017
---
# <a name="log-in-with-azure-powershell"></a><span data-ttu-id="f99d9-103">Inicio de sesión con Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="f99d9-103">Log in with Azure PowerShell</span></span>

<span data-ttu-id="f99d9-104">Azure PowerShell admite varios métodos de inicio de sesión.</span><span class="sxs-lookup"><span data-stu-id="f99d9-104">Azure PowerShell supports multiple login methods.</span></span> <span data-ttu-id="f99d9-105">La manera más sencilla de empezar es iniciar sesión de forma interactiva en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="f99d9-105">The simplest way to get started is to log in interactively at the command line.</span></span>

## <a name="interactive-log-in"></a><span data-ttu-id="f99d9-106">Inicio de sesión interactivo</span><span class="sxs-lookup"><span data-stu-id="f99d9-106">Interactive log in</span></span>

1. <span data-ttu-id="f99d9-107">Escriba `Login-AzureRmAccount`.</span><span class="sxs-lookup"><span data-stu-id="f99d9-107">Type `Login-AzureRmAccount`.</span></span> <span data-ttu-id="f99d9-108">Aparecerá un cuadro de diálogo que le pide sus credenciales de Azure.</span><span class="sxs-lookup"><span data-stu-id="f99d9-108">You will get dialog box asking for your Azure credentials.</span></span>

2. <span data-ttu-id="f99d9-109">Escriba la dirección de correo electrónico y la contraseña asociadas a su cuenta.</span><span class="sxs-lookup"><span data-stu-id="f99d9-109">Type the email address and password associated with your account.</span></span> <span data-ttu-id="f99d9-110">Azure autentica y guarda las credenciales y, luego, cierra la ventana.</span><span class="sxs-lookup"><span data-stu-id="f99d9-110">Azure authenticates and saves the credential information, and then closes the window.</span></span>

## <a name="log-in-with-a-service-principal"></a><span data-ttu-id="f99d9-111">Inicio de sesión con una entidad de servicio</span><span class="sxs-lookup"><span data-stu-id="f99d9-111">Log in with a service principal</span></span>

<span data-ttu-id="f99d9-112">Las entidades de servicio proporcionan una manera de crear cuentas no interactivas que puede usar para manipular recursos.</span><span class="sxs-lookup"><span data-stu-id="f99d9-112">Service principals provide a way for you to create non-interactive accounts that you can use to manipulate resources.</span></span> <span data-ttu-id="f99d9-113">Las entidades de servicio son parecidas a las cuentas de usuario a las que puede aplicar reglas con Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="f99d9-113">Service principals are like user accounts to which you can apply rules using Azure Active Directory.</span></span> <span data-ttu-id="f99d9-114">Mediante la concesión de los permisos mínimos necesarios a una entidad de servicio, puede asegurarse de que sus scripts de automatización son aún más seguros.</span><span class="sxs-lookup"><span data-stu-id="f99d9-114">By granting the minimum permissions needed to a service principal, you can ensure your automation scripts are even more secure.</span></span>

1. <span data-ttu-id="f99d9-115">Si aún no tiene una entidad de servicio, [cree una](create-azure-service-principal-azureps.md).</span><span class="sxs-lookup"><span data-stu-id="f99d9-115">If you don't already have a service principal, [create one](create-azure-service-principal-azureps.md).</span></span>

2. <span data-ttu-id="f99d9-116">Inicie sesión con la entidad de servicio.</span><span class="sxs-lookup"><span data-stu-id="f99d9-116">Log in with the service principal.</span></span>

    ```powershell
    Login-AzureRmAccount -ServicePrincipal -ApplicationId  "http://my-app" -Credential $pscredential -TenantId $tenantid
    ```

    <span data-ttu-id="f99d9-117">Para obtener el valor de TenantId, inicie sesión de forma interactiva y, a continuación, obtenga este valor de su suscripción.</span><span class="sxs-lookup"><span data-stu-id="f99d9-117">To get your TenantId, log in interactively and then get the TenantId from your subscription.</span></span>

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

## <a name="log-in-to-another-cloud"></a><span data-ttu-id="f99d9-118">Inicio de sesión en otra nube</span><span class="sxs-lookup"><span data-stu-id="f99d9-118">Log in to another Cloud</span></span>

<span data-ttu-id="f99d9-119">Azure Cloud Services proporciona distintos entornos que cumplen con las reglamentaciones sobre el control de datos de las distintas administraciones públicas.</span><span class="sxs-lookup"><span data-stu-id="f99d9-119">Azure cloud services provide different environments that adhere to the data-handling regulations of various governments.</span></span> <span data-ttu-id="f99d9-120">Si la cuenta de Azure está en una de las nubes de administración pública, debe especificar el entorno cuando inicie sesión.</span><span class="sxs-lookup"><span data-stu-id="f99d9-120">If your Azure account is in one the government clouds, you need to specify the environment when you sign in.</span></span> <span data-ttu-id="f99d9-121">Por ejemplo, si la cuenta está en la nube de China, inicie sesión con el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="f99d9-121">For example, if you account is in the China cloud you sign on using the following command:</span></span>

```powershell
Login-AzureRmAccount -EnvironmentName AzureChinaCloud
```

<span data-ttu-id="f99d9-122">Use el comando siguiente para obtener una lista de los entornos disponibles:</span><span class="sxs-lookup"><span data-stu-id="f99d9-122">Use the following command to get a list of available environments:</span></span>

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

## <a name="learn-more-about-managing-azure-role-based-access"></a><span data-ttu-id="f99d9-123">Más información sobre la administración del acceso basado en rol de Azure</span><span class="sxs-lookup"><span data-stu-id="f99d9-123">Learn more about managing Azure role-based access</span></span>

<span data-ttu-id="f99d9-124">Para más información sobre la autenticación y la administración de la suscripción en Azure, consulte [Administrar cuentas, suscripciones y roles administrativos](/azure/active-directory/role-based-access-control-configure).</span><span class="sxs-lookup"><span data-stu-id="f99d9-124">For more information about authentication and subscription management in Azure, see [Manage Accounts, Subscriptions, and Administrative Roles](/azure/active-directory/role-based-access-control-configure).</span></span>

<span data-ttu-id="f99d9-125">Cmdlets de Azure PowerShell para administración de roles</span><span class="sxs-lookup"><span data-stu-id="f99d9-125">Azure PowerShell cmdlets for role management</span></span>

* [<span data-ttu-id="f99d9-126">Get-AzureRmRoleAssignment</span><span class="sxs-lookup"><span data-stu-id="f99d9-126">Get-AzureRmRoleAssignment</span></span>](/powershell/module/AzureRM.Resources/Get-AzureRmRoleAssignment)
* [<span data-ttu-id="f99d9-127">Get-AzureRmRoleDefinition</span><span class="sxs-lookup"><span data-stu-id="f99d9-127">Get-AzureRmRoleDefinition</span></span>](/powershell/module/AzureRM.Resources/Get-AzureRmRoleDefinition)
* [<span data-ttu-id="f99d9-128">New-AzureRmRoleAssignment</span><span class="sxs-lookup"><span data-stu-id="f99d9-128">New-AzureRmRoleAssignment</span></span>](/powershell/module/AzureRM.Resources/New-AzureRmRoleAssignment)
* [<span data-ttu-id="f99d9-129">New-AzureRmRoleDefinition</span><span class="sxs-lookup"><span data-stu-id="f99d9-129">New-AzureRmRoleDefinition</span></span>](/powershell/module/AzureRM.Resources/New-AzureRmRoleDefinition)
* [<span data-ttu-id="f99d9-130">Remove-AzureRmRoleAssignment</span><span class="sxs-lookup"><span data-stu-id="f99d9-130">Remove-AzureRmRoleAssignment</span></span>](/powershell/module/AzureRM.Resources/Remove-AzureRmRoleAssignment)
* [<span data-ttu-id="f99d9-131">Remove-AzureRmRoleDefinition</span><span class="sxs-lookup"><span data-stu-id="f99d9-131">Remove-AzureRmRoleDefinition</span></span>](/powershell/module/AzureRM.Resources/Remove-AzureRmRoleDefinition)
* [<span data-ttu-id="f99d9-132">Set-AzureRmRoleDefinition</span><span class="sxs-lookup"><span data-stu-id="f99d9-132">Set-AzureRmRoleDefinition</span></span>](/powershell/moduel/AzureRM.Resources/Set-AzureRmRoleDefinition)
