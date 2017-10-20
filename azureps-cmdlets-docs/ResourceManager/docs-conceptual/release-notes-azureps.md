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
ms.openlocfilehash: d8a891673df343551cbd805016c2d25ee4e31c8c
ms.sourcegitcommit: 9d2d35944106bdb6758853b050089bc804e6b9d2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/17/2017
---
# <a name="release-notes"></a>Notas de la versión

Esta es una lista de los cambios realizados en esta versión de Azure PowerShell.

## <a name="20170925---version-440"></a>25/09/2017: versión 4.4.0
* AnalysisServices
  * Se ha agregado un nuevo commandlet de dataplane para permitir la sincronización de bases de datos desde una instancia de lectura-escritura a instancias de solo lectura
    - Se ha incluido un archivo de ayuda para el commandlet
    - Se han agregado pruebas en memoria y una prueba de escenario (solo en vivo)
  * Se han corregido los errores del commandlet Add-AzureAsAccount
* Automation
  * Se han corregido los documentos de ayuda de los cmdlets que se corrigieron en la versión anterior.
  * Se han agregado 4 nuevos cmdlets para la compatibilidad con el lanzamiento por fases de las configuraciones de nodos DSC.
    - Start-AzureRmAutomationDscNodeConfigurationDeployment
    - Stop-AzureRmAutomationDscNodeConfigurationDeployment
    - Get-AzureRmAutomationDscNodeConfigurationDeployment
    - Get-AzureRmAutomationDscNodeConfigurationDeploymentSchedule
* CognitiveServices
  * Integración con la versión 2.0.0 del SDK de administración de Cognitive Services.
  * Get-AzureRmCognitiveServicesAccount ya admite correctamente la paginación.
* Proceso
  * Característica de comando de ejecución:
    - Nuevo cmdlet: "Invoke-AzureRmVMRunCommand" invoca un comando de ejecución en una máquina virtual
    - Nuevo cmdlet: "Get-AzureRmVMRunCommandDocument" muestra los documentos disponibles sobre los comandos de ejecución
  * Se ha agregado el parámetro "StorageAccountType" a Set-AzureRmDataDisk
  * Compatibilidad de la zona de disponibilidad con máquinas virtuales, conjuntos de escalado de máquinas virtuales y discos
    - Nuevo parámetro: se ha agregado "Zone" a New-AzureRmVM, New-AzureRmVMConfig, New-AzureRmVmssConfig, New-AzureRmDiskConfig
  * Característica de actualización gradual del conjunto de escalado de máquinas virtuales:
    - Nuevo cmdlet: "Start-AzureRmVmssRollingOSUpgrade" invoca la actualización gradual del sistema operativo de un conjunto de escalado de máquinas virtuales
    - Nuevo cmdlet: "Set-AzureRmVmssRollingUpgradePolicy" establece la directiva de actualizaciones para la actualización gradual de un conjunto de escalado de máquinas virtuales.
    - Nuevo cmdlet: "Stop-AzureRmVmssRollingUpgrade" cancela la actualización gradual de un conjunto de escalado de máquinas virtuales
    - Nuevo cmdlet: "Get-AzureRmVmssRollingUpgrade" muestra el estado de la actualización gradual del conjunto de escalado de máquinas virtuales.
  * Se ha introducido el parámetro de modificador AssignIdentity para la identidad asignada por el sistema.
    - Nuevo parámetro: se ha agregado "AssignIdentity" a New-AzureRmVMConfig, New-AzureRmVmssConfig y Update-AzureRmVM
  * Característica de cifrado de disco VMSS:
    - Nuevo cmdlet: "Set-AzureRmVmssDiskEncryptionExtension" habilita el cifrado de discos en el conjunto de escalado de máquinas virtuales
    - Nuevo cmdlet: "Disable-AzureRmVmssDiskEncryption" deshabilita el cifrado de discos en el conjunto de escalado de máquinas virtuales
    - Nuevo cmdlet: "Get-AzureRmVmssDiskEncryptionStatus" muestra el estado del cifrado de discos de un conjunto de escalado de máquinas virtuales
    - Nuevo cmdlet: "Get-AzureRmVmssVMDiskEncryptionStatus" muestra el estado del cifrado de discos de las máquinas virtuales de un conjunto de escalado
