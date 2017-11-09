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
ms.openlocfilehash: 0a3f152751fee569d3ac5fba6bcff8c1737f7b8c
ms.sourcegitcommit: b256bf48e15ee98865de0fae50e7b81878b03a54
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/03/2017
---
# <a name="release-notes"></a>Notas de la versión

Esta es una lista de los cambios realizados en esta versión de Azure PowerShell.

## <a name="version-170"></a>Versión 1.7.0

* **Cambio de comportamiento de los parámetros -Force, –Confirm y $ConfirmPreference en todos los cmdlets. Esta implementación se cambia para ir en línea con las directrices de PowerShell. Para la mayoría de cmdlets, esto significa la eliminación del parámetro Force y la omisión del mensaje ShouldProcess; los usuarios tendrán que incluir el parámetro "-Confirm:$false" en los scripts de PowerShell.** Este cambio soluciona los siguientes problemas:
  - Implementación correcta de la funcionalidad –WhatIf, que permite a un usuario determinar los efectos de un script o cmdlet sin tener que realizar ningún cambio real
  - Control sobre los mensajes mediante un parámetro $ConfirmPreference de sesión, de manera que se pregunta al usuario en función del efecto de un posible cambio (según se indica en la configuración de ConfirmImpact en el cmdlet)
  - Control de cmdlet específico sobre los mensajes de confirmación con el parámetro –Confirm
  - Uso coherente de ShouldContinue y el parámetro –Force en los cmdlets, solo para aquellas acciones que requieran preguntar al usuario por la naturaleza especial de los cambios (por ejemplo, la eliminación de archivos ocultos)
  - Coherencia con otros cmdlets de PowerShell, de manera que el conocimiento de scripts de PowerShell de otros cmdlets se aplique inmediatamente a los cmdlets de Azure PowerShell.

**Observe que ahora para *omitir automáticamente todos los mensajes en todas las circunstancias*, los cmdlets de Azure PowerShell requieren que el usuario proporcione dos parámetros:**
```powershell
My-CmdletWithConfirmation –Confirm:$false -Force
```
* Azure Compute
  - Set-AzureRmVMADDomainExtension
  - Get-AzureRmVMADDomainExtension
  - Parámetro -Redeploy para Restart-AzureVM
  - Parámetro -Validate para Move-AzureService, Move-AzureStorageAccount y Move-AzureVirtualNetwork
  - Los parámetros de nombre y versión para los cmdlets de extensión son opcionales, como antes.
  - New-AzureVM puede obtener un tipo de licencia de objeto de máquina virtual.
* Azure Storage
  - Cambio del parámetro Tags a Tag e incorporación del alias de parámetro Tags
    + New-AzureRmStorageAccount
    + Set-AzureRmStorageAccount
* Red de Azure
  - Incorporación de un nuevo cmdlet para el emparejamiento de redes virtuales
* Azure Redis Cache
  - Incorporación de un nuevo cmdlet para Reset-AzureRmRedisCache
  - Incorporación de un nuevo cmdlet para Export-AzureRmRedisCache
  - Incorporación de un nuevo cmdlet para Import-AzureRmRedisCache
  - Modificación del cmdlet New-AzureRmRedisCache para incluir el cambio de parámetro para la red virtual
* Copia de seguridad/restauración de Azure SQL Database
  - Cmdlets para la característica de copia de seguridad LTR (retención a largo plazo)
  - Get-AzureRmSqlServerBackupLongTermRetentionVault
  - Get-AzureRmSqlDatabaseBackupLongTermRetentionPolicy
  - Set-AzureRmSqlServerBackupLongTermRetentionVault
  - Set-AzureRmSqlDatabaseBackupLongTermRetentionPolicy
  - Restore-AzureRmSqlDatabase es ahora compatible con la restauración a un momento dado de una base de datos eliminada
  - Restore-AzureRmSqlDatabase es ahora compatible con la restauración de una copia de seguridad con retención a largo plazo
