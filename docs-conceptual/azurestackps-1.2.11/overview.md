---
title: "Introducción a PowerShell de Azure Stack | Microsoft Docs"
description: "Información general sobre la instalación y configuración de PowerShell de Azure Stack."
author: SnehaGunda
manager: Byronr
ms.product: azure-stack
ms.service: powershell
ms.devlang: powershell
ms.topic: reference
ms.author: sngun
ms.manager: byronr
ms.openlocfilehash: f895992b4200f260189b3dbc541452e73a377b00
ms.sourcegitcommit: 8446ae373ac6928871ec8f10d3a4918b4601d5b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/27/2018
---
# <a name="azure-stack-powershell"></a><span data-ttu-id="d87d5-103">PowerShell de Azure Stack</span><span class="sxs-lookup"><span data-stu-id="d87d5-103">Azure Stack PowerShell</span></span>

<span data-ttu-id="d87d5-104">Azure Stack requiere los dos módulos de PowerShell siguientes:</span><span class="sxs-lookup"><span data-stu-id="d87d5-104">Azure Stack requires the following two PowerShell modules:</span></span>  

1. <span data-ttu-id="d87d5-105">El módulo **AzureRM** compatible con Azure Stack, que está disponible al instalar el perfil de versión de API **2017-03-09-profile**.</span><span class="sxs-lookup"><span data-stu-id="d87d5-105">The Azure Stack compatible **AzureRM** module which is available by installing the **2017-03-09-profile** API Version Profile.</span></span> <span data-ttu-id="d87d5-106">Los operadores de Azure Stack y los usuarios pueden usar los cmdlets que se instalan con este perfil.</span><span class="sxs-lookup"><span data-stu-id="d87d5-106">The cmdlets installed by using this profile can be used by Azure Stack operators and users.</span></span>

2. <span data-ttu-id="d87d5-107">La versión más reciente es la instalación **1.2.11** del módulo **AzureStack**.</span><span class="sxs-lookup"><span data-stu-id="d87d5-107">The most current version is the **1.2.11** install of the **AzureStack** module.</span></span> <span data-ttu-id="d87d5-108">Los operadores de Azure Stack son los únicos que pueden usar los cmdlets que se instalan con este módulo.</span><span class="sxs-lookup"><span data-stu-id="d87d5-108">The cmdlets installed by using this module can be used by Azure Stack operators only.</span></span> <span data-ttu-id="d87d5-109">Los operadores pueden realizar operaciones tales como administrar ofertas, planes, servicios, cuotas, etc. mediante los cmdlets de PowerShell proporcionados con este módulo.</span><span class="sxs-lookup"><span data-stu-id="d87d5-109">Operators can perform operations such as manage offers, plans, services, quotas, etc. by using the PowerShell cmdlets provided by this module.</span></span> <span data-ttu-id="d87d5-110">Para aprender sobre los cmdlets de PowerShell disponibles en este módulo, consulte la referencia de [AzureStackAdmin](https://docs.microsoft.com/powershell/module/azurerm.azurestackadmin/?view=azurestackps-1.2.11#azurerm.azurestackadmin) y [AzureStackStorage](https://docs.microsoft.com/powershell/module/azurerm.azurestackstorage/?view=azurestackps-1.2.11#azurerm.azurestackstorage).</span><span class="sxs-lookup"><span data-stu-id="d87d5-110">To learn about the PowerShell cmdlets available in this module, see the [AzureStackAdmin](https://docs.microsoft.com/powershell/module/azurerm.azurestackadmin/?view=azurestackps-1.2.11#azurerm.azurestackadmin) and [AzureStackStorage](https://docs.microsoft.com/powershell/module/azurerm.azurestackstorage/?view=azurestackps-1.2.11#azurerm.azurestackstorage) Reference content.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d87d5-111">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="d87d5-111">Next Steps</span></span>

* <span data-ttu-id="d87d5-112">[Install PowerShell for Azure Stack](https://docs.microsoft.com/azure/azure-stack/azure-stack-powershell-install?view=azurestackps-1.2.9&toc=%2fpowershell%2fmodule%2ftoc.json%3fview%3dazurestackps-1.2.9&view=azurestackps-1.2.9) (Instalación de PowerShell para Azure Stack)</span><span class="sxs-lookup"><span data-stu-id="d87d5-112">[Install PowerShell for Azure Stack](https://docs.microsoft.com/azure/azure-stack/azure-stack-powershell-install?view=azurestackps-1.2.9&toc=%2fpowershell%2fmodule%2ftoc.json%3fview%3dazurestackps-1.2.9&view=azurestackps-1.2.9)</span></span>
* <span data-ttu-id="d87d5-113">[Configure PowerShell for use with Azure Stack](https://docs.microsoft.com/azure/azure-stack/azure-stack-powershell-configure?view=azurestackps-1.2.9&toc=%2fpowershell%2fmodule%2ftoc.json%3fview%3dazurestackps-1.2.9&view=azurestackps-1.2.9) (Configuración de PowerShell para usarlo con Azure Stack)</span><span class="sxs-lookup"><span data-stu-id="d87d5-113">[Configure PowerShell for use with Azure Stack](https://docs.microsoft.com/azure/azure-stack/azure-stack-powershell-configure?view=azurestackps-1.2.9&toc=%2fpowershell%2fmodule%2ftoc.json%3fview%3dazurestackps-1.2.9&view=azurestackps-1.2.9)</span></span>
