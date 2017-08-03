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
ms.date: 07/26/2017
ms.openlocfilehash: cc2fe75f498f9043e5a4b632c144877af0143173
ms.sourcegitcommit: 20bcef86db4e4869125bb63085fcffd009c19280
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/27/2017
---
# <a name="release-notes"></a>Notas de la versión

Esta es una lista de los cambios realizados en esta versión de Azure PowerShell.

## <a name="20170717---version-421"></a>17/07/2017: versión 4.2.1
* Proceso
    - Solución del problema con el disco de VM y cmdlets de actualización y creación de instantáneas de disco de VM (vínculo) [https://github.com/azure/azure-powershell/issues/4309]
      - New-AzureRmDisk
      - New-AzureRmSnapshot
      - Update-AzureRmDisk
      - Update-AzureRmSnapshot
* Perfil
    - Solución de problemas con la autenticación de usuarios no interactivos (vínculo) en RDFE [https://github.com/Azure/azure-powershell/issues/4299]
* ServiceManagement
    - Solución de problemas con la autenticación de usuarios no interactivos (vínculo)[https://github.com/Azure/azure-powershell/issues/4299]

## <a name="2017711---version-420"></a>11/07/2017: versión 4.2.0
* AnalysisServices
    * Adición de la nueva API de dataplane
        - API de introducción para capturar el registro de servidor AS, Export-AzureAnalysisServicesInstanceLog
* Automation
    * Configuración correcta del valor TimeZone para programaciones semanales y mensuales para New-AzureRmAutomationSchedule
        - Puede encontrar más información en este problema: https://github.com/Azure/azure-powershell/issues/3043
* AzureBatch
    - Nuevo cmdlet Get-AzureBatchJobPreparationAndReleaseTaskStatus agregado.
    - Inicio y final del rango de bytes agregado a los parámetros de Get-AzureBatchNodeFileContent.
* CognitiveServices
    * Integración con la versión 1.0.0 del SDK de administración de Cognitive Services.
    * Solución de un error de comprobación de la longitud del nombre de cuenta.
* Proceso
    * Soporte técnico del tipo de cuenta de almacenamiento para el disco de imagen:
        - Parámetro 'StorageAccountType' agregado a Set-AzureRmImageOsDisk y Add-AzureRmImageDataDisk
    * Característica PrivateIP y PublicIP en la configuración de IP Vmss:
        - Los nombres 'PrivateIPAddressVersion', 'PublicIPAddressConfigurationName', 'PublicIPAddressConfigurationIdleTimeoutInMinutes', 'DnsSetting' se agregan a New-AzureRmVmssIpConfig
        - Parámetro 'PrivateIPAddressVersion' para la especificación de IPv4 o IPv6 agregado a New-AzureRmVmssIpConfig
    * Característica de mantenimiento del rendimiento:
        - Parámetro de conmutador 'PerformMaintenance' agregado a Restart-AzureRmVM.
        - Get-AzureRmVM -Status muestra la información de mantenimiento del rendimiento de la VM determinada
    * Característica de identidad de máquina virtual:
        - Parámetro 'IdentityType' agregado a New-AzureRmVMConfig y UpdateAzureRmVM
        - Get-AzureRmVM muestra la información de la identidad de la VM determinada
    * Característica de identidad de Vmss:
        - Parámetro 'IdentityType' agregado a New-AzureRmVmssConfig
        - Get-AzureRmVmss muestra la información de la identidad de un Vmss determinado
    * Característica de diagnósticos de arranque de Vmss:
        - Nuevo cmdlet para establecer el diagnóstico de arranque del objeto Vmss: Set-AzureRmVmssBootDiagnostics
        - Parámetro de 'BootDiagnostic' agregado a New-AzureRmVmssConfig
    * Característica de LicenseType de Vmss:
        - Parámetro 'LicenseType' agregado a New-AzureRmVmssConfig
    * Compatibilidad con RecoveryPolicyMode:
        - Parámetro 'RecoveryPolicyMode' agregado a New-AzureRmVmssConfig
    * Característica de SKU de recursos de proceso:
        - El nuevo cmdlet 'Get-AzureRmComputeResourceSku' muestra todos los SKU de recursos de proceso
* DataFactories
    * New-AzureRmDataFactoryGatewayKey en desuso
    * Presentación de la característica de clave de autenticación de puerta de enlace agregando New-AzureRmDataFactoryGatewayAuthKey y Get-AzureRmDataFactoryGatewayAuthKey
* DataLakeAnalytics
    * Adición de soporte técnico para CRUD de directiva de proceso a través de los siguientes comandos:
        - New-AzureRMDataLakeAnalyticsComputePolicy
        - Get-AzureRMDataLakeAnalyticsComputePolicy
        - Remove-AzureRMDataLakeAnalyticsComputePolicy
        - Update-AzureRMDataLakeAnalyticsComputePolicy
    * Agregue compatibilidad para los metadatos de relaciones de trabajo para ayudar en las canalizaciones de trabajo y los trabajos recurrentes. Se actualizan o agregan los siguientes comandos:
        - Submit-AzureRMDataLakeAnalyticsJob
        - Get-AzureRMDataLakeAnalyticsJob
        - Get-AzureRMDataLakeAnalyticsJobRecurrence
        - Get-AzureRMDataLakeAnalyticsJobPipeline
    * Audiencia de token actualizada para las API de trabajo y catálogo para usar la audiencia específica de Data Lake correcta en lugar de la audiencia de Azure Resource.
* DataLakeStore
    * Soporte técnico agregado para rotaciones de claves de KeyVault administradas en el cmdlet Set-AzureRMDataLakeStoreAccount
    * Calidad de actualización de vida agregada para activar automáticamente una llamada de `enableKeyVault` cuando se agrega un KeyVault de usuario administrado o se rota una clave.
    * Audiencia de token actualizada para las API de trabajo y catálogo para usar la audiencia específica de Data Lake correcta en lugar de la audiencia de Azure Resource.
    * Solución de error de limitación del tamaño de los archivos creados/anexados con los siguientes cmdlets:
        - New-AzureRmDataLakeStoreItem
        - Add-AzureRmDataLakeStoreItemContent
* Dns
    * Corrección de errores en el escenario de canalización para Get-AzureRmDnsZone
        - Puede encontrar más información aquí: https://github.com/Azure/azure-powershell/issues/4203
* HDInsight
    * Compatibilidad agregada para habilitar/deshabilitar Operations Management Suite(OMS)
    * Nuevos cmdlets
        - Enable-AzureRmHDInsightOperationsManagementSuite
        - Disable-AzureRmHDInsightOperationsManagementSuite
        - Get-AzureRmHDInsightOperationsManagementSuite
    * Adición de nuevos parámetros para establecer configuraciones personalizadas de Spark en Add-AzureRmHDInsightConfigValues
        - Parámetros SparkDefaults y SparkThriftConf para Spark 1.6
        - Parámetros Spark2Defaults y Spark2ThriftConf para Spark 2.0
* Información detallada
    * En el problema #4215 (solicitud de cambio) se quita el límite de 15 días en la ventana de tiempo para el cmdlet Get-AzureRmLog. También cambios secundarios en los nombres de prueba unitaria.
    * Problema n.º 3957 solucionado para Get-AzureRmLog
        - Problema n.º 1: el back-end devuelve registros en páginas de 200 registros, vinculados por el token de continuación a la siguiente página. Los clientes verán que el cmdlet devuelve solo 200 registros a pesar de que sabían que habían más. Esto sucedía independientemente del valor que establecen para MaxEvents, a no ser que ese valor sea inferior a 200.
        - Problema n.º 2: la documentación contenía datos incorrectos sobre este cmdlet, p. ej.: la ventana de tiempo predeterminada era de 1 hora.
        - Corrección n.º 1: el cmdlet ahora sigue el token de continuación devuelto por el back-end hasta que alcanza MaxEvents o el final del conjunto.<br>El valor predeterminado de MaxEvents es 1000 y el máximo es 100 000. Se ignora cualquier valor de MaxEvents inferior a 1 y se utiliza el valor predeterminado. Estos valores y el comportamiento no cambiaron, ahora están documentados correctamente.<br>Se ha agregado un alias para MaxEvents ,MaxRecords, puesto que el nombre del cmdlet no trata ya sobre los eventos, sino sobre los registros.
        - Corrección n.º 2: la documentación contiene información correcta y más detallada: nuevo alias, ventana de tiempo correcta, valor predeterminado correcto y valores mínimos y máximos.
* KeyVault
    * Quite la dirección de correo electrónico de la consultar de directorio cuando se especifique -UserPrincipalName en los cmdlets Set-AzureRMKeyVaultAccessPolicy y Remove-AzureRMKeyVaultAccessPolicy.
      - Ambos cmdlets tienen ahora un parámetro -EmailAddress que puede usarse en lugar del parámetro -UserPrincipalName cuando la consulta para la dirección de correo electrónico es adecuada.  Si hay más de una dirección de correo electrónico coincidente en el directorio, se producirá un error en el cmdlet.
* Red
    * New-AzureRmIpsecPolicy: SALifeTimeSeconds y SADataSizeKilobytes ya no son parámetros obligatorios
        - El valor predeterminado de SALifeTimeSeconds es de 27 000 segundos
        - El valor predeterminado de SADataSizeKilobytes es de 102 400 000 KB
    * Compatibilidad agregada para la configuración del conjunto de cifrado personalizado con la directiva SSL y enumeración de todas las API de opciones de SSL en Application Gateway
        - Parámetro opcional agregado: -PolicyType, -PolicyName, -MinProtocolVersion y -Ciphersuite
            - Add-AzureRmApplicationGatewaySslPolicy
            - New-AzureRmApplicationGatewaySslPolicy
            - Set-AzureRmApplicationGatewaySslPolicy
        - Get-AzureRmApplicationGatewayAvailableSslOptions agregado (Alias: List-AzureRmApplicationGatewayAvailableSslOptions)
        - Get-AzureRmApplicationGatewaySslPredefinedPolicy agregado (Alias: List-AzureRmApplicationGatewaySslPredefinedPolicy)
    * Compatibilidad de redireccionamiento agregada en Application Gateway
        - Add-AzureRmApplicationGatewayRedirectConfiguration agregado
        - Get-AzureRmApplicationGatewayRedirectConfiguration agregado
        - New-AzureRmApplicationGatewayRedirectConfiguration agregado
        - Remove-AzureRmApplicationGatewayRedirectConfiguration agregado
        - Set-AzureRmApplicationGatewayRedirectConfiguration agregado
        - Parámetro opcional agregado -RedirectConfiguration
            - Add-AzureRmApplicationGatewayRequestRoutingRule
            - New-AzureRmApplicationGatewayRequestRoutingRule
            - Set-AzureRmApplicationGatewayRequestRoutingRule
        - Parámetro opcional agregado -DefaultRedirectConfiguration
            - Add-AzureRmApplicationGatewayUrlPathMapConfig
            - New-AzureRmApplicationGatewayUrlPathMapConfig
            - Set-AzureRmApplicationGatewayUrlPathMapConfig
        - Parámetro opcional agregado -RedirectConfiguration
            - Add-AzureRmApplicationGatewayPathRuleConfig
            - New-AzureRmApplicationGatewayPathRuleConfig
            - Set-AzureRmApplicationGatewayPathRuleConfig
        - Parámetro opcional agregado -RedirectConfigurations
            - New-AzureRmApplicationGateway
            - Set-AzureRmApplicationGateway
    * Compatibilidad agregada para sitios web de Azure en Application Gateway
        - New-AzureRmApplicationGatewayProbeHealthResponseMatch agregado
        - Parámetros opcionales agregados -PickHostNameFromBackendHttpSettings, -MinServers y -Match
            - Add-AzureRmApplicationGatewayProbeConfig
            - New-AzureRmApplicationGatewayProbeConfig
            - Set-AzureRmApplicationGatewayProbeConfig
        - Parámetros opcionales agregados -PickHostNameFromBackendAddress, -AffinityCookieName, -ProbeEnabled y -Path
            - Add-AzureRmApplicationGatewayBackendHttpSettings
            - New-AzureRmApplicationGatewayBackendHttpSettings
            - Set-AzureRmApplicationGatewayBackendHttpSettings
    * Actualización de Get-AzureRmPublicIPaddress para recuperar los recursos de publicipaddress creados a través del conjunto de escalado de VM
    * Cmdlet agregado para obtener el uso actual de la red virtual
        - Get-AzureRmVirtualNetworkUsageList
* Perfil
    * Error corregido al usar Import-AzureRmContext o Save-AzureRmContext
        - Puede encontrar más información en este problema: https://github.com/Azure/azure-powershell/issues/3954
* RecoveryServices.SiteRecovery
    * Introducción a un nuevo módulo para las operaciones de Azure Site Recovery.
        - Todos los cmdlets empiezan por AzureRmRecoveryServicesAsr *
* Sql
    * Adición de los cmdlets de PowerShell de sincronización de datos en AzureRM.Sql
    * Cmdlets AzureRmSqlServer actualizados para usar la nueva versión de la API de REST que evita los tiempos de expiración cuando se crea un servidor.
    * Cmdlets de actualización del servidor en desuso porque ya no existe la versión antigua del servidor (2.0).
    * Adición del nuevo parámetro del conmutador opcional "AssignIdentity" a los cmdlets New-AzureRmSqlServer y Set-AzureRmSqlServer cmdlets para admitir el aprovisionamiento de una identidad de recursos para el recurso de SQL Server
    * El parámetro ResourceGroupName es ahora opcional para Get-AzureRmSqlServer
        - Puede encontrar más información en el siguiente problema: https://github.com/Azure/azure-powershell/issues/635
* ServiceManagement para ExpressRoute:
    * Cmdlet New-AzureBgpPeering actualizado para agregar las siguientes opciones nuevas:
        - PeerAddressType: los valores de "IPv4" o "IPv6" pueden especificarse para crear el emparejamiento BGP del tipo de familia de dirección correspondiente
    * Cmdlet Set-AzureBgpPeering actualizado para agregar las siguientes opciones nuevas:
        - PeerAddressType: los valores de "IPv4" o "IPv6" pueden especificarse para actualizar el emparejamiento BGP del tipo de familia de dirección correspondiente
    * Cmdlet Remove-AzureBgpPeering actualizado para agregar las siguientes opciones nuevas:
        - PeerAddressType: los valores de "IPv4", IPv6" o "All" pueden especificarse para quitar el emparejamiento BGP del tipo de familia de dirección correspondiente o todos ellos

## <a name="20170607---version-410"></a>07/06/2017: versión 4.1.0
* AnalysisServices
    * Nuevas SKU agregadas: B1, B2, S0
    * Escala verticalmente/reducción verticalmente
* CognitiveServices
    * Actualización de la visualización detallada de acuerdos de licencia cuando se crean recursos de Cognitive Services
* Proceso
    * Solución de Test-AzureRmVMAEMExtension para máquinas virtuales con varios discos administrados
    * Set-AzureRmVMAEMExtension actualizado: adición de información de almacenamiento en caché para discos administrados premium
    * Add-AzureRmVhd: el límite de tamaño en VHD ha aumentado a 4 TB.
    * Stop-AzureRmVM: documentación aclaratoria del parámetro STayProvisioned
    * New-AzureRmDiskUpdateConfig
      * Parámetros en desuso: CreateOption, StorageAccountId, ImageReference, SourceUri, SourceResourceId
    * Set-AzureRmDiskUpdateImageReference: cmdlet en desuso
    * New-AzureRmSnapshotUpdateConfig
      * Parámetros en desuso: CreateOption, StorageAccountId, ImageReference, SourceUri, SourceResourceId
    * Set-AzureRmSnapshotUpdateImageReference: cmdlet en desuso
* DataLakeStore
    * Enable-AzureRmDataLakeStoreKeyVault (Enable-AdlStoreKeyVault)
      * Habilitación del cifrado administrado de KeyVault para un almacén de DataLake
* DevTestLabs
    * Actualice los cmdlets para trabajar con la versión de la API de DevTest Labs actualizada.
* IotHub
    * Adición de la compatibilidad de enrutamiento para cmdlets de IoTHub
* KeyVault
  * Nuevos cmdlets para admitir claves de cuenta de almacenamiento administrado de KeyVault
    * Get-AzureKeyVaultManagedStorageAccount
    * Add-AzureKeyVaultManagedStorageAccount
    * Remove-AzureKeyVaultManagedStorageAccount
    * Update-AzureKeyVaultManagedStorageAccount
    * Update-AzureKeyVaultManagedStorageAccountKey
    * Get-AzureKeyVaultManagedStorageSasDefinition
    * Set-AzureKeyVaultManagedStorageSasDefinition
    * Remove-AzureKeyVaultManagedStorageSasDefinition
* Red
    * Get-AzureRmNetworkUsage: nuevo cmdlet para mostrar la información de capacidad y uso de red
    * Opciones de GatewaySku nuevas agregadas para VirtualNetworkGateways
        * VpnGw1, VpnGw2, VpnGw3 son las nuevas SKU agregadas para puertas de enlace VPN
    * Set-AzureRmNetworkWatcherConfigFlowLog
      * Ejemplos de ayuda solucionados
* NotificationHubs
    * Actualización transparente para cmdlets de NotificationHubs para la nueva API
* Perfil
    * Resolve-AzureRmError
      * Nuevo cmdlet para mostrar los detalles de errores y excepciones generados por los cmdlets, incluidos los datos de respuesta/solicitud del servidor
    * Send-Feedback
      * Envío de comentarios habilitado sin tener que iniciar sesión
    * Get-AzureRmSubscription
      * Solución de errores en la recuperación de suscripciones CSP
* Recursos
    * Problema corregido en el que Get-AzureRMRoleAssignment generaría una solicitud errónea si el número de roleassignments era superior a 1000
        * Los usuarios puede usar ahora Get-AzureRMRoleAssignment incluso si el roleassignments devuelto es superior a 1000
* Sql
    * Restore-AzureRmSqlDatabase: actualización del ejemplo de documentación
* Storage
    * Adición de la compatibilidad de la configuración AssignIdentity para cmdlets de cuenta de almacenamiento del modo de recursos
        * New-AzureRmStorageAccount
        * Set-AzureRmStorageAccount
    * Adición de la compatibilidad de claves de cliente a los cmdlets de cuenta de almacenamiento del modo de recursos
        * Set-AzureRmStorageAccount
        * New-AzureRmStorageAccountEncryptionKeySource
* TrafficManager

    * Nueva configuración del monitor 'MonitorIntervalInSeconds', 'MonitorTimeoutInSeconds', 'MonitorToleratedNumberOfFailures'
    * Nuevo protocolo del monitor 'TCP'
* ServiceManagement
    * Add-AzureVhd: el límite de tamaño en VHD ha aumentado a 4 TB.
    * New-AzureBGPPeering: compatibilidad con LegacyMode
* Azure.Storage
    * Actualización de ayuda para los parámetros que aceptan caracteres comodín y actualización del tipo StorageContext

## <a name="20170523---version-402"></a>23/05/2017: versión 4.0.2
* Perfil
    * Add-AzureRmAccount
      * Alias del parámetro `-EnvironmentName` agregado para la compatibilidad con versiones anteriores de 2.x de AzureRM.profile

## <a name="20170512---version-401"></a>12/05/2017: versión 4.0.1
 * Corrección del problema con New-AzureStorageContext en escenarios sin conexión: https://github.com/Azure/azure-powershell/issues/3939

## <a name="20170510---version-400"></a>10/05/2017: versión 4.0.0


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
