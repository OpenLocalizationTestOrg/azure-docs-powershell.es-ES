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
ms.sourcegitcommit: b256bf48e15ee98865de0fae50e7b81878b03a54
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/03/2017
---
# <a name="release-notes"></a>Notas de la versión

Esta es una lista de los cambios realizados en esta versión de Azure PowerShell.

## <a name="version-129"></a>Versión 1.2.9

Cambios de esta versión

* Módulo AzureRm.AzureStackAdmin
    + Cambios en el cmdlet Add-AzureRmResourceProviderRegistration para la compatibilidad del administrador de Azure Resource Manager y la división de inquilino de Azure Resource Manager. Incorporación de un nuevo parámetro -ResourceManagerType.
    + Eliminación de los parámetros -AdminUri, -ApiVersion, -SubscriptionId y -Token de los respectivos cmdlets. Hemos impreso las advertencias de que ignorarían estos parámetros y ahora se han eliminado.
* Módulo AzureStackStorage
    + Incorporación de nuevos cmdlets para admitir escenarios de migración de contenedores.
    + Los cmdlets que hacen referencia a componentes internos y características subyacentes se han eliminado.
* AzureRM.BootStrapper
    + Creación de un nuevo módulo para administrar las versiones de los cmdlets de Azure PowerShell mediante perfiles de versión