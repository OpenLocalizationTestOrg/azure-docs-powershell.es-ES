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
ms.date: 08/31/2017
ms.openlocfilehash: ed681a6e920f698caab978ad57fcee9a76420afd
ms.sourcegitcommit: e6b7e20bbd04eda51416c56b13f867102b602d1a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2017
---
# <a name="overview-of-azure-powershell"></a><span data-ttu-id="e050c-103">Introducción a Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="e050c-103">Overview of Azure PowerShell</span></span>

<span data-ttu-id="e050c-104">Azure PowerShell ofrece un conjunto de cmdlets que usan el modelo [Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview) para administrar los recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="e050c-104">Azure PowerShell provides a set of cmdlets that use the [Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview) model for managing your Azure resources.</span></span> <span data-ttu-id="e050c-105">Se puede usar en el explorador con [Azure Cloud Shell](/azure/cloud-shell/overview), o lo puede instalar en el equipo local y usarlo en cualquier sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e050c-105">You can use it in your browser with [Azure Cloud Shell](/azure/cloud-shell/overview), or you can install it on your local machine and use it in any PowerShell session.</span></span>

<span data-ttu-id="e050c-106">Use [Cloud Shell](/azure/cloud-shell/overview) para ejecutar Azure PowerShell en el explorador o [instálelo](install-azurerm-ps.md) en su propio equipo.</span><span class="sxs-lookup"><span data-stu-id="e050c-106">Use the [Cloud Shell](/azure/cloud-shell/overview) to run the Azure PowerShell in your browser, or [install](install-azurerm-ps.md) it on own computer.</span></span> <span data-ttu-id="e050c-107">A continuación, lea el artículo de [introducción](get-started-azureps.md) para empezar a usarlo.</span><span class="sxs-lookup"><span data-stu-id="e050c-107">Then read the [Get Started](get-started-azureps.md) article to begin using it.</span></span> <span data-ttu-id="e050c-108">Para más información sobre la versión más reciente, consulte las [notas de la versión](release-notes-azureps.md).</span><span class="sxs-lookup"><span data-stu-id="e050c-108">For information about the latest release, see the [release notes](release-notes-azureps.md).</span></span>

<span data-ttu-id="e050c-109">Los ejemplos siguientes pueden ayudarle a obtener información sobre cómo realizar escenarios comunes con Azure PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e050c-109">The following samples can help you learn how to perform common scenarios with Azure PowerShell:</span></span>

* [<span data-ttu-id="e050c-110">Máquinas virtuales Linux</span><span class="sxs-lookup"><span data-stu-id="e050c-110">Linux Virtual Machines</span></span>](/azure/virtual-machines/virtual-machines-linux-powershell-samples?toc=/powershell/azure/toc.json)
* [<span data-ttu-id="e050c-111">Máquinas virtuales Windows</span><span class="sxs-lookup"><span data-stu-id="e050c-111">Windows Virtual Machines</span></span>](/azure/virtual-machines/virtual-machines-windows-powershell-samples?toc=/powershell/azure/toc.json)
* [<span data-ttu-id="e050c-112">Web Apps</span><span class="sxs-lookup"><span data-stu-id="e050c-112">Web Apps</span></span>](/azure/app-service-web/app-service-powershell-samples?toc=/powershell/azure/toc.json)
* [<span data-ttu-id="e050c-113">Bases de datos SQL Database</span><span class="sxs-lookup"><span data-stu-id="e050c-113">SQL Databases</span></span>](/azure/sql-database/sql-database-powershell-samples?toc=/powershell/azure/toc.json)

> [!NOTE]<span data-ttu-id="e050c-114"> &gt; Si dispone de implementaciones que usan el modelo de implementación clásica que no se pueden convertir, puede instalar la versión de Service Management de Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e050c-114"> > If you have deployments that use the classic deployment model that cannot be converted, you can install the Service Management version of Azure PowerShell.</span></span> <span data-ttu-id="e050c-115">Para más información, consulte [Install the Azure PowerShell Service Management module](/powershell/azure/servicemanagement/install-azure-ps) (Instalación del módulo Service Management de Azure PowerShell).</span><span class="sxs-lookup"><span data-stu-id="e050c-115">For more information, see [Install the Azure PowerShell Service Management module](/powershell/azure/servicemanagement/install-azure-ps).</span></span>


### <a name="need-help-with-powershell"></a><span data-ttu-id="e050c-116">¿Necesita ayuda con PowerShell?</span><span class="sxs-lookup"><span data-stu-id="e050c-116">Need help with PowerShell?</span></span>

<span data-ttu-id="e050c-117">Si no está familiarizado con PowerShell, puede resultarle útil una introducción a este producto.</span><span class="sxs-lookup"><span data-stu-id="e050c-117">If you are unfamiliar with PowerShell, you may find an introduction to PowerShell helpful.</span></span>

* [<span data-ttu-id="e050c-118">Instalación de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e050c-118">Installing PowerShell</span></span>](/powershell/scripting/installing-windows-powershell)
* [<span data-ttu-id="e050c-119">Scripting con PowerShell</span><span class="sxs-lookup"><span data-stu-id="e050c-119">Scripting with PowerShell</span></span>](/powershell/scripting/scripting-with-windows-powershell)

<span data-ttu-id="e050c-120">También puede ver este vídeo: [PowerShell Basics: (Part 1) Getting Started with PowerShell](https://channel9.msdn.com/Blogs/Taste-of-Premier/PowerShellBasicsPart1) [Conceptos básicos de PowerShell: (parte 1) Introducción a PowerShell].</span><span class="sxs-lookup"><span data-stu-id="e050c-120">You can also watch this video: [PowerShell Basics: (Part 1) Getting Started with PowerShell](https://channel9.msdn.com/Blogs/Taste-of-Premier/PowerShellBasicsPart1).</span></span>

## <a name="other-azure-powershell-modules"></a><span data-ttu-id="e050c-121">Otros módulos de Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="e050c-121">Other Azure PowerShell modules</span></span>

* [<span data-ttu-id="e050c-122">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="e050c-122">Azure Active Directory</span></span>](/powershell/azure/active-directory/)
* [<span data-ttu-id="e050c-123">Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="e050c-123">Azure Information Protection</span></span>](/powershell/azure/aip/)
* [<span data-ttu-id="e050c-124">Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="e050c-124">Azure Service Fabric</span></span>](/powershell/azure/service-fabric/)
* [<span data-ttu-id="e050c-125">Azure ElasticDB</span><span class="sxs-lookup"><span data-stu-id="e050c-125">Azure ElasticDB</span></span>](/powershell/azure/elasticdbjobs/)
