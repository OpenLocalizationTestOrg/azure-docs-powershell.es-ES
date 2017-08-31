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
ms.date: 07/26/2017
ms.openlocfilehash: 02bfc15fec83ed4078d9a054b450c5a3cd66b8e2
ms.sourcegitcommit: db5c50de90764a9bdc7c1f1dbca3aed5bfeb05fa
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2017
---
# <a name="overview-of-azure-powershell"></a><span data-ttu-id="e9a89-103">Introducción a Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="e9a89-103">Overview of Azure PowerShell</span></span>

<span data-ttu-id="e9a89-104">Azure PowerShell ofrece un conjunto de cmdlets que usan el modelo [Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview) para administrar los recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="e9a89-104">Azure PowerShell provides a set of cmdlets that use the [Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview) model for managing your Azure resources.</span></span>

<span data-ttu-id="e9a89-105">Revise el artículo de la [instalación](install-azurerm-ps.md) para que Azure PowerShell esté rápidamente en pleno rendimiento en el sistema.</span><span class="sxs-lookup"><span data-stu-id="e9a89-105">Review the [Install](install-azurerm-ps.md) article to get Azure PowerShell up and running on your system.</span></span> <span data-ttu-id="e9a89-106">A continuación, lea el artículo de [introducción](get-started-azureps.md) para empezar a usarlo.</span><span class="sxs-lookup"><span data-stu-id="e9a89-106">Then read the [Get Started](get-started-azureps.md) article to begin using it.</span></span> <span data-ttu-id="e9a89-107">Para más información sobre la versión más reciente, consulte las [notas de la versión](release-notes-azureps.md).</span><span class="sxs-lookup"><span data-stu-id="e9a89-107">For information about the latest release, see the [release notes](release-notes-azureps.md).</span></span>

<span data-ttu-id="e9a89-108">Los ejemplos siguientes pueden ayudarle a obtener información sobre cómo realizar escenarios comunes con Azure PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e9a89-108">The following samples can help you learn how to perform common scenarios with Azure PowerShell:</span></span>

* [<span data-ttu-id="e9a89-109">Máquinas virtuales Linux</span><span class="sxs-lookup"><span data-stu-id="e9a89-109">Linux Virtual Machines</span></span>](/azure/virtual-machines/virtual-machines-linux-powershell-samples?toc=/powershell/azure/toc.json)
* [<span data-ttu-id="e9a89-110">Máquinas virtuales Windows</span><span class="sxs-lookup"><span data-stu-id="e9a89-110">Windows Virtual Machines</span></span>](/azure/virtual-machines/virtual-machines-windows-powershell-samples?toc=/powershell/azure/toc.json)
* [<span data-ttu-id="e9a89-111">Web Apps</span><span class="sxs-lookup"><span data-stu-id="e9a89-111">Web Apps</span></span>](/azure/app-service-web/app-service-powershell-samples?toc=/powershell/azure/toc.json)
* [<span data-ttu-id="e9a89-112">Bases de datos SQL Database</span><span class="sxs-lookup"><span data-stu-id="e9a89-112">SQL Databases</span></span>](/azure/sql-database/sql-database-powershell-samples?toc=/powershell/azure/toc.json)

> [!NOTE]<span data-ttu-id="e9a89-113"> > Si dispone de implementaciones que usan el modelo de implementación clásica que no se pueden convertir, puede instalar la versión de Service Management de Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e9a89-113"> > If you have deployments that use the classic deployment model that cannot be converted, you can install the Service Management version of Azure PowerShell.</span></span> <span data-ttu-id="e9a89-114">Para más información, consulte [Install the Azure PowerShell Service Management module](/powershell/azure/servicemanagement/install-azure-ps) (Instalación del módulo Service Management de Azure PowerShell).</span><span class="sxs-lookup"><span data-stu-id="e9a89-114">For more information, see [Install the Azure PowerShell Service Management module](/powershell/azure/servicemanagement/install-azure-ps).</span></span>

### <a name="need-help-with-powershell"></a><span data-ttu-id="e9a89-115">¿Necesita ayuda con PowerShell?</span><span class="sxs-lookup"><span data-stu-id="e9a89-115">Need help with PowerShell?</span></span>

<span data-ttu-id="e9a89-116">Si no está familiarizado con PowerShell, puede resultarle útil una introducción a este producto.</span><span class="sxs-lookup"><span data-stu-id="e9a89-116">If you are unfamiliar with PowerShell, you may find an introduction to PowerShell helpful.</span></span>

* [<span data-ttu-id="e9a89-117">Instalación de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e9a89-117">Installing PowerShell</span></span>](/powershell/scripting/installing-windows-powershell)
* [<span data-ttu-id="e9a89-118">Scripting con PowerShell</span><span class="sxs-lookup"><span data-stu-id="e9a89-118">Scripting with PowerShell</span></span>](/powershell/scripting/scripting-with-windows-powershell)

<span data-ttu-id="e9a89-119">También puede ver este vídeo: [PowerShell Basics: (Part 1) Getting Started with PowerShell](https://channel9.msdn.com/Blogs/Taste-of-Premier/PowerShellBasicsPart1) [Conceptos básicos de PowerShell: (parte 1) Introducción a PowerShell].</span><span class="sxs-lookup"><span data-stu-id="e9a89-119">You can also watch this video: [PowerShell Basics: (Part 1) Getting Started with PowerShell](https://channel9.msdn.com/Blogs/Taste-of-Premier/PowerShellBasicsPart1).</span></span>

## <a name="other-azure-powershell-modules"></a><span data-ttu-id="e9a89-120">Otros módulos de Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="e9a89-120">Other Azure PowerShell modules</span></span>

* [<span data-ttu-id="e9a89-121">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="e9a89-121">Azure Active Directory</span></span>](/powershell/azure/active-directory/)
* [<span data-ttu-id="e9a89-122">Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="e9a89-122">Azure Information Protection</span></span>](/powershell/azure/aip/)
* [<span data-ttu-id="e9a89-123">Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="e9a89-123">Azure Service Fabric</span></span>](/powershell/azure/service-fabric/)
* [<span data-ttu-id="e9a89-124">Azure ElasticDB</span><span class="sxs-lookup"><span data-stu-id="e9a89-124">Azure ElasticDB</span></span>](/powershell/azure/elasticdbjobs/)
