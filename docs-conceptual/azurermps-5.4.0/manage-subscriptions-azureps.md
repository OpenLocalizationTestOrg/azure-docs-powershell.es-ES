---
title: "Administración de suscripciones de Azure con Azure PowerShell | Microsoft Docs"
description: "Administración de suscripciones de Azure con Azure PowerShell"
keywords: "Azure PowerShell, suscripción"
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/30/2017
ms.openlocfilehash: 68d03ec8d1a86fb3b270d02a4697bbf9af847f2d
ms.sourcegitcommit: 7e77fe7ecd2112d6b4515517509c5c723e750e27
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2018
---
# <a name="manage-multiple-azure-subscriptions"></a>Administración de varias suscripciones de Azure

Si es nuevo en Azure, probablemente solo tenga una única suscripción. Pero si ya lleva usando Azure durante un tiempo, puede haber creado varias suscripciones de Azure. Puede configurar Azure PowerShell para ejecutar comandos en una suscripción determinada.

1. Obtenga una lista de todas las suscripciones de su cuenta.

    ```powershell
    Get-AzureRmSubscription
    ```

    ```
    Environment           : AzureCloud
    Account               : username@contoso.com
    TenantId              : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    SubscriptionId        : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    SubscriptionName      : My Production Subscription
    CurrentStorageAccount :

    Environment           : AzureCloud
    Account               : username@contoso.com
    TenantId              : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    SubscriptionId        : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    SubscriptionName      : My DevTest Subscription
    CurrentStorageAccount :

    Environment           : AzureCloud
    Account               : username@contoso.com
    TenantId              : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    SubscriptionId        : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    SubscriptionName      : My Demos
    CurrentStorageAccount :
    ```

2. Establezca el valor predeterminado.

    ```powershell
    Select-AzureRmSubscription -SubscriptionName "My Demos"
    ```

3. Compruebe el cambio mediante la ejecución del cmdlet `Get-AzureRmContext`.

    ```powershell
    Get-AzureRmContext
    ```

    ```
    Environment           : AzureCloud
    Account               : username@contoso.com
    TenantId              : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    SubscriptionId        : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    SubscriptionName      : My Demos
    CurrentStorageAccount :
    ```

Cuando esté establecida la suscripción predeterminada, todos los comandos de Azure PowerShell subsiguientes se ejecutarán en esta suscripción.
