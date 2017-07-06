---
title: Registro de cambios de Azure PowerShell | Microsoft Docs
description: "Es un historial de los cambios realizados en la versión más reciente de Azure PowerShell."
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.service: azure-resource-manager
ms.product: azure
ms.devlang: powershell
ms.topic: conceptual
ms.workload: 
ms.date: 05/18/2017
ms.openlocfilehash: 5c8fa2a5a8f94cd24b66f42c237749a7b89af3b3
ms.sourcegitcommit: 226527be7cb647acfe2ea9ab151185053ab3c6db
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2017
---
# <a name="release-notes"></a>Notas de la versión

Esta es una lista de los cambios realizados en esta versión de Azure PowerShell.

## <a name="version-400"></a>Versión 4.0.0

* Esta versión contiene cambios innovadores. Consulte [la guía de migración](https://aka.ms/azps-migration-guide) para ver detalles de los cambios y el impacto en los scripts existentes.
* ApiManagement
  - Se agregó compatibilidad con la configuración de grupos externos en New-AzureRmApiManagementGroup.
* Facturación
  - Nuevo cmdlet Get-AzureRmBillingPeriod
    + Cmdlet para recuperar los períodos de facturación de Azure correspondientes a la suscripción.
  - Actualización del cmdlet Get-AzureRmBillingInvoice
  - Nueva propiedad BillingPeriodNames
  - Resultados en vista de lista
* Proceso
  - Se actualizaron los cmdlets Set-AzureRmVMAEMExtension y Test-AzureRmVMAEMExtension para admitir Managed Disks Premium.
  - Copia de seguridad de la configuración de cifrado para las máquinas virtuales IaaS y restauración en caso de error
  - La opción ChefServiceInterval ahora se llama ChefDaemonInterval. Sin embargo, el nombre anterior seguirá funcionando.
  - Eliminación de las propiedades DataDiskNames y NetworkInterfaceIDs duplicadas del objeto de VM PS.
  - Los parámetros DataDiskNames y NetworkInterfaceIDs ahora son opcionales en Remove-AzureRmVMDataDisk y Remove-AzureRmVMNetworkInterface, respectivamente.
  - Corrección del problema de canalización de los cmdlets Get cuando estos devuelven un objeto de lista.
  - Se ha cambiado el nombre a los cmdlets que daban problemas con los cmdlets de RDFE. Consulte el error https://github.com/Azure/azure-powershell/issues/2917 para más detalles.
    + El nombre de `New-AzureVMSqlServerAutoBackupConfig` ha cambiado a `New-AzureRmVMSqlServerAutoBackupConfig`
    + El nombre de `New-AzureVMSqlServerAutoPatchingConfig` ha cambiado a `New-AzureRmVMSqlServerAutoPatchingConfig`
    + El nombre de `New-AzureVMSqlServerKeyVaultCredentialConfig` ha cambiado a `New-AzureRmVMSqlServerKeyVaultCredentialConfig`
* Consumo
  - Nuevo cmdlet Get-AzureRmConsumptionUsageDetail
    + Cmdlet para recuperar detalles de uso de la suscripción.
* ContainerRegistry
  - Incorporación de cmdlets de PowerShell para Azure Container Registry.
    + New-AzureRmContainerRegistry
    + Get-AzureRmContainerRegistry
    + Update-AzureRmContainerRegistry
    + Remove-AzureRmContainerRegistry
    + Get-AzureRmContainerRegistryCredential
    + Update-AzureRmContainerRegistryCredential
    + Test-AzureRmContainerRegistryNameAvailability
* DataLakeAnalytics
  - Incorporación de compatibilidad con las funciones de obtención y enumerar paquetes de catálogo.
  - Incorporación de compatibilidad para mostrar los elementos de catálogo siguientes de elementos antecesores más detallados:
    + Tabla
    + TVF
    + Ver
    + Estadísticas
* DataLakeStore
  - Para `Import-AzureRMDataLakeStoreItem` y `Export-AzureRMDataLakeStoreItem`, el registro de seguimiento se deshabilitó de manera predeterminada para mejorar el rendimiento. Si desea habilitarlo, use los parámetros `-DiagnosticLogLevel` y `-DiagnosticLogPath`.
  - Se corrigió un error que, en algunas ocasiones, podría hacer que PowerShell se bloqueara cargar muchos archivos pequeños en ADLS.
* EventHub
  - Corrección de errores:
    + Corrección para el error del cmdlet Set-AzureRmEventHubNamespace: el valor de "Tier" no puede ser nulo, debería ser "SkuName".
    + Set-AzureRmEventHub: corrección del error "Referencia a objeto no establecida como instancia de un objeto" durante la actualización de EventHub.
* Información detallada
  - Add-AzureRm*AlertRule
    + Devuelve un único objeto: newResource, statusCode, requestId
  - Get-AzureRmAlertRule
    + Ahora la salida se enumera, en lugar de considerarse un único objeto. Su tipo no cambia, sigue siendo una lista.
  - Remove-AzureRmAlertRule
    + El código de estado sigue el código de estado devuelto por la solicitud; antes, era siempre Correcto.
  - Add-AzureRmAutoscaleSetting
    + Ahora devuelve un único objeto (no una lista como antes) que contiene statusCode, requestId y el recurso recién creado y actualizado.
    + El código de estado sigue el estado devuelto por la solicitud; antes, era siempre Correcto.
  - New-AzureRmAutoscaleRule
    + Se extendió el parámetro ScaleActionType, que ahora recibe los valores siguientes: ChangeCount, PercentChangeCount, ExactCount.
  - Remove-AzureRmAutoscaleSetting
    + El valor de statusCode en la salida sigue el valor de statusCode devuelto por la solicitud. Anteriormente, siempre era Correcto.
  - Get-AzureRMLogProfile
    + Ahora se enumera la salida. Antes se consideraba un único objeto. El tipo de la salida sigue siendo una lista, igual que antes.
  - Remove-AzureRmLogProfile
    + Se ha implementado el parámetro PassThru.
  - API de métricas
    + El SDK ahora recupera las métricas de MDM.
  - Get-AzureRmMetricDefinition
    + La salida sigue siendo una lista, pero ha cambiado la estructura.
  - Get-AzureRmMetric
    + La llamada ha cambiado. Esta es la nueva sintaxis: Get-AzureRmMetric ResourceId [MetricNames [TimeGrain] [AggregationType] [StartTime] [EndTime]] [DetailedOutput]
    + La salida es una lista y la estructura de sus elementos ha cambiado.
* KeyVault
  - Se ha agregado compatibilidad con la copia de seguridad y restauración de los secretos de KeyVault.
    + Es posible crear copias de seguridad de los secretos y restaurarlos, coincidiendo con la funcionalidad que actualmente se admite para las claves.

  - Los cmdlets de copia de seguridad para claves y secretos ahora aceptan un objeto correspondiente como parámetro de entrada.
    + El llamador puede encadenar operaciones de recuperación y copia de seguridad: Get-AzureKeyVaultKey -VaultName myVault -Name myKey | Backup-AzureKeyVaultKey

  - Los cmdlets de copia de seguridad admiten ahora un modificador -Force para sobrescribir un archivo existente.
    + Tenga en cuenta que ya no se iniciará el intento de sobrescribir un archivo existente sino que, en su lugar, se preguntará al usuario cómo proceder.
* LogicApp
  - Nuevos parámetros para los cmdlets de recuperación ante desastres de número de control de intercambio:
    + Parámetro opcional -AgreementType ("X12" o "Edifact") para especificar los números de control pertinentes.
* MachineLearning
  - Uso de la nueva versión del SDK de .NET para Azure Machine Learning e incorporación de un nuevo cmdlet.
    + Add-AzureRmMlWebServiceRegionalProperty
  - Correcciones menores en el texto de ayuda.
* Red
  - Se agregó el cmdlet Test-AzureRmNetworkWatcherConnectivity.
    + Devuelve información de conectividad de una máquina virtual de origen especificada y un destino.
    + Si no se puede establecer la conectividad entre el origen y el destino, el cmdlet devuelve detalles sobre el problema.
* Perfil
  - Se agregó el cmdlet "Send-Feedback" permite que un usuario inicie un conjunto de mensajes que envía comentarios al equipo de Azure PowerShell.
  - Se han quitado los siguientes alias ya que daban problemas con nombres de cmdlet existentes en el módulo de Azure:
    + `Enable-AzureDataCollection` (admitido por `Enable-AzureRmDataCollection`)
    + `Disable-AzureDataCollection` (admitido por `Disable-AzureRmDataCollection`)
* Retransmisión
  - Agrega cmdlets para Azure Relay, que permite que los usuarios creen y administren todos los recursos de Azure Relay.
    + `New-AzureRmRelayNamespace`
    + `Get-AzureRmRelayNamespace`
    + `Set-AzureRmRelayNamespace`
    + `Remove-AzureRmRelayNamespace`
    + `New-AzureRmWcfRelay`
    + `Get-AzureRmWcfRelay`
    + `Set-AzureRmWcfRelay`
    + `Remove-AzureRmWcfRelay`
    + `New-AzureRmRelayHybridConnection`
    + `Get-AzureRmRelayHybridConnection`
    + `Set-AzureRmRelayHybridConnection`
    + `Remove-AzureRmRelayHybridConnection`
    + `Test-AzureRmRelayName`
    + `Get-AzureRmRelayOperation`
    + `New-AzureRmRelayKey`
    + `Get-AzureRmRelayKey`
    + `New-AzureRmRelayAuthorizationRule`
    + `Get-AzureRmRelayAuthorizationRule`
    + `Set-AzureRmRelayAuthorizationRule`
    + `Remove-AzureRmRelayAuthorizationRule`
* Recursos
  - Compatibilidad con implementaciones entre grupos de recursos para New-AzureRmResourceGroupDeployment.
    + Ahora los usuarios pueden usar implementaciones anidadas para implementarlas en distintos grupos de recursos.
* ServiceBus

  - Corrección de errores: los valores de la propiedad del objeto de cola de ServiceBus se establecieron en "null"; el objeto se usa como parámetro de entrada en el cmdlet Set-AzureRmServiceBusQueue para actualizar la cola.
   - Las propiedades afectadas son LockDuration, EntityAvailabilityStatus, DuplicateDetectionHistoryTimeWindow, MaxDeliveryCount y MessageCount.
* ServiceFabric

  - Se agregaron cmdlets para Service Fabric.
    + Add-AzureRmServiceFabricApplicationCertificate: agrega un certificado que se usará como certificado de la aplicación.
    + Add-AzureRmServiceFabricClientCertificate: agrega un nombre común o una huella digital a la configuración del clúster para la autenticación de cliente.
    + Add-AzureRmServiceFabricClusterCertificate: agrega un certificado de clúster secundario al clúster para sustituir el certificado existente.
    + Add-AzureRmServiceFabricNodes: agrega nodos o máquinas virtuales de un tipo de nodo específico a un clúster.
    + Add-AzureRmServiceFabricNodeType: agrega un tipo de nodo o máquinas virtuales a un clúster existente.
    + Get-AzureRmServiceFabricCluster: obtiene los detalles del recurso del clúster.
    + New-AzureRmServiceFabricCluster: crea un nuevo clúster de ServiceFabric. Este comando tiene muchas sobrecargas para abarcar distintos escenarios.
    + Remove-AzureRmServiceFabricClientCertificate: quita un certificado de cliente e impide que se use para acceder a un clúster.
    + Remove-AzureRmServiceFabricClusterCertificate: quita un certificado de clúster e impide que se use para la seguridad del clúster.
    + Remove-AzureRmServiceFabricNodes: quita nodos de un tipo de nodo específico de un clúster.
    + Remove-AzureRmServiceFabricNodeType: quita un tipo de nodo de un clúster.
    + Remove-AzureRmServiceFabricSettings: quita uno o varios valores de configuración de ServiceFabric de un clúster.
    + Set-AzureRmServiceFabricSettings: agrega o actualiza uno o varios valores de configuración de ServiceFabric de un clúster.
    + Set-AzureRmServiceFabricUpgradeType: cambia el tipo de actualización de ServiceFabric de un clúster.
    + Update-AzureRmServiceFabricDurability: cambia el nivel de durabilidad de un clúster.
    + Update-AzureRmServiceFabricReliability: cambia el nivel de confiabilidad de un clúster.
* Sql
  - Se ha agregado el parámetro -SampleName a New-AzureRmSqlDatabase.
  - Actualizaciones a los cmdlets del grupo de conmutación por error
  - Eliminación de los parámetros "Tag"
  - Se han quitado los parámetros "PartnerResourceGroupName" y "PartnerServerName" del cmdlet Remove-AzureRmSqlDatabaseFailoverGroup.
  - Incorporación del parámetro "GracePeriodWithDataLossHours" a los cmdlets New- y Set-, que reemplazará finalmente a "GracePeriodWithDataLossHour".
  - La documentación se desarrolló y actualizó
  - Cambio de formato de los objetos devueltos y corrección de algunos errores en que los campos no siempre se rellenaban
  - Incorporación de las propiedades "DatabaseNames" y "PartnerLocation" en el objeto del grupo de conmutación por error
  - Corrección de error en que el cmdlet Switch- se devuelve inmediatamente en lugar de esperar que se complete la operación
  - Corrección de error de desbordamiento de enteros cuando se usan valores altos de períodos de gracia
  - Ajuste del período de gracia a un mínimo de 1 hora si se proporciona un valor inferior.
  - Eliminación de "Usage_Anomaly" de los valores aceptados para el parámetro "ExcludedDetectionType" del cmdlet Set-AzureRmSqlDatabaseThreatDetectionPolicy y el cmdlet Set-AzureRmSqlServerThreatDetectionPolicy.
* Almacenamiento
  - Actualización del SDK de SRP a 6.3.0
  - New/Set-AzureRmStorageAccount: incorporación de un parámetro nuevo para admitir EnableHttpsTrafficOnly
  - New/Set/Get-AzureRmStorageAccount: la cuenta de almacenamiento devuelta contiene un nuevo atributo EnableHttpsTrafficOnly
* Azure.Storage
  - Actualización a Biblioteca de cliente de Azure Storage 8.1.1 y Biblioteca de Azure Storage DataMovement 0.5.1
  - Incorporación de un cmdlet nuevo para admitir la característica Copia incremental de blob.
