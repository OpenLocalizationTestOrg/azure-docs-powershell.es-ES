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
ms.openlocfilehash: 368404bcb5218814b4965bb1bcda1e2876441d2a
ms.sourcegitcommit: 226527be7cb647acfe2ea9ab151185053ab3c6db
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2017
---
# <span data-ttu-id="b1eaf-103">Otros métodos de instalación</span><span class="sxs-lookup"><span data-stu-id="b1eaf-103">Other installation methods</span></span>
<a id="other-installation-methods" class="xliff"></a>

<span data-ttu-id="b1eaf-104">Azure PowerShell tiene varios métodos de instalación.</span><span class="sxs-lookup"><span data-stu-id="b1eaf-104">Azure PowerShell has multiple installation methods.</span></span> <span data-ttu-id="b1eaf-105">El método preferido es usar PowerShellGet con la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b1eaf-105">Using PowerShellGet with the PowerShell Gallery is the preferred method.</span></span> <span data-ttu-id="b1eaf-106">Azure PowerShell puede instalarse mediante el Instalador de plataforma web (WPI) o con el archivo MSI disponible en [GitHub](https://github.com/Azure/azure-powershell/releases/latest).</span><span class="sxs-lookup"><span data-stu-id="b1eaf-106">Azure PowerShell can be installed using the Web Platform Installer (WebPI) or by using the MSI file available from [GitHub](https://github.com/Azure/azure-powershell/releases/latest).</span></span>

## <span data-ttu-id="b1eaf-107">Instalación mediante el Instalador de plataforma web</span><span class="sxs-lookup"><span data-stu-id="b1eaf-107">Install using the Web Platform Installer</span></span>
<a id="install-using-the-web-platform-installer" class="xliff"></a>