* ContainerInstance
  * Se han agregado cmdlets de PowerShell para Azure Container Instance
    - New-AzureRmContainerGroup
    - Get-AzureRmContainerGroup
    - Remove-AzureRmContainerGroup
    - Get-AzureRmContainerInstanceLog
* Información detallada
  * Nuevo cmdlet Disable-AzureRmActivityLogAlert
    - Un nuevo cmdlet para deshabilitar una alerta de registro de actividad existente.
    - Opcionalmente, se pueden configurar las etiquetas con este cmdlet también.
  * Nuevo cmdlet Enable-AzureRmActivityLogAlert
    - Un nuevo cmdlet para habilitar una alerta de registro de actividad existente.
    - Opcionalmente, se pueden configurar las etiquetas con este cmdlet también.
  * Nuevo cmdlet Get-AzureRmActivityLogAlert
    - Un nuevo cmdlet para recuperar una o varias alertas de registro de actividad existente.
    - Las alertas se pueden recuperar por nombre, grupo de recursos o suscripción.
  * Nuevo cmdlet New-AzureRmActionGroup
    - Un nuevo cmdlet para crear un objeto ActionGroup en memoria (ninguna solicitud implicada).
  * Nuevo cmdlet New-AzureRmActivityLogAlertCondition
    - Un nuevo cmdlet para crear un objeto de condición hoja de alerta de registro de actividad en memoria (ninguna solicitud implicada).
  * Nuevo cmdlet Set-AzureRmActivityLogAlert
    - Un nuevo cmdlet para crear o actualizar una alerta de registro de actividad.
  * Nuevo cmdlet Remove-AzureRmActivityLogAlert
    - Un nuevo cmdlet para eliminar una alerta de registro de actividad.
  * Nuevo cmdlet Set-AzureRmActionGroup
    - Un nuevo cmdlet para crear un nuevo grupo de acciones o actualizar uno ya existente.
  * Nuevo cmdlet Get-AzureRmActionGroup
    - Un nuevo cmdlet para recuperar uno o varios grupos de acciones.
    - Los grupos de acciones se pueden recuperar por nombre, grupo de recursos o suscripción.
  * Nuevo cmdlet Remove-AzureRmActionGroup
    - Un nuevo cmdlet para eliminar un grupo de acciones.
  * Nuevo cmdlet New-AzureRmActionGroupReceiver
    - Un nuevo cmdlet para crear un nuevo receptor de grupo de acciones en memoria.
* KeyVault
  * Cmdlets nuevos o actualizados para permitir la compatibilidad con la eliminación temporal de los certificados de Key Vault
    * Get-AzureKeyVaultCertificate
    * Remove-AzureKeyVaultCertificate
    * Undo-AzureKeyVaultCertificateRemoval
