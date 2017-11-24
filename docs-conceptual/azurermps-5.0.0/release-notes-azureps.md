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
ms.date: 11/14/2017
ms.openlocfilehash: ab35cbc4ec1a0bd4e7ee40e1864bd7941f5bca87
ms.sourcegitcommit: 79dd3700b5cb4cb90b268778b482082052160093
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/14/2017
---
# <a name="release-notes"></a>Notas de la versión

Esta es una lista de los cambios realizados en esta versión de Azure PowerShell.

## <a name="20171110-version-501"></a>2017.11.10: versión 5.0.1
* Se corrigió el problema de carga del ensamblado que provocaban errores en algunos cmdlets cuando se ejecutaban en los siguientes módulos:
    - AzureRM.ApiManagement
    - AzureRM.Backup
    - AzureRM.Batch
    - AzureRM.Compute
    - AzureRM.DataFactories
    - AzureRM.HDInsight
    - AzureRM.KeyVault
    - AzureRM.RecoveryServices
    - AzureRM.RecoveryServices.Backup
    - AzureRM.RecoveryServices.SiteRecovery
    - AzureRM.RedisCache
    - AzureRM.SiteRecovery
    - AzureRM.Sql
    - AzureRM.Storage
    - AzureRM.StreamAnalytics

## <a name="2017118---version-500"></a>8/11/2017: versión 5.0.0
* NOTA: Esta es una versión con cambios importantes. Consulte la guía de migración (https://aka.ms/azps-migration-guide) para obtener una lista completa de los cambios realizados.
* Todos los cmdlets de AzureRM ahora admiten la ayuda en línea
    - Ejecute Get-Help con el parámetro -Online para abrir la ayuda en línea en el explorador de Internet predeterminado
* AnalysisServices
    * Se corrigió el comando Synchronize-AzureAsInstance para que funcione la sincronización con la nueva API de REST de AsAzure
* ApiManagement
    * Consulte la guía de migración para más información sobre los cambios importantes realizados en ApiManagement en esta versión
    * Se actualizó el cmdlet Get-AzureRmApiManagementUser para corregir el error https://github.com/Azure/azure-powershell/issues/4510
    * Se actualizó el cmdlet New-AzureRmApiManagementApi para crear una API con ruta de acceso vacía https://github.com/Azure/azure-powershell/issues/4069
* ApplicationInsights
    * Se agregaron comandos para obtener, crear o quitar recursos de Application Insights
        - Get-AzureRmApplicationInsights
        - New-AzureRmApplicationInsights
        - Remove-AzureRmApplicationInsights
    * Se agregaron comandos para obtener o actualizar los precios y la capacidad diaria de los recursos de Application Insights
        - Get-AzureRmApplicationInsights -IncludeDailyCap
        - Set-AzureRmApplicationInsightsPricingPlan
        - Set-AzureRmApplicationInsightsDailyCap
    * Se agregaron comandos para obtener, crear, actualizar o quitar exportaciones continuas de recursos de Application Insights
        - Get-AzureRmApplicationInsightsContinuousExport
        - Set-AzureRmApplicationInsightsContinuousExport
        - New-AzureRmApplicationInsightsContinuousExport
        - Remove-AzureRmApplicationInsightsContinuousExport
    * Se agregaron comandos para obtener, crear o quitar claves de API de recursos de Application Insights
        - Get-AzureRmApplicationInsightsApiKey
        - New-AzureRmApplicationInsightsApiKey
        - Remove-AzureRmApplicationInsightsApiKey
* AzureBatch
    * Se agregaron nuevos parámetros a `New-AzureRmBatchAccount`.
        - `PoolAllocationMode`: modo de asignación que se usará para crear grupos en la cuenta de Batch. Para crear una cuenta de Batch que asigne nodos de grupo en la suscripción del usuario, establezca esta propiedad en `UserSubscription`.
        - `KeyVaultId`: identificador de recurso del almacén de claves de Azure asociado a la cuenta de Batch.
        - `KeyVaultUrl`: URL del almacén de claves de Azure asociado a la cuenta de Batch.
    * Se actualizaron los parámetros de `New-AzureBatchTask`.
        - Se quitó el modificador `RunElevated`. Se agregó el parámetro `UserIdentity` para reemplazar a `RunElevated`, y el comportamiento equivalente se puede lograr construyendo `PSUserIdentity` de la siguiente manera:
            - $autoUser = New-Object Microsoft.Azure.Commands.Batch.Models.PSAutoUserSpecification -ArgumentList @("Task", "Admin")
            - $userIdentity = New-Object Microsoft.Azure.Commands.Batch.Models.PSUserIdentity $autoUser
        - Se agregó el parámetro `AuthenticationTokenSettings`. Este parámetro permite solicitar al servicio Batch que proporcione un token de autenticación a la tarea cuando se ejecuta, y evita tener que pasar las claves de la cuenta de Batch a la tarea para emitir las solicitudes al servicio Batch.
        - Se agregó el parámetro `ContainerSettings`.
            - Este parámetro permite solicitar al servicio Batch que ejecute la tarea dentro de un contenedor.
        - Se agregó el parámetro `OutputFiles`.
            - Este parámetro permite configurar la tarea para cargar archivos en Azure Storage después de haber terminado.
    * Se actualizaron los parámetros de `New-AzureBatchPool`.
        - Se agregó el parámetro `UserAccounts`.
            - Este parámetro define las cuentas de usuario creadas en cada nodo del grupo.
        - Se agregó `TargetLowPriorityComputeNodes` y se cambió el nombre de `TargetDedicated` a `TargetDedicatedComputeNodes`.
            - Se creó el alias `TargetDedicated` para el parámetro `TargetDedicatedComputeNodes`.
        - Se agregó el parámetro `NetworkConfiguration`.
            - Este parámetro permite configurar las opciones de red de los grupos.
    * Se actualizaron los parámetros de `New-AzureBatchCertificate`.
        - El parámetro `Password` ahora es `SecureString`.
    * Se actualizaron los parámetros de `New-AzureBatchComputeNodeUser`.
        - El parámetro `Password` ahora es `SecureString`.
    * Se actualizaron los parámetros de `Set-AzureBatchComputeNodeUser`.
        - El parámetro `Password` ahora es `SecureString`.
    * Se cambió el nombre del parámetro `Name` a `Path` en `Get-AzureBatchNodeFile`, `Get-AzureBatchNodeFileContent` y `Remove-AzureBatchNodeFile`.
        - Se creó el alias `Name` para el parámetro `Path`.
    * Cambios en los objetos
        - Vea el registro de cambios de Batch para obtener la lista completa de los cambios
    * Se agregó compatibilidad para la autenticación basada en Azure Active Directory.
        - Para usar la autenticación de Azure Active Directory, recupere un objeto `BatchAccountContext` mediante el cmdlet `Get-AzureRmBatchAccount` y proporcione este `BatchAccountContext` al parámetro `-BatchContext` de un cmdlet del servicio Batch. La autenticación de Azure Active Directory es obligatoria para las cuentas con `PoolAllocationMode = UserSubscription`.
        - Para las cuentas existentes o las nuevas cuentas que se crean con `PoolAllocationMode = BatchService`, puede seguir usando la autenticación de clave compartida; para ello, recupere un objeto `BatchAccountContext` mediante el cmdlet `Get-AzureRmBatchAccoutKeys`.
* Proceso
    * Comandos de extensión de Azure Disk Encryption
        - El nuevo parámetro de 'Set-AzureRmVmDiskEncryptionExtension': '-EncryptFormatAll' formatea con cifrado discos de datos
        - Los nuevos parámetros de 'Set-AzureRmVmDiskEncryptionExtension': '-ExtensionPublisherName' y '-ExtensionType' permiten cambiar a otras versiones de la extensión
        - Los nuevos parámetros de 'Disable-AzureRmVmDiskEncryption': '-ExtensionPublisherName' y '-ExtensionType' permiten cambiar a otras versiones de la extensión
        - Los nuevos parámetros de 'Get-AzureRmVmDiskEncryptionStatus': '-ExtensionPublisherName' y '-ExtensionType' permiten cambiar a otras versiones de la extensión
* DataLakeAnalytics
    * Consulte la guía de migración para más información sobre los cambios importantes realizados en DataLakeAnalytics en esta versión
    * Se cambió uno de los dos valores de OutputTypes de Get-AzureRmDataLakeAnalyticsAccount
        - List\<DataLakeAnalyticsAccount> a List\<PSDataLakeAnalyticsAccountBasic>
        - Las propiedades de PSDataLakeAnalyticsAccountBasic son un subconjunto estricto de las propiedades de DataLakeAnalyticsAccount
        - El servicio no devuelve las propiedades adicionales que se encuentran en DataLakeAnalyticsAccount.  Por lo tanto, el objetivo de este cambio es reflejar esto con precisión. Estas propiedades adicionales están aún en PSDataLakeAnalyticsAccountBasic, pero están etiquetadas como obsoletas.
    * Se cambió uno de los dos valores de OutputTypes de Get-AzureRmDataLakeAnalyticsJob
        - List\<JobInformation> a List\<PSJobInformationBasic>
        - Las propiedades de PSJobInformationBasic son un subconjunto estricto de las propiedades de JobInformation
        - El servicio no devuelve las propiedades adicionales que se encuentran en JobInformation.  Por lo tanto, el objetivo de este cambio es reflejar esto con precisión. Estas propiedades adicionales están aún en PSJobInformationBasic, pero están etiquetadas como obsoletas.
* DataLakeStore
    * Consulte la guía de migración para más información sobre los cambios importantes realizados en DataLakeStore en esta versión
    * Se cambió uno de los dos valores de OutputTypes de Get-AzureRmDataLakeStoreAccount
        - List\<PSDataLakeStoreAccount> a List\<PSDataLakeStoreAccountBasic>
        - Las propiedades de PSDataLakeStoreAccountBasic son un subconjunto estricto de las propiedades de PSDataLakeStoreAccount
        - El servicio no devuelve las propiedades adicionales que se encuentran en PSDataLakeStoreAccount.  Por lo tanto, el objetivo de este cambio es reflejar esto con precisión. Estas propiedades adicionales están aún en PSDataLakeStoreAccountBasic, pero están etiquetadas como obsoletas.
* Dns
    * Compatibilidad con los tipos de registro CAA en Azure DNS
       - Admite todas las operaciones en el tipo de registro CAA
* EventHub
    * Consulte la guía de migración para más información sobre los cambios importantes realizados en EventHub en esta versión
* Información detallada
    * Consulte la guía de migración para más información sobre los cambios importantes realizados en Insights en esta versión
* Red
    * Consulte la guía de migración para más información sobre los cambios importantes realizados en Network en esta versión
    * Se agregó un cmdlet para enumerar los proveedores de servicios de Internet disponibles para una región de Azure específica
        - Get-AzureRmNetworkWatcherReachabilityProvidersList
    * Se agregó un cmdlet para obtener la puntuación de la latencia relativa de los proveedores de servicios de Internet desde una ubicación específica a las regiones de Azure
        - Get-AzureRmNetworkWatcherReachabilityReport
* Perfil
    - Set-AzureRmDefault
        - Use este cmdlet para establecer un grupo de recursos predeterminado.  Esto hará que el parámetro -ResourceGroup sea opcional para algunos cmdlets y usará el valor predeterminado cuando no se especifique un grupo de recursos
        - ```Set-AzureRmDefault -ResourceGroupName "ExampleResourceGroup"```
        - Si el grupo de recursos especificado existe en la suscripción, este grupo de recursos se establecerá en el valor predeterminado.  En caso contrario, se creará el grupo de recursos y se establecerá como predeterminado.
    - Get-AzureRmDefault
        - Use este cmdlet para obtener el grupo de recursos predeterminado actual (y otros valores predeterminados en el futuro).
        - ```Get-AzureRmDefault -ResourceGroup```
    - Clear-AzureRmDefault
        - Use este cmdlet para quitar el grupo de recursos predeterminado actual
        - ```Clear-AzureRmDefault -ResourceGroup```
    - Add-AzureRmEnvironment y Set-AzureRmEnvironment
        - Agregue el parámetro BatchAudience, que permite especificar la audiencia de Active Directory para Azure Batch que se usará al adquirir los tokens de autenticación del servicio Batch.
* RecoveryServices.Backup
    * Se agregaron cmdlets para realizar una recuperación instantánea de archivos.
        - Get-AzureRmRecoveryServicesBackupRPMountScript
        - Disable-AzureRmRecoveryServicesBackupRPMountScript
    * Se actualizó el SDK de RecoveryServices.Backup a la versión más reciente
    * Se actualizaron las pruebas para la carga de trabajo de Azure Virtual Machines para que todas las configuraciones necesarias para las ejecuciones de pruebas las realicen las propias pruebas.
    * Corrige https://github.com/Azure/azure-powershell/issues/3164
* RecoveryServices.SiteRecovery
    * Cambios de ASR VMware para Azure Site Recovery (los cmdlets admiten actualmente operaciones de Enterprise a Enterprise, de Enterprise en Azure y de Hyper-v a Azure)
        - New-AzureRmRecoveryServicesAsrPolicy
        - New-AzureRmRecoveryServicesAsrProtectedItem
        - Update-AzureRmRecoveryServicesAsrPolicy
        - Update-AzureRmRecoveryServicesAsrProtectionDirection
    * Se agregó compatibilidad para almacenes basados en AAD
    * Se agregaron cmdlets para administrar recursos de VCenter
        - Get-AzureRmRecoveryServicesAsrVCenter
        - New-AzureRmRecoveryServicesAsrVCenter
        - Remove-AzureRmRecoveryServicesAsrVCenter
        - Update-AzureRmRecoveryServicesAsrVCenter
    * Se agregaron otros cmdlets
        - Get-AzureRmRecoveryServicesAsrAlertSetting
        - Get-AzureRmRecoveryServicesAsrEvent
        - New-AzureRmRecoveryServicesAsrProtectableItem
        - Set-AzureRmRecoveryServicesAsrAlertSetting
        - Start-AzureRmRecoveryServicesAsrResynchronizeReplicationJob
        - Start-AzureRmRecoveryServicesAsrSwitchProcessServerJob
        - Start-AzureRmRecoveryServicesAsrTestFailoverCleanupJob
        - Update-AzureRmRecoveryServicesAsrMobilityService
* ServiceBus
    - Consulte la guía de migración para más información sobre los cambios importantes realizados en ServiceBus en esta versión
* Sql
    * Se agregó compatibilidad para enumerar y cancelar la operación asincrónica updateslo en la base de datos
        - Se actualizó el cmdlet existente Get-AzureRmSqlDatabaseActivity para devolver el estado de la operación updateslo de la base de datos.
        - Se agregó el nuevo cmdlet Stop-AzureRmSqlDatabaseActivity para cancelar la operación asincrónica updateslo en la base de datos.
    * Se agregó compatibilidad para redundancia de zona para las bases de datos y los grupos elásticos
        - Se agregó el parámetro modificador ZoneRedundant a New-AzureRmSqlDatabase
        - Se agregó el parámetro modificador ZoneRedundant a Set-AzureRmSqlDatabase
        - Se agregó el parámetro modificador ZoneRedundant a New-AzureRmSqlElasticPool
        - Se agregó el parámetro modificador ZoneRedundant a Set-AzureRmSqlElasticPool
    * Se agregó compatibilidad para los alias de DNS de servidor
        - Se agregó el cmdlet Get-AzureRmSqlServerDnsAlias que obtiene los alias de dns de servidor por nombre de servidor y nombre de alias, o una lista de alias de dns de servidor para un servidor SQL de Azure.
        - Se agregó el cmdlet New-AzureRmSqlServerDnsAlias que crea el nuevo alias de dns del servidor para un servidor SQL de Azure determinado
        - Se agregó el cmdlet Set-AzurermSqlServerDnsAlias que permite actualizar un servidor SQL de Azure al alias de dns de servidor al que apunta
        - Se agregó el cmdlet Remove-AzureRmSqlServerDnsAlias que quita un alias de dns del servidor para un servidor SQL de Azure
* Azure.Storage
    * Actualización a Biblioteca de cliente de Azure Storage 8.5.0 y Biblioteca de Azure Storage DataMovement 0.6.3
    * Se agregó compatibilidad con instantáneas de recursos compartidos de archivos
        - Se agregó el parámetro 'SnapshotTime' a Get-AzureStorageShare
        - Se agregó el parámetro 'IncludeAllSnapshot' a Remove-AzureStorageShare