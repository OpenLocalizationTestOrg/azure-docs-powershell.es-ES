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
ms.sourcegitcommit: c42c7176276ec4e1cc3360a93e6b15d32083bf9f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2017
---
# <a name="manage-multiple-azure-subscriptions"></a><span data-ttu-id="afd6b-104">Administración de varias suscripciones de Azure</span><span class="sxs-lookup"><span data-stu-id="afd6b-104">Manage multiple Azure subscriptions</span></span>

<span data-ttu-id="afd6b-105">Si es nuevo en Azure, probablemente solo tenga una única suscripción.</span><span class="sxs-lookup"><span data-stu-id="afd6b-105">If you are brand new to Azure, you probably only have a single subscription.</span></span> <span data-ttu-id="afd6b-106">Pero si ya lleva usando Azure durante un tiempo, puede haber creado varias suscripciones de Azure.</span><span class="sxs-lookup"><span data-stu-id="afd6b-106">But if you have been using Azure for a while, you may have created multiple Azure subscriptions.</span></span> <span data-ttu-id="afd6b-107">Puede configurar Azure PowerShell para ejecutar comandos en una suscripción determinada.</span><span class="sxs-lookup"><span data-stu-id="afd6b-107">You can configure Azure PowerShell to execute commands against a particular subscription.</span></span>

1. <span data-ttu-id="afd6b-108">Obtenga una lista de todas las suscripciones de su cuenta.</span><span class="sxs-lookup"><span data-stu-id="afd6b-108">Get a list of all subscriptions in your account.</span></span>

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

2. <span data-ttu-id="afd6b-109">Establezca el valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="afd6b-109">Set the default.</span></span>

    ```powershell
    Select-AzureRmSubscription -SubscriptionName "My Demos"
    ```

3. <span data-ttu-id="afd6b-110">Compruebe el cambio mediante la ejecución del cmdlet `Get-AzureRmContext`.</span><span class="sxs-lookup"><span data-stu-id="afd6b-110">Verify the change by running the `Get-AzureRmContext` cmdlet.</span></span>

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

<span data-ttu-id="afd6b-111">Cuando esté establecida la suscripción predeterminada, todos los comandos de Azure PowerShell subsiguientes se ejecutarán en esta suscripción.</span><span class="sxs-lookup"><span data-stu-id="afd6b-111">Once you set your default subscription, all subsequent Azure PowerShell commands run against this subscription.</span></span>
