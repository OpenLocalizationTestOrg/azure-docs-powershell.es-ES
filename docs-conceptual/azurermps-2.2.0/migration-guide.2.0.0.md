# <a name="table-of-contents"></a>Tabla de contenido
1. [Eliminación de los parámetros Force](#removal-of-force-parameters)
2. [Cambio de los parámetros Tag](#change-of-tag-parameters)
3. [Cambios substanciales en cmdlets de Storage](#breaking-changes-to-storage-cmdlets)
4. [Cambios sustanciales en los cmdlets de AD](#breaking-changes-to-ad-cmdlets)

## <a name="removal-of-force-parameters"></a>Eliminación de los parámetros Force

En esta versión hemos eliminado todos los parámetros `Force` obsoletos de cmdlets y las advertencias correspondientes de que el parámetro se quitará en futuras versiones.

Este cambio afecta a los siguientes cmdlets:

**ApiManagement**
- Remove-AzureRmApiManagement
- Remove-AzureRmApiManagementApi
- Remove-AzureRmApiManagementGroup
- Remove-AzureRmApiManagementLogger
- Remove-AzureRmApiManagementOpenIdConnectProvider
- Remove-AzureRmApiManagementOperation
- Remove-AzureRmApiManagementPolicy
- Remove-AzureRmApiManagementProduct
- Remove-AzureRmApiManagementProperty
- Remove-AzureRmApiManagementSubscription
- Remove-AzureRmApiManagementUser

**Automation**
- Remove-AzureRmAutomationCertificate
- Remove-AzureRmAutomationCredential
- Remove-AzureRmAutomationVariable
- Remove-AzureRmAutomationWebhook

**Batch**
- Remove-AzureBatchCertificate
- Remove-AzureBatchComputeNode
- Remove-AzureBatchComputeNodeUser

**DataFactories**
- Resume-AzureRmDataFactoryPipeline
- Set-AzureRmDataFactoryPipelineActivePeriod
- Suspend-AzureRmDataFactoryPipeline

**DataLakeStore**
- Remove-AzureRmDataLakeStoreItemAclEntry
- Set-AzureRmDataLakeStoreItemAcl
- Set-AzureRmDataLakeStoreItemAclEntry
- Set-AzureRmDataLakeStoreItemOwner

**OperationalInsights**
- Remove-AzureRmOperationalInsightsSavedSearch

**Perfil**
- Remove-AzureRmEnvironment

**RedisCache**
- Remove-AzureRmRedisCacheDiagnostics

**Recursos**
- Register-AzureRmProviderFeature
- Register-AzureRmResourceProvider
- Remove-AzureRmADServicePrincipal
- Remove-AzureRmPolicyAssignment
- Remove-AzureRmResourceGroupDeployment
- Remove-AzureRmRoleAssignment
- Stop-AzureRmResourceGroupDeployment
- Unregister-AzureRmResourceProvider

**Storage**
- Remove-AzureStorageContainerStoredAccessPolicy
- Remove-AzureStorageQueueStoredAccessPolicy
- Remove-AzureStorageShareStoredAccessPolicy
- Remove-AzureStorageTableStoredAccessPolicy

**StreamAnalytics**
- Remove-AzureRmStreamAnalyticsFunction
- Remove-AzureRmStreamAnalyticsInput
- Remove-AzureRmStreamAnalyticsJob
- Remove-AzureRmStreamAnalyticsOutput

**Tag**
- Remove-AzureRmTag

<br>

Si tiene un script que utiliza cualquiera de los cmdlets anteriores, el cambio se puede corregir quitando el parámetro `Force`.

```powershell
# Old
New-AzureRmResourceGroup -Name $resourceGroupName -Location $location -Force

# New
New-AzureRmResourceGroup -Name $resourceGroupName -Location $location
```

<br>

## <a name="change-of-tag-parameters"></a>Cambio de los parámetros Tag

En esta versión, el nombre de parámetro `Tags` se ha cambiado a `Tag` y el tipo se ha cambiado de `Hashtable[]` a `Hashtable`, lo que cambia el formato de los pares clave-valor.

Anteriormente, cada entrada de `Hashtable[]` representaba un par de clave-valor individual:

```powershell
$tags = @{ Name = "test1"; Value = "testval1" }, @{ Name = "test2", Value = "testval2" }
$tags[0].Name  # Key for the first entry, "test1"
$tags[0].Value # Value for the first entry, "testval1"
$tags[1].Name  # Key for the second entry, "test2"
$tags[1].Value # Value for the second entry, "testval2"
```

Ahora, `Name` y `Value` ya no son necesarios, lo que permite crear pares clave-valor mediante la asignación de `Key = "Value"` en `Hashtable`:

```powershell
$tag = @{ test1 = "testval1"; test2 = "testval2" }
$tag["test1"] # Gets the value associated with the key "test1"
$tag["test2"] # Gets the value associated with the key "test2"
```

Este cambio afecta a los siguientes cmdlets:

**Batch**
- Get-AzureRmBatchAccount
- New-AzureRmBatchAccount
- Set-AzureRmBatchAccount

**Proceso**
- New-AzureRmVM
- Update-AzureRmVM

**DataLakeAnalytics**
- New-AzureRmDataLakeAnalyticsAccount
- Set-AzureRmDataLakeAnalyticsAccount

**DataLakeStore**
- New-AzureRmDataLakeStoreAccount
- Set-AzureRmDataLakeStoreAccount

**Dns**
- New-AzureRmDnsZone
- Set-AzureRmDnsZone

**KeyVault**
- Get-AzureRmKeyVault
- New-AzureRmKeyVault

**Red**
- New-AzureRmApplicationGateway
- New-AzureRmExpressRouteCircuit
- New-AzureRmLoadBalancer
- New-AzureRmLocalNetworkGateway
- New-AzureRmNetworkInterface
- New-AzureRmNetworkSecurityGroup
- New-AzureRmPublicIpAddress
- New-AzureRmRouteTable
- New-AzureRmVirtualNetwork
- New-AzureRmVirtualNetworkGateway
- New-AzureRmVirtualNetworkGatewayConnection
- New-AzureRmVirtualNetworkPeering

**Recursos**
- Find-AzureRmResource
- Find-AzureRmResourceGroup
- New-AzureRmResource
- New-AzureRmResourceGroup
- Set-AzureRmResource
- Set-AzureRmResourceGroup

**SQL**
- New-AzureRmSqlDatabase
- New-AzureRmSqlDatabaseCopy
- New-AzureRmSqlDatabaseSecondary
- New-AzureRmSqlElasticPool
- New-AzureRmSqlServer
- Set-AzureRmSqlDatabase
- Set-AzureRmSqlElasticPool
- Set-AzureRmSqlServer

**Storage**
- New-AzureRmStorageAccount
- Set-AzureRmStorageAccount

**TrafficManager**
- New-AzureRmTrafficManagerProfile

<br>

Si tiene un script que utiliza cualquiera de los cmdlets anteriores, el cambio se puede corregir cambiando el parámetro `Tags` a `Tag`, así como cambiando `Tag` al formato nuevo.

```powershell
# Old
New-AzureRmResourceGroup -Name $resourceGroupName -Location -location -Tags @{ Name = "testtag"; Value = "testval" }

# New
New-AzureRmResourceGroup -Name $resourceGroupName -Location -location -Tag @{ testtag = "testval" }
```

<br>

## <a name="breaking-changes-to-storage-cmdlets"></a>Cambios sustanciales en los cmdlets de Storage

Los siguientes cmdlets han resultado afectados en esta versión:

**Get-AzureRmStorageAccountKey**
- Ahora, el cmdlet devuelve una lista de claves, en lugar de un objeto con propiedades para cada clave

```powershell
# Old
$key = (Get-AzureRmStorageAccountKey -ResourceGroupName $resourceGroupName -Name $accountName).Key1

# New
$key = (Get-AzureRmStorageAccountKey -ResourceGroupName $resourceGroupName -Name $accountName)[0].Value
```

**New-AzureRmStorageAccountKey**
- El nombre del campo `StorageAccountRegenerateKeyResponse` del resultado de este cmdlet cambia a `StorageAccountListKeysResults`, que ahora es una lista de claves, en lugar de un objeto con propiedades para cada clave

```powershell
# Old
$key = (New-AzureRmStorageAccountKey -ResourceGroupName $resourceGroupName -Name $accountName).StorageAccountKeys.Key1

# New
$key = (New-AzureRmStorageAccountKey -ResourceGroupName $resourceGroupName -Name $accountName).Keys[0].Value
```

**New/Get/Set-AzureRmStorageAccount**
- El nombre del campo `AccountType` del resultado de este cmdlet cambia a `Sku.Name`
- El tipo de salida del blob, tabla, cola, archivo de PrimaryEndpoints y SecondaryEndpoints ha cambiado de `Uri` a `String`

```powershell
# Old
$accountType = (Get-AzureRmStorageAccount -ResourceGroupName $resourceGroupName -Name $accountName).AccountType

# New
$accountType = (Get-AzureRmStorageAccount -ResourceGroupName $resourceGroupName -Name $accountName).Sku.Name
```

```powershell
# Old 
$blobEndpoint = (Get-AzureRmStorageAccount -ResourceGroupName $resourceGroupName -Name $accountName).PrimaryEndpoints.Blob.ToString()
$blobEndpoint = (Get-AzureRmStorageAccount -ResourceGroupName $resourceGroupName -Name $accountName).PrimaryEndpoints.Blob.AbsolutePath

# New
$blobEndpoint = (Get-AzureRmStorageAccount -ResourceGroupName $resourceGroupName -Name $accountName).PrimaryEndpoints.Blob.ToString()
$blobEndpoint = (Get-AzureRmStorageAccount -ResourceGroupName $resourceGroupName -Name $accountName).PrimaryEndpoints.Blob
```

<br>

## <a name="breaking-changes-to-ad-cmdlets"></a>Cambios sustanciales en los cmdlets de AD

Los siguientes cmdlets han resultado afectados en esta versión:

**Get-AzureRMADServicePrincipal**
- El nombre del campo `ServicePrincipalName` del resultado de este cmdlet cambia a `ServicePrincipalNames` y ahora es una colección. Ahora muestra `ApplicationId` también como uno de los SPN, junto con identifierUri.

```powershell
# Old
$servicePrincipals = Get-AzureRmADServicePrincipal -SearchString $displayName
$spn = $servicePrincipals[0].ServicePrincipalName

# New
$servicePrincipals = Get-AzureRmADServicePrincipal -SearchString $displayName
$spn = $servicePrincipals[0].ServicePrincipalNames[0]
```

**Get-AzureRmADApplication**
- El nombre del parámetro `ApplicationObjectId` ha cambiado a `ObjectId`.
- En la salida de este cdmlet, el nombre de `ApplicationObjectId` se cambia a `ObjectId`.

```powershell
# Old
$app = Get-AzureRmADApplication -ApplicationObjectId $applicationObjectId
$objectId = $app.ApplicationObjectId

# New
$app = Get-AzureRmADApplication -ObjectId $objectId
$objectId = $app.ObjectId
```

**Remove-AzureRmADApplication**
- El nombre del parámetro `ApplicationObjectId` ha cambiado a `ObjectId`.

```powershell
# Old
$app = Remove-AzureRmADApplication -ApplicationObjectId $applicationObjectId -Force

# New
$app = Remove-AzureRmADApplication -ObjectId $objectId -Force
```

**New-AzureRmADApplication**
- En la salida de este cdmlet, el nombre de `ApplicationObjectId` se cambia a `ObjectId`.
- Se quitan los parámetros `KeyValue`, `KeyUsage`, `KeyType`.

```powershell
# Old
$app = New-AzureRmADApplication -DisplayName $displayName -HomePage $homePage -IdentifierUris $identifierUris -KeyValue $kv -KeyType $kt -KeyUsage $ku
$id = $app.ApplicationObjectId

# New
$app = New-AzureRmADApplication -DisplayName $displayName -HomePage $homePage -IdentifierUris $identifierUris
$id = $app.ObjectId
New-AzureRmADAppCredential -ObjectId $id -Password $kv
```

**Get-AzureRmADGroup**
- El campo `Mail` se ha quitado de la salida.

**Get-AzureRmADUser**
- El campo `Mail` se ha quitado de la salida.

**New-AzureRmADServicePrincipal**
- El parámetro `DisableAccount` se ha eliminado.

```powershell
# Old
$servicePrincipal = New-AzureRmADServicePrincipal -DisplayName $displayName -Password $password -DisableAccount true

# New
$servicePrincipal = New-AzureRmADServicePrincipal -DisplayName $displayName -Password $password
Remove-AzureRmADServicePrincipal -ObjectId $servicePrincipal.ObjectId
```