* Red
  * Se ha agregado compatibilidad con los servicios de puntos de conexión para las subredes de Virtual Network
    - Se ha actualizado Add-AzureRmVirtualSubnetConfig: se ha agregado el parámetro opcional -ServiceEndpoint
    - Se ha actualizado New-AzureRmVirtualSubnetConfig: se ha agregado el parámetro opcional -ServiceEndpoint
    - Se ha actualizado Set-AzureRmVirtualSubnetConfig: se ha agregado el parámetro opcional -ServiceEndpoint
  * Se ha agregado un cmdlet para enumerar los servicios de puntos de conexión disponibles en una ubicación
    - Get-AzureRmVirtualNetworkAvailableEndpointService
  * Se ha agregado la capacidad de configurar la autenticación P2S externa basada en RADIUS en los commandlets siguientes
    - New-AzureVirtualNetworkGateway
    - Set-AzureVirtualNetworkGateway
    - Set-AzureRmVirtualNetworkGatewayVpnClientConfig
  * Se ha agregado un cmdlet para permitir la generación de VpnProfiles para la autenticación P2S externa basada en RADIUS
    - New-AzureRmVpnClientConfiguration
    - Get-AzureRmVpnClientConfiguration
  * Se ha agregado compatibilidad con el parámetro SKU para las direcciones IP públicas y las instancias de Load Balancer
    - Se ha actualizado New-AzureRMLoadBalancer: se ha agregado el parámetro opcional -Sku
    - Se ha actualizado New-AzureRMPublicIpAddress: se ha agregado el parámetro opcional -Sku
  * Se ha agregado compatibilidad con DisableOutboundSNAT a las reglas de Load Balancer
    - Se ha actualizado New-AzureRMLoadBalancerRuleConfig: se ha agregado el parámetro opcional DisableOutboundSNAT
    - Se ha actualizado Add-AzureRMLoadBalancerRuleConfig: se ha agregado el parámetro opcional DisableOutboundSNAT
    - Se ha actualizado Set-AzureRMLoadBalancerRuleConfig: se ha agregado el parámetro opcional DisableOutboundSNAT
  * Se agregó compatibilidad con P2S de IkeV2
    - Se ha actualizado New-AzureRmVirtualNetworkGateway: se ha agregado el parámetro opcional -VpnClientProtocol, con un valor predeterminado establecido en [ "SSTP", "IkeV2" ]
    - Se ha actualizado Set-AzureRmVirtualNetworkGateway: se ha agregado el parámetro opcional -VpnClientProtocol
  * Se ha agregado compatibilidad con las reglas multivalor para las reglas de seguridad de red y las reglas de seguridad de red vigentes
    - Se ha actualizado Add-AzureRmNetworkSecurityRuleConfig: se han actualizado los parámetros SourcePortRange, DestinationPortRange, SourceAddressPrefix para que puedan aceptar una lista de cadenas
    - Se ha actualizado New-AzureRmNetworkSecurityRuleConfig: se han actualizado los parámetros SourcePortRange, DestinationPortRange, SourceAddressPrefix para que puedan aceptar una lista de cadenas
    - Se ha actualizado Set-AzureRmNetworkSecurityRuleConfig: se han actualizado los parámetros SourcePortRange, DestinationPortRange, SourceAddressPrefix para que puedan aceptar una lista de cadenas
    - Se ha actualizado Add-AzureRmNetworkSecurityRuleConfig: se han actualizado los parámetros SourcePortRange, DestinationPortRange, SourceAddressPrefix para que puedan aceptar una lista de cadenas
    - Se ha actualizado New-AzureRmNetworkSecurityGroup: se ha actualizado el parámetro SecurityRules para que acepte los parámetros SourcePortRange, DestinationPortRange, SourceAddressPrefix que constituyen una lista de cadenas en el objeto PSSecurityRule
    - Se ha actualizado Get-AzureRmEffectiveNetworkSecurityGroup: se ha agregado el parámetro TagMap
    - Se ha actualizado Get-AzureRmEffectiveNetworkSecurityGroup: se ha actualizado el objeto PSEffectiveSecurityRule devuelto con los parámetros SourcePortRange, DestinationPortRange, SourceAddressPrefix que constituyen una lista de cadenas.
  * Se ha agregado compatibilidad con la protección contra DDoS para las redes virtuales
    - Se ha actualizado New-AzureRmVirtualNetwork: se han agregado los parámetros de modificador EnableDDoSProtection y EnableVmProtection
    - Se han agregado las propiedades EnableDDoSProtection y EnableVmProtection en el objeto PSVirtualNetwork
  * Se ha agregado compatibilidad con la instancia interna de alta disponibilidad de Load Balancer
    - Se ha actualizado Add-AzureRmLoadBalancerRuleConfig: se ha agregado All como valor aceptable para el parámetro Protocol
    - Se ha actualizado New-AzureRmLoadBalancerRuleConfig: se ha agregado All como valor aceptable para el parámetro Protocol
    - Se ha actualizado Set-AzureRmLoadBalancerRuleConfig: se ha agregado All como valor aceptable para el parámetro Protocol
  * Se ha agregado compatibilidad con los grupos de seguridad de la aplicación
    - Se ha agregado New-AzureRmApplicationSecurityGroup
    - Se ha agregado Get-AzureRmApplicationSecurityGroup
    - Se ha agregado Remove-AzureRmApplicationSecurityGroup
    - Se ha actualizado New-AzureRmNetworkInterface: se han agregado los parámetros opcionales ApplicationSecurityGroup y ApplicationSecurityGroupId
    - Se ha actualizado New-AzureRmNetworkInterfaceIpConfig: se han agregado los parámetros opcionales ApplicationSecurityGroup y ApplicationSecurityGroupId
    - Se ha actualizado Add-AzureRmNetworkInterfaceIpConfig: se han agregado los parámetros opcionales ApplicationSecurityGroup y ApplicationSecurityGroupId
    - Se ha actualizado Set-AzureRmNetworkInterfaceIpConfig: se han agregado los parámetros opcionales ApplicationSecurityGroup y ApplicationSecurityGroupId
    - Se ha actualizado New-AzureRmNetworkSecurityRuleConfig: se han agregado los parámetros opcionales SourceApplicationSecurityGroup, SourceApplicationSecurityGroupId, DestinationApplicationSecurityGroup y DestinationApplicationSecurityGroupId
    - Se ha actualizado Add-AzureRmNetworkSecurityRuleConfig: se han agregado los parámetros opcionales SourceApplicationSecurityGroup, SourceApplicationSecurityGroupId, DestinationApplicationSecurityGroup y DestinationApplicationSecurityGroupId
    - Se ha actualizado Set-AzureRmNetworkSecurityRuleConfig: se han agregado los parámetros opcionales SourceApplicationSecurityGroup, SourceApplicationSecurityGroupId, DestinationApplicationSecurityGroup y DestinationApplicationSecurityGroupId
  * Se han agregado nuevos comandos para los scripts de VpnDeviceConfiguration
    - Get-AzureRmVirtualNetworkGatewaySupportedVpnDevices
    - Get-AzureRmVirtualNetworkGatewayConnectionVpnDeviceConfigScript
