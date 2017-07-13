---
title: Registro de cambios de Azure PowerShell | Microsoft Docs
description: "Es un historial de los cambios realizados en la versión más reciente de Azure PowerShell."
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.service: azure-powershell
ms.product: azure
ms.devlang: powershell
ms.topic: conceptual
ms.workload: 
ms.date: 05/18/2017
ms.openlocfilehash: 5fe7591855577e083aad5923aed37b18d0b2a40c
ms.sourcegitcommit: 226527be7cb647acfe2ea9ab151185053ab3c6db
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2017
---
# <span data-ttu-id="c60cd-103">Notas de la versión</span><span class="sxs-lookup"><span data-stu-id="c60cd-103">Release notes</span></span>
<a id="release-notes" class="xliff"></a>

<span data-ttu-id="c60cd-104">Esta es una lista de los cambios realizados en esta versión de Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c60cd-104">This is a list of changes made to Azure PowerShell in this release.</span></span>

## <span data-ttu-id="c60cd-105">Versión 1.2.9</span><span class="sxs-lookup"><span data-stu-id="c60cd-105">Version 1.2.9</span></span>
<a id="version-129" class="xliff"></a>

<span data-ttu-id="c60cd-106">Cambios de esta versión</span><span class="sxs-lookup"><span data-stu-id="c60cd-106">Changes This Release</span></span>

* <span data-ttu-id="c60cd-107">Módulo AzureRm.AzureStackAdmin</span><span class="sxs-lookup"><span data-stu-id="c60cd-107">AzureRm.AzureStackAdmin Module</span></span>
    + <span data-ttu-id="c60cd-108">Cambios en el cmdlet Add-AzureRmResourceProviderRegistration para la compatibilidad del administrador de Azure Resource Manager y la división de inquilino de Azure Resource Manager.</span><span class="sxs-lookup"><span data-stu-id="c60cd-108">Changes in the Add-AzureRmResourceProviderRegistration cmdlet for the support of Admin Azure resource manager and tenant azure resource manager split.</span></span> <span data-ttu-id="c60cd-109">Incorporación de un nuevo parámetro -ResourceManagerType.</span><span class="sxs-lookup"><span data-stu-id="c60cd-109">A new parameter -ResourceManagerType has been added.</span></span>
    + <span data-ttu-id="c60cd-110">Eliminación de los parámetros -AdminUri, -ApiVersion, -SubscriptionId y -Token de los respectivos cmdlets.</span><span class="sxs-lookup"><span data-stu-id="c60cd-110">Removal of the parameters -AdminUri, -ApiVersion, -SubscriptionId and -Token from each cmdlets.</span></span> <span data-ttu-id="c60cd-111">Hemos impreso las advertencias de que ignorarían estos parámetros y ahora se han eliminado.</span><span class="sxs-lookup"><span data-stu-id="c60cd-111">We have been printing warnings that these parameters will be deprecated and now they got removed.</span></span>
* <span data-ttu-id="c60cd-112">Módulo AzureStackStorage</span><span class="sxs-lookup"><span data-stu-id="c60cd-112">AzureStackStorage module</span></span>
    + <span data-ttu-id="c60cd-113">Incorporación de nuevos cmdlets para admitir escenarios de migración de contenedores.</span><span class="sxs-lookup"><span data-stu-id="c60cd-113">Added new cmdlets to support container migration scenarios.</span></span>
    + <span data-ttu-id="c60cd-114">Los cmdlets que hacen referencia a componentes internos y características subyacentes se han eliminado.</span><span class="sxs-lookup"><span data-stu-id="c60cd-114">Removed cmdlets referring to internal components and underlying features.</span></span>
* <span data-ttu-id="c60cd-115">AzureRM.BootStrapper</span><span class="sxs-lookup"><span data-stu-id="c60cd-115">AzureRM.BootStrapper</span></span>
    + <span data-ttu-id="c60cd-116">Creación de un nuevo módulo para administrar las versiones de los cmdlets de Azure PowerShell mediante perfiles de versión</span><span class="sxs-lookup"><span data-stu-id="c60cd-116">Created new module to manage versions of Azure PowerShell cmdlets through the use of version profiles</span></span>