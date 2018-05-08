---
title: "Instalación y configuración de Azure PowerShell | Microsoft Docs"
description: "Instalación y configuración de Azure PowerShell para usarlo por primera vez."
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 05/17/2017
ms.openlocfilehash: 0c1500a8748a3aa4546c6ce1e8d16a635b056edb
ms.sourcegitcommit: b256bf48e15ee98865de0fae50e7b81878b03a54
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/03/2017
---
# <a name="install-and-configure-azure-powershell"></a><span data-ttu-id="8f445-103">Instale y configure Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8f445-103">Install and configure Azure PowerShell</span></span>

<span data-ttu-id="8f445-104">La instalación de Azure PowerShell desde la Galería de PowerShell es el método de instalación preferido.</span><span class="sxs-lookup"><span data-stu-id="8f445-104">Installing Azure PowerShell from the PowerShell Gallery is the preferred method of installation.</span></span>

## <a name="step-1-install-powershellget"></a><span data-ttu-id="8f445-105">Paso 1: Instalación de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="8f445-105">Step 1: Install PowerShellGet</span></span>

<span data-ttu-id="8f445-106">La instalación de elementos de la Galería de PowerShell requiere el módulo PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="8f445-106">Installing items from the PowerShell Gallery requires the PowerShellGet module.</span></span> <span data-ttu-id="8f445-107">Asegúrese de que tiene la versión adecuada de PowerShellGet y otros requisitos del sistema.</span><span class="sxs-lookup"><span data-stu-id="8f445-107">Make sure you have the appropriate version of PowerShellGet and other system requirements.</span></span> <span data-ttu-id="8f445-108">Ejecute el siguiente comando para ver si tiene instalado PowerShellGet en el sistema.</span><span class="sxs-lookup"><span data-stu-id="8f445-108">Run the following command to see if you have PowerShellGet installed on your system.</span></span>

```powershell
Get-Module PowerShellGet -list | Select-Object Name,Version,Path
```

<span data-ttu-id="8f445-109">Debería ver algo parecido a los siguiente:</span><span class="sxs-lookup"><span data-stu-id="8f445-109">You should see something similar to the following output:</span></span>

```
Name          Version Path
----          ------- ----
PowerShellGet 1.0.0.1 C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PowerShellGet.psd1
```

