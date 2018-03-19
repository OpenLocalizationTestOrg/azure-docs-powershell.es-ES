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
ms.date: 2/20/2018
ms.openlocfilehash: 61306d057c81f533267a452f7a7e11b839b09718
ms.sourcegitcommit: 20af779cd523c758d40e23d60eb989a4ef982d5c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2018
---
# <a name="release-notes"></a>Notas de la versión

Esta es una lista de los cambios realizados en esta versión de Azure PowerShell.

---

## <a name="550---march-2018"></a>5.5.0: marzo de 2018
#### <a name="azurermprofile"></a>AzureRM.Profile
* Se ha corregido un problema con la importación de alias
* Carga de la versión 10.0.3 de Newtonsoft.Json en paralelo con la versión 6.0.8

#### <a name="azurestorage"></a>Azure.Storage
* Compatibilidad con la característica de eliminación temporal
    - Enable-AzureStorageDeleteRetentionPolicy
    - Disable-AzureStorageDeleteRetentionPolicy
    - Get-AzureStorageBlob

#### <a name="azurermanalysisservices"></a>AzureRM.AnalysisServices
* Se ha corregido un problema con la importación de alias
* Se ha agregado compatibilidad con la característica de escalado horizontal del firewall y las consultas, así como compatibilidad con la versión de la API de 2017-08-01.

#### <a name="azurermautomation"></a>AzureRM.Automation
* Se ha corregido un problema con la importación de alias

#### <a name="azurermcdn"></a>AzureRM.Cdn
* Se ha corregido un problema con la importación de alias

#### <a name="azurermcognitiveservices"></a>AzureRM.CognitiveServices
* Se han actualizado notice.txt y el mensaje de aviso.

#### <a name="azurermcompute"></a>AzureRM.Compute
* "New-AzureRmVMSS" imprime las cadenas de conexión en el modo detallado.
* "New-AzureRmVMSS" admite dirección IP pública, reglas de equilibrio de carga y reglas NAT de entrada.
* Característica WriteAccelerator
    - Se ha agregado el parámetro modificador WriteAccelerator a los siguientes cmdlet: Set-AzureRmVMOSDisk Set-AzureRmVMDataDisk Add-AzureRmVMDataDisk Add-AzureRmVmssDataDisk
    - Se ha agregado el parámetro modificador OsDiskWriteAccelerator al siguiente cmdlet: Set-AzureRmVmssStorageProfile.
    - Se ha agregado el parámetro booleano OsDiskWriteAccelerator a los siguientes cmdlet: Update-AzureRmVM     Update-AzureRmVmss

#### <a name="azurermdatafactories"></a>AzureRM.DataFactories
* Se ha corregido el problema de cifrado de credenciales que producía un error no significativo en algunas operaciones de cifrado
* Se permite la compartición del entorno de ejecución de integración entre factorías de datos

#### <a name="azurermdatafactoryv2"></a>AzureRM.DataFactoryV2
* Se han agregado los parámetros "SetupScriptContainerSasUri" y "Edition" al comando "Set-AzureRmDataFactoryV2IntegrationRuntime" para habilitar la funcionalidad de selección de instalación personalizada y edición
* Se ha corregido el problema de cifrado de credenciales que producía un error no significativo en algunas operaciones de cifrado.
* Se permite la compartición del entorno de ejecución de integración entre factorías de datos

#### <a name="azurermhdinsight"></a>AzureRM.HDInsight
* Se ha corregido un problema con la importación de alias

#### <a name="azurermkeyvault"></a>AzureRM.KeyVault
* Se ha corregido el ejemplo de Set-AzureRmKeyVaultAccessPolicy

#### <a name="azurermnetwork"></a>AzureRM.Network
* Se ha corregido un problema con la importación de alias

#### <a name="azurermoperationalinsights"></a>AzureRM.OperationalInsights
* Se ha corregido un problema con la importación de alias

#### <a name="azurermrecoveryservices"></a>AzureRM.RecoveryServices
* Se ha corregido un problema con la importación de alias

#### <a name="azurermrecoveryservicessiterecovery"></a>AzureRM.RecoveryServices.SiteRecovery
* Se ha corregido un problema con la importación de alias

#### <a name="azurermresources"></a>AzureRM.Resources
* Se ha corregido un problema con la importación de alias

#### <a name="azurermservicebus"></a>AzureRM.ServiceBus
* Se ha agregado la propiedad EnableBatchedOperations a Queue
* Se ha agregado la propiedad DeadLetteringOnFilterEvaluationExceptions a Subscriptions

