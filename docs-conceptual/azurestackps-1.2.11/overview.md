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
# <a name="azure-stack-powershell"></a>PowerShell de Azure Stack

Azure Stack requiere los dos módulos de PowerShell siguientes:  

1. El módulo **AzureRM** compatible con Azure Stack, que está disponible al instalar el perfil de versión de API **2017-03-09-profile**. Los operadores de Azure Stack y los usuarios pueden usar los cmdlets que se instalan con este perfil.

2. La versión más reciente es la instalación **1.2.11** del módulo **AzureStack**. Los operadores de Azure Stack son los únicos que pueden usar los cmdlets que se instalan con este módulo. Los operadores pueden realizar operaciones tales como administrar ofertas, planes, servicios, cuotas, etc. mediante los cmdlets de PowerShell proporcionados con este módulo. Para aprender sobre los cmdlets de PowerShell disponibles en este módulo, consulte la referencia de [AzureStackAdmin](https://docs.microsoft.com/powershell/module/azurerm.azurestackadmin/?view=azurestackps-1.2.11#azurerm.azurestackadmin) y [AzureStackStorage](https://docs.microsoft.com/powershell/module/azurerm.azurestackstorage/?view=azurestackps-1.2.11#azurerm.azurestackstorage).

## <a name="next-steps"></a>Pasos siguientes

* [Install PowerShell for Azure Stack](https://docs.microsoft.com/azure/azure-stack/azure-stack-powershell-install?view=azurestackps-1.2.9&toc=%2fpowershell%2fmodule%2ftoc.json%3fview%3dazurestackps-1.2.9&view=azurestackps-1.2.9) (Instalación de PowerShell para Azure Stack)
* [Configure PowerShell for use with Azure Stack](https://docs.microsoft.com/azure/azure-stack/azure-stack-powershell-configure?view=azurestackps-1.2.9&toc=%2fpowershell%2fmodule%2ftoc.json%3fview%3dazurestackps-1.2.9&view=azurestackps-1.2.9) (Configuración de PowerShell para usarlo con Azure Stack)
