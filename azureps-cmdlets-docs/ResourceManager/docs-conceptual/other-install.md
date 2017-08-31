---
title: Otras maneras de instalar Azure PowerShell | Microsoft Docs
description: "Cómo instalar Azure PowerShell con el paquete MSI o el Instalador de plataforma web."
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 05/15/2017
ms.openlocfilehash: 9cee582f74b7f3260c6ae167a8ac358d360ad8ab
ms.sourcegitcommit: 45587b5091293288e16cfae8ac412e0d42f8f450
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2017
---
# <a name="other-installation-methods"></a><span data-ttu-id="bf033-103">Otros métodos de instalación</span><span class="sxs-lookup"><span data-stu-id="bf033-103">Other installation methods</span></span>

<span data-ttu-id="bf033-104">Azure PowerShell tiene varios métodos de instalación.</span><span class="sxs-lookup"><span data-stu-id="bf033-104">Azure PowerShell has multiple installation methods.</span></span> <span data-ttu-id="bf033-105">El método preferido es usar PowerShellGet con la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bf033-105">Using PowerShellGet with the PowerShell Gallery is the preferred method.</span></span> <span data-ttu-id="bf033-106">Azure PowerShell puede instalarse mediante el Instalador de plataforma web (WPI) o con el archivo MSI disponible en [GitHub](https://github.com/Azure/azure-powershell/releases/latest).</span><span class="sxs-lookup"><span data-stu-id="bf033-106">Azure PowerShell can be installed using the Web Platform Installer (WebPI) or by using the MSI file available from [GitHub](https://github.com/Azure/azure-powershell/releases/latest).</span></span>

## <a name="docker"></a><span data-ttu-id="bf033-107">Docker</span><span class="sxs-lookup"><span data-stu-id="bf033-107">Docker</span></span>

<span data-ttu-id="bf033-108">Mantenemos una imagen de Docker preconfigurada con Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bf033-108">We maintain a Docker image preconfigured with Azure PowerShell.</span></span>

<span data-ttu-id="bf033-109">Ejecute el contenedor con `docker run`.</span><span class="sxs-lookup"><span data-stu-id="bf033-109">Run the container with `docker run`.</span></span>

```powershell
docker run azuresdk/azure-powershell
```

<span data-ttu-id="bf033-110">Además, mantenemos un subconjunto de cmdlets como un contenedor de PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="bf033-110">In addition, we maintain a subset of cmdlets as a PowerShell Core container.</span></span>

<span data-ttu-id="bf033-111">Para Mac/Linux, use la imagen `latest`.</span><span class="sxs-lookup"><span data-stu-id="bf033-111">For Mac/Linux, use the `latest` image.</span></span>

```bash
docker run azuresdk/azure-powershell-core:latest
```

<span data-ttu-id="bf033-112">Para Windows, use la imagen `nanoserver`.</span><span class="sxs-lookup"><span data-stu-id="bf033-112">For Windows, use the `nanoserver` image.</span></span>

```powershell
docker run azuresdk/azure-powershell-core:nanoserver
```

