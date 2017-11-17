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
ms.date: 09/06/2017
ms.openlocfilehash: 73c099375cecc8abdd5d6179109513946e7e793b
ms.sourcegitcommit: b256bf48e15ee98865de0fae50e7b81878b03a54
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/03/2017
---
# <a name="other-installation-methods"></a><span data-ttu-id="7f25c-103">Otros métodos de instalación</span><span class="sxs-lookup"><span data-stu-id="7f25c-103">Other installation methods</span></span>

<span data-ttu-id="7f25c-104">Azure PowerShell tiene varios métodos de instalación.</span><span class="sxs-lookup"><span data-stu-id="7f25c-104">Azure PowerShell has multiple installation methods.</span></span> <span data-ttu-id="7f25c-105">El método preferido es usar PowerShellGet con la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7f25c-105">Using PowerShellGet with the PowerShell Gallery is the preferred method.</span></span> <span data-ttu-id="7f25c-106">Azure PowerShell se puede instalar en Windows mediante el Instalador de plataforma web (WebPI) o por medio del archivo MSI disponible en GitHub.</span><span class="sxs-lookup"><span data-stu-id="7f25c-106">Azure PowerShell can be installed on Windows using the Web Platform Installer (WebPI) or by using the MSI file available from GitHub.</span></span> <span data-ttu-id="7f25c-107">También se puede instalar en un contenedor de Docker.</span><span class="sxs-lookup"><span data-stu-id="7f25c-107">Azure PowerShell can also be installed in a Docker container.</span></span>

## <a name="install-on-windows-using-the-web-platform-installer"></a><span data-ttu-id="7f25c-108">Instalación en Windows mediante el Instalador de plataforma web</span><span class="sxs-lookup"><span data-stu-id="7f25c-108">Install on Windows using the Web Platform Installer</span></span>