#### <a name="azurermservicefabric"></a>AzureRM.ServiceFabric
* Actualización del cmdlet de Service Fabric
  - Se han actualizado las plantillas de ARM
  - Las operaciones con errores ya no se revierten
  - Add-AzureRmServiceFabricNodeType
    - El valor predeterminado para las máquinas virtuales es discos administrados
    - Se utiliza la subred del conjunto de escalado de máquinas virtuales existente
    - Todas las operaciones son idempotentes
  - Remove-AzureRmServiceFabricNodeType limpia los conjuntos de escalado de máquinas virtuales y los tipos de nodo de clúster creados parcialmente
  - Se ha corregido la salida del objeto PSCluster para tipos de propiedad complejos

#### <a name="azurermsql"></a>AzureRM.Sql
* Se ha corregido un problema con la importación de alias
* La respuesta de Get-AzureRmSqlServer, New-AzureRmSqlServer y Remove-AzureRmSqlServer ahora incluye la propiedad FullyQualifiedDomainName.

#### <a name="azurermwebsites"></a>AzureRM.Websites
* Se ha corregido un problema con la importación de alias
* New-AzureRMWebApp: se ha agregado un conjunto de parámetros para la creación simplificada de aplicaciones web, con compatibilidad con el repositorio de git local.

## <a name="540---february-2018"></a>5.4.0: febrero de 2018
#### <a name="azurermautomation"></a>AzureRM.Automation
* Se ha agregado un alias de New-AzureRmAutomationModule a Import-AzureRmAutomationModule

#### <a name="azurermcompute"></a>AzureRM.Compute
* Se ha corregido el problema de ErrorAction en algunos de los cmdlet Get.

#### <a name="azurermcontainerinstance"></a>AzureRM.ContainerInstance
* Se aplica al SDK de Azure Container Instances de 2018-02-01
    - Compatibilidad con etiqueta de nombre DNS

#### <a name="azurermdevtestlabs"></a>AzureRM.DevTestLabs
* Se han corregido todos los cmdlet GET que no funcionaban anteriormente.

#### <a name="azurermeventhub"></a>AzureRM.EventHub
* Se ha corregido un error en Get-AzureRmEventHubGeoDRConfiguration help

#### <a name="azurermnetwork"></a>AzureRM.Network
* Se ha agregado un cmdlet para crear un nuevo monitor de conexión
    - New-AzureRmNetworkWatcherConnectionMonitor
* Se ha agregado un cmdlet para actualizar un monitor de conexión
    - Set-AzureRmNetworkWatcherConnectionMonitor
* Se ha agregado un cmdlet para obtener el monitor de conexión o la lista de monitores de conexión
    - Get-AzureRmNetworkWatcherConnectionMonitor
* Se ha agregado un cmdlet para consultar un monitor de conexión
    - Get-AzureRmNetworkWatcherConnectionMonitorReport
* Se ha agregado un cmdlet para iniciar un monitor de conexión
    - Start-AzureRmNetworkWatcherConnectionMonitor
* Se ha agregado un cmdlet para detener un monitor de conexión
    - Stop-AzureRmNetworkWatcherConnectionMonitor
* Se ha agregado un cmdlet para eliminar un monitor de conexión
    - Remove-AzureRmNetworkWatcherConnectionMonitor
* Se ha actualizado la documentación de Set-AzureRmApplicationGatewayBackendAddressPool para eliminar un ejemplo en desuso
* Se ha agregado la marca EnableHttp2 a Application Gateway
    - Se ha actualizado New-AzureRmApplicationGateway: se ha agregado el parámetro opcional -EnableHttp2
* Se ha agregado IpTags a PublicIpAddress
    - Se ha actualizado New-AzureRmPublicIpAddress: se ha agregado IpTags
    - Se ha agregado Iptag a New-AzureRmPublicIpTag
* Se ha agregado la propiedad DisableBgpRoutePropagation en RouteTable y effectiveRoute.

#### <a name="azurermresources"></a>AzureRM.Resources
* Register-AzureRmProviderFeature: se ha agregado un ejemplo que faltaba en la documentación
* Register-AzureRmResourceProvider: se ha agregado un ejemplo que faltaba en la documentación

#### <a name="azurermstorage"></a>AzureRM.Storage
* Son obsoletos los siguientes parámetros en los cmdlet para una nueva cuenta de almacenamiento y para establecer una cuenta de almacenamiento: EnableEncryptionService y DisableEncryptionService, ya que el cifrado en reposo está habilitado de forma predeterminada y no se puede deshabilitar.
    - New-AzureRmStorageAccount
    - Set-AzureRmStorageAccount


