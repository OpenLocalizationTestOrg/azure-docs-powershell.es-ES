---
title: "<span data-ttu-id=\"bab5c-101\">Instalación y configuración del módulo Service Management de Azure PowerShell | Microsoft Docs</span><span class=\"sxs-lookup\"><span data-stu-id=\"bab5c-101\">Install and configure the Azure PowerShell Service Management module | Microsoft Docs</span></span>"
description: "<span data-ttu-id=\"bab5c-102\">Instalación y configuración de Azure PowerShell para usarlo por primera vez</span><span class=\"sxs-lookup\"><span data-stu-id=\"bab5c-102\">How to install and configure Azure PowerShell for first time use.</span></span>"
services: azure
author: sdwheeler
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/06/2017
ms.openlocfilehash: c51c727c1cb022eca59f819c7f24d8e058c677da
ms.sourcegitcommit: 226527be7cb647acfe2ea9ab151185053ab3c6db
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2017
---
# <span data-ttu-id="bab5c-103">Instalación del módulo Service Management de Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="bab5c-103">Installing the Azure PowerShell Service Management module</span></span>
<a id="installing-the-azure-powershell-service-management-module" class="xliff"></a>

<span data-ttu-id="bab5c-104">La instalación de Azure PowerShell desde la [Galería de PowerShell](https://www.powershellgallery.com/) es el método de instalación preferido.</span><span class="sxs-lookup"><span data-stu-id="bab5c-104">Installing Azure PowerShell from the [PowerShell Gallery](https://www.powershellgallery.com/) is the preferred method of installation.</span></span>

## <span data-ttu-id="bab5c-105">Paso 1: Instalación de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="bab5c-105">Step 1: Install PowerShellGet</span></span>
<a id="step-1-install-powershellget" class="xliff"></a>

<span data-ttu-id="bab5c-106">La instalación de elementos de la Galería de PowerShell requiere el módulo PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="bab5c-106">Installing items from the PowerShell Gallery requires the PowerShellGet module.</span></span> <span data-ttu-id="bab5c-107">Asegúrese de que tiene la versión adecuada de PowerShellGet y otros requisitos del sistema.</span><span class="sxs-lookup"><span data-stu-id="bab5c-107">Make sure you have the appropriate version of PowerShellGet and other system requirements.</span></span> <span data-ttu-id="bab5c-108">Ejecute el siguiente comando para ver si tiene instalado PowerShellGet en el sistema.</span><span class="sxs-lookup"><span data-stu-id="bab5c-108">Run the following command to see if you have PowerShellGet installed on your system.</span></span>

```powershell
Get-Module PowerShellGet -list | Select-Object Name,Version,Path
```

<span data-ttu-id="bab5c-109">Debería ver algo parecido a los siguiente:</span><span class="sxs-lookup"><span data-stu-id="bab5c-109">You should see something similar to the following output:</span></span>

```
Name          Version Path
----          ------- ----
PowerShellGet 1.0.0.1 C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PowerShellGet.psd1
```

<span data-ttu-id="bab5c-110">Si no tiene instalado PowerShellGet, consulte la sección [Cómo obtener PowerShellGet](install-azurerm-ps.md#how-to-get-powershellget).</span><span class="sxs-lookup"><span data-stu-id="bab5c-110">If you do not have PowerShellGet installed, see the [How to get PowerShellGet](install-azurerm-ps.md#how-to-get-powershellget).</span></span>

## <span data-ttu-id="bab5c-111">Paso 2: Instalación de Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="bab5c-111">Step 2: Install Azure PowerShell</span></span>
<a id="step-2-install-azure-powershell" class="xliff"></a>

<span data-ttu-id="bab5c-112">Ejecute el siguiente comando desde la consola de Windows PowerShell como administrador:</span><span class="sxs-lookup"><span data-stu-id="bab5c-112">Run the following command from the Windows PowerShell console running as Administrator:</span></span>

```powershell
Install-Module Azure
```

<span data-ttu-id="bab5c-113">El módulo de Azure es un módulo consolidado para los cmdlets de Azure Resource Manager.</span><span class="sxs-lookup"><span data-stu-id="bab5c-113">The Azure module is a rollup module for the Azure Resource Manager cmdlets.</span></span> <span data-ttu-id="bab5c-114">Cuando se instala el módulo de AzureRM, los restantes módulos de Azure que no se hayan instalado anteriormente se descargarán de la Galería de PowerShell y se instalarán.</span><span class="sxs-lookup"><span data-stu-id="bab5c-114">When you install the AzureRM module, any other Azure modules that have not previously been installed will be downloaded and installed from the PowerShell Gallery.</span></span>

<span data-ttu-id="bab5c-115">El módulo Azure Service Management comparte dependencias con los módulos de Resource Manager de Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bab5c-115">The Azure Service Management module shares dependencies with the Azure PowerShell Resource Manager modules.</span></span> <span data-ttu-id="bab5c-116">Si ha instalado los módulos de Resource Manager de Azure PowerShell, será preciso que agregue el parámetro `-AllowClobber` al comando de instalación,</span><span class="sxs-lookup"><span data-stu-id="bab5c-116">If you have installed the Azure PowerShell Resource Manager modules, you will need to add the `-AllowClobber` parameter to the install command.</span></span> <span data-ttu-id="bab5c-117">ya que ello permite que se actualicen las dependencias compartidas existentes.</span><span class="sxs-lookup"><span data-stu-id="bab5c-117">This allows this existing shared dependencies to be updated.</span></span> <span data-ttu-id="bab5c-118">Sin este parámetro, no se puede realizar la instalación del módulo.</span><span class="sxs-lookup"><span data-stu-id="bab5c-118">Without this parameter, installation of the module fails.</span></span>

```powershell
Install-Module Azure -AllowClobber
```

<span data-ttu-id="bab5c-119">Después de instalar el módulo, para importarlo debe ejecutar el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="bab5c-119">After you install this module, you can import the module by running the following command:</span></span>

```powershell
Import-Module Azure
```

## <span data-ttu-id="bab5c-120">Uso de los cmdlets</span><span class="sxs-lookup"><span data-stu-id="bab5c-120">To use the cmdlets</span></span>
<a id="to-use-the-cmdlets" class="xliff"></a>

<span data-ttu-id="bab5c-121">Para empezar a trabajar con los cmdlets de Azure Service Management, antes debe iniciar sesión en su cuenta de Azure.</span><span class="sxs-lookup"><span data-stu-id="bab5c-121">To start working with the Azure Service Management cmdlets, first log on to your Azure account.</span></span> <span data-ttu-id="bab5c-122">Para ello, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="bab5c-122">To log on to your account, run the following command:</span></span>

```powershell
Add-AzureAccount
```

<span data-ttu-id="bab5c-123">Tras iniciar sesión en Azure, Azure PowerShell crea un contexto para la sesión determinada.</span><span class="sxs-lookup"><span data-stu-id="bab5c-123">After logging into Azure, Azure PowerShell creates a context for the given session.</span></span> <span data-ttu-id="bab5c-124">Dicho contexto contiene el entorno, la cuenta, el inquilino y la suscripción de Azure PowerShell que se utilizarán para todos los cmdlets de dicha sesión.</span><span class="sxs-lookup"><span data-stu-id="bab5c-124">That context contains the Azure PowerShell environment, account, tenant, and subscription that will be used for all cmdlets within that session.</span></span> <span data-ttu-id="bab5c-125">Ya está listo para usar los siguientes módulos.</span><span class="sxs-lookup"><span data-stu-id="bab5c-125">Now you are ready to use the modules below.</span></span>

## <span data-ttu-id="bab5c-126">Cmdlets de Azure Service Management</span><span class="sxs-lookup"><span data-stu-id="bab5c-126">Azure Service Management cmdlets</span></span>
<a id="azure-service-management-cmdlets" class="xliff"></a>

<span data-ttu-id="bab5c-127">Los módulos de Azure PowerShell se actualizan con frecuencia.</span><span class="sxs-lookup"><span data-stu-id="bab5c-127">Azure PowerShell modules are updated frequently.</span></span> <span data-ttu-id="bab5c-128">Si observa que la ayuda en línea del cmdlet incluye cmdlets o parámetros que no están en el módulo, descargue e instale la versión más reciente del mismo.</span><span class="sxs-lookup"><span data-stu-id="bab5c-128">If you notice that the online cmdlet help includes cmdlets or parameters that are not in your module, download and install the latest version of the module.</span></span> <span data-ttu-id="bab5c-129">Para buscar la versión de un módulo, escriba: `(Get-Module Azure).Version`.</span><span class="sxs-lookup"><span data-stu-id="bab5c-129">To find the version of your module, type: `(Get-Module Azure).Version`.</span></span>

<span data-ttu-id="bab5c-130">Para ver scripts de ejemplo que pueden ayudarle a automatizar algunas de las tareas comunes de Azure, consulte el [Centro de scripts de Microsoft Azure](http://www.windowsazure.com/documentation/scripts/).</span><span class="sxs-lookup"><span data-stu-id="bab5c-130">For sample scripts that can help you automate some of the common tasks in Azure, see the [Windows Azure Script Center](http://www.windowsazure.com/documentation/scripts/).</span></span>

<span data-ttu-id="bab5c-131">Para obtener información general acerca de cómo instalar, aprendizaje, usar y personalizar Windows PowerShell, consulte [Scripting con Windows PowerShell](http://go.microsoft.com/fwlink/p/?linkid=320210) (Scripting con Windows PowerShell).</span><span class="sxs-lookup"><span data-stu-id="bab5c-131">For general information about installing, learning, using, and customizing Windows PowerShell, see [Scripting with Windows PowerShell](http://go.microsoft.com/fwlink/p/?linkid=320210).</span></span>
