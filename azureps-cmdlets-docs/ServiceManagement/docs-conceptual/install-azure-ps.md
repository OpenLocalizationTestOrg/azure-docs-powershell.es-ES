---
title: "Instalación y configuración del módulo Service Management de Azure PowerShell | Microsoft Docs"
description: "Instalación y configuración de Azure PowerShell para usarlo por primera vez"
services: azure
author: sdwheeler
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/06/2017
ms.openlocfilehash: 164af369d49e3044e5409c28d8b6145ebc067313
ms.sourcegitcommit: 020066d68d4ab68da162a4ae0cb4e239241f950f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2017
---
# <a name="installing-the-azure-powershell-service-management-module"></a><span data-ttu-id="8826e-103">Instalación del módulo Service Management de Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="8826e-103">Installing the Azure PowerShell Service Management module</span></span>

<span data-ttu-id="8826e-104">La instalación de Azure PowerShell desde la [Galería de PowerShell](https://www.powershellgallery.com/) es el método de instalación preferido.</span><span class="sxs-lookup"><span data-stu-id="8826e-104">Installing Azure PowerShell from the [PowerShell Gallery](https://www.powershellgallery.com/) is the preferred method of installation.</span></span>

## <a name="step-1-install-powershellget"></a><span data-ttu-id="8826e-105">Paso 1: Instalación de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="8826e-105">Step 1: Install PowerShellGet</span></span>

<span data-ttu-id="8826e-106">La instalación de elementos de la Galería de PowerShell requiere el módulo PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="8826e-106">Installing items from the PowerShell Gallery requires the PowerShellGet module.</span></span> <span data-ttu-id="8826e-107">Asegúrese de que tiene la versión adecuada de PowerShellGet y otros requisitos del sistema.</span><span class="sxs-lookup"><span data-stu-id="8826e-107">Make sure you have the appropriate version of PowerShellGet and other system requirements.</span></span> <span data-ttu-id="8826e-108">Ejecute el siguiente comando para ver si tiene instalado PowerShellGet en el sistema.</span><span class="sxs-lookup"><span data-stu-id="8826e-108">Run the following command to see if you have PowerShellGet installed on your system.</span></span>

```powershell
Get-Module PowerShellGet -list | Select-Object Name,Version,Path
```

<span data-ttu-id="8826e-109">Debería ver algo parecido a los siguiente:</span><span class="sxs-lookup"><span data-stu-id="8826e-109">You should see something similar to the following output:</span></span>

```
Name          Version Path
----          ------- ----
PowerShellGet 1.0.0.1 C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PowerShellGet.psd1
```

<span data-ttu-id="8826e-110">Si no tiene instalado PowerShellGet, consulte la sección [Cómo obtener PowerShellGet](#how-to-get-powershellget).</span><span class="sxs-lookup"><span data-stu-id="8826e-110">If you do not have PowerShellGet installed, see the [How to get PowerShellGet](#how-to-get-powershellget).</span></span>

## <a name="step-2-install-azure-powershell"></a><span data-ttu-id="8826e-111">Paso 2: Instalación de Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="8826e-111">Step 2: Install Azure PowerShell</span></span>

<span data-ttu-id="8826e-112">Ejecute el siguiente comando desde la consola de Windows PowerShell como administrador:</span><span class="sxs-lookup"><span data-stu-id="8826e-112">Run the following command from the Windows PowerShell console running as Administrator:</span></span>

```powershell
Install-Module Azure
```

<span data-ttu-id="8826e-113">El módulo de Azure es un módulo consolidado para los cmdlets de Azure Resource Manager.</span><span class="sxs-lookup"><span data-stu-id="8826e-113">The Azure module is a rollup module for the Azure Resource Manager cmdlets.</span></span> <span data-ttu-id="8826e-114">Cuando se instala el módulo de AzureRM, los restantes módulos de Azure que no se hayan instalado anteriormente se descargarán de la Galería de PowerShell y se instalarán.</span><span class="sxs-lookup"><span data-stu-id="8826e-114">When you install the AzureRM module, any other Azure modules that have not previously been installed will be downloaded and installed from the PowerShell Gallery.</span></span>

<span data-ttu-id="8826e-115">El módulo Azure Service Management comparte dependencias con los módulos de Resource Manager de Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8826e-115">The Azure Service Management module shares dependencies with the Azure PowerShell Resource Manager modules.</span></span> <span data-ttu-id="8826e-116">Si ha instalado los módulos de Resource Manager de Azure PowerShell, será preciso que agregue el parámetro `-AllowClobber` al comando de instalación,</span><span class="sxs-lookup"><span data-stu-id="8826e-116">If you have installed the Azure PowerShell Resource Manager modules, you will need to add the `-AllowClobber` parameter to the install command.</span></span> <span data-ttu-id="8826e-117">ya que ello permite que se actualicen las dependencias compartidas existentes.</span><span class="sxs-lookup"><span data-stu-id="8826e-117">This allows this existing shared dependencies to be updated.</span></span> <span data-ttu-id="8826e-118">Sin este parámetro, no se puede realizar la instalación del módulo.</span><span class="sxs-lookup"><span data-stu-id="8826e-118">Without this parameter, installation of the module fails.</span></span>

```powershell
Install-Module Azure -AllowClobber
```

<span data-ttu-id="8826e-119">Después de instalar el módulo, para importarlo debe ejecutar el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="8826e-119">After you install this module, you can import the module by running the following command:</span></span>

```powershell
Import-Module Azure
```

## <a name="to-use-the-cmdlets"></a><span data-ttu-id="8826e-120">Uso de los cmdlets</span><span class="sxs-lookup"><span data-stu-id="8826e-120">To use the cmdlets</span></span>

<span data-ttu-id="8826e-121">Para empezar a trabajar con los cmdlets de Azure Service Management, antes debe iniciar sesión en su cuenta de Azure.</span><span class="sxs-lookup"><span data-stu-id="8826e-121">To start working with the Azure Service Management cmdlets, first log on to your Azure account.</span></span> <span data-ttu-id="8826e-122">Para ello, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="8826e-122">To log on to your account, run the following command:</span></span>

```powershell
Add-AzureAccount
```

<span data-ttu-id="8826e-123">Tras iniciar sesión en Azure, Azure PowerShell crea un contexto para la sesión determinada.</span><span class="sxs-lookup"><span data-stu-id="8826e-123">After logging into Azure, Azure PowerShell creates a context for the given session.</span></span> <span data-ttu-id="8826e-124">Dicho contexto contiene el entorno, la cuenta, el inquilino y la suscripción de Azure PowerShell que se utilizarán para todos los cmdlets de dicha sesión.</span><span class="sxs-lookup"><span data-stu-id="8826e-124">That context contains the Azure PowerShell environment, account, tenant, and subscription that will be used for all cmdlets within that session.</span></span> <span data-ttu-id="8826e-125">Ya está listo para usar los siguientes módulos.</span><span class="sxs-lookup"><span data-stu-id="8826e-125">Now you are ready to use the modules below.</span></span>

## <a name="azure-service-management-cmdlets"></a><span data-ttu-id="8826e-126">Cmdlets de Azure Service Management</span><span class="sxs-lookup"><span data-stu-id="8826e-126">Azure Service Management cmdlets</span></span>

<span data-ttu-id="8826e-127">Los módulos de Azure PowerShell se actualizan con frecuencia.</span><span class="sxs-lookup"><span data-stu-id="8826e-127">Azure PowerShell modules are updated frequently.</span></span> <span data-ttu-id="8826e-128">Si observa que la ayuda en línea del cmdlet incluye cmdlets o parámetros que no están en el módulo, descargue e instale la versión más reciente del mismo.</span><span class="sxs-lookup"><span data-stu-id="8826e-128">If you notice that the online cmdlet help includes cmdlets or parameters that are not in your module, download and install the latest version of the module.</span></span> <span data-ttu-id="8826e-129">Para buscar la versión de un módulo, escriba: `(Get-Module Azure).Version`.</span><span class="sxs-lookup"><span data-stu-id="8826e-129">To find the version of your module, type: `(Get-Module Azure).Version`.</span></span>

<span data-ttu-id="8826e-130">Para ver scripts de ejemplo que pueden ayudarle a automatizar algunas de las tareas comunes de Azure, consulte el [Centro de scripts de Microsoft Azure](http://www.windowsazure.com/documentation/scripts/).</span><span class="sxs-lookup"><span data-stu-id="8826e-130">For sample scripts that can help you automate some of the common tasks in Azure, see the [Windows Azure Script Center](http://www.windowsazure.com/documentation/scripts/).</span></span>

<span data-ttu-id="8826e-131">Para obtener información general acerca de cómo instalar, aprendizaje, usar y personalizar Windows PowerShell, consulte [Scripting con Windows PowerShell](http://go.microsoft.com/fwlink/p/?linkid=320210) (Scripting con Windows PowerShell).</span><span class="sxs-lookup"><span data-stu-id="8826e-131">For general information about installing, learning, using, and customizing Windows PowerShell, see [Scripting with Windows PowerShell](http://go.microsoft.com/fwlink/p/?linkid=320210).</span></span>

### <a name="how-to-get-powershellget"></a><span data-ttu-id="8826e-132">Cómo obtener PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="8826e-132">How to get PowerShellGet</span></span>

|<span data-ttu-id="8826e-133">Versión del SO.</span><span class="sxs-lookup"><span data-stu-id="8826e-133">OS Version</span></span>|<span data-ttu-id="8826e-134">Instrucciones de instalación</span><span class="sxs-lookup"><span data-stu-id="8826e-134">Install instructions</span></span>|
|---|---|
|<span data-ttu-id="8826e-135">Tengo Windows 10 o Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="8826e-135">I have Windows 10 or Windows Server 2016</span></span>|<span data-ttu-id="8826e-136">Integrado en Windows Management Framework (WMF) 5.0 incluido en el sistema operativo</span><span class="sxs-lookup"><span data-stu-id="8826e-136">Built into Windows Management Framework (WMF) 5.0 included in the OS</span></span>|
|<span data-ttu-id="8826e-137">Quiero actualizar a PowerShell 5</span><span class="sxs-lookup"><span data-stu-id="8826e-137">I want to upgrade to PowerShell 5</span></span>|[<span data-ttu-id="8826e-138">Instalar la versión más reciente de WMF</span><span class="sxs-lookup"><span data-stu-id="8826e-138">Install the latest version of WMF</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)|
|<span data-ttu-id="8826e-139">Uso una versión de Windows con PowerShell 3 o PowerShell 4</span><span class="sxs-lookup"><span data-stu-id="8826e-139">I am running on a version of Windows with PowerShell 3 or PowerShell 4</span></span>|[<span data-ttu-id="8826e-140">Obtener los módulos PackageManagement</span><span class="sxs-lookup"><span data-stu-id="8826e-140">Get the PackageManagement modules</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217)|

<a id="helpmechoose"></a>
### <a name="checking-the-version-of-azure-powershell"></a><span data-ttu-id="8826e-141">Comprobación de la versión de Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="8826e-141">Checking the version of Azure PowerShell</span></span>

<span data-ttu-id="8826e-142">Si bien se recomienda que actualice a la versión más reciente lo antes posible, se admiten varias versiones de Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8826e-142">Although we encourage you to upgrade to the latest version as early as possible, several versions of Azure PowerShell are support.</span></span> <span data-ttu-id="8826e-143">Para determinar la versión de Azure PowerShell instalada, ejecute `Get-Module AzureRM` desde la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="8826e-143">To determine the version of Azure PowerShell you have installed, run `Get-Module AzureRM` from your command line.</span></span>

```powershell
Get-Module AzureRM -list | Select-Object Name,Version,Path
```