<span data-ttu-id="7f25c-109">La instalación de la versión más reciente de Azure PowerShell desde WebPI es igual al de las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="7f25c-109">Installing the latest Azure PowerShell from WebPI is the same as it was for previous versions.</span></span>
<span data-ttu-id="7f25c-110">Descargue el [paquete WebPI de Azure PowerShell](http://aka.ms/webpi-azps) e inicie la instalación.</span><span class="sxs-lookup"><span data-stu-id="7f25c-110">Download the [Azure PowerShell WebPI package](http://aka.ms/webpi-azps) and start the install.</span></span>

> [!NOTE]
> <span data-ttu-id="7f25c-111">Si ha instalado previamente módulos de Azure de la Galería de PowerShell, el instalador los quita automáticamente.</span><span class="sxs-lookup"><span data-stu-id="7f25c-111">If you have previously installed Azure modules from the PowerShell Gallery, the installer automatically removes them.</span></span> <span data-ttu-id="7f25c-112">Esto simplifica el entorno al garantizar que solo se instala una versión de Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7f25c-112">This simplifies your environment by ensuring that only one version of Azure PowerShell is installed.</span></span> <span data-ttu-id="7f25c-113">Sin embargo, puede haber escenarios en los que haya que tener varias versiones instaladas al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="7f25c-113">However, there are scenarios where you may need multiple versions installed at the same time.</span></span>
>
> <span data-ttu-id="7f25c-114">Los módulos de la Galería de PowerShell instalan los módulos de `$env:ProgramFiles\WindowsPowerShell\Modules`.</span><span class="sxs-lookup"><span data-stu-id="7f25c-114">PowerShell Gallery modules install modules in `$env:ProgramFiles\WindowsPowerShell\Modules`.</span></span> <span data-ttu-id="7f25c-115">En cambio, el programa de instalación de WebPI instala los módulos de Azure en `$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\`.</span><span class="sxs-lookup"><span data-stu-id="7f25c-115">In contrast, the WebPI installer installs the Azure modules in `$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\`.</span></span>
>
> <span data-ttu-id="7f25c-116">Si se produce un error durante la instalación, puede quitar manualmente las carpetas de Azure* de su carpeta `$env:ProgramFiles\WindowsPowerShell\Modules` e intentar la instalación de nuevo.</span><span class="sxs-lookup"><span data-stu-id="7f25c-116">If an error occurs during install, you can manually remove the Azure* folders in your `$env:ProgramFiles\WindowsPowerShell\Modules` folder, and try the installation again.</span></span>

<span data-ttu-id="7f25c-117">Una vez completada la instalación, la configuración `$env:PSModulePath` debe incluir los directorios que contienen los cmdlets de Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7f25c-117">Once the installation completes, your `$env:PSModulePath` setting should include the directories containing the Azure PowerShell cmdlets.</span></span> <span data-ttu-id="7f25c-118">El comando siguiente puede utilizarse para comprobar que Azure PowerShell está instalado correctamente.</span><span class="sxs-lookup"><span data-stu-id="7f25c-118">The following command can be used to verify that the Azure PowerShell is installed properly.</span></span>

```powershell
# To make sure the Azure PowerShell module is available after you install
Get-Module -ListAvailable Azure* | Select-Object Name, Version, Path
```

> [!NOTE]
> <span data-ttu-id="7f25c-119">Existe un problema conocido que puede producirse cuando la instalación se realiza desde WebPI.</span><span class="sxs-lookup"><span data-stu-id="7f25c-119">There is a known issue that can occur when installing from WebPI.</span></span> <span data-ttu-id="7f25c-120">Si el equipo requiere un reinicio debido a actualizaciones del sistema u otras instalaciones, puede hacer que las actualizaciones de `$env:PSModulePath` no incluyan la ruta de acceso donde está instalado Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7f25c-120">If your computer requires a restart due to system updates or other installations, it may cause updates to `$env:PSModulePath` to fail to include the path where Azure PowerShell is installed.</span></span>

<span data-ttu-id="7f25c-121">Al intentar cargar o ejecutar cmdlets después de la instalación, puede recibir el mensaje de error siguiente:</span><span class="sxs-lookup"><span data-stu-id="7f25c-121">When attempting to load or execute cmdlets after installation, you can receive the following error message:</span></span>

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

<span data-ttu-id="7f25c-122">Este error puede corregirse si se reinicia el equipo o se importa el módulo mediante la ruta de acceso completa.</span><span class="sxs-lookup"><span data-stu-id="7f25c-122">This error can be corrected by restarting the machine or importing the module using the fully qualified path.</span></span> <span data-ttu-id="7f25c-123">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="7f25c-123">For example:</span></span>

```powershell
Import-Module "$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\AzureRM.psd1"
```

## <a name="install-on-windows-using-the-msi-package"></a><span data-ttu-id="7f25c-124">Instalación en Windows mediante el paquete MSI</span><span class="sxs-lookup"><span data-stu-id="7f25c-124">Install on Windows using the MSI Package</span></span>

<span data-ttu-id="7f25c-125">Azure PowerShell puede instalarse con el archivo MSI disponible en [GitHub](https://github.com/Azure/azure-powershell/releases/latest).</span><span class="sxs-lookup"><span data-stu-id="7f25c-125">Azure PowerShell can be installed using the MSI file available from [GitHub](https://github.com/Azure/azure-powershell/releases/latest).</span></span> <span data-ttu-id="7f25c-126">Si ha instalado versiones anteriores de los módulos de Azure, el instalador las quita automáticamente.</span><span class="sxs-lookup"><span data-stu-id="7f25c-126">If you have installed previous versions of Azure modules, the installer automatically removes them.</span></span> <span data-ttu-id="7f25c-127">El paquete MSI instala los módulos en `$env:ProgramFiles\WindowsPowerShell\Modules`, pero no crea carpetas específicas de versión.</span><span class="sxs-lookup"><span data-stu-id="7f25c-127">The MSI package installs modules in `$env:ProgramFiles\WindowsPowerShell\Modules` but does not create version-specific folders.</span></span>

## <a name="install-in-a-docker-container"></a><span data-ttu-id="7f25c-128">Instalación en un contenedor de Docker</span><span class="sxs-lookup"><span data-stu-id="7f25c-128">Install in a Docker container</span></span>

<span data-ttu-id="7f25c-129">Mantenemos una imagen de Docker preconfigurada con Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7f25c-129">We maintain a Docker image preconfigured with Azure PowerShell.</span></span>

<span data-ttu-id="7f25c-130">Ejecute el contenedor con `docker run`.</span><span class="sxs-lookup"><span data-stu-id="7f25c-130">Run the container with `docker run`.</span></span>

```powershell
docker run azuresdk/azure-powershell
```

<span data-ttu-id="7f25c-131">Además, mantenemos un subconjunto de cmdlets como un contenedor de PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="7f25c-131">In addition, we maintain a subset of cmdlets as a PowerShell Core container.</span></span>

<span data-ttu-id="7f25c-132">Para Mac/Linux, use la imagen `latest`.</span><span class="sxs-lookup"><span data-stu-id="7f25c-132">For Mac/Linux, use the `latest` image.</span></span>

```bash
docker run azuresdk/azure-powershell-core:latest
```

<span data-ttu-id="7f25c-133">Para Windows, use la imagen `nanoserver`.</span><span class="sxs-lookup"><span data-stu-id="7f25c-133">For Windows, use the `nanoserver` image.</span></span>

```powershell
docker run azuresdk/azure-powershell-core:nanoserver
```

<span data-ttu-id="7f25c-134">Azure PowerShell se instala en la imagen a través de `Install-Module` desde la [Galería de PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="7f25c-134">Azure PowerShell is installed on the image via `Install-Module` from the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>