## <a name="530---february-2018"></a>5.3.0: febrero de 2018
### <a name="azurermprofile"></a>AzureRM.Profile
* Se ha agregado la advertencia de desuso para PowerShell 3 y 4
* Se ha cambiado el nombre de `Add-AzureRmAccount` a `Connect-AzureRmAccount`; se ha agregado un alias para el antiguo nombre del cmdlet y se han redirigido otros alias (`Login-AzAccount` y `Login-AzureRmAccount`) al nuevo nombre del cmdlet.
* Se ha cambiado el nombre de `Remove-AzureRmAccount` a `Disconnect-AzureRmAccount`; se ha agregado un alias para el antiguo nombre del cmdlet y se han redirigido otros alias (`Logout-AzAccount` y `Logout-AzureRmAccount`) al nuevo nombre del cmdlet.
* Se han corregido las cadenas de recursos para que utilicen `Connect-AzureRmAccount` en lugar de `Login-AzureRmAccount`
* `Add-AzureRmEnvironment` y `Set-AzureRmEnvironment`
  - Se han agregado `-AzureOperationalInsightsEndpoint` y `-AzureOperationalInsightsEndpointResourceId` como parámetros para su uso con el RP del plano de datos de OperationalInsights.

### <a name="azurermanalysisservices"></a>AzureRM.AnalysisServices
* Se ha corregido el uso de `Login-AzureRmAccount` para que utilice `Connect-AzureRmAccount`

### <a name="azurermcompute"></a>AzureRM.Compute
* Se ha agregado el parámetro `-AvailabilitySetName` al conjunto de parámetros simplificado de `New-AzureRmVM`.
* Se ha corregido el uso de `Login-AzureRmAccount` para que utilice `Connect-AzureRmAccount`
* Compatibilidad con la identidad asignada por el usuario en máquinas virtuales y conjuntos de escalado de máquinas virtuales
    - Se han agregado los parámetros `-IdentityType` y `-IdentityId` a `New-AzureRmVMConfig`, `New-AzureRmVmssConfig`, `Update-AzureRmVM` y `Update-AzureRmVmss`
* Se ha agregado el parámetro `-EnableIPForwarding` a `Add-AzureRmVmssNetworkInterfaceConfig`
* Se ha agregado el parámetro `-Priority` a `New-AzureRmVmssConfig`

### <a name="azurermdatalakeanalytics"></a>AzureRM.DataLakeAnalytics
* Se ha corregido el uso de `Login-AzureRmAccount` para que utilice `Connect-AzureRmAccount`

### <a name="azurermdatalakestore"></a>AzureRM.DataLakeStore
* Se ha corregido el uso de `Login-AzureRmAccount` para que utilice `Connect-AzureRmAccount`
* Se ha corregido el mensaje de error de `Test-AzureRmDataLakeStoreAccount` cuando se ejecuta este cmdlet sin haber iniciado sesión con `Login-AzureRmAccount`

### <a name="azurermeventgrid"></a>AzureRM.EventGrid
* Se actualizó para usar la versión 2018-01-01 de la API.

### <a name="azurermeventhub"></a>AzureRM.EventHub
* Se han agregado los nuevos comandos siguientes para las operaciones de recuperación geográfica ante desastres.
    - Crear un nuevo alias (configuración de la recuperación ante desastres): - `New-AzureRmEventHubGeoDRConfiguration` - Recuperar un alias (configuración de la recuperación ante desastres): - `Get-AzureRmEventHubGeoDRConfiguration` - Deshabilitar la recuperación ante desastres y detener la replicación de cambios del espacio de nombres principal al secundario - `Set-AzureRmEventHubGeoDRConfigurationBreakPair` - Invocar la conmutación por error de la recuperación ante desastres y volver a configurar el alias para que apunte al espacio de nombres secundario - `Set-AzureRmEventHubGeoDRConfigurationFailOver` - Eliminar un alias (configuración de la recuperación ante desastres): `Remove-AzureRmEventHubGeoDRConfiguration`
* Se han agregado los siguientes nuevos comandos para comprobar el nombre del espacio de nombres y la disponibilidad del nombre o alias de la configuración de la recuperación geográfica ante desastres.
    - Comprobar la disponibilidad del nombre del espacio de nombres o del nombre del alias (configuración de la recuperación ante desastres): - `Test-AzureRmEventHubName`

### <a name="azurerminsights"></a>AzureRM.Insights
* Se ha corregido el uso de `Login-AzureRmAccount` para que utilice `Connect-AzureRmAccount`

### <a name="azurermkeyvault"></a>AzureRM.KeyVault
* Se ha corregido el uso de `Login-AzureRmAccount` para que utilice `Connect-AzureRmAccount`

### <a name="azurermnetwork"></a>AzureRM.Network
* Se ha corregido el mensaje de sobrescritura "está seguro de que desea sobrescribir el recurso"

