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
ms.openlocfilehash: 2a03697e0f3e80d63c48f2dc5615f6c99b9ef716
ms.sourcegitcommit: 226527be7cb647acfe2ea9ab151185053ab3c6db
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2017
---
# <a name="azure-stack-powershell"></a><span data-ttu-id="6260f-103">PowerShell de Azure Stack</span><span class="sxs-lookup"><span data-stu-id="6260f-103">Azure Stack PowerShell</span></span> 

<span data-ttu-id="6260f-104">Azure Stack requiere los dos módulos de PowerShell siguientes:</span><span class="sxs-lookup"><span data-stu-id="6260f-104">Azure Stack requires the following two PowerShell modules:</span></span>  

1. <span data-ttu-id="6260f-105">El módulo **AzureRM** compatible con Azure Stack, que está disponible al instalar el perfil de versión de API **2017-03-09-profile**.</span><span class="sxs-lookup"><span data-stu-id="6260f-105">The Azure Stack compatible **AzureRM** module which is available by installing the **2017-03-09-profile** API Version Profile.</span></span> <span data-ttu-id="6260f-106">Los administradores de la nube de Azure Stack y los inquilinos pueden usar los cmdlets que se instalan con este perfil.</span><span class="sxs-lookup"><span data-stu-id="6260f-106">The cmdlets installed by using this profile can be used by the Azure Stack cloud administrators and the tenants.</span></span> <span data-ttu-id="6260f-107">Para aprender más sobre los cmdlets de PowerShell que están disponibles en este perfil, consulte la referencia de PowerShell para el módulo de la [versión 1.2.9 de AzureRM](https://docs.microsoft.com/en-us/powershell/azure/overview?view=azurermps-1.2.9).</span><span class="sxs-lookup"><span data-stu-id="6260f-107">To learn about the PowerShell cmdlets that are available in this profile, see the PowerShell reference content for the [1.2.9 version of AzureRM](https://docs.microsoft.com/en-us/powershell/azure/overview?view=azurermps-1.2.9) module.</span></span>  

2. <span data-ttu-id="6260f-108">La versión **1.2.9** del módulo **AzureStack**.</span><span class="sxs-lookup"><span data-stu-id="6260f-108">The **1.2.9** version of the **AzureStack** module.</span></span> <span data-ttu-id="6260f-109">Los administradores de la nube de Azure Stack son los únicos que pueden usar los cmdlets que se instalan con este módulo.</span><span class="sxs-lookup"><span data-stu-id="6260f-109">The cmdlets installed by using this module can be used by Azure Stack cloud administrators only.</span></span> <span data-ttu-id="6260f-110">El administrador puede realizar operaciones tales como administrar ofertas, planes, servicios, cuotas, etc. mediante los cmdlets de PowerShell proporcionados con este módulo.</span><span class="sxs-lookup"><span data-stu-id="6260f-110">Administrator can perform operations such as manage offers, plans, services, quotas, etc. by using the PowerShell cmdlets provided by this module.</span></span> <span data-ttu-id="6260f-111">Para aprender sobre los cmdlets de PowerShell disponibles en este módulo, consulte la referencia de [AzureStackAdmin](https://docs.microsoft.com/en-us/powershell/module/azurerm.azurestackadmin/?view=azurestackps-1.2.9#azurerm.azurestackadmin) y [AzureStackStorage](https://docs.microsoft.com/en-us/powershell/module/azurerm.azurestackstorage/?view=azurestackps-1.2.9#azurerm.azurestackstorage).</span><span class="sxs-lookup"><span data-stu-id="6260f-111">To learn about the PowerShell cmdlets available in this module, see the [AzureStackAdmin](https://docs.microsoft.com/en-us/powershell/module/azurerm.azurestackadmin/?view=azurestackps-1.2.9#azurerm.azurestackadmin) and [AzureStackStorage](https://docs.microsoft.com/en-us/powershell/module/azurerm.azurestackstorage/?view=azurestackps-1.2.9#azurerm.azurestackstorage) Reference content.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6260f-112">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="6260f-112">Next Steps</span></span>

* [<span data-ttu-id="6260f-113">Install PowerShell for Azure Stack</span><span class="sxs-lookup"><span data-stu-id="6260f-113">Install PowerShell for Azure Stack</span></span>](https://docs.microsoft.com/en-us/azure/azure-stack/azure-stack-powershell-install?view=azurestackps-1.2.9&toc=%2fpowershell%2fmodule%2ftoc.json%3fview%3dazurestackps-1.2.9&view=azurestackps-1.2.9) (Instalación de PowerShell para Azure Stack)
* [<span data-ttu-id="6260f-114">Configure PowerShell for use with Azure Stack</span><span class="sxs-lookup"><span data-stu-id="6260f-114">Configure PowerShell for use with Azure Stack</span></span>](https://docs.microsoft.com/en-us/azure/azure-stack/azure-stack-powershell-configure?view=azurestackps-1.2.9&toc=%2fpowershell%2fmodule%2ftoc.json%3fview%3dazurestackps-1.2.9&view=azurestackps-1.2.9) (Configuración de PowerShell para usarlo con Azure Stack)