<span data-ttu-id="8f445-110">Si no tiene instalado PowerShellGet, consulte la sección [Cómo obtener PowerShellGet](#how-to-get-powershellget) de este artículo.</span><span class="sxs-lookup"><span data-stu-id="8f445-110">If you do not have PowerShellGet installed, see the [How to get PowerShellGet](#how-to-get-powershellget) section of this article.</span></span>

> [!NOTE]
> <span data-ttu-id="8f445-111">El uso de PowerShellGet requiere una directiva de ejecución que permita ejecutar scripts.</span><span class="sxs-lookup"><span data-stu-id="8f445-111">Using PowerShellGet requires an Execution Policy that allows you to run scripts.</span></span> <span data-ttu-id="8f445-112">Para más información sobre la directiva de ejecución de PowerShell, consulte [About Execution Policies](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_execution_policies) (Acerca de las directivas de ejecución).</span><span class="sxs-lookup"><span data-stu-id="8f445-112">For more information about PowerShell's Execution Policy, see [About Execution Policies](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_execution_policies).</span></span>

## <a name="step-2-install-azure-powershell"></a><span data-ttu-id="8f445-113">Paso 2: Instalación de Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="8f445-113">Step 2: Install Azure PowerShell</span></span>

<span data-ttu-id="8f445-114">La instalación de Azure PowerShell desde la Galería de PowerShell requiere privilegios elevados.</span><span class="sxs-lookup"><span data-stu-id="8f445-114">Installing Azure PowerShell from the PowerShell Gallery requires elevated privileges.</span></span> <span data-ttu-id="8f445-115">Ejecute el siguiente comando desde una sesión de PowerShell con privilegios elevados:</span><span class="sxs-lookup"><span data-stu-id="8f445-115">Run the following command from an elevated PowerShell session:</span></span>

```powershell
# Install the Azure Resource Manager modules from the PowerShell Gallery
Install-Module AzureRM
```

<span data-ttu-id="8f445-116">De forma predeterminada, la Galería de PowerShell no está configurada como un repositorio de confianza para PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="8f445-116">By default, the PowerShell gallery is not configured as a Trusted repository for PowerShellGet.</span></span> <span data-ttu-id="8f445-117">La primera vez que use PSGallery verá el siguiente mensaje:</span><span class="sxs-lookup"><span data-stu-id="8f445-117">The first time you use the PSGallery you see the following prompt:</span></span>

```
Untrusted repository

You are installing the modules from an untrusted repository. If you trust this repository, change
its InstallationPolicy value by running the Set-PSRepository cmdlet.

Are you sure you want to install the modules from 'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): Y
```

<span data-ttu-id="8f445-118">Responda "Sí" o "Sí a todo" para continuar con la instalación.</span><span class="sxs-lookup"><span data-stu-id="8f445-118">Answer 'Yes' or 'Yes to All' to continue with the installation.</span></span>

> [!NOTE]
> <span data-ttu-id="8f445-119">Si tiene una versión de NuGet anterior a la 2.8.5.201, se le pedirá que descargue e instale la versión más reciente de NuGet.</span><span class="sxs-lookup"><span data-stu-id="8f445-119">If you have a version older than 2.8.5.201 of NuGet, you are prompted to download and install the latest version of NuGet.</span></span>

<span data-ttu-id="8f445-120">AzureRM es un módulo consolidado para los cmdlets de Azure Resource Manager.</span><span class="sxs-lookup"><span data-stu-id="8f445-120">The AzureRM module is a rollup module for the Azure Resource Manager cmdlets.</span></span> <span data-ttu-id="8f445-121">Al instalar el módulo AzureRM, los módulos de Azure PowerShell que no se hayan instalado anteriormente se descargan de la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8f445-121">When you install the AzureRM module, any Azure PowerShell module not previously installed is downloaded and from the PowerShell Gallery.</span></span>

<span data-ttu-id="8f445-122">Si tiene instalada una versión anterior de Azure PowerShell, puede que reciba un error.</span><span class="sxs-lookup"><span data-stu-id="8f445-122">If you have a previous version of Azure PowerShell installed you may receive an error.</span></span> <span data-ttu-id="8f445-123">Para resolver este problema, consulte la sección [Actualización a una nueva versión de Azure PowerShell](#update-azps) de este artículo.</span><span class="sxs-lookup"><span data-stu-id="8f445-123">To resolve this issue, see the [Updating to a new version of Azure PowerShell](#update-azps) section of this article.</span></span>

## <a name="step-3-load-the-azurerm-module"></a><span data-ttu-id="8f445-124">Paso 3: Carga del módulo AzureRM</span><span class="sxs-lookup"><span data-stu-id="8f445-124">Step 3: Load the AzureRM module</span></span>
<span data-ttu-id="8f445-125">Una vez que se instala, debe cargarse en la sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8f445-125">Once the module is installed, you need to load the module into your PowerShell session.</span></span> <span data-ttu-id="8f445-126">Esta acción debe hacerse en una sesión de PowerShell normal (sin privilegios elevados).</span><span class="sxs-lookup"><span data-stu-id="8f445-126">You should do this in a normal (non-elevated) PowerShell session.</span></span> <span data-ttu-id="8f445-127">Los módulos se cargan mediante el cmdlet, `Import-Module` como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="8f445-127">Modules are loaded using the `Import-Module` cmdlet, as follows:</span></span>

```powershell
Import-Module AzureRM
```

## <a name="next-steps"></a><span data-ttu-id="8f445-128">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="8f445-128">Next Steps</span></span>

<span data-ttu-id="8f445-129">Para más información sobre el uso de Azure PowerShell, consulte los siguientes artículos:</span><span class="sxs-lookup"><span data-stu-id="8f445-129">For more information about using Azure PowerShell, see the following articles:</span></span>

* [<span data-ttu-id="8f445-130">Introducción a Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="8f445-130">Get started with Azure PowerShell</span></span>](get-started-azureps.md)

## <a name="frequently-asked-questions"></a><span data-ttu-id="8f445-131">Preguntas más frecuentes</span><span class="sxs-lookup"><span data-stu-id="8f445-131">Frequently asked questions</span></span>

### <a name="how-to-get-powershellget"></a><span data-ttu-id="8f445-132">Cómo obtener PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="8f445-132">How to get PowerShellGet</span></span>

|<span data-ttu-id="8f445-133">Versión del SO.</span><span class="sxs-lookup"><span data-stu-id="8f445-133">OS Version</span></span>|<span data-ttu-id="8f445-134">Instrucciones de instalación</span><span class="sxs-lookup"><span data-stu-id="8f445-134">Install instructions</span></span>|
|---|---|
|<span data-ttu-id="8f445-135">Tengo Windows 10 o Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="8f445-135">I have Windows 10 or Windows Server 2016</span></span>|<span data-ttu-id="8f445-136">Integrado en Windows Management Framework (WMF) 5.0 incluido en el sistema operativo</span><span class="sxs-lookup"><span data-stu-id="8f445-136">Built into Windows Management Framework (WMF) 5.0 included in the OS</span></span>|
|<span data-ttu-id="8f445-137">Quiero actualizar a PowerShell 5</span><span class="sxs-lookup"><span data-stu-id="8f445-137">I want to upgrade to PowerShell 5</span></span>|[<span data-ttu-id="8f445-138">Instalar la versión más reciente de WMF</span><span class="sxs-lookup"><span data-stu-id="8f445-138">Install the latest version of WMF</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)|
|<span data-ttu-id="8f445-139">Uso una versión de Windows con PowerShell 3 o PowerShell 4</span><span class="sxs-lookup"><span data-stu-id="8f445-139">I am running on a version of Windows with PowerShell 3 or PowerShell 4</span></span>|[<span data-ttu-id="8f445-140">Obtener los módulos PackageManagement</span><span class="sxs-lookup"><span data-stu-id="8f445-140">Get the PackageManagement modules</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217)|

<a id="helpmechoose"></a>
### <a name="checking-the-version-of-azure-powershell"></a><span data-ttu-id="8f445-141">Comprobación de la versión de Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="8f445-141">Checking the version of Azure PowerShell</span></span>

<span data-ttu-id="8f445-142">Si bien se recomienda que actualice a la versión más reciente lo antes posible, se admiten varias versiones de Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8f445-142">Although we encourage you to upgrade to the latest version as early as possible, several versions of Azure PowerShell are support.</span></span> <span data-ttu-id="8f445-143">Para determinar la versión de Azure PowerShell instalada, ejecute `Get-Module AzureRM` desde la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="8f445-143">To determine the version of Azure PowerShell you have installed, run `Get-Module AzureRM` from your command line.</span></span>

```powershell
Get-Module AzureRM -list | Select-Object Name,Version,Path
```

### <a name="support-for-classic-deployment-methods"></a><span data-ttu-id="8f445-144">Compatibilidad con métodos de implementación clásicos</span><span class="sxs-lookup"><span data-stu-id="8f445-144">Support for classic deployment methods</span></span>

<span data-ttu-id="8f445-145">Si dispone de implementaciones que usan el modelo de implementación clásica, puede instalar la versión de Service Management de Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8f445-145">If you have deployments that use the classic deployment model you can install the Service Management version of Azure PowerShell.</span></span> <span data-ttu-id="8f445-146">Para más información, consulte [Install the Azure PowerShell Service Management module](/powershell/azure/servicemanagement/install-azure-ps) (Instalación del módulo Service Management de Azure PowerShell).</span><span class="sxs-lookup"><span data-stu-id="8f445-146">For more information, see [Install the Azure PowerShell Service Management module](/powershell/azure/servicemanagement/install-azure-ps).</span></span> <span data-ttu-id="8f445-147">Los módulos Azure y AzureRM comparten dependencias comunes.</span><span class="sxs-lookup"><span data-stu-id="8f445-147">The Azure and AzureRM modules share common dependencies.</span></span> <span data-ttu-id="8f445-148">Si usa los módulos Azure y AzureRM, debe instalar la misma versión de cada paquete.</span><span class="sxs-lookup"><span data-stu-id="8f445-148">If you use both the Azure and AzureRM modules, you should install the same version of each package.</span></span>

### <a id="update-azps"></a><span data-ttu-id="8f445-149">Actualización a una nueva versión de Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="8f445-149">Updating to a new version of Azure PowerShell</span></span>

<span data-ttu-id="8f445-150">Si tiene instalada una versión anterior de Azure PowerShell que incluye el módulo Service Management, puede recibir el error siguiente:</span><span class="sxs-lookup"><span data-stu-id="8f445-150">If you have a previous version of Azure PowerShell installed that includes the Service Management module, you may receive the following error:</span></span>

```
PackageManagement\Install-Package : A command with name 'Get-AzureStorageContainerAcl' is already
available on this system. This module 'Azure.Storage' may override the existing commands. If you
still want to install this module 'Azure.Storage', use -AllowClobber parameter.

At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1772 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], Exception
    + FullyQualifiedErrorId : CommandAlreadyAvailable,Validate-ModuleCommandAlreadyAvailable,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage
```

<span data-ttu-id="8f445-151">Como indica el mensaje de error, debe usar el parámetro - AllowClobber para instalar el módulo.</span><span class="sxs-lookup"><span data-stu-id="8f445-151">As the error message states, you need to use the -AllowClobber parameter to install the module.</span></span> <span data-ttu-id="8f445-152">Use el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="8f445-152">Use the following command:</span></span>

```powershell
# Install the Azure Resource Manager modules from the PowerShell Gallery
Install-Module AzureRM -AllowClobber
```

<span data-ttu-id="8f445-153">Para más información, consulte el tema de ayuda de [Install-Module](https://msdn.microsoft.com/powershell/reference/5.1/PowerShellGet/install-module).</span><span class="sxs-lookup"><span data-stu-id="8f445-153">For more information, see the help topic for [Install-Module](https://msdn.microsoft.com/powershell/reference/5.1/PowerShellGet/install-module).</span></span>

### <a name="installing-module-versions-side-by-side"></a><span data-ttu-id="8f445-154">Instalación de versiones de módulo en paralelo</span><span class="sxs-lookup"><span data-stu-id="8f445-154">Installing module versions side by side</span></span>

<span data-ttu-id="8f445-155">El método de instalación PowerShellGet es el único método que admite la instalación de varias versiones.</span><span class="sxs-lookup"><span data-stu-id="8f445-155">The PowerShellGet method of installation is the only method that supports the installation of multiple versions.</span></span> <span data-ttu-id="8f445-156">Por ejemplo, puede tener scripts escritos con una versión anterior de Azure PowerShell que no tenga tiempo de actualizar o recursos para hacerlo.</span><span class="sxs-lookup"><span data-stu-id="8f445-156">For example, you may have scripts written using a previous version of Azure PowerShell that you don't have the time or resources to updated.</span></span> <span data-ttu-id="8f445-157">Los comandos siguientes muestran cómo instalar varias versiones de Azure PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8f445-157">The following commands illustrate how to install multiple versions of Azure PowerShell:</span></span>

```powershell
Install-Module -Name AzureRM -RequiredVersion 3.7.0
Install-Module -Name AzureRM -RequiredVersion 1.2.9
```

<span data-ttu-id="8f445-158">Solo una versión del módulo se puede cargar en una sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8f445-158">Only one version of the module can be loaded in a PowerShell session.</span></span> <span data-ttu-id="8f445-159">Debe abrir una nueva ventana de PowerShell y usar `Import-Module` para importar una versión específica de los cmdlets de AzureRM:</span><span class="sxs-lookup"><span data-stu-id="8f445-159">You must open a new PowerShell window and use `Import-Module` to import a specific version of the AzureRM cmdlets:</span></span>

```powershell
Import-Module AzureRM -RequiredVersion 1.2.9
```

> [!NOTE]
> <span data-ttu-id="8f445-160">La versión 2.1.0 y la versión 1.2.6 son las primeras versiones de módulos diseñadas para instalarse y usarse en paralelo.</span><span class="sxs-lookup"><span data-stu-id="8f445-160">Version 2.1.0 and version 1.2.6 are the first module versions designed to be installed and used side by side.</span></span> <span data-ttu-id="8f445-161">Al cargar una versión anterior de Azure PowerShell, se cargan versiones incompatibles del módulo **AzureRM.Profile**.</span><span class="sxs-lookup"><span data-stu-id="8f445-161">When loading an earlier version of the Azure PowerShell, incompatible versions of the **AzureRM.Profile** module are loaded.</span></span> <span data-ttu-id="8f445-162">Como resultado, cada vez que ejecuta un cmdlet se le pide que inicie sesión.</span><span class="sxs-lookup"><span data-stu-id="8f445-162">This results in the cmdlets prompting you to log in whenever you execute a cmdlet.</span></span>

### <a name="other-installation-methods"></a><span data-ttu-id="8f445-163">Otros métodos de instalación</span><span class="sxs-lookup"><span data-stu-id="8f445-163">Other installation methods</span></span>

<span data-ttu-id="8f445-164">Para más información sobre la instalación mediante el Instalador de plataforma web o el paquete MSI, consulte [Otros métodos de instalación](other-install.md)</span><span class="sxs-lookup"><span data-stu-id="8f445-164">For information about installing using the Web Platform Installer or the MSI Package, see [Other installation methods](other-install.md)</span></span>