* Perfil
  * Compatibilidad de la tarea de inicio con los cmdlets de AzureRm.
    * Se ha agregado a todos los cmdlets AzureRm el parámetro -AzureRmContext, que puede aceptar un contexto (salida de un cmdlet Context).
      - Patrón común para los trabajos con la persistencia de contexto DESHABILITADA: `Start-Job {param ($context) New-AzureRmVM -AzureRmContext $context [... other parameters]} -ArgumentList (Get-AzureRmContext)`
      - Patrón común para los trabajos con la persistencia de contexto HABILITADA: `Start-Job {New-AzureRmVM [... other parameters]}`
  * La información de inicio de sesión se conservan entre sesiones, nuevos cmdlets:
    - Enable-AzureRmContextAutosave: habilita la conservación de la información de inicio de sesión entre sesiones.
    - Disable-AzureRmContextAutosave: deshabilita la conservación de la información de inicio de sesión entre sesiones.
  * Administración de la información de contexto, nuevos cmdlets
    - Select-AzureRmContext: selecciona el contexto con nombre activo.
    - Rename-AzureRmContext: cambia el nombre de un contexto ya existente para facilitar las consultas.
    - Remove-AzureRmContext: quita un contexto existente.
    - Remove-AzureRmAccount: quita todas las credenciales, las suscripciones y los inquilinos asociados a una cuenta.
  * Administración de la información de contexto, cambios en los cmdlets:
    - Se ha agregado Scope = (Process | CurrentUser) a todos los cmdlets que cambian las credenciales
    - Get-AzureRmContext: se ha agregado el parámetro ListAvailable para enumerar todos los contextos guardados
