---
title: "Instalación y configuración de Azure PowerShell en macOS y Linux | Microsoft Docs"
description: "Instalación y configuración de Azure PowerShell para usarlo por primera vez en macOS y Linux."
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 09/06/2017
ms.openlocfilehash: 94b39c18acaca7a4b17b5207feed025442665acc
ms.sourcegitcommit: c42c7176276ec4e1cc3360a93e6b15d32083bf9f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2017
---
# <a name="install-and-configure-azure-powershell-on-macos-and-linux"></a><span data-ttu-id="386cb-103">Instalación y configuración de Azure PowerShell en macOS y Linux</span><span class="sxs-lookup"><span data-stu-id="386cb-103">Install and configure Azure PowerShell on macOS and Linux</span></span>

<span data-ttu-id="386cb-104">Ahora es posible instalar PowerShell 6 (beta) y Azure PowerShell en plataformas que no sean Windows.</span><span class="sxs-lookup"><span data-stu-id="386cb-104">It is now possible to install PowerShell 6 (beta) and Azure PowerShell on non-Windows platforms.</span></span>
<span data-ttu-id="386cb-105">El proceso de instalación de Azure PowerShell en macOS y Linux no es tan diferente al de Windows, sin embargo, primero se debe instalar PowerShell 6 (beta).</span><span class="sxs-lookup"><span data-stu-id="386cb-105">The process of installing Azure PowerShell on macOS and Linux is not that different from Windows, however, you must first install PowerShell 6 (beta).</span></span>

> [!NOTE]

