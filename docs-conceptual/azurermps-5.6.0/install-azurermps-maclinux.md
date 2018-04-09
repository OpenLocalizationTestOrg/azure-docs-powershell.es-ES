---
title: Instalación y configuración de Azure PowerShell en macOS y Linux | Microsoft Docs
description: Instalación y configuración de Azure PowerShell para usarlo por primera vez en macOS y Linux.
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 01/12/2018
ms.openlocfilehash: eed7a35fcf20a17c83d9e5e3272be4b77fa12c34
ms.sourcegitcommit: 8376e0bc5f862d382d7283ba72990e3707591e7b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/30/2018
---
# <a name="install-and-configure-azure-powershell-on-macos-and-linux"></a><span data-ttu-id="d5b87-103">Instalación y configuración de Azure PowerShell en macOS y Linux</span><span class="sxs-lookup"><span data-stu-id="d5b87-103">Install and configure Azure PowerShell on macOS and Linux</span></span>

<span data-ttu-id="d5b87-104">Ya se pueden instalar PowerShell Core v6 y Azure PowerShell en plataformas distintas de Windows.</span><span class="sxs-lookup"><span data-stu-id="d5b87-104">It is now possible to install PowerShell Core v6 and Azure PowerShell on non-Windows platforms.</span></span>
<span data-ttu-id="d5b87-105">El proceso de instalación de Azure PowerShell en macOS y Linux no es tan distinto del de Windows; sin embargo, primero hay que instalar PowerShell Core v6.</span><span class="sxs-lookup"><span data-stu-id="d5b87-105">The process of installing Azure PowerShell on macOS and Linux is not that different from Windows, however, you must first install PowerShell Core v6.</span></span>

> [!NOTE]