* Recursos
  * Se han agregado cmdlets PolicySetDefinition
    - Se ha agregado el cmdlet New-AzureRmPolicySetDefinition para crear una definición de un conjunto de directivas
    - Se ha agregado el cmdlet Get-AzureRmPolicySetDefinition para que enumere todas las definiciones de conjuntos de directivas o para que obtenga una definición de conjunto de directivas específica
    - Se ha agregado el cmdlet Remove-AzureRmPolicySetDefinition para eliminar una definición de un conjunto de directivas
    - Se ha agregado el cmdlet Set-AzureRmPolicySetDefinition para actualizar una definición de un conjunto de directivas ya existente
  * Se han agregado los parámetros -PolicySetDefinition, -Sku y -NotScope a los cmdlets New-AzureRmPolicyAssignment y Set-AzureRmPolicyAssignment
  * Se ha agregado compatibilidad para pasar la dirección URL de la directiva a los cmdlets New-AzureRmPolicyDefinition y Set-AzureRmPolicyDefinition
  * Se ha agregado el parámetro -Mode al cmdlet New-AzureRmPolicyDefinition
  * Se ha agregado compatibilidad para la eliminación de roleassignment mediante el objeto PSRoleAssignment
    - Los usuarios ahora pueden usar PSRoleassignmnet inputobject con el commandlet Remove-AzureRMRoleAssignment para quitar roleassignment.
  * Se han agregado los cmdlets de ManagedApplication
    - Se ha agregado el cmdlet New-AzureRmManagedApplication para crear una aplicación administrada
    - Se ha agregado el cmdlet Get-AzureRmManagedApplication para enumerar todas las aplicaciones administradas de una suscripción o para obtener una aplicación administrada específica
    - Se ha agregado el cmdlet Remove-AzureRmManagedApplication para eliminar una aplicación administrada
    - Se ha agregado el cmdlet Set-AzureRmManagedApplication para actualizar una aplicación administrada ya existente
  * Se han agregado los cmdlets de ManagedApplicationDefinition
    - Se ha agregado el cmdlet New-AzureRmManagedApplicationDefinition para crear una definición de aplicación administrada mediante un identificador URI de archivo ZIP o mediante los archivos json mainTemplate y createUiDefinition
    - Se ha agregado el cmdlet Get-AzureRmManagedApplicationDefinition para enumerar todas las definiciones de aplicaciones administradas de un grupo de recursos o para obtener una definición específica
    - Se ha agregado el cmdlet Remove-AzureRmManagedApplicationDefinition para eliminar una definición de una aplicación administrada
    - Se ha agregado el cmdlet Set-AzureRmManagedApplicationDefinition para actualizar una definición de aplicación administrada ya existente
* Sql
  * Se ha agregado compatibilidad con las reglas de red virtual
    - Se ha agregado el cmdlet Get-AzureRmSqlServerVirtualNetworkRule que permite obtener las reglas de red virtual por medio de un nombre de regla específico o una lista de reglas de red virtual de un servidor de Azure SQL.
    - Se ha agregado el cmdlet Set-AzureRmSqlServerVirtualNetworkRule que permite cambiar la red virtual hacia la que apunta la regla.
    - Se ha agregado el cmdlet Remove-AzureRmSqlServerVirtualNetworkRule que elimina una regla de red virtual de un servidor de Azure SQL.
    - Se ha agregado el cmdlet New-AzureRmSqlServerVirtualNetworkRule que crea una nueva regla de red virtual para un servidor de Azure SQL.
* Sitios web
  * Se ha agregado el nivel PremiumV2 a los planes de App Service
* Azure.Storage
  * Actualización a Biblioteca de cliente de Azure Storage 8.4.0 y Biblioteca de Azure Storage DataMovement 0.6.1
  * Se ha agregado compatibilidad con PremiumPageBlobTier en las API Upload y Copy Blob
    - Set-AzureStorageBlobContent
    - Start-AzureStorageBlobCopy
  * Se ha refinado el formato de salida de consola de AzureStorageContainer, AzureStorageBlob, AzureStorageQueue, AzureStorageTable
    - Get-AzureStorageContainer
    - Get-AzureStorageBlob
    - Get-AzureStorageQueue
    - Get-AzureStorageTable

## <a name="20170810---version-431"></a>10/08/2017: versión 4.3.1
  * Actualización para corregir las firmas de ensamblados

