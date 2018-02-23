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
ms.sourcegitcommit: 7e77fe7ecd2112d6b4515517509c5c723e750e27
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2018
---
# <a name="log-in-with-azure-powershell"></a><span data-ttu-id="ae849-103">Inicio de sesión con Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="ae849-103">Log in with Azure PowerShell</span></span>

<span data-ttu-id="ae849-104">Azure PowerShell admite varios métodos de inicio de sesión.</span><span class="sxs-lookup"><span data-stu-id="ae849-104">Azure PowerShell supports multiple login methods.</span></span> <span data-ttu-id="ae849-105">La manera más sencilla de empezar es iniciar sesión de forma interactiva en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="ae849-105">The simplest way to get started is to log in interactively at the command line.</span></span>

## <a name="interactive-log-in"></a><span data-ttu-id="ae849-106">Inicio de sesión interactivo</span><span class="sxs-lookup"><span data-stu-id="ae849-106">Interactive log in</span></span>

1. <span data-ttu-id="ae849-107">Escriba `Login-AzureRmAccount`.</span><span class="sxs-lookup"><span data-stu-id="ae849-107">Type `Login-AzureRmAccount`.</span></span> <span data-ttu-id="ae849-108">Aparecerá un cuadro de diálogo que le pide sus credenciales de Azure.</span><span class="sxs-lookup"><span data-stu-id="ae849-108">You will get dialog box asking for your Azure credentials.</span></span>

2. <span data-ttu-id="ae849-109">Escriba la dirección de correo electrónico y la contraseña asociadas a su cuenta.</span><span class="sxs-lookup"><span data-stu-id="ae849-109">Type the email address and password associated with your account.</span></span> <span data-ttu-id="ae849-110">Azure autentica y guarda las credenciales y, luego, cierra la ventana.</span><span class="sxs-lookup"><span data-stu-id="ae849-110">Azure authenticates and saves the credential information, and then closes the window.</span></span>

## <a name="log-in-with-a-service-principal"></a><span data-ttu-id="ae849-111">Inicio de sesión con una entidad de servicio</span><span class="sxs-lookup"><span data-stu-id="ae849-111">Log in with a service principal</span></span>

<span data-ttu-id="ae849-112">Las entidades de servicio proporcionan una manera de crear cuentas no interactivas que puede usar para manipular recursos.</span><span class="sxs-lookup"><span data-stu-id="ae849-112">Service principals provide a way for you to create non-interactive accounts that you can use to manipulate resources.</span></span> <span data-ttu-id="ae849-113">Las entidades de servicio son parecidas a las cuentas de usuario a las que puede aplicar reglas con Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="ae849-113">Service principals are like user accounts to which you can apply rules using Azure Active Directory.</span></span> <span data-ttu-id="ae849-114">Mediante la concesión de los permisos mínimos necesarios a una entidad de servicio, puede asegurarse de que sus scripts de automatización son aún más seguros.</span><span class="sxs-lookup"><span data-stu-id="ae849-114">By granting the minimum permissions needed to a service principal, you can ensure your automation scripts are even more secure.</span></span>

1. <span data-ttu-id="ae849-115">Si aún no tiene una entidad de servicio, [cree una](create-azure-service-principal-azureps.md).</span><span class="sxs-lookup"><span data-stu-id="ae849-115">If you don't already have a service principal, [create one](create-azure-service-principal-azureps.md).</span></span>

2. <span data-ttu-id="ae849-116">Inicie sesión con la entidad de servicio.</span><span class="sxs-lookup"><span data-stu-id="ae849-116">Log in with the service principal.</span></span>

    ```powershell
    Login-AzureRmAccount -ServicePrincipal -ApplicationId  "http://my-app" -Credential $pscredential -TenantId $tenantid
    ```

    <span data-ttu-id="ae849-117">Para obtener el valor de TenantId, inicie sesión de forma interactiva y, a continuación, obtenga este valor de su suscripción.</span><span class="sxs-lookup"><span data-stu-id="ae849-117">To get your TenantId, log in interactively and then get the TenantId from your subscription.</span></span>

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

### <a name="log-in-using-an-azure-vm-managed-service-identity"></a><span data-ttu-id="ae849-118">Inicio de sesión con una identidad de servicio administrada de Azure VM</span><span class="sxs-lookup"><span data-stu-id="ae849-118">Log in using an Azure VM Managed Service Identity</span></span>

<span data-ttu-id="ae849-119">Managed Service Identity (MSI) es la versión preliminar de una característica de Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="ae849-119">Managed Service Identity (MSI) is a preview feature of Azure Active Directory.</span></span> <span data-ttu-id="ae849-120">Puede usar una entidad de servicio de MSI para iniciar sesión y adquirir un token de acceso solo para aplicaciones para tener acceso a otros recursos.</span><span class="sxs-lookup"><span data-stu-id="ae849-120">You can use an MSI service principal for sign-in, and acquire an app-only access token to access other resources.</span></span>