> <span data-ttu-id="d5b87-106">Actualmente, tanto PowerShell 6 como Azure PowerShell para .NET Core están en versión beta.</span><span class="sxs-lookup"><span data-stu-id="d5b87-106">At this time, both PowerShell Core v6 and Azure PowerShell for .NET Core are still in beta.</span></span>
> <span data-ttu-id="d5b87-107">La compatibilidad con estos productos es limitada.</span><span class="sxs-lookup"><span data-stu-id="d5b87-107">Support for these products is limited.</span></span> <span data-ttu-id="d5b87-108">Si tiene problemas o detecta errores, regístrelos en GitHub.</span><span class="sxs-lookup"><span data-stu-id="d5b87-108">If you have problems or discover bugs, please file Issues in GitHub.</span></span>
>
> * [<span data-ttu-id="d5b87-109">Problemas de PowerShell Core v6</span><span class="sxs-lookup"><span data-stu-id="d5b87-109">Issues for PowerShell Core v6</span></span>](https://github.com/PowerShell/PowerShell/issues)
> * [<span data-ttu-id="d5b87-110">Problemas de Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5b87-110">Issues for Azure PowerShell</span></span>](https://github.com/azure/azure-docs-powershell/issues)

## <a name="step-1-install-powershell-core-v6"></a><span data-ttu-id="d5b87-111">Paso 1: Instalación de PowerShell Core v6</span><span class="sxs-lookup"><span data-stu-id="d5b87-111">Step 1: Install PowerShell Core v6</span></span>

<span data-ttu-id="d5b87-112">El proceso de instalación de PowerShell Core v6 varía en función del sistema operativo de destino.</span><span class="sxs-lookup"><span data-stu-id="d5b87-112">The process of installing PowerShell Core v6 varies depending on the target operating system.</span></span>
<span data-ttu-id="d5b87-113">Aunque PowerShell Core v6 se puede instalar en Windows, este artículo se centra en macOS y Linux.</span><span class="sxs-lookup"><span data-stu-id="d5b87-113">While it is possible to install PowerShell Core v6 on Windows, this article focuses on macOS and Linux.</span></span> <span data-ttu-id="d5b87-114">Si quiere usar Azure PowerShell en Windows, consulte el artículo de [instalación](./install-azurerm-ps.md) para Windows.</span><span class="sxs-lookup"><span data-stu-id="d5b87-114">If you want to use Azure PowerShell on Windows, see the [install](./install-azurerm-ps.md) article for Windows.</span></span>

<span data-ttu-id="d5b87-115">La instalación de **PowerShell Core v6** en Linux o macOS varía en función de la distribución de Linux y de la versión del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="d5b87-115">Installing **PowerShell Core v6** on Linux or macOS varies depending on the Linux distribution and OS version.</span></span>
<span data-ttu-id="d5b87-116">En el siguiente artículo encontrará instrucciones detalladas para su instalación:</span><span class="sxs-lookup"><span data-stu-id="d5b87-116">Detailed instructions can be found in the following article:</span></span>

- [<span data-ttu-id="d5b87-117">Instalación de PowerShell Core en macOS y Linux</span><span class="sxs-lookup"><span data-stu-id="d5b87-117">Installing PowerShell Core on macOS and Linux</span></span>](/powershell/scripting/setup/installing-powershell-core-on-macos-and-linux)

## <a name="step-2-install-azure-powershell-for-net-core"></a><span data-ttu-id="d5b87-118">Paso 2: Instalación de Azure PowerShell para .NET Core</span><span class="sxs-lookup"><span data-stu-id="d5b87-118">Step 2: Install Azure PowerShell for .NET Core</span></span>

<span data-ttu-id="d5b87-119">PowerShell Core v6 viene con el módulo PowerShellGet ya instalado.</span><span class="sxs-lookup"><span data-stu-id="d5b87-119">PowerShell Core v6 comes with the PowerShellGet module already installed.</span></span> <span data-ttu-id="d5b87-120">Esto facilita la instalación de cualquier módulo que se publica en la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5b87-120">This makes it easy to install any module that is published to the PowerShell Gallery.</span></span> <span data-ttu-id="d5b87-121">Para instalar Azure PowerShell, abra una nueva sesión de PowerShell y ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="d5b87-121">To install Azure PowerShell, open a new PowerShell session and run the following command:</span></span>

```powershell
Install-Module AzureRM.NetCore
```

## <a name="step-3-load-the-azurermnetcore-module"></a><span data-ttu-id="d5b87-122">Paso 3: Carga del módulo AzureRM.Netcore</span><span class="sxs-lookup"><span data-stu-id="d5b87-122">Step 3: Load the AzureRM.Netcore module</span></span>

<span data-ttu-id="d5b87-123">Una vez que se instala, debe cargarse en la sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5b87-123">Once the module is installed, you need to load the module into your PowerShell session.</span></span> <span data-ttu-id="d5b87-124">Los módulos se cargan mediante el cmdlet, `Import-Module` como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="d5b87-124">Modules are loaded using the `Import-Module` cmdlet, as follows:</span></span>

```powershell
Import-Module AzureRM.Netcore
Import-Module AzureRM.Profile.Netcore
```

<span data-ttu-id="d5b87-125">Cuando finalice la importación, puede probar su módulo recién instalado; para ello, intente iniciar sesión en Azure mediante el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="d5b87-125">After the import completes, you can test your newly installed and module by attempting to sign into Azure using the following command:</span></span>

```powershell
Connect-AzureRmAccount
```

<span data-ttu-id="d5b87-126">El comando anterior debe solicitarle que vaya a `https://aka.ms/devicelogin` y escriba el código proporcionado.</span><span class="sxs-lookup"><span data-stu-id="d5b87-126">The above command should prompt you to go to `https://aka.ms/devicelogin` and enter the provided code.</span></span>

## <a name="available-cmdlets"></a><span data-ttu-id="d5b87-127">Cmdlets disponibles</span><span class="sxs-lookup"><span data-stu-id="d5b87-127">Available cmdlets</span></span>

<span data-ttu-id="d5b87-128">Los módulos de Azure PowerShell para .NET Standard se encuentran aún en desarrollo.</span><span class="sxs-lookup"><span data-stu-id="d5b87-128">The Azure PowerShell modules for .NET Standard are still in development.</span></span> <span data-ttu-id="d5b87-129">Estos módulos no proporcionan el conjunto completo de cmdlets que están disponibles para la versión de Windows de los módulos.</span><span class="sxs-lookup"><span data-stu-id="d5b87-129">These modules do not provide the full set of cmdlets that are available for the Windows version of the modules.</span></span> <span data-ttu-id="d5b87-130">Las siguientes funciones se implementan en los módulos de AzureRM.Netcore:</span><span class="sxs-lookup"><span data-stu-id="d5b87-130">The following functions are implemented in AzureRM.Netcore modules:</span></span>

* <span data-ttu-id="d5b87-131">Administración de cuentas</span><span class="sxs-lookup"><span data-stu-id="d5b87-131">Account management</span></span>
  - <span data-ttu-id="d5b87-132">Inicie sesión con la cuenta de Microsoft, la cuenta organizativa o la entidad de servicio mediante Microsoft Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d5b87-132">Login with Microsoft account, Organizational account, or Service Principal through Microsoft Azure Active Directory</span></span>
  - <span data-ttu-id="d5b87-133">Guarde las credenciales en el disco con Save-AzureRmContext y cargue las credenciales guardadas mediante Import-AzureRmContext.</span><span class="sxs-lookup"><span data-stu-id="d5b87-133">Save Credentials to disk with Save-AzureRmContext and load saved credentials using Import-AzureRmContext</span></span>
* <span data-ttu-id="d5b87-134">Environment</span><span class="sxs-lookup"><span data-stu-id="d5b87-134">Environment</span></span>
  - <span data-ttu-id="d5b87-135">Obtenga los diferentes entornos de Microsoft Azure de uso inmediato.</span><span class="sxs-lookup"><span data-stu-id="d5b87-135">Get the different out-of-box Microsoft Azure environments</span></span>
  - <span data-ttu-id="d5b87-136">Agregue, defina o quite entornos personalizados (como los entornos Azure Stack o Windows Azure Pack)</span><span class="sxs-lookup"><span data-stu-id="d5b87-136">Add/Set/Remove customized environments (like your Azure Stack or Windows Azure Pack environments)</span></span>
* <span data-ttu-id="d5b87-137">Cmdlets del plano de administración para servicios de Azure que usan las interfaces de Resource Manager y Service Management.</span><span class="sxs-lookup"><span data-stu-id="d5b87-137">Management plane cmdlets for Azure services using Resource Manager and Service Management interfaces.</span></span>
  - <span data-ttu-id="d5b87-138">Máquina virtual</span><span class="sxs-lookup"><span data-stu-id="d5b87-138">Virtual Machine</span></span>
  - <span data-ttu-id="d5b87-139">App Service (Websites)</span><span class="sxs-lookup"><span data-stu-id="d5b87-139">App Service (Websites)</span></span>
  - <span data-ttu-id="d5b87-140">SQL Database</span><span class="sxs-lookup"><span data-stu-id="d5b87-140">SQL Database</span></span>
  - <span data-ttu-id="d5b87-141">Storage</span><span class="sxs-lookup"><span data-stu-id="d5b87-141">Storage</span></span>
  - <span data-ttu-id="d5b87-142">Red</span><span class="sxs-lookup"><span data-stu-id="d5b87-142">Network</span></span>

## <a name="next-steps"></a><span data-ttu-id="d5b87-143">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="d5b87-143">Next Steps</span></span>

<span data-ttu-id="d5b87-144">Para más información sobre el uso de Azure PowerShell, consulte el artículo [Introducción a Azure PowerShell](get-started-azureps.md).</span><span class="sxs-lookup"><span data-stu-id="d5b87-144">For more information about using Azure PowerShell, see the [Get started with Azure PowerShell](get-started-azureps.md) article.</span></span>