## <a name="20170807---version-430"></a>07/08/2017: versión 4.3.0
* AnalysisServices
  * Se corrigió el error en Set-AzureRmAnalysisServciesServer
    - Si no se proporcionó administrador, se quitará el administrador.
  * BackupBlobContainerUri se agregó en New-AzureRmAnalysisServicesServer y Set-AzureRmAnalysisServicesServer
    - Habilite para establecer/deshabilitar el contenedor de blobs de copia de seguridad para copia de seguridad/restauración del servidor de Azure Analysis Services
  * La búsqueda de SKU se actualizó en New-AzureRmAnalysisServicesServer y Set-AzureRmAnalysisServicesServer
    - La SKU codificada de forma rígida se modificó en la búsqueda dinámica.
  * Add-AzureAnalysisServicesAccount para admitir el inicio de sesión con entidad de servicio
* Automation
  * Se realizaron cambios en los cmdlets de AutomationDSC* para extraer más de 100 registros
  * Se solución el problema en que las secuencias de Detallado dejaban de funcionar después de llamar a algunos cmdlets de Automation (por ejemplo, Get-AzureRmAutomationVariable, Get-AzureRmAutomationJob).
  * Se agregó compatibilidad con la creación de versiones de compilación NodeConfiguration en StartAzureAutomationDscCompilationJob y ImportAzureAutomationDscNodeConfiguration
  * Corrección de errores de problemas existentes: corrige el problema de alias #3775 y el alias runOn y la compatibilidad con HybridWorkers.
* Proceso
  * Set-AzureRmVMAEMExtension: agregue compatibilidad con los tamaños de discos Premium nuevos
  * Set-AzureRmVMAEMExtension: agregue compatibilidad con la serie M
  * Agregue el parámetro ForceUpdateTag a Add-AzureRmVmssExtension
  * Agregue el parámetro Primary a New-AzureRmVmssIpConfig
  * Agregue el parámetro EnableAcceleratedNetworking a Add-AzureRmVmssNetworkInterfaceConfig
  * Agregue InstanceId a Set-AzureRmVmss
  * Exponga MaintenanceRedeployStatus a la salida de Get-AzureRmVM -Status
  * Exponga restricción y capacidad al formato de tabla de Get-AzureRmComputeResourceSku
* DataLakeStore
  * Corrección del problema: https://github.com/Azure/azure-powershell/issues/4323
* EventHub
  * Se agregó la propiedad ResourceGroup a NamespaceAttributes
    - "ResourceGroup" Obtiene el nombre del grupo de recursos donde está el espacio de nombres
  * Se actualizaron los cmdlets con Parametersets para espacio de nombres y EventHub para la operación de AuthorizationRule
    - New-AzureRmEventHubAuthorizationRule: agrega una nueva AuthorizationRule a espacio de nombres o EventHub existente.
    - Get-AzureRmEventHubAuthorizationRule: obtiene AuthorizationRule / lista de AuthorizationRules para espacio de nombres o EventHub existente.
    - Set-AzureRmEventHubAuthorizationRule: actualiza las propiedades de la AuthorizationRule existente de espacio de nombres de EventHub.
    - Remove-AzureRmEventHubAuthorizationRule: elimina la AuthorizationRule existente de espacio de nombres o EventHub existente.
    - New-AzureRmEventHubKey: genera una clave principal o secundaria para la AuthorizationRule de un espacio de nombres o EventHub existente.
    - Get-AzureRmEventHubKey: obtiene una clave principal o secundaria para la AuthorizationRule de un espacio de nombres o EventHub existente.
* Red
    * Se agregó compatibilidad de IPv6 y un parámetro opcional nuevo: PeerAddressType
      * New-AzureRmExpressRouteCircuitPeeringConfig:
      * Set-AzureRmExpressRouteCircuitPeeringConfig: se agregó compatibilidad de IPv6. Se agregó un parámetro opcional nuevo
      * Remove-AzureRmExpressRouteCircuitPeeringConfig: se agregó compatibilidad de IPv6. Se agregó un parámetro opcional nuevo
    * El parámetro -ProbeEnabled se marcó como obsoleto
      - Add-AzureRmApplicationGatewayBackendHttpSettings
      - New-AzureRmApplicationGatewayBackendHttpSettings
      - Set-AzureRmApplicationGatewayBackendHttpSettings