<span data-ttu-id="bf033-113">Azure PowerShell se instala en la imagen a través de `Install-Module` desde la [Galería de PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="bf033-113">Azure PowerShell is installed on the image via `Install-Module` from the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>

## <a name="install-using-the-web-platform-installer"></a><span data-ttu-id="bf033-114">Instalación mediante el Instalador de plataforma web</span><span class="sxs-lookup"><span data-stu-id="bf033-114">Install using the Web Platform Installer</span></span>

<span data-ttu-id="bf033-115">La instalación de la versión más reciente de Azure PowerShell desde WebPI es igual al de las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="bf033-115">Installing the latest Azure PowerShell from WebPI is the same as it was for previous versions.</span></span>
<span data-ttu-id="bf033-116">Descargue el [paquete WebPI de Azure PowerShell](http://aka.ms/webpi-azps) e inicie la instalación.</span><span class="sxs-lookup"><span data-stu-id="bf033-116">Download the [Azure PowerShell WebPI package](http://aka.ms/webpi-azps) and start the install.</span></span>

> [!NOTE]
> <span data-ttu-id="bf033-117">Si ha instalado previamente módulos de Azure de la Galería de PowerShell, el instalador los quita automáticamente.</span><span class="sxs-lookup"><span data-stu-id="bf033-117">If you have previously installed Azure modules from the PowerShell Gallery, the installer automatically removes them.</span></span> <span data-ttu-id="bf033-118">Esto simplifica el entorno al garantizar que solo se instala una versión de Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bf033-118">This simplifies your environment by ensuring that only one version of Azure PowerShell is installed.</span></span> <span data-ttu-id="bf033-119">Sin embargo, puede haber escenarios en los que haya que tener varias versiones instaladas al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="bf033-119">However, there are scenarios where you may need multiple versions installed at the same time.</span></span>
>
> <span data-ttu-id="bf033-120">Los módulos de la Galería de PowerShell instalan los módulos de `$env:ProgramFiles\WindowsPowerShell\Modules`.</span><span class="sxs-lookup"><span data-stu-id="bf033-120">PowerShell Gallery modules install modules in `$env:ProgramFiles\WindowsPowerShell\Modules`.</span></span> <span data-ttu-id="bf033-121">En cambio, el programa de instalación de WebPI instala los módulos de Azure en `$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\`.</span><span class="sxs-lookup"><span data-stu-id="bf033-121">In contrast, the WebPI installer installs the Azure modules in `$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\`.</span></span>
>
> <span data-ttu-id="bf033-122">Si se produce un error durante la instalación, puede quitar manualmente las carpetas de Azure* de su carpeta `$env:ProgramFiles\WindowsPowerShell\Modules` e intentar la instalación de nuevo.</span><span class="sxs-lookup"><span data-stu-id="bf033-122">If an error occurs during install, you can manually remove the Azure* folders in your `$env:ProgramFiles\WindowsPowerShell\Modules` folder, and try the installation again.</span></span>

<span data-ttu-id="bf033-123">Una vez completada la instalación, la configuración `$env:PSModulePath` debe incluir los directorios que contienen los cmdlets de Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bf033-123">Once the installation completes, your `$env:PSModulePath` setting should include the directories containing the Azure PowerShell cmdlets.</span></span> <span data-ttu-id="bf033-124">El comando siguiente puede utilizarse para comprobar que Azure PowerShell está instalado correctamente.</span><span class="sxs-lookup"><span data-stu-id="bf033-124">The following command can be used to verify that the Azure PowerShell is installed properly.</span></span>

```powershell
# To make sure the Azure PowerShell module is available after you install
Get-Module -ListAvailable Azure* | Select-Object Name, Version, Path
```

> [!NOTE]
> <span data-ttu-id="bf033-125">Existe un problema conocido que puede producirse cuando la instalación se realiza desde WebPI.</span><span class="sxs-lookup"><span data-stu-id="bf033-125">There is a known issue that can occur when installing from WebPI.</span></span> <span data-ttu-id="bf033-126">Si el equipo requiere un reinicio debido a actualizaciones del sistema u otras instalaciones, puede hacer que las actualizaciones de `$env:PSModulePath` no incluyan la ruta de acceso donde está instalado Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bf033-126">If your computer requires a restart due to system updates or other installations, it may cause updates to `$env:PSModulePath` to fail to include the path where Azure PowerShell is installed.</span></span>

<span data-ttu-id="bf033-127">Al intentar cargar o ejecutar cmdlets después de la instalación, puede recibir el mensaje de error siguiente:</span><span class="sxs-lookup"><span data-stu-id="bf033-127">When attempting to load or execute cmdlets after installation, you can receive the following error message:</span></span>

```
PS C:\> Login-AzureRmAccount
Login-AzureRmAccount : The term 'Login-AzureRmAccount' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or if a path was
included, verify that the path is correct and try again.
At line:1 char:1
+ Login-AzureRmAccount
+ ~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Login-AzureRmAccount:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

<span data-ttu-id="bf033-128">Este error puede corregirse si se reinicia el equipo o se importa el módulo mediante la ruta de acceso completa.</span><span class="sxs-lookup"><span data-stu-id="bf033-128">This error can be corrected by restarting the machine or importing the module using the fully qualified path.</span></span> <span data-ttu-id="bf033-129">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="bf033-129">For example:</span></span>

```powershell
Import-Module "$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\AzureRM.psd1"
```

## <a name="install-using-the-msi-package"></a><span data-ttu-id="bf033-130">Instalación mediante el paquete MSI</span><span class="sxs-lookup"><span data-stu-id="bf033-130">Install using the MSI Package</span></span>

<span data-ttu-id="bf033-131">Azure PowerShell puede instalarse con el archivo MSI disponible en [GitHub](https://github.com/Azure/azure-powershell/releases/latest).</span><span class="sxs-lookup"><span data-stu-id="bf033-131">Azure PowerShell can be installed using the MSI file available from [GitHub](https://github.com/Azure/azure-powershell/releases/latest).</span></span> <span data-ttu-id="bf033-132">Si ha instalado versiones anteriores de los módulos de Azure, el instalador las quita automáticamente.</span><span class="sxs-lookup"><span data-stu-id="bf033-132">If you have installed previous versions of Azure modules, the installer automatically removes them.</span></span> <span data-ttu-id="bf033-133">El paquete MSI instala los módulos en `$env:ProgramFiles\WindowsPowerShell\Modules`, pero no crea carpetas específicas de versión.</span><span class="sxs-lookup"><span data-stu-id="bf033-133">The MSI package installs modules in `$env:ProgramFiles\WindowsPowerShell\Modules` but does not create version-specific folders.</span></span>