<span data-ttu-id="b1eaf-108">La instalación de la versión más reciente de Azure PowerShell desde WebPI es igual al de las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="b1eaf-108">Installing the latest Azure PowerShell from WebPI is the same as it was for previous versions.</span></span>
<span data-ttu-id="b1eaf-109">Descargue el [paquete WebPI de Azure PowerShell](http://aka.ms/webpi-azps) e inicie la instalación.</span><span class="sxs-lookup"><span data-stu-id="b1eaf-109">Download the [Azure PowerShell WebPI package](http://aka.ms/webpi-azps) and start the install.</span></span>

> [!NOTE]
> <span data-ttu-id="b1eaf-110">Si ha instalado previamente módulos de Azure de la Galería de PowerShell, el instalador los quita automáticamente.</span><span class="sxs-lookup"><span data-stu-id="b1eaf-110">If you have previously installed Azure modules from the PowerShell Gallery, the installer automatically removes them.</span></span> <span data-ttu-id="b1eaf-111">Esto simplifica el entorno al garantizar que solo se instala una versión de Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b1eaf-111">This simplifies your environment by ensuring that only one version of Azure PowerShell is installed.</span></span> <span data-ttu-id="b1eaf-112">Sin embargo, puede haber escenarios en los que haya que tener varias versiones instaladas al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="b1eaf-112">However, there are scenarios where you may need multiple versions installed at the same time.</span></span>
>
> <span data-ttu-id="b1eaf-113">Los módulos de la Galería de PowerShell instalan los módulos de `$env:ProgramFiles\WindowsPowerShell\Modules`.</span><span class="sxs-lookup"><span data-stu-id="b1eaf-113">PowerShell Gallery modules install modules in `$env:ProgramFiles\WindowsPowerShell\Modules`.</span></span> <span data-ttu-id="b1eaf-114">En cambio, el programa de instalación de WebPI instala los módulos de Azure en `$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\`.</span><span class="sxs-lookup"><span data-stu-id="b1eaf-114">In contrast, the WebPI installer installs the Azure modules in `$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\`.</span></span>
>
> <span data-ttu-id="b1eaf-115">Si se produce un error durante la instalación, puede quitar manualmente las carpetas de Azure* de su carpeta `$env:ProgramFiles\WindowsPowerShell\Modules` e intentar la instalación de nuevo.</span><span class="sxs-lookup"><span data-stu-id="b1eaf-115">If an error occurs during install, you can manually remove the Azure* folders in your `$env:ProgramFiles\WindowsPowerShell\Modules` folder, and try the installation again.</span></span>

<span data-ttu-id="b1eaf-116">Una vez completada la instalación, la configuración `$env:PSModulePath` debe incluir los directorios que contienen los cmdlets de Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b1eaf-116">Once the installation completes, your `$env:PSModulePath` setting should include the directories containing the Azure PowerShell cmdlets.</span></span> <span data-ttu-id="b1eaf-117">El comando siguiente puede utilizarse para comprobar que Azure PowerShell está instalado correctamente.</span><span class="sxs-lookup"><span data-stu-id="b1eaf-117">The following command can be used to verify that the Azure PowerShell is installed properly.</span></span>

```powershell
# To make sure the Azure PowerShell module is available after you install
Get-Module -ListAvailable Azure* | Select-Object Name, Version, Path
```

> [!NOTE]
> <span data-ttu-id="b1eaf-118">Existe un problema conocido que puede producirse cuando la instalación se realiza desde WebPI.</span><span class="sxs-lookup"><span data-stu-id="b1eaf-118">There is a known issue that can occur when installing from WebPI.</span></span> <span data-ttu-id="b1eaf-119">Si el equipo requiere un reinicio debido a actualizaciones del sistema u otras instalaciones, puede hacer que las actualizaciones de `$env:PSModulePath` no incluyan la ruta de acceso donde está instalado Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b1eaf-119">If your computer requires a restart due to system updates or other installations, it may cause updates to `$env:PSModulePath` to fail to include the path where Azure PowerShell is installed.</span></span>

<span data-ttu-id="b1eaf-120">Al intentar cargar o ejecutar cmdlets después de la instalación, puede recibir el mensaje de error siguiente:</span><span class="sxs-lookup"><span data-stu-id="b1eaf-120">When attempting to load or execute cmdlets after installation, you can receive the following error message:</span></span>

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

<span data-ttu-id="b1eaf-121">Este error puede corregirse si se reinicia el equipo o se importa el módulo mediante la ruta de acceso completa.</span><span class="sxs-lookup"><span data-stu-id="b1eaf-121">This error can be corrected by restarting the machine or importing the module using the fully qualified path.</span></span> <span data-ttu-id="b1eaf-122">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="b1eaf-122">For example:</span></span>

```powershell
Import-Module "$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\AzureRM.psd1"
```

## <span data-ttu-id="b1eaf-123">Instalación mediante el paquete MSI</span><span class="sxs-lookup"><span data-stu-id="b1eaf-123">Install using the MSI Package</span></span>
<a id="install-using-the-msi-package" class="xliff"></a>

<span data-ttu-id="b1eaf-124">Azure PowerShell puede instalarse con el archivo MSI disponible en [GitHub](https://github.com/Azure/azure-powershell/releases/latest).</span><span class="sxs-lookup"><span data-stu-id="b1eaf-124">Azure PowerShell can be installed using the MSI file available from [GitHub](https://github.com/Azure/azure-powershell/releases/latest).</span></span> <span data-ttu-id="b1eaf-125">Si ha instalado versiones anteriores de los módulos de Azure, el instalador las quita automáticamente.</span><span class="sxs-lookup"><span data-stu-id="b1eaf-125">If you have installed previous versions of Azure modules, the installer automatically removes them.</span></span> <span data-ttu-id="b1eaf-126">El paquete MSI instala los módulos en `$env:ProgramFiles\WindowsPowerShell\Modules`, pero no crea carpetas específicas de versión.</span><span class="sxs-lookup"><span data-stu-id="b1eaf-126">The MSI package installs modules in `$env:ProgramFiles\WindowsPowerShell\Modules` but does not create version-specific folders.</span></span>
