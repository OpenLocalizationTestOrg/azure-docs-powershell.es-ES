---
title: "Introducción a Azure PowerShell | Microsoft Docs"
description: "Información general de Azure PowerShell con vínculos a la instalación y configuración."
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.manager: carmonm
ms.date: 05/15/2017
ms.openlocfilehash: dbcc818ecc06d3206b8ccd6f8743c670c86cead0
ms.sourcegitcommit: 5f2c794bfa44ec4ffacdd73f548288874210a498
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2017
---
# <span data-ttu-id="0f0e1-103">Introducción a Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f0e1-103">Overview of Azure PowerShell</span></span>
<a id="overview-of-azure-powershell" class="xliff"></a>

<span data-ttu-id="0f0e1-104">Azure PowerShell ofrece un conjunto de cmdlets que usan el modelo [Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview) para administrar los recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="0f0e1-104">Azure PowerShell provides a set of cmdlets that use the [Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview) model for managing your Azure resources.</span></span>

<span data-ttu-id="0f0e1-105">Revise el artículo de la [instalación](install-azurerm-ps.md) para que Azure PowerShell esté rápidamente en pleno rendimiento en el sistema.</span><span class="sxs-lookup"><span data-stu-id="0f0e1-105">Review the [Install](install-azurerm-ps.md) article to get Azure PowerShell up and running on your system.</span></span> <span data-ttu-id="0f0e1-106">A continuación, lea el artículo de [introducción](get-started-azureps.md) para empezar a usarlo.</span><span class="sxs-lookup"><span data-stu-id="0f0e1-106">Then read the [Get Started](get-started-azureps.md) article to begin using it.</span></span> <span data-ttu-id="0f0e1-107">Para más información sobre la versión más reciente, consulte las [notas de la versión](release-notes-azureps.md).</span><span class="sxs-lookup"><span data-stu-id="0f0e1-107">For information about the latest release, see the [release notes](release-notes-azureps.md).</span></span>

<span data-ttu-id="0f0e1-108">Los ejemplos siguientes pueden ayudarle a obtener información sobre cómo realizar escenarios comunes con Azure PowerShell:</span><span class="sxs-lookup"><span data-stu-id="0f0e1-108">The following samples can help you learn how to perform common scenarios with Azure PowerShell:</span></span>

* [<span data-ttu-id="0f0e1-109">Máquinas virtuales Linux</span><span class="sxs-lookup"><span data-stu-id="0f0e1-109">Linux Virtual Machines</span></span>](/azure/virtual-machines/virtual-machines-linux-powershell-samples?toc=/powershell/azure/toc.json)
* [<span data-ttu-id="0f0e1-110">Máquinas virtuales Windows</span><span class="sxs-lookup"><span data-stu-id="0f0e1-110">Windows Virtual Machines</span></span>](/azure/virtual-machines/virtual-machines-windows-powershell-samples?toc=/powershell/azure/toc.json)
* [<span data-ttu-id="0f0e1-111">Web Apps</span><span class="sxs-lookup"><span data-stu-id="0f0e1-111">Web Apps</span></span>](/azure/app-service-web/app-service-powershell-samples?toc=/powershell/azure/toc.json)
* [<span data-ttu-id="0f0e1-112">Bases de datos SQL Database</span><span class="sxs-lookup"><span data-stu-id="0f0e1-112">SQL Databases</span></span>](/azure/sql-database/sql-database-powershell-samples?toc=/powershell/azure/toc.json)


> [!NOTE]<span data-ttu-id="0f0e1-113"> > Si dispone de implementaciones que usan el modelo de implementación clásica que no se pueden convertir, puede instalar la versión de Service Management de Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0f0e1-113"> > If you have deployments that use the classic deployment model that cannot be converted, you can install the Service Management version of Azure PowerShell.</span></span> <span data-ttu-id="0f0e1-114">Para más información, consulte [Install the Azure PowerShell Service Management module](/powershell/azure/servicemanagement/install-azure-ps) (Instalación del módulo Service Management de Azure PowerShell).</span><span class="sxs-lookup"><span data-stu-id="0f0e1-114">For more information, see [Install the Azure PowerShell Service Management module](/powershell/azure/servicemanagement/install-azure-ps).</span></span>


### <span data-ttu-id="0f0e1-115">¿Necesita ayuda con PowerShell?</span><span class="sxs-lookup"><span data-stu-id="0f0e1-115">Need help with PowerShell?</span></span>
<a id="need-help-with-powershell" class="xliff"></a>

<span data-ttu-id="0f0e1-116">Si no está familiarizado con PowerShell, puede resultarle útil una introducción a este producto.</span><span class="sxs-lookup"><span data-stu-id="0f0e1-116">If you are unfamiliar with PowerShell, you may find an introduction to PowerShell helpful.</span></span> <span data-ttu-id="0f0e1-117">Para empezar a trabajar con PowerShell, consulte [Scripting con PowerShell](https://technet.microsoft.com/library/bb978526.aspx).</span><span class="sxs-lookup"><span data-stu-id="0f0e1-117">To get started with PowerShell, see [Scripting with PowerShell](https://technet.microsoft.com/library/bb978526.aspx).</span></span>

<span data-ttu-id="0f0e1-118">También puede ver este vídeo: [PowerShell Basics: (Part 1) Getting Started with PowerShell](https://channel9.msdn.com/Blogs/Taste-of-Premier/PowerShellBasicsPart1) [Conceptos básicos de PowerShell: (parte 1) Introducción a PowerShell].</span><span class="sxs-lookup"><span data-stu-id="0f0e1-118">You can also watch this video: [PowerShell Basics: (Part 1) Getting Started with PowerShell](https://channel9.msdn.com/Blogs/Taste-of-Premier/PowerShellBasicsPart1).</span></span>

## <span data-ttu-id="0f0e1-119">Otros módulos de Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f0e1-119">Other Azure PowerShell modules</span></span>
<a id="other-azure-powershell-modules" class="xliff"></a>

* [<span data-ttu-id="0f0e1-120">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="0f0e1-120">Azure Active Directory</span></span>](/powershell/azure/active-directory/)
* [<span data-ttu-id="0f0e1-121">Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="0f0e1-121">Azure Information Protection</span></span>](/powershell/azure/aip/)
* [<span data-ttu-id="0f0e1-122">Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="0f0e1-122">Azure Service Fabric</span></span>](/powershell/azure/oservice-fabric/)
* [<span data-ttu-id="0f0e1-123">Azure ElasticDB</span><span class="sxs-lookup"><span data-stu-id="0f0e1-123">Azure ElasticDB</span></span>](/powershell/azure/elasticdbjobs/)