* Perfil
    * La recopilación de datos se habilitó de manera predeterminada. Microsoft recopila los datos de uso para mejorar la experiencia del usuario. Los datos son anónimos y no incluyen valores de argumento de la línea de comandos.
      - Use el cmdlet Disable-AzureRmDataCollection para desactivar la característica
      - Use el cmdlet Enable-AzureRmDataCollection para activar esta característica
* Recursos
    * Agregue compatibilidad con la validación de ámbitos para los cmdlets roledefinition y roleassignment siguientes antes de enviar la solicitud a ARM
      - Get-AzureRMRoleAssignment
      - New-AzureRMRoleAssignment
      - Remove-AzureRMRoleAssignment
      - Get-AzureRMRoleDefinition
      - New-AzureRMRoleDefinition
      - Remove-AzureRMRoleDefinition
      - Set-AzureRMRoleDefinition
* ServiceBus
    * Los commandlets nuevos que aparecen a continuación se agregaron para AuthorizationRules para espacio de nombres, cola y tema. Según el conjunto de parámetros, se realizan las operaciones de regla de autorización.
     - New-AzureRmServiceBusAuthorizationRule: agrega una nueva AuthorizationRule al espacio de nombres, cola o tema de ServiceBus.
     - Get-AzureRmServiceBusAuthorizationRule: obtiene AuthorizationRule / lista de AuthorizationRules para el espacio de nombres, cola o tema de ServiceBus.
     - Set-AzureRmServiceBusAuthorizationRule: actualiza las propiedades de la AuthorizationRule existente de espacio de nombres, cola o tema de ServiceBus.
     - New-AzureRmServiceBusKey: genera una clave principal o secundaria para la AuthorizationRule de un espacio de nombres, cola o tema existente de ServiceBus.
     - Get-AzureRmServiceBusKey: obtiene la clave principal o secundaria para la AuthorizationRule de un espacio de nombres, cola o tema existente de ServiceBus.
     - Remove-AzureRmServiceBusNamespaceAuthorizationRule: elimina la AuthorizationRule existente de espacio de nombres, cola o tema de ServiceBus.
    * Se agregó la propiedad Resource Group a NamespceAttributes
* Sql
    * Actualización de Set-AzureRmSqlServerTransparentDataEncryptionProtector para mostrar una advertencia y requerir confirmación si el tipo de protector de cifrado se establece en AzureKeyVault
    * Incorporación de cmdlets actualizados nuevos para la configuración de auditoría
      - Cmdlet Get-AzureRmSqlDatabaseAuditing que obtiene la configuración de auditoría de una base de datos SQL de Azure.
      - Cmdlet Get-AzureRmSqlServerAuditing que obtiene la configuración de auditoría de un servidor SQL de Azure.
      - Cmdlet Set-AzureRmSqlDatabaseAuditing que cambia la configuración de auditoría de una base de datos SQL de Azure.
      - Cmdlet Set-AzureRmSqlServerAuditing que cambia la configuración de auditoría de un servidor SQL de Azure.
    * Desuso de los cmdlets de la directiva de auditoría existente
      - Get-AzureRmSqlDatabaseAuditingPolicy
      - Get-AzureRmSqlServerAuditingPolicy
      - Set-AzureRmSqlDatabaseAuditingPolicy
      - Set-AzureRmSqlServerAuditingPolicy
      - Use-AzureRmSqlServerAuditingPolicy
      - Remove-AzureRmSqlDatabaseAuditing
      - Remove-AzureRmSqlServerAuditing
    * El análisis del archivo de esquema para Update-AzureRmSqlSyncGroup ahora distingue mayúsculas de minúsculas.
* Storage
    * Incorporación de la compatibilidad de NeworkRule a los cmdlets de cuenta de almacenamiento del modo de recursos
      - New-AzureRmStorageAccount
      - Set-AzureRmStorageAccount
      - Get-AzureRmStorageAccountNetworkRuleSet
      - Update-AzureRmStorageAccountNetworkRuleSet
      - Add-AzureRmStorageAccountNetworkRule
      - Remove-AzureRmStorageAccountNetworkRule

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
