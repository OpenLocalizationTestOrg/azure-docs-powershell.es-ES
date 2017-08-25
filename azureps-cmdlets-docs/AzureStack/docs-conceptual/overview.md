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
# <a name="azure-stack-powershell"></a>PowerShell de Azure Stack 

Azure Stack requiere los dos módulos de PowerShell siguientes:  

1. El módulo **AzureRM** compatible con Azure Stack, que está disponible al instalar el perfil de versión de API **2017-03-09-profile**. Los administradores de la nube de Azure Stack y los inquilinos pueden usar los cmdlets que se instalan con este perfil. Para aprender más sobre los cmdlets de PowerShell que están disponibles en este perfil, consulte la referencia de PowerShell para el módulo de la [versión 1.2.9 de AzureRM](https://docs.microsoft.com/en-us/powershell/azure/overview?view=azurermps-1.2.9).  

2. La versión **1.2.9** del módulo **AzureStack**. Los administradores de la nube de Azure Stack son los únicos que pueden usar los cmdlets que se instalan con este módulo. El administrador puede realizar operaciones tales como administrar ofertas, planes, servicios, cuotas, etc. mediante los cmdlets de PowerShell proporcionados con este módulo. Para aprender sobre los cmdlets de PowerShell disponibles en este módulo, consulte la referencia de [AzureStackAdmin](https://docs.microsoft.com/en-us/powershell/module/azurerm.azurestackadmin/?view=azurestackps-1.2.9#azurerm.azurestackadmin) y [AzureStackStorage](https://docs.microsoft.com/en-us/powershell/module/azurerm.azurestackstorage/?view=azurestackps-1.2.9#azurerm.azurestackstorage).

## <a name="next-steps"></a>Pasos siguientes

* [Install PowerShell for Azure Stack](https://docs.microsoft.com/en-us/azure/azure-stack/azure-stack-powershell-install?view=azurestackps-1.2.9&toc=%2fpowershell%2fmodule%2ftoc.json%3fview%3dazurestackps-1.2.9&view=azurestackps-1.2.9) (Instalación de PowerShell para Azure Stack)
* [Configure PowerShell for use with Azure Stack](https://docs.microsoft.com/en-us/azure/azure-stack/azure-stack-powershell-configure?view=azurestackps-1.2.9&toc=%2fpowershell%2fmodule%2ftoc.json%3fview%3dazurestackps-1.2.9&view=azurestackps-1.2.9) (Configuración de PowerShell para usarlo con Azure Stack)