#### <a name="azurermoperationalinsights"></a>AzureRM.OperationalInsights
* Se ha agregado compatibilidad para la consulta de la API V2 a través de `Invoke-AzureRmOperationalInsightsQuery`. Consulte [https://dev.loganalytics.io/](https://dev.loganalytics.io/) para más información sobre la nueva API.

### <a name="azurermresources"></a>AzureRM.Resources
* `Get-AzureRmADServicePrincipal`: se ha eliminado `-ServicePrincipalName` del conjunto de parámetros vacío predeterminado por ser redundante con el conjunto de parámetros de SPN

### <a name="azurermservicebus"></a>AzureRM.ServiceBus
* Se ha agregado una corrección de funcionalidad a `Remove-AzureRmServiceBusRule` y `Get-AzureRmServiceBusKey`
* Se han agregado los nuevos cmdlets siguientes para las operaciones de recuperación geográfica ante desastres.
    - Crear un nuevo alias (configuración de la recuperación ante desastres): - `New-AzureRmServiceBusDRConfigurations` - Recuperar un alias (configuración de la recuperación ante desastres): - `Get-AzureRmServiceBusDRConfigurations` - Deshabilitar la recuperación ante desastres y detener la replicación de cambios del espacio de nombres principal al secundario - `Set-AzureRmServiceBusDRConfigurationsBreakPairing` - Invocar la conmutación por error de la recuperación ante desastres y volver a configurar el alias para que apunte al espacio de nombres secundario - `Set-AzureRmServiceBusDRConfigurationsFailOver` - Eliminar un alias (configuración de la recuperación ante desastres): `Remove-AzureRmServiceBusDRConfigurations`
* Se han actualizado los cmdlets `Test-AzureRmServiceBusName` para admitir las operaciones para comprobar la disponibilidad del nombre de alias de la recuperación geográfica ante desastres.
    - Comprobar la disponibilidad del nombre del espacio de nombres o del nombre del alias (configuración de la recuperación ante desastres): - `Test-AzureRmServiceBusName`

### <a name="azurermusageaggregates"></a>AzureRM.UsageAggregates
* Se ha corregido el uso de `Login-AzureRmAccount` para que utilice `Connect-AzureRmAccount`

## <a name="520---january-2018"></a>5.2.0 - enero de 2018
#### <a name="azurermprofile"></a>AzureRM.Profile
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual
* Add-AzureRmAccount
  * Se ha agregado inicio de sesión -MSI para la autenticación con las credenciales de la identidad de servicio administrada de la máquina virtual actual o el servicio
  * Se ha corregido la autenticación de Key Vault en el inicio de sesión con tokens de acceso proporcionados por el usuario

#### <a name="azurestorage"></a>Azure.Storage
* Se han agregado cmdlets para obtener y establecer las propiedades del servicio de almacenamiento
    - Get-AzureStorageServiceProperty
    - Update-AzureStorageServiceProperty

#### <a name="azurermanalysisservices"></a>AzureRM.AnalysisServices
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual

#### <a name="azurermapimanagement"></a>AzureRM.ApiManagement
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual
* Se ha establecido como obsoleto -Tags en favor de -Tag para New-AzureRmApiManagementProperty, Set-AzureRmApiManagementProperty y New-AzureRmApiManagement

#### <a name="azurermapplicationinsights"></a>AzureRM.ApplicationInsights
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual

#### <a name="azurermautomation"></a>AzureRM.Automation
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual
* Se ha establecido como obsoleto -Tags en favor de -Tag para Set-AzureRmAutomationRunbook

#### <a name="azurermbackup"></a>AzureRM.Backup
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual

#### <a name="azurermbatch"></a>AzureRM.Batch
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual

#### <a name="azurermcdn"></a>AzureRM.Cdn
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual
* Se ha establecido como obsoleto -Tags en favor de -Tag para New-AzureRmCdnEndpoint y New-AzureRmCdnProfile

#### <a name="azurermcognitiveservices"></a>AzureRM.CognitiveServices
* Integración con la versión 3.0.0 del SDK de administración de Cognitive Services.

#### <a name="azurermcompute"></a>AzureRM.Compute
* Se agregó un conjunto de parámetros simplificado a New-AzureRmVmss, que crea un conjunto de escalado de máquinas virtuales y todos los recursos necesarios con valores predeterminados inteligentes
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual
* Se ha establecido como obsoleto -Tags en favor de -Tag para New-AzureRmVm y Update-AzureRmVm
* Se ha corregido el cmdlet Get-AzureRmComputeResourceSku cuando la zona está incluida en una restricción.
* Se ha actualizado el esquema de configuración del agente de diagnósticos para compatibilidad con el receptor de Azure Monitor.

#### <a name="azurermcontainerinstance"></a>AzureRM.ContainerInstance
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual

#### <a name="azurermcontainerregistry"></a>AzureRM.ContainerRegistry
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual

#### <a name="azurermdatafactories"></a>AzureRM.DataFactories
* Se ha habilitado la compatibilidad con Azure Key Vault para todos los servicios vinculados al almacén de datos
* Se ha agregado la propiedad tipo de licencia al entorno de ejecución de integración SSIS de Azure
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual
* Se ha establecido como obsoleto -Tags en favor de -Tag para New-AzureRmDataFactory

#### <a name="azurermdatafactoryv2"></a>AzureRM.DataFactoryV2
* Se ha habilitado la compatibilidad con Azure Key Vault para todos los servicios vinculados al almacén de datos
* Se ha agregado la propiedad tipo de licencia al entorno de ejecución de integración SSIS de Azure
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual
* Agregue el parámetro "LicenseType" al comando "Set-AzureRmDataFactoryV2IntegrationRuntime" para habilitar la funcionalidad AHUB

#### <a name="azurermdatalakeanalytics"></a>AzureRM.DataLakeAnalytics
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual
* Se ha establecido como obsoleto -Tags en favor de -Tag para New-AzureRmDataLakeAnalyticsAccount y Set-AzureRmDataLakeAnalyticsAccount

#### <a name="azurermdatalakestore"></a>AzureRM.DataLakeStore
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual
* Se ha establecido como obsoleto -Tags en favor de -Tag para New-AzureRmDataLakeStoreAccount y Set-AzureRmDataLakeStoreAccount

#### <a name="azurermdevtestlabs"></a>AzureRM.DevTestLabs
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual

#### <a name="azurermdns"></a>AzureRM.Dns
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual

#### <a name="azurermeventgrid"></a>AzureRM.EventGrid
* Se ha agregado el siguiente cmdlet nuevo:
    - Update-AzureRmEventGridSubscription
        - Se han actualizado las propiedades de una suscripción a eventos de Event Grid.
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual

#### <a name="azurermeventhub"></a>AzureRM.EventHub
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual

#### <a name="azurermhdinsight"></a>AzureRM.HDInsight
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual

#### <a name="azurerminsights"></a>AzureRM.Insights
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual

#### <a name="azurermiothub"></a>AzureRM.IotHub
* Se ha agregado compatibilidad con la adición de certificado a los cmdlets de IoTHub
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual

#### <a name="azurermkeyvault"></a>AzureRM.KeyVault
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual
* Se agregó compatibilidad con -AsJob para cmdlets de KeyVault de ejecución prolongada. Se permite que cmdlets seleccionados se ejecuten en segundo plano y devuelvan un trabajo para realizar un seguimiento y controlar el progreso.
    * El cmdlet afectado es: Remove-AzureRmKeyVault
* Se ha corregido un error en Set-AzureRmKeyVaultAccessPolicy en el que el filtro de AAD establecía el SPN en el UPN proporcionado, en lugar de establecer el UPN
   - Consulte el siguiente problema para más información: https://github.com/Azure/azure-powershell/issues/5201

#### <a name="azurermlogicapp"></a>AzureRM.LogicApp
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual

#### <a name="azurermmachinelearning"></a>AzureRM.MachineLearning
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual
* Se ha establecido como obsoleto -Tags en favor de -Tag para Update-AzureRmMlCommitmentPlan

#### <a name="azurermmachinelearningcompute"></a>AzureRM.MachineLearningCompute
* Se ha agregado el parámetro IncludeAllResources al cmdlet Remove-AzureRmMlOpCluster
    - Con este parámetro modificador se eliminarán todos los recursos que se crearon originalmente con el clúster
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual

#### <a name="azurermmedia"></a>AzureRM.Media
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual
* Se ha establecido como obsoleto -Tags en favor de -Tag para Set-AzureRmMediaService y New-AzureRmMediaService

#### <a name="azurermnetwork"></a>AzureRM.Network
* Se ha agregado compatibilidad con -AsJob a los cmdlets de red de ejecución prolongada. Se permite que cmdlets seleccionados se ejecuten en segundo plano y devuelvan un trabajo para realizar un seguimiento y controlar el progreso.
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual

#### <a name="azurermnotificationhubs"></a>AzureRM.NotificationHubs
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual
* Se ha establecido como obsoleto -Tags en favor de -Tag para New-AzureRmNotificationHubsNamespace y Set-AzureRmNotificationHubsNamespace

#### <a name="azurermoperationalinsights"></a>AzureRM.OperationalInsights
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual
* Se ha establecido como obsoleto -Tags en favor de -Tag para New-AzureRmOperationalInsightsSavedSearch, Set-AzureRmOperationalInsightsSavedSearch, New-AzureRmOperationalInsightsWorkspace y Set-AzureRmOperationalInsightsWorkspace

#### <a name="azurermpowerbiembedded"></a>AzureRM.PowerBIEmbedded
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual

#### <a name="azurermrecoveryservices"></a>AzureRM.RecoveryServices
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual

#### <a name="azurermrecoveryservicesbackup"></a>AzureRM.RecoveryServices.Backup
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual
* Se ha agregado la opción -UseOriginalStorageAccount al cmdlet Restore-AzureRmRecoveryServicesBackupItem.
    - La habilitación de esta marca se traduce en la restauración de los discos a sus cuentas de almacenamiento originales, lo que permite a los usuarios mantener la configuración de la máquina virtual restaurada tan similar a las máquinas virtuales originales como sea posible.
    - También ayuda a mejorar el rendimiento de la operación de restauración.

#### <a name="azurermrediscache"></a>AzureRM.RedisCache
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual
* Se han agregado 3 nuevos cmdlets para reglas del firewall
* Se han agregado 3 nuevos cmdlets para la replicación geográfica
* Se ha agregado compatibilidad con etiquetas y zonas
* Se ha convertido ResourceGroup en opcional en los casos posibles.

#### <a name="azurermrelay"></a>AzureRM.Relay
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual

#### <a name="azurermresources"></a>AzureRM.Resources
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual
* Se ha agregado compatibilidad con -AsJob a los cmdlets de recursos de ejecución prolongada. Se permite que cmdlets seleccionados se ejecuten en segundo plano y devuelvan un trabajo para realizar un seguimiento y controlar el progreso.
* Se ha agregado el alias Get-AzureRmProviderOperation a Get-AzureRmResourceProviderAction para cumplir con las convenciones de nomenclatura

#### <a name="azurermscheduler"></a>AzureRM.Scheduler
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual

#### <a name="azurermservermanagement"></a>AzureRM.ServerManagement
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual
* Se ha establecido como obsoleto -Tags en favor de -Tag para New-AzureRmServerManagementNode y New-AzureRmServerManagementGateway

#### <a name="azurermservicebus"></a>AzureRM.ServiceBus
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual

#### <a name="azurermservicefabric"></a>AzureRM.ServiceFabric
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual

#### <a name="azurermsiterecovery"></a>AzureRM.SiteRecovery
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual

#### <a name="azurermsql"></a>AzureRM.Sql
* Se ha actualizado la descripción de los parámetros de los comandos de auditoría
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual
* Se ha agregado el parámetro - AsJob a los cmdlets de larga ejecución
* Se ha establecido como obsoleto el parámetro -DatabaseName de Get-AzureRmSqlServiceObjective

#### <a name="azurermstorage"></a>AzureRM.Storage
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual
* Se ha corregido un problema de referencia nula en la ejecución del cmdlet New-AzureRMStorageAccount con el parámetro -EnableEncryptionService None
* Se ha agregado compatibilidad con -AsJob a los cmdlets de almacenamiento de ejecución prolongada. Se permite que cmdlets seleccionados se ejecuten en segundo plano y devuelvan un trabajo para realizar un seguimiento y controlar el progreso.
    - Los cmdlets afectados son New-, Remove-, Add- y Update- de la cuenta de almacenamiento y la regla de red de la cuenta de almacenamiento.

#### <a name="azurermstreamanalytics"></a>AzureRM.StreamAnalytics
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual

#### <a name="azurermtrafficmanager"></a>AzureRM.TrafficManager
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual

#### <a name="azurermwebsites"></a>AzureRM.Websites
* Se ha agregado una función de autocompletar la ubicación a los parámetros -Location que posibilita la función de autocompletar con el tabulador entre las distintas ubicaciones válidas
* Se ha agregado una función de autocompletar grupos de recursos a los parámetros -ResourceGroup que posibilita la función de autocompletar con el tabulador en los grupos de recursos de la suscripción actual
* Se ha agregado compatibilidad con -AsJob a los cmdlets de Websites de ejecución prolongada. Se permite que cmdlets seleccionados se ejecuten en segundo plano y devuelvan un trabajo para realizar un seguimiento y controlar el progreso.
     - Los cmdlets afectados son New-, Remove-, Add- y Set- para aplicaciones WebApps, AppServicePlan y Slots

## <a name="2017128-version-511"></a>2017.12.8 versión 5.1.1
* AnalysisServices
    - Cambio de la validación del conjunto de ubicación a búsqueda dinámica para admitir todas las nubes.
* Automation
    - Actualización a Import-AzureRMAutomationRunbook
        - Ahora se admiten runbooks de Python2
* Batch
    - Se ha corregido un error por el que las operaciones de cuenta sin un grupo de recursos no detectaban automáticamente el grupo de recursos
* Proceso
    - Get-AzureRmComputeResourceSku muestra información de zona.
    - Se ha actualizado Disable-AzureRmVmssDiskEncryption para corregir el problema https://github.com/Azure/azure-powershell/issues/5038
    - Se agregó compatibilidad con -AsJob para cmdlets de Compute de ejecución prolongada. Se permite que cmdlets seleccionados se ejecuten en segundo plano y devuelvan un trabajo para realizar un seguimiento y controlar el progreso.
        - Los cmdlets afectados incluyen: cmdlets New-, Update-, Set-, Remove-, Start-, Restart-, Stop- para máquinas virtuales y conjuntos de escalado de máquinas virtuales
    - Se agregó un conjunto de parámetros simplificado a New-AzureRmVM, que crea una máquina virtual y todos los recursos necesarios con valores predeterminados inteligentes
* ContainerInstance
    - Se aplica al SDK de Azure Container Instances de 2017-10-01
        - Se admite la ejecución hasta su finalización de contenedores
        - Se admite el montaje de volumen de Azure File
        - Se admite la apertura de varios puertos para la dirección IP pública
* ContainerRegistry
    - Nuevos cmdlets para replicación geográfica y webhooks
        - Get/New/Remove-AzureRmContainerRegistryReplication
        - Get/New/Remove/Test/Update-AzureRmContainerRegistryWebhook
* DataFactories
    - La funcionalidad de cifrado de credenciales funciona ahora con "Acceso remoto" habilitado (a través de red) y con "Acceso remoto" deshabilitado (equipo local).
* DataFactoryV2
    - Se agregaron dos nuevos cmdlets: Update-AzureRmDataFactoryV2 y Stop-AzureRmDataFactoryV2PipelineRun
* DataLakeAnalytics
    - Se agregó un parámetro llamado ScriptParameter a Submit-AzureRmDataLakeAnalyticsJob
        - Puede encontrar información detallada sobre ScriptParameter utilizando Get-Help en Submit-AzureRmDataLakeAnalyticsJob
    - Se cambió el parámetro MaxDegreeOfParallelism a MaxAnalyticsUnits en New-AzureRmDataLakeAnalyticsAccount
        - Se agregó un alias para el parámetro MaxAnalyticsUnits: MaxDegreeOfParallelism
    - Se cambió el parámetro MaxDegreeOfParallelismPerJob a MaxAnalyticsUnitsPerJob en New-AzureRmDataLakeAnalyticsComputePolicy
        - Se agregó un alias para el parámetro MaxAnalyticsUnitsPerJob: MaxDegreeOfParallelismPerJob
    - Se cambió el parámetro MaxDegreeOfParallelism a MaxAnalyticsUnits en Set-AzureRmDataLakeAnalyticsAccount
        - Se agregó un alias para el parámetro MaxAnalyticsUnits: MaxDegreeOfParallelism
    - Se cambió el parámetro DegreeOfParallelism a AnalyticsUnits en Submit-AzureRmDataLakeAnalyticsJob
        - Se agregó un alias para el parámetro AnalyticsUnits: DegreeOfParallelism
    - Se cambió el parámetro MaxDegreeOfParallelismPerJob a MaxAnalyticsUnitsPerJob en Update-AzureRmDataLakeAnalyticsComputePolicy
        - Se agregó un alias para el parámetro MaxAnalyticsUnitsPerJob: MaxDegreeOfParallelismPerJob
* MachineLearningCompute
    - Se agregó Set-AzureRmMlOpCluster
        - Actualización del número de agentes o la configuración SSL de un clúster
    - Las propiedades del orquestador son opcionales
        - El servicio creará una entidad de servicio si no se proporciona, por lo que las propiedades del orquestador ahora son opcionales
* PowerBIEmbedded
    - Se agregó compatibilidad con los cmdlets de capacidad de Power BI Embedded
    - Nuevo cmdlet Get-AzureRmPowerBIEmbeddedCapacity: obtiene los detalles de una capacidad de Power BI Embedded.
    - Nuevo cmdlet New-AzureRmPowerBIEmbeddedCapacity: crea una nueva capacidad de Power BI Embedded
    - Nuevo cmdlet Remove-AzureRmPowerBIEmbeddedCapacity: elimina una instancia de una capacidad de Power BI Embedded
    - Nuevo cmdlet Resume-AzureRmPowerBIEmbeddedCapacity: reanuda una instancia de una capacidad de Power BI Embedded
    - Nuevo cmdlet Suspend-AzureRmPowerBIEmbeddedCapacity: suspende una instancia de una capacidad de Power BI Embedded
    - Nuevo cmdlet Test-AzureRmPowerBIEmbeddedCapacity: comprueba la existencia de una instancia de una capacidad de Power BI Embedded
    - Nuevo cmdlet Update-AzureRmPowerBIEmbeddedCapacity: modifica una instancia de una capacidad de Power BI Embedded
* Perfil
    - Se ha actualizado USGovernmentActiveDirectoryEndpoint a https://login.microsoftonline.us/
        - Para más información sobre las asignaciones de punto de conexión de Azure Government, consulte la siguiente documentación: https://docs.microsoft.com/en-us/azure/azure-government/documentation-government-developer-guide#endpoint-mapping
    - Se agregó compatibilidad con -AsJob para los cmdlets, lo que permite que cmdlets seleccionados se ejecuten en segundo plano y devuelvan un trabajo para realizar un seguimiento y controlar el progreso
    - Se agregó el parámetro -AsJob al cmdlet Get-AzureRmSubscription
* RecoveryServices.Backup
    - Error corregido: Get-AzureRmRecoveryServicesBackupItem debe hacer una comparación sin distinción entre mayúsculas y minúsculas para el filtro de nombre de contenedor.
    - Error corregido: AzureVmItem ahora tiene una propiedad que muestra la última vez que se ha producido una operación de copia de seguridad, LastBackupTime.
* Recursos
    - Se corrigió un problema por el que Get-AzureRMRoleAssignment producía asignaciones sin nombre de definición de rol para los roles personalizados
        - Los usuarios ahora pueden usar Get-AzureRMRoleAssignment con asignaciones en las que los nombres de definición de rol son independientes del tipo de rol
    - Se corrigió un problema en el que Set-AzureRMRoleRoleDefinition generaba un error "definición de roles no encontrada" cuando había un nuevo ámbito en assignablescopes
        - Los usuarios ahora pueden usar Set-AzureRMRoleRoleDefinition con ámbitos asignables incluidos los nuevos ámbitos independientes de la posición del ámbito
    - Se permite que los ámbitos finalicen con "/"
        - Los usuarios ahora pueden usar los cmdlets RoleDefinition y RoleAssignment con ámbitos que terminan con "/", de un modo coherente con la API y la CLI
    - Se permite a los usuarios crear RoleAssignment utilizando marcas de delegación
        - Los usuarios ahora pueden utilizar New-AzureRMRoleAssignment con una opción de agregar la marca de delegación
    - Se corrigió RoleAssignment get para respetar el parámetro de ámbito
    - Se agregó un alias para ServicePrincipalName en el cmdlet New-AzureRmRoleAssignment
        - Los usuarios ahora pueden usar ApplicationId en lugar de ServicePrincipalName con el cmdlet New-AzureRmRoleAssignment
* SiteRecovery
    - Se agregaron advertencias sobre el desuso de todos los cmdlets de este módulo como preparación para los importantes cambios de la próxima versión.
        - Consulte la guía de los próximos cambios para más información sobre cómo migrar sus cmdlets de AzureRM.
* Sql
    - Se agregó la posibilidad de cambiar de nombre la base de datos con Set-AzureRmSqlDatabase
    - Se ha corregido el problema https://github.com/Azure/azure-powershell/issues/4974
        - Ya no se produce un error cuando se proporciona un valor de AUDIT_CHANGED_GROUP no válido para los cmdlets de auditoría y se quitará en una próxima versión.
    - Se ha corregido el problema https://github.com/Azure/azure-powershell/issues/5046
        - Ya no se ignora el parámetro AuditAction en los cmdlets de auditoría
    - Se corrigió un problema en los cmdlets de auditoría cuando se proporciona el valor "Secondary" para StorageKeyType
        - Al configurar la auditoría de blobs, se usaba la clave principal de la cuenta de almacenamiento en lugar de la clave secundaria al proporcionar el valor "Secondary" para el parámetro StorageKeyType.
    - Se cambió el texto del mensaje de confirmación de Set-AzureRmSqlServerTransparentDataEncryptionProtector
* Azure (RDFE)
    - Se eliminaron todos los cmdlet de RemoteApp
* Azure.Storage
    - Actualización a Azure Storage Client Library 8.6.0 y Azure Storage DataMovement Library 0.6.5

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
* NOTA: Esta es una versión con cambios importantes. Consulte la guía de migración (https://aka.ms/azps-migration-guide)) para una lista completa de los cambios importantes realizados.
* Todos los cmdlets de AzureRM ahora admiten la ayuda en línea
    - Ejecute Get-Help con el parámetro -Online para abrir la ayuda en línea en el explorador de Internet predeterminado
* AnalysisServices
    * Se corrigió el comando Synchronize-AzureAsInstance para que funcione la sincronización con la nueva API de REST de AsAzure
* ApiManagement
    * Consulte la guía de migración para más información sobre los cambios importantes realizados en ApiManagement en esta versión
    * Se ha actualizado el cmdlet Get-AzureRmApiManagementUser para solucionar el problema https://github.com/Azure/azure-powershell/issues/4510
    * Se ha actualizado el cmdlet New-AzureRmApiManagementApi para crear una API con ruta de acceso vacía https://github.com/Azure/azure-powershell/issues/4069
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
    * Correcciones https://github.com/Azure/azure-powershell/issues/3164
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