<span data-ttu-id="ae849-121">Para más información acerca de MSI, consulte [How to use an Azure VM Managed Service Identity (MSI) for sign-in and token acquisition](/azure/active-directory/msi-how-to-get-access-token-using-msi) (Uso de Managed Service Identity (MSI) para el inicio de sesión y la adquisición de tokens).</span><span class="sxs-lookup"><span data-stu-id="ae849-121">For more information about MSI, see [How to use an Azure VM Managed Service Identity (MSI) for sign-in and token acquisition](/azure/active-directory/msi-how-to-get-access-token-using-msi).</span></span>

## <a name="log-in-to-another-cloud"></a><span data-ttu-id="ae849-122">Inicio de sesión en otra nube</span><span class="sxs-lookup"><span data-stu-id="ae849-122">Log in to another Cloud</span></span>

<span data-ttu-id="ae849-123">Azure Cloud Services proporciona distintos entornos que cumplen con las reglamentaciones sobre el control de datos de las distintas administraciones públicas.</span><span class="sxs-lookup"><span data-stu-id="ae849-123">Azure cloud services provide different environments that adhere to the data-handling regulations of various governments.</span></span> <span data-ttu-id="ae849-124">Si la cuenta de Azure está en una de las nubes de administración pública, debe especificar el entorno cuando inicie sesión.</span><span class="sxs-lookup"><span data-stu-id="ae849-124">If your Azure account is in one the government clouds, you need to specify the environment when you sign in.</span></span> <span data-ttu-id="ae849-125">Por ejemplo, si la cuenta está en la nube de China, inicie sesión con el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="ae849-125">For example, if you account is in the China cloud you sign on using the following command:</span></span>

```powershell
Login-AzureRmAccount -EnvironmentName AzureChinaCloud
```

<span data-ttu-id="ae849-126">Use el comando siguiente para obtener una lista de los entornos disponibles:</span><span class="sxs-lookup"><span data-stu-id="ae849-126">Use the following command to get a list of available environments:</span></span>

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

## <a name="learn-more-about-managing-azure-role-based-access"></a><span data-ttu-id="ae849-127">Más información sobre la administración del acceso basado en rol de Azure</span><span class="sxs-lookup"><span data-stu-id="ae849-127">Learn more about managing Azure role-based access</span></span>

<span data-ttu-id="ae849-128">Para más información sobre la autenticación y la administración de la suscripción en Azure, consulte [Administrar cuentas, suscripciones y roles administrativos](/azure/active-directory/role-based-access-control-configure).</span><span class="sxs-lookup"><span data-stu-id="ae849-128">For more information about authentication and subscription management in Azure, see [Manage Accounts, Subscriptions, and Administrative Roles](/azure/active-directory/role-based-access-control-configure).</span></span>

<span data-ttu-id="ae849-129">Cmdlets de Azure PowerShell para administración de roles</span><span class="sxs-lookup"><span data-stu-id="ae849-129">Azure PowerShell cmdlets for role management</span></span>

* [<span data-ttu-id="ae849-130">Get-AzureRmRoleAssignment</span><span class="sxs-lookup"><span data-stu-id="ae849-130">Get-AzureRmRoleAssignment</span></span>](/powershell/module/AzureRM.Resources/Get-AzureRmRoleAssignment)
* [<span data-ttu-id="ae849-131">Get-AzureRmRoleDefinition</span><span class="sxs-lookup"><span data-stu-id="ae849-131">Get-AzureRmRoleDefinition</span></span>](/powershell/module/AzureRM.Resources/Get-AzureRmRoleDefinition)
* [<span data-ttu-id="ae849-132">New-AzureRmRoleAssignment</span><span class="sxs-lookup"><span data-stu-id="ae849-132">New-AzureRmRoleAssignment</span></span>](/powershell/module/AzureRM.Resources/New-AzureRmRoleAssignment)
* [<span data-ttu-id="ae849-133">New-AzureRmRoleDefinition</span><span class="sxs-lookup"><span data-stu-id="ae849-133">New-AzureRmRoleDefinition</span></span>](/powershell/module/AzureRM.Resources/New-AzureRmRoleDefinition)
* [<span data-ttu-id="ae849-134">Remove-AzureRmRoleAssignment</span><span class="sxs-lookup"><span data-stu-id="ae849-134">Remove-AzureRmRoleAssignment</span></span>](/powershell/module/AzureRM.Resources/Remove-AzureRmRoleAssignment)
* [<span data-ttu-id="ae849-135">Remove-AzureRmRoleDefinition</span><span class="sxs-lookup"><span data-stu-id="ae849-135">Remove-AzureRmRoleDefinition</span></span>](/powershell/module/AzureRM.Resources/Remove-AzureRmRoleDefinition)
* [<span data-ttu-id="ae849-136">Set-AzureRmRoleDefinition</span><span class="sxs-lookup"><span data-stu-id="ae849-136">Set-AzureRmRoleDefinition</span></span>](/powershell/moduel/AzureRM.Resources/Set-AzureRmRoleDefinition)