> <span data-ttu-id="386cb-106">En este momento, tanto PowerShell 6 como Azure PowerShell para .NET Core están en versión beta.</span><span class="sxs-lookup"><span data-stu-id="386cb-106">At this time, both PowerShell 6 (beta) and Azure PowerShell for .NET Core are still in beta.</span></span>
> <span data-ttu-id="386cb-107">La compatibilidad con estos productos es limitada.</span><span class="sxs-lookup"><span data-stu-id="386cb-107">Support for these products is limited.</span></span> <span data-ttu-id="386cb-108">Si tiene problemas o detecta errores, regístrelos en GitHub.</span><span class="sxs-lookup"><span data-stu-id="386cb-108">If you have problems or discover bugs, please file Issues in GitHub.</span></span>
>
> * [<span data-ttu-id="386cb-109">Problemas de PowerShell 6 (beta)</span><span class="sxs-lookup"><span data-stu-id="386cb-109">Issues for PowerShell 6 (beta)</span></span>](https://github.com/PowerShell/PowerShell/issues)
> * [<span data-ttu-id="386cb-110">Problemas de Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="386cb-110">Issues for Azure PowerShell</span></span>](https://github.com/azure/azure-docs-powershell/issues)

## <a name="step-1-install-powershell-6-beta"></a><span data-ttu-id="386cb-111">Paso 1: Instalación de PowerShell 6 (beta)</span><span class="sxs-lookup"><span data-stu-id="386cb-111">Step 1: Install PowerShell 6 (beta)</span></span>

<span data-ttu-id="386cb-112">El proceso de instalación de PowerShell 6 (beta) varía según el sistema operativo de destino.</span><span class="sxs-lookup"><span data-stu-id="386cb-112">The process of installing PowerShell 6 (beta) on varies depending on the target operating system.</span></span>
<span data-ttu-id="386cb-113">Aunque es posible instalar PowerShell 6 (beta) en Windows, este artículo se centra en macOS y Linux.</span><span class="sxs-lookup"><span data-stu-id="386cb-113">While it is possible to install PowerShell 6 (beta) on Windows, this article focuses on macOS and Linux.</span></span> <span data-ttu-id="386cb-114">Si quiere usar Azure PowerShell en Windows, consulte el artículo de [instalación](./install-azurerm-ps.md) para Windows.</span><span class="sxs-lookup"><span data-stu-id="386cb-114">If you want to use Azure PowerShell on Windows, see the [install](./install-azurerm-ps.md) article for Windows.</span></span>

<span data-ttu-id="386cb-115">Para instalar **PowerShell 6** (beta) en Linux o macOS, necesita:</span><span class="sxs-lookup"><span data-stu-id="386cb-115">To install **PowerShell 6** (beta) on Linux or macOS, you need to:</span></span>

1. <span data-ttu-id="386cb-116">Obtener PowerShell para el sistema operativo y la versión específicos, en [GitHub](https://github.com/powershell/powershell#get-powershell)</span><span class="sxs-lookup"><span data-stu-id="386cb-116">Get PowerShell for the specific OS and version, from [GitHub](https://github.com/powershell/powershell#get-powershell)</span></span>
2. <span data-ttu-id="386cb-117">Seguir las instrucciones de instalación</span><span class="sxs-lookup"><span data-stu-id="386cb-117">Follow the installation instructions</span></span>
   - [<span data-ttu-id="386cb-118">Linux</span><span class="sxs-lookup"><span data-stu-id="386cb-118">Linux</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md)
   - [<span data-ttu-id="386cb-119">macOS</span><span class="sxs-lookup"><span data-stu-id="386cb-119">macOS</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#macos-1012)

## <a name="step-2-install-azure-powershell-for-net-core"></a><span data-ttu-id="386cb-120">Paso 2: Instalación de Azure PowerShell para .NET Core</span><span class="sxs-lookup"><span data-stu-id="386cb-120">Step 2: Install Azure PowerShell for .NET Core</span></span>

<span data-ttu-id="386cb-121">PowerShell 6 (beta) viene con el módulo PowerShellGet ya instalado.</span><span class="sxs-lookup"><span data-stu-id="386cb-121">PowerShell 6 (beta) comes with the PowerShellGet module already installed.</span></span> <span data-ttu-id="386cb-122">Esto facilita la instalación de cualquier módulo que se publica en la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="386cb-122">This makes it easy to install any module that is published to the PowerShell Gallery.</span></span> <span data-ttu-id="386cb-123">Para instalar Azure PowerShell, abra una nueva sesión de PowerShell y ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="386cb-123">To install Azure PowerShell, open a new PowerShell session and run the following command:</span></span>

```powershell
Install-Module AzureRM.NetCore
```

## <a name="step-3-load-the-azurermnetcore-module"></a><span data-ttu-id="386cb-124">Paso 3: Carga del módulo AzureRM.Netcore</span><span class="sxs-lookup"><span data-stu-id="386cb-124">Step 3: Load the AzureRM.Netcore module</span></span>

<span data-ttu-id="386cb-125">Una vez que se instala, debe cargarse en la sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="386cb-125">Once the module is installed, you need to load the module into your PowerShell session.</span></span> <span data-ttu-id="386cb-126">Los módulos se cargan mediante el cmdlet, `Import-Module` como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="386cb-126">Modules are loaded using the `Import-Module` cmdlet, as follows:</span></span>

```powershell
Import-Module AzureRM.Netcore
```

<span data-ttu-id="386cb-127">Cuando finalice la importación, puede probar su módulo recién instalado; para ello, intente iniciar sesión en Azure mediante el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="386cb-127">After the import completes, you can test your newly installed and module by attempting to sign into Azure using the following command:</span></span>

```powershell
Login-AzureRMAccount
```

<span data-ttu-id="386cb-128">El comando anterior debe solicitarle que vaya a `https://aka.ms/devicelogin` y escriba el código proporcionado.</span><span class="sxs-lookup"><span data-stu-id="386cb-128">The above command should prompt you to go to `https://aka.ms/devicelogin` and enter the provided code.</span></span>

## <a name="available-cmdlets"></a><span data-ttu-id="386cb-129">Cmdlets disponibles</span><span class="sxs-lookup"><span data-stu-id="386cb-129">Available cmdlets</span></span>

<span data-ttu-id="386cb-130">Los módulos de Azure PowerShell para .NET Standard se encuentran aún en desarrollo.</span><span class="sxs-lookup"><span data-stu-id="386cb-130">The Azure PowerShell modules for .NET Standard are still in development.</span></span> <span data-ttu-id="386cb-131">Estos módulos no proporcionan el conjunto completo de cmdlets que están disponibles para la versión de Windows de los módulos.</span><span class="sxs-lookup"><span data-stu-id="386cb-131">These modules do not provide the full set of cmdlets that are available for the Windows version of the modules.</span></span> <span data-ttu-id="386cb-132">Las siguientes funciones se implementan en los módulos de AzureRM.Netcore:</span><span class="sxs-lookup"><span data-stu-id="386cb-132">The following functions are implemented in AzureRM.Netcore modules:</span></span>

* <span data-ttu-id="386cb-133">Administración de cuentas</span><span class="sxs-lookup"><span data-stu-id="386cb-133">Account management</span></span>
  - <span data-ttu-id="386cb-134">Inicie sesión con la cuenta de Microsoft, la cuenta organizativa o la entidad de servicio mediante Microsoft Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="386cb-134">Login with Microsoft account, Organizational account, or Service Principal through Microsoft Azure Active Directory</span></span>
  - <span data-ttu-id="386cb-135">Guarde las credenciales en el disco con Save-AzureRmContext y cargue las credenciales guardadas mediante Import-AzureRmContext.</span><span class="sxs-lookup"><span data-stu-id="386cb-135">Save Credentials to disk with Save-AzureRmContext and load saved credentials using Import-AzureRmContext</span></span>
* <span data-ttu-id="386cb-136">Environment</span><span class="sxs-lookup"><span data-stu-id="386cb-136">Environment</span></span>
  - <span data-ttu-id="386cb-137">Obtenga los diferentes entornos de Microsoft Azure de uso inmediato.</span><span class="sxs-lookup"><span data-stu-id="386cb-137">Get the different out-of-box Microsoft Azure environments</span></span>
  - <span data-ttu-id="386cb-138">Agregue, defina o quite entornos personalizados (como los entornos Azure Stack o Windows Azure Pack)</span><span class="sxs-lookup"><span data-stu-id="386cb-138">Add/Set/Remove customized environments (like your Azure Stack or Windows Azure Pack environments)</span></span>
* <span data-ttu-id="386cb-139">Cmdlets del plano de administración para servicios de Azure que usan las interfaces de Resource Manager y Service Management.</span><span class="sxs-lookup"><span data-stu-id="386cb-139">Management plane cmdlets for Azure services using Resource Manager and Service Management interfaces.</span></span>
  - <span data-ttu-id="386cb-140">Máquina virtual</span><span class="sxs-lookup"><span data-stu-id="386cb-140">Virtual Machine</span></span>
  - <span data-ttu-id="386cb-141">App Service (Websites)</span><span class="sxs-lookup"><span data-stu-id="386cb-141">App Service (Websites)</span></span>
  - <span data-ttu-id="386cb-142">SQL Database</span><span class="sxs-lookup"><span data-stu-id="386cb-142">SQL Database</span></span>
  - <span data-ttu-id="386cb-143">Storage</span><span class="sxs-lookup"><span data-stu-id="386cb-143">Storage</span></span>
  - <span data-ttu-id="386cb-144">Red</span><span class="sxs-lookup"><span data-stu-id="386cb-144">Network</span></span>

## <a name="next-steps"></a><span data-ttu-id="386cb-145">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="386cb-145">Next Steps</span></span>

<span data-ttu-id="386cb-146">Para más información sobre el uso de Azure PowerShell, consulte el artículo [Introducción a Azure PowerShell](get-started-azureps.md).</span><span class="sxs-lookup"><span data-stu-id="386cb-146">For more information about using Azure PowerShell, see the [Get started with Azure PowerShell](get-started-azureps.md) article.</span></span>
