Instalador de Azure PowerShell 4.3.1: [vínculo](https://github.com/Azure/azure-powershell/releases/download/v4.3.1-August2017/azure-powershell.4.3.1.msi)

Módulo de galería para cmdlets de ARM: [vínculo](https://www.powershellgallery.com/packages/AzureRM/4.3.1)

Módulo de galería para cmdlets heredados para administración de servicios (RDFE): [vínculo](https://www.powershellgallery.com/packages/Azure/4.3.1)

## <a name="changes-in-431"></a>Cambios en 4.3.1

- Se corrigió un problema con ciertos ensamblados que no se firmaron, lo que generaba un error `could not load file or assembly` cuando se importaban los módulos

## <a name="changes-in-430"></a>Cambios en 4.3.0

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
    * Se agregó compatibilidad con la creación de versiones de compilación NodeConfiguration en StartAzureAutomationDscCompilationJob y ImportAzureAutomationDscNodeConfiguration.
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
    * Los commandlets se actualizaron con un nuevo parámetro y alias de parámetro
        - Los cmdlets siguientes se actualizaron con Parametersets para espacio de nombres y EventHub para la operación de AuthorizationRule
        - New-AzureRmEventHubAuthorizationRule
            + Agrega una nueva AuthorizationRule a espacio de nombres o EventHub existente.
        - Get-AzureRmEventHubAuthorizationRule
            + Obtiene AuthorizationRule / lista de AuthorizationRules para espacio de nombres o EventHub existente.
        - Set-AzureRmEventHubAuthorizationRule
            + Actualiza las propiedades de la AuthorizationRule existente de espacio de nombres de EventHub.
        - Remove-AzureRmEventHubAuthorizationRule
            + Elimina la AuthorizationRule existente de espacio de nombres o EventHub existente.
        - New-AzureRmEventHubKey
            + Genera una clave principal o secundaria para la AuthorizationRule de un espacio de nombres o EventHub existente.
        - Get-AzureRmEventHubKey
            + Obtiene una clave principal o secundaria para la AuthorizationRule de un espacio de nombres o EventHub existente.
* Red
    * New-AzureRmExpressRouteCircuitPeeringConfig: se agregó compatibilidad de IPv6. Se agregó un parámetro opcional nuevo
        - PeerAddressType
    * Set-AzureRmExpressRouteCircuitPeeringConfig: se agregó compatibilidad de IPv6. Se agregó un parámetro opcional nuevo
        - PeerAddressType
    * Remove-AzureRmExpressRouteCircuitPeeringConfig: se agregó compatibilidad de IPv6. Se agregó un parámetro opcional nuevo
        - PeerAddressType
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
     - New-AzureRmServiceBusAuthorizationRule
       - Agrega una nueva AuthorizationRule al espacio de nombres, cola o tema de ServiceBus.
     - Get-AzureRmServiceBusAuthorizationRule
       - Obtiene AuthorizationRule / lista de AuthorizationRules para el espacio de nombres, cola o tema de ServiceBus.
     - Set-AzureRmServiceBusAuthorizationRule
       - Actualiza las propiedades de la AuthorizationRule existente de espacio de nombres, cola o tema de ServiceBus.
     - New-AzureRmServiceBusKey
       - Genera una clave principal o secundaria para la AuthorizationRule de un espacio de nombres, cola o tema existente de ServiceBus.
     - Get-AzureRmServiceBusKey
       - Obtiene la clave principal o secundaria para la AuthorizationRule de un espacio de nombres, cola o tema existente de ServiceBus.
     - Remove-AzureRmServiceBusNamespaceAuthorizationRule
       - Elimina la AuthorizationRule existente de espacio de nombres, cola o tema de ServiceBus.
    * Se agregó la propiedad Resource Group a NamespceAttributes
* Sql
    * Actualización de Set-AzureRmSqlServerTransparentDataEncryptionProtector para mostrar una advertencia y requerir confirmación si el tipo de protector de cifrado se establece en AzureKeyVault
    * Incorporación de cmdlets actualizados nuevos para la configuración de auditoría
        - Actualización del cmdlet Get-AzureRmSqlDatabaseAuditing que obtiene la configuración de auditoría de una base de datos SQL de Azure.
        - Incorporación del cmdlet Get-AzureRmSqlServerAuditing que obtiene la configuración de auditoría de un servidor SQL de Azure.
        - Incorporación del cmdlet Set-AzureRmSqlDatabaseAuditing que cambia la configuración de auditoría de una base de datos SQL de Azure.
        - Incorporación del cmdlet Set-AzureRmSqlServerAuditing que cambia la configuración de auditoría de un servidor SQL de Azure.
    * Desuso de los cmdlets de la directiva de auditoría existente
        - Get-AzureRmSqlDatabaseAuditingPolicy en desuso
        - Get-AzureRmSqlServerAuditingPolicy en desuso
        - Set-AzureRmSqlDatabaseAuditingPolicy en desuso
        - Set-AzureRmSqlServerAuditingPolicy en desuso
        - Use-AzureRmSqlServerAuditingPolicy en desuso
        - Remove-AzureRmSqlDatabaseAuditing en desuso
        - Remove-AzureRmSqlServerAuditing en desuso
    * El análisis del archivo de esquema para Update-AzureRmSqlSyncGroup ahora distingue mayúsculas de minúsculas.
* Storage
    * Incorporación de la compatibilidad de NeworkRule a los cmdlets de cuenta de almacenamiento del modo de recursos
        - New-AzureRmStorageAccount
        - Set-AzureRmStorageAccount
        - Get-AzureRmStorageAccountNetworkRuleSet
        - Update-AzureRmStorageAccountNetworkRuleSet
        - Add-AzureRmStorageAccountNetworkRule
        - Remove-AzureRmStorageAccountNetworkRule

Consulte los [cambios que se realizaron desde la última versión](https://github.com/Azure/azure-powershell/compare/v4.2.1-July2017...v4.3.1-August2017)