* Azure LogicApp
  - Incorporación de cmdlets para las cuentas de integración de LogicApp.
  - Get-AzureRmIntegrationAccountAgreement
  - Get-AzureRmIntegrationAccountCallbackUrl
  - Get-AzureRmIntegrationAccountCertificate
  - Get-AzureRmIntegrationAccount
  - Get-AzureRmIntegrationAccountMap
  - Get-AzureRmIntegrationAccountPartner
  - Get-AzureRmIntegrationAccountSchema
  - New-AzureRmIntegrationAccountAgreement
  - New-AzureRmIntegrationAccountCertificate
  - New-AzureRmIntegrationAccount
  - New-AzureRmIntegrationAccountMap
  - New-AzureRmIntegrationAccountPartner
  - New-AzureRmIntegrationAccountSchema
  - Remove-AzureRmIntegrationAccountAgreement
  - Remove-AzureRmIntegrationAccountCertificate
  - Remove-AzureRmIntegrationAccount
  - Remove-AzureRmIntegrationAccountMap
  - Remove-AzureRmIntegrationAccountPartner
  - Remove-AzureRmIntegrationAccountSchema
  - Set-AzureRmIntegrationAccountAgreement
  - Set-AzureRmIntegrationAccountCertificate
  - Set-AzureRmIntegrationAccount
  - Set-AzureRmIntegrationAccountMap
  - Set-AzureRmIntegrationAccountPartner
  - Set-AzureRmIntegrationAccountSchema
* Almacén de Azure Data Lake
  - Mejora considerable del rendimiento de carga y descarga de archivos y carpetas.
  - Esto incluye un pequeño cambio en los nombres de parámetro para la descarga y la inclusión de dos nuevos parámetros de carga:
    + NumThreads -> PerFileThreadCount, que indica el número de subprocesos para usar en un solo archivo
    + ConcurrentFileCount, que indica el número de archivos para cargar o descargar en paralelo con la carga o descarga de carpetas.
  - Los valores predeterminados de subprocesamiento ahora están diseñados para proporcionar un rendimiento mejor e integral para la mayoría de tamaños de archivo. Si el rendimiento no es como lo desea, los valores indicados anteriormente se pueden modificar para adaptarlos.
* Análisis con Azure Data Lake
  - Get-AzureRMDataLakeAnalyticsDataSource ahora devuelve todos los orígenes de datos cuando se realiza una llamada sin argumentos.
  - Este cambio también elimina el parámetro de tipo de origen de datos del cmdlet.
  - Este cambio produce un nuevo objeto que se devuelve para la operación de lista con las siguientes propiedades:
    + Type, tipo del origen de los datos
    + Name, nombre del origen de los datos
    + IsDefault, que se establece en true para el origen de datos predeterminado de la cuenta
  - Corrección de Get-AzureRMDataLakeAnalyticsJob para que se enumeren ciertos valores de desplazamiento de hora de fecha al filtrar por submittedBefore y submittedAfter.
* Web Apps
  - Incorporación del cmdlet Swap-AzureRmWebAppSlot para el intercambio normal y el intercambio con vista previa
  - Extensión del cmdlet Set-AzureRmWebAppSlot para admitir el intercambio automático
* Azure API Management
  - Corrección de los cmdlets de implementación de Azure API Management para AzureChinaCloud.
  - Eliminación de la habilitación de manera predeterminada del acceso de Git del cmdlet Set-AzureRmApiManagementTenantGitAccess.
* Azure Backup Recovery Services
  - Incorporación de compatibilidad con la carga de trabajo de Azure SQL
  - Incorporación de compatibilidad con la copia de seguridad y la restauración de máquinas virtuales de Azure cifradas
  - Backup-AzureRmRecoveryServicesBackupItem: incorporación de la característica de tiempo de retención opcional para los puntos de recuperación
  - Correcciones de errores menores de filtrado en los cmdlets Get-AzureRmRecoveryServicesBackupContainer y Get-AzureRmRecoveryServicesBackupItem
* Azure Automation
  - Incorporación de Get-AzureRmAutomationHybridWorkerGroup
