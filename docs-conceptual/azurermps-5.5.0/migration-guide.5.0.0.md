# <a name="breaking-changes-for-microsoft-azure-powershell-500"></a>Cambios sustanciales en Microsoft Azure PowerShell 5.0.0

Este documento sirve no solo como notificación de los cambios sustanciales, sino también como guía de migración para los consumidores de los cmdlets de Microsoft Azure PowerShell. En todas las secciones se describen tanto el ímpetu del cambio como la ruta de acceso de la migración más sencilla. Para ver el contexto en profundidad, consulte la solicitud de incorporación de cambios asociada a cada cambio.

## <a name="table-of-contents"></a>Tabla de contenido

- [Cambios sustanciales en cmdlets de ApiManagement](#breaking-changes-to-apimanagement-cmdlets)
- [Cambios sustanciales en los cmdlets de Batch](#breaking-changes-to-batch-cmdlets)
- [Cambios substanciales en cmdlets de Compute](#breaking-changes-to-compute-cmdlets)
- [Cambios substanciales en cmdlets de EventHub](#breaking-changes-to-eventhub-cmdlets)
- [Cambios substanciales en cmdlets de Insights](#breaking-changes-to-insights-cmdlets)
- [Cambios substanciales en cmdlets de Network](#breaking-changes-to-network-cmdlets)
- [Cambios sustanciales en los cmdlets de Resources](#breaking-changes-to-resources-cmdlets)
- [Cambios sustanciales en los cmdlets de ServiceBus](#breaking-changes-to-servicebus-cmdlets)

## <a name="breaking-changes-to-apimanagement-cmdlets"></a>Cambios sustanciales en los cmdlets de ApiManagement

### <a name="new-azurermapimanagementbackendproxy"></a>**New-AzureRmApiManagementBackendProxy**
- Los parámetros "UserName" y "Password" se han reemplazado en favor de PSCredential

```powershell
# Old
New-AzureRmApiManagementBackendProxy [other required parameters] -UserName "plain-text string" -Password "plain-text string"

# New
New-AzureRmApiManagementBackendProxy [other required parameters] -Credential $PSCredentialVariable
```

### <a name="new-azurermapimanagementuser"></a>**New-AzureRmApiManagementUser**
- El parámetro "Password" se ha reemplazar en favor de SecureString

```powershell
# Old
New-AzureRmApiManagementUser [other required parameters] -Password "plain-text string"

# New
New-AzureRmApiManagementUser [other required parameters] -Password $SecureStringVariable
```

### <a name="set-azurermapimanagementuser"></a>**Set-AzureRmApiManagementUser**
- El parámetro "Password" se ha reemplazar en favor de SecureString

```powershell
# Old
Set-AzureRmApiManagementUser [other required parameters] -Password "plain-text string"

# New
Set-AzureRmApiManagementUser [other required parameters] -Password $SecureStringVariable
```

## <a name="breaking-changes-to-batch-cmdlets"></a>Cambios sustanciales en los cmdlets de Batch

### <a name="new-azurebatchcertificate"></a>**New-AzureBatchCertificate**
- El parámetro `Password` se ha sustituido en favor de SecureString

```powershell
# Old
New-AzureBatchCertificate [other required parameters] -Password "plain-text string"

# New
New-AzureBatchCertificate [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurebatchcomputenodeuser"></a>**New-AzureBatchComputeNodeUser**
- El parámetro `Password` se ha sustituido en favor de SecureString

```powershell
# Old
New-AzureBatchComputeNodeUser [other required parameters] -Password "plain-text string"

# New
New-AzureBatchComputeNodeUser [other required parameters] -Password $SecureStringVariable
```

### <a name="set-azurermbatchcomputenodeuser"></a>**Set-AzureRmBatchComputeNodeUser**
- El parámetro `Password` se ha sustituido en favor de SecureString

```powershell
# Old
Set-AzureRmBatchComputeNodeUser [other required parameters] -Password "plain-text string"

# New
Set-AzureRmBatchComputeNodeUser [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurebatchtask"></a>**New-AzureBatchTask**
 - El modificador `RunElevated` se ha reemplazado por `UserIdentity`.

```powershell
# Old
New-AzureBatchTask -Id $taskId1 -JobId $jobId -CommandLine "cmd /c echo hello" -RunElevated $TRUE

# New
$autoUser = New-Object Microsoft.Azure.Commands.Batch.Models.PSAutoUserSpecification -ArgumentList @("Task", "Admin")
$userIdentity = New-Object Microsoft.Azure.Commands.Batch.Models.PSUserIdentity $autoUser
New-AzureBatchTask -Id $taskId1 -JobId $jobId -CommandLine "cmd /c echo hello" -UserIdentity $userIdentity
```

Adicionalmente, esto afecta a la propiedad `RunElevated` de `PSCloudTask`, `PSStartTask`, `PSJobManagerTask`, `PSJobPreparationTask` y `PSJobReleaseTask`.

### <a name="psmultiinstancesettings"></a>**PSMultiInstanceSettings**

- El constructor `PSMultiInstanceSettings` no toma un parámetro `numberOfInstances` requerido, sino que toma un parámetro `coordinationCommandLine` requerido.

```powershell
# Old
$settings = New-Object Microsoft.Azure.Commands.Batch.Models.PSMultiInstanceSettings -ArgumentList @(2)
$settings.CoordinationCommandLine = "cmd /c echo hello"
New-AzureBatchTask [other parameters] -MultiInstanceSettings $settings

# New
$settings = New-Object Microsoft.Azure.Commands.Batch.Models.PSMultiInstanceSettings -ArgumentList @("cmd /c echo hello", 2)
New-AzureBatchTask [other parameters] -MultiInstanceSettings $settings
```

### <a name="get-azurebatchtask"></a>**Get-AzureBatchTask**
 - Se ha quitado la propiedad `RunElevated` en `PSCloudTask`. Se ha agregado la propiedad `UserIdentity` para reemplazar a `RunElevated`.

```powershell
# Old
$task = Get-AzureBatchTask [parameters]
$task.RunElevated

# New
$task = Get-AzureBatchTask [parameters]
$task.UserIdentity.AutoUser.ElevationLevel
```

Adicionalmente, esto afecta a la propiedad `RunElevated` en `PSCloudTask`, `PSStartTask`, `PSJobManagerTask`, `PSJobPreparationTask` y `PSJobReleaseTask`.

### <a name="multiple-types"></a>**Tipos múltiples**

- Se ha cambiado el nombre de la propiedad `SchedulingError` en `PSExitConditions` a `PreProcessingError`.

```powershell
# Old
$task = Get-AzureBatchTask [parameters]
$task.ExitConditions.SchedulingError

# New
$task = Get-AzureBatchTask [parameters]
$task.ExitConditions.PreProcessingError
```

### <a name="multiple-types"></a>**Tipos múltiples**

- Se ha cambiado el nombre de la propiedad `SchedulingError` en `PSJobPreparationTaskExecutionInformation`, `PSJobReleaseTaskExecutionInformation`, `PSStartTaskInformation`, `PSSubtaskInformation` y `PSTaskExecutionInformation` a `FailureInformation`.
  - `FailureInformation`se devuelve alguna vez que se produzca un error en alguna tarea. Aquí se incluyen todos los casos de error de programación anteriores, así como los códigos de salida de tareas distintos de cero y los errores de carga de archivos de la nueva característica de archivos de salida.
  - La estructura no varía, por lo que cuando se usa este tipo no es necesario realizar ningún cambio en el código.

```powershell
# Old
$task = Get-AzureBatchTask [parameters]
$task.ExecutionInformation.SchedulingError

# New
$task = Get-AzureBatchTask [parameters]
$task.ExecutionInformation.FailureInformation
```

Afecta también a: Get-AzureBatchPool, Get-AzureBatchSubtask y Get-AzureBatchJobPreparationAndReleaseTaskStatus

### <a name="new-azurebatchpool"></a>**New-AzureBatchPool**
 - `TargetDedicated` se ha reemplazado por `TargetDedicatedComputeNodes` y `TargetLowPriorityComputeNodes`.
 - `TargetDedicatedComputeNodes` tiene un alias `TargetDedicated`.

```powershell
# Old
New-AzureBatchPool [other parameters] [-TargetDedicated <Int32>]

# New
New-AzureBatchPool [other parameters] [-TargetDedicatedComputeNodes <Int32>] [-TargetLowPriorityComputeNodes <Int32>]
```

Afecta también a: Start-AzureBatchPoolResize

### <a name="get-azurebatchpool"></a>**Get-AzureBatchPool**
 - Se ha cambiado el nombre de las propiedades `TargetDedicated` y `CurrentDedicated` de `PSCloudPool` a `TargetDedicatedComputeNodes` y `CurrentDedicatedComputeNodes`.

```powershell
# Old
$pool = Get-AzureBatchPool [parameters]
$pool.TargetDedicated
$pool.CurrentDedicated

# New
$pool = Get-AzureBatchPool [parameters]
$pool.TargetDedicatedComputeNodes
$pool.CurrentDedicatedComputeNodes
```

### <a name="type-pscloudpool"></a>**Tipo PSCloudPool**

- Se ha cambiado el nombre de `ResizeError` a `ResizeErrors` en `PSCloudPool` y ahora es una colección.

```powershell
# Old
$pool = Get-AzureBatchPool [parameters]
$pool.ResizeError

# New
$pool = Get-AzureBatchPool [parameters]
$pool.ResizeErrors[0]
```

### <a name="new-azurebatchjob"></a>**New-AzureBatchJob**
- Se ha cambiado el nombre de la propiedad `TargetDedicated` en `PSPoolSpecification` a `TargetDedicatedComputeNodes`.

```powershell
# Old
$poolInfo = New-Object Microsoft.Azure.Commands.Batch.Models.PSPoolInformation
$poolInfo.AutoPoolSpecification = New-Object Microsoft.Azure.Commands.Batch.Models.PSAutoPoolSpecification
$poolInfo.AutoPoolSpecification.PoolSpecification = New-Object Microsoft.Azure.Commands.Batch.Models.PSPoolSpecification
$poolInfo.AutoPoolSpecification.PoolSpecification.TargetDedicated = 5
New-AzureBatchJob [other parameters] -PoolInformation $poolInfo

# New
$poolInfo = New-Object Microsoft.Azure.Commands.Batch.Models.PSPoolInformation
$poolInfo.AutoPoolSpecification = New-Object Microsoft.Azure.Commands.Batch.Models.PSAutoPoolSpecification
$poolInfo.AutoPoolSpecification.PoolSpecification = New-Object Microsoft.Azure.Commands.Batch.Models.PSPoolSpecification
$poolInfo.AutoPoolSpecification.PoolSpecification.TargetDedicatedComputeNodes = 5
New-AzureBatchJob [other parameters] -PoolInformation $poolInfo
```

### <a name="get-azurebatchnodefile"></a>**Get-AzureBatchNodeFile**
 - `Name` se ha reemplazado por `Path`.
 - `Path` tiene un alias `Name`.

```powershell
# Old
Get-AzureBatchNodeFile [other parameters] [[-Name] <String>]

# New
Get-AzureBatchNodeFile [other parameters] [[-Path] <String>]
```

Afecta también a : Get-AzureBatchNodeFileContent y Remove-AzureBatchNodeFile

### <a name="type-psnodefile"></a>Tipo **PSNodeFile**

 - Se ha cambiado el nombre de la propiedad `Name` en `PSNodeFile` a `Path`.

```powershell
# Old
$file = Get-AzureBatchNodeFile [parameters]
$file.Name

# New
$file = Get-AzureBatchNodeFile [parameters]
$file.Path
```

### <a name="get-azurebatchsubtask"></a>**Get-AzureBatchSubtask**
- Las propiedades `PreviousState` y `State` de `PSSubtaskInformation` dejan de ser del tipo `TaskState`, ahora son del tipo `SubtaskState`.
  - A diferencia de `TaskState`, `SubtaskState` no tiene ningún el valor `Active`, ya que no es posible que las subtareas estén en estado `Active`.

```powershell
# Old
$subtask = Get-AzureBatchSubtask [parameters]
if ($subtask.State -eq Microsoft.Azure.Batch.Common.TaskState.Running) { }

# New
$subtask = Get-AzureBatchSubtask [parameters]
if ($subtask.State -eq Microsoft.Azure.Batch.Common.SubtaskState.Running) { }
```

## <a name="breaking-changes-to-compute-cmdlets"></a>Cambios substanciales en cmdlets de Compute

### <a name="set-azurermvmaccessextension"></a>**Set-AzureRmVMAccessExtension**
- Los parámetros "UserName" y "Password" se han reemplazado en favor de PSCredential

```powershell
# Old
Set-AzureRmVMAccessExtension [other required parameters] -UserName "plain-text string" -Password "plain-text string"

# New
Set-AzureRmVMAccessExtension [other required parameters] -Credential $PSCredential
```

## <a name="breaking-changes-to-eventhub-cmdlets"></a>Cambios sustanciales en los cmdlets de EventHub

### <a name="new-azurermeventhubnamespaceauthorizationrule"></a>**New-AzureRmEventHubNamespaceAuthorizationRule**
- Se ha eliminado el cmdlet 'New-AzureRmEventHubNamespaceAuthorizationRule'. Use el cmdlet 'New-AzureRmEventHubAuthorizationRule'
    
### <a name="get-azurermeventhubnamespaceauthorizationrule"></a>**Get-AzureRmEventHubNamespaceAuthorizationRule**
- Se ha eliminado el cmdlet 'Get-AzureRmEventHubNamespaceAuthorizationRule'. Use el cmdlet 'Get-AzureRmEventHubAuthorizationRule'
    
### <a name="set-azurermeventhubnamespaceauthorizationrule"></a>**Set-AzureRmEventHubNamespaceAuthorizationRule**
- Se ha eliminado el cmdlet 'Set-AzureRmEventHubNamespaceAuthorizationRule'. Use el cmdlet 'Set-AzureRmEventHubAuthorizationRule'
    
### <a name="remove-azurermeventhubnamespaceauthorizationrule"></a>**Remove-AzureRmEventHubNamespaceAuthorizationRule**
- Se ha eliminado el cmdlet 'Remove-AzureRmEventHubNamespaceAuthorizationRule'. Use el cmdlet 'Remove-AzureRmEventHubAuthorizationRule'
    
### <a name="new-azurermeventhubnamespacekey"></a>**New-AzureRmEventHubNamespaceKey**
- Se ha eliminado el cmdlet 'New-AzureRmEventHubNamespaceKey'. Use el cmdlet 'New-AzureRmEventHubKey'
    
### <a name="get-azurermeventhubnamespacekey"></a>**Get-AzureRmEventHubNamespaceKey**
- Se ha eliminado el cmdlet 'Get-AzureRmEventHubNamespaceKey'. Use el cmdlet 'Get-AzureRmEventHubKey'
    
### <a name="new-azurermeventhubnamespace"></a>**New-AzureRmEventHubNamespace**
- Se quitarán las propiedades 'Status' y 'Enabled' de NamespceAttributes. 

```powershell
# Old
# The $namespace has Status and Enabled property  
$namespace = New-AzureRmEventHubNamespace <parameters>
$namespace.Status
$namespace.Enabled

# New
# The call remains the same, but the returned values NameSpace object will not have the Status and Enabled property    
$namespace = Get-AzureRmEventHubNamespace <parameters>
```
    
### <a name="get-azurermeventhubnamespace"></a>**Get-AzureRmEventHubNamespace**
- Se quitarán las propiedades 'Status' y 'Enabled' de NamespceAttributes. 

```powershell
# Old
# The $namespace has Status and Enabled property 
$namespace = Get-AzureRmEventHubNamespace <parameters>
$namespace.Status
$namespace.Enabled

# New
# The call remains the same, but the returned values NameSpace object will not have the Status and Enabled property    
$namespace = Get-AzureRmEventHubNamespace <parameters>
```
    
### <a name="set-azurermeventhubnamespace"></a>**Set-AzureRmEventHubNamespace**
- Se quitarán las propiedades 'Status' y 'Enabled' de NamespceAttributes. 

```powershell
# Old
# The $namespace has Status and Enabled property 
$namespace = Set-AzureRmEventHubNamespace <parameters>
$namespace.Status
$namespace.Enabled

# New
# The call remains the same, but the returned values NameSpace object will not have the Status and Enabled property    
$namespace = Set-AzureRmEventHubNamespace <parameters>
``` 
  
### <a name="new-azurermeventhubconsumergroup"></a>**New-AzureRmEventHubConsumerGroup**
- Se eliminará la propiedad 'EventHubPath' de ConsumerGroupAttributes.

```powershell
# Old
# The $consumergroup has EventHubPath property 
$consumergroup = New-AzureRmEventHubConsumerGroup <parameters>
$consumergroup.EventHubPath

# New
# The call remains the same, but the returned values ConsumerGroup object will not have the EventHubPath property    
$consumergroup = New-AzureRmEventHubConsumerGroup <parameters>
```
    
### <a name="set-azurermeventhubconsumergroup"></a>**Set-AzureRmEventHubConsumerGroup**
- Se eliminará la propiedad 'EventHubPath' de ConsumerGroupAttributes.

```powershell
# Old
# The $consumergroup has EventHubPath property 
$consumergroup = Set-AzureRmEventHubConsumerGroup <parameters>
$consumergroup.EventHubPath

# New
# The call remains the same, but the returned values ConsumerGroup object will not have the EventHubPath property    
$consumergroup = Set-AzureRmEventHubConsumerGroup <parameters>
```
    
### <a name="get-azurermeventhubconsumergroup"></a>**Get-AzureRmEventHubConsumerGroup**
- Se eliminará la propiedad 'EventHubPath' de ConsumerGroupAttributes.

```powershell
# Old
# The $consumergroup has EventHubPath property 
$consumergroup = Get-AzureRmEventHubConsumerGroup <parameters>
$consumergroup.EventHubPath

# New
# The call remains the same, but the returned values ConsumerGroup object will not have the EventHubPath property    
$consumergroup = Get-AzureRmEventHubConsumerGroup <parameters>
```

## <a name="breaking-changes-to-insights-cmdlets"></a>Cambios sustanciales en los cmdlets de Insights

### <a name="add-azurermlogalertrule"></a>**Add-AzureRMLogAlertRule**
- El cmdlet **Add-AzureRMLogAlertRule** está en desuso
- A partir del 1 de octubre el uso de este cmdlet no tendrá ningún efecto, ya que esta funcionalidad se ha pasado a las alertas de registro de actividad. Consulte https://aka.ms/migratemealerts para más información.

### <a name="get-azurermusage"></a>**Get-AzureRMUsage**
- El cmdlet **AzureRMUsage Get** está en desuso

### <a name="get-azurermalerthistory--get-azurermautoscalehistory--get-azurermlogs"></a>**Get-AzureRmAlertHistory** / **Get-AzureRmAutoscaleHistory** / **Get-AzureRmLogs**
- Cambio de salida: el campo EventChannels del objeto EventData (que devuelven estos cmdlets) está en desuso, ya que ahora devuelve un valor constante (Admin, Operation).

### <a name="get-azurermalertrule"></a>**Get-AzureRmAlertRule**
- Cambio de salida: la salida de este cmdlet se acoplará; es decir, se elimina el campo de propiedades para mejorar la experiencia del usuario.

```powershell
# Old
$rules = Get-AzureRmAlertRule -ResourceGroup $resourceGroup
if ($rules -and $rules.count -ge 1)
{
    Write-Host -Foreground Red "Error updating alert rule"
    Write-Host $rules[0].Id
    Write-Host $rules[0].Properties.IsEnabled
    Write-Host $rules[0].Properties.Condition
}

# New
$rules = Get-AzureRmAlertRule -ResourceGroup $resourceGroup
if ($rules -and $rules.count -ge 1)
{
    Write-Host -Foreground red "Error updating alert rule"
    Write-Host $rules[0].Id

    # Properties will remain for a while
    Write-Host $rules[0].Properties.IsEnabled
      
    # But the properties will be at the top level too. Later Properties will be removed
    Write-Host $rules[0].IsEnabled
    Write-Host $rules[0].Condition
}
```

### <a name="get-azurermautoscalesetting"></a>**Get-AzureRmAutoscaleSetting**
- Cambio de salida: el campo AutoscaleSettingResourceName dejará de utilizarse, ya que su valor es siempre el mismo que el del campo Name.

```powershell
# Old
$s1 = Get-AzureRmAutoscaleSetting -ResourceGroup $resourceGroup -Name MySetting
if ($s1.AutoscaleSettingResourceName -ne $s1.Name)
{
    Write-Host "There is something wrong with the name"
}

# New
$s1 = Get-AzureRmAutoscaleSetting -ResourceGroup $resourceGroup -Name MySetting
    
# there won't be a AutoscaleSettingResourceName
Write-Host $s1.Name    
```

### <a name="remove-azurermalertrule--remove-azurermlogprofile"></a>**Remove-AzureRmAlertRule** / **Remove-AzureRmLogProfile**
- Cambio de salida: el tipo de la salida cambiará para devolver un solo objeto que contiene el Id. de solicitud y el código de estado.

```powershell
# Old
$s1 = Remove-AzureRmAlertRule -ResourceGroup $resourceGroup -name $ruleName
if ($s1 -ne $null)
{
    $r = $s1[0].RequestId
    $s = $s1[0].StatusCode
}

# New
$s1 = Remove-AzureRmAlertRule -ResourceGroup $resourceGroup -name $ruleName
$r = $s1.RequestId
$s = $s1.StatusCode
```

## <a name="breaking-changes-to-network-cmdlets"></a>Cambios sustanciales en los cmdlets de Network

### <a name="add-azurermapplicationgatewaysslcertificate"></a>**Add-AzureRmApplicationGatewaySslCertificate**
- El parámetro "Password" se ha reemplazar en favor de SecureString

```powershell
# Old
Add-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password "plain-text string"

# New
Add-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurermapplicationgatewaysslcertificate"></a>**New-AzureRmApplicationGatewaySslCertificate**
- El parámetro "Password" se ha reemplazar en favor de SecureString

```powershell
# Old
New-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password "plain-text string"

# New
New-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password $SecureStringVariable
```

### <a name="set-azurermapplicationgatewaysslcertificate"></a>**Set-AzureRmApplicationGatewaySslCertificate**
- El parámetro "Password" se ha reemplazar en favor de SecureString

```powershell
# Old
Set-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password "plain-text string"

# New
Set-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password $SecureStringVariable
```

## <a name="breaking-changes-to-resources-cmdlets"></a>Cambios sustanciales en los cmdlets de Resources

### <a name="new-azurermadappcredential"></a>**New-AzureRmADAppCredential**
- El parámetro "Password" se ha reemplazar en favor de SecureString

```powershell
# Old
New-AzureRmADAppCredential [other required parameters] -Password "plain-text string"

# New
New-AzureRmADAppCredential [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurermadapplication"></a>**New-AzureRmADApplication**
- El parámetro "Password" se ha reemplazar en favor de SecureString

```powershell
# Old
New-AzureRmADApplication [other required parameters] -Password "plain-text string"

# New
New-AzureRmADApplication [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurermadserviceprincipal"></a>**New-AzureRmADServicePrincipal**
- El parámetro "Password" se ha reemplazar en favor de SecureString

```powershell
# Old
New-AzureRmADServicePrincipal [other required parameters] -Password "plain-text string"

# New
New-AzureRmADServicePrincipal [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurermadspcredential"></a>**New-AzureRmADSpCredential**
- El parámetro "Password" se ha reemplazar en favor de SecureString

```powershell
# Old
New-AzureRmADSpCredential [other required parameters] -Password "plain-text string"

# New
New-AzureRmADSpCredential [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurermaduser"></a>**New-AzureRmADUser**
- El parámetro "Password" se ha reemplazar en favor de SecureString

```powershell
# Old
New-AzureRmADUser [other required parameters] -Password "plain-text string"

# New
New-AzureRmADUser [other required parameters] -Password $SecureStringVariable
```

### <a name="set-azurermaduser"></a>**Set-AzureRmADUser**
- El parámetro "Password" se ha reemplazar en favor de SecureString

```powershell
# Old
Set-AzureRmADUser [other required parameters] -Password "plain-text string"

# New
Set-AzureRmADUser [other required parameters] -Password $SecureStringVariable
```

## <a name="breaking-changes-to-servicebus-cmdlets"></a>Cambios sustanciales en los cmdlets de ServiceBus

### <a name="get-azurermservicebustopicauthorizationrule"></a>**Get-AzureRmServiceBusTopicAuthorizationRule**
- Se ha eliminado el cmdlet 'Get-AzureRmServiceBusTopicAuthorizationRule'. Use el cmdlet 'Get-AzureRmServiceBusAuthorizationRule'.    

### <a name="get-azurermservicebustopickey"></a>**Get-AzureRmServiceBusTopicKey**
- Se ha eliminado el cmdlet 'Get-AzureRmServiceBusTopicKey'. Use el cmdlet 'Get-AzureRmServiceBusKey'.

### <a name="new-azurermservicebustopicauthorizationrule"></a>**New-AzureRmServiceBusTopicAuthorizationRule**
- Se ha eliminado el cmdlet 'Get-AzureRmServiceBusTopicAuthorizationRule'. Use el cmdlet 'Get-AzureRmServiceBusAuthorizationRule'.

### <a name="new-azurermservicebustopickey"></a>**New-AzureRmServiceBusTopicKey**
- Se ha eliminado el cmdlet 'New-AzureRmServiceBusTopicKey'. Use el cmdlet 'Get-AzureRmServiceBusKey'.

### <a name="remove-azurermservicebustopicauthorizationrule"></a>**Remove-AzureRmServiceBusTopicAuthorizationRule**
- Se ha eliminado el cmdlet 'Remove-AzureRmServiceBusTopicAuthorizationRule'. Use el cmdlet 'Remove-AzureRmServiceBusAuthorizationRule'.

### <a name="set-azurermservicebustopicauthorizationrule"></a>**Set-AzureRmServiceBusTopicAuthorizationRule**
- Se ha eliminado el cmdlet 'Set-AzureRmServiceBusTopicAuthorizationRule'. Use el cmdlet 'Set-AzureRmServiceBusAuthorizationRule'.

### <a name="new-azurermservicebusnamespacekey"></a>**New-AzureRmServiceBusNamespaceKey**
- Se ha eliminado el cmdlet 'New-AzureRmServiceBusNamespaceKey'. Use el cmdlet 'Get-AzureRmServiceBusKey'.

### <a name="get-azurermservicebusqueueauthorizationrule"></a>**Get-AzureRmServiceBusQueueAuthorizationRule**
- Se ha eliminado el cmdlet 'Get-AzureRmServiceBusQueueAuthorizationRule'. Use el cmdlet 'Get-AzureRmServiceBusAuthorizationRule'.

### <a name="get-azurermservicebusqueuekey"></a>**Get-AzureRmServiceBusQueueKey**
- Se ha eliminado el cmdlet 'Get-AzureRmServiceBusQueueKey'. Use el cmdlet 'Get-AzureRmServiceBusKey'.

### <a name="new-azurermservicebusqueueauthorizationrule"></a>**New-AzureRmServiceBusQueueAuthorizationRule**
- Se ha eliminado el cmdlet 'New-AzureRmServiceBusQueueAuthorizationRule'. Use el cmdlet 'Get-AzureRmServiceBusAuthorizationRule'.

### <a name="new-azurermservicebusqueuekey"></a>**New-AzureRmServiceBusQueueKey**
- Se ha eliminado el cmdlet 'New-AzureRmServiceBusQueueKey'. Use el cmdlet 'Get-AzureRmServiceBusKey'.

### <a name="remove-azurermservicebusqueueauthorizationrule"></a>**Remove-AzureRmServiceBusQueueAuthorizationRule**
- Se ha eliminado el cmdlet 'Remove-AzureRmServiceBusQueueAuthorizationRule'. Use el cmdlet 'GRemove-AzureRmServiceBusAuthorizationRule'.

### <a name="set-azurermservicebusqueueauthorizationrule"></a>**Set-AzureRmServiceBusQueueAuthorizationRule**
- Se ha eliminado el cmdlet 'Set-AzureRmServiceBusQueueAuthorizationRule'. Use el cmdlet 'Set-AzureRmServiceBusAuthorizationRule'.

### <a name="get-azurermservicebusnamespaceauthorizationrule"></a>**Get-AzureRmServiceBusNamespaceAuthorizationRule**
- Se ha eliminado el cmdlet 'Get-AzureRmServiceBusNamespaceAuthorizationRule'. Use el cmdlet 'Get-AzureRmServiceBusAuthorizationRule'.

### <a name="get-azurermservicebusnamespacekey"></a>**Get-AzureRmServiceBusNamespaceKey**
- Se ha eliminado el cmdlet 'Get-AzureRmServiceBusNamespaceKey'. Use el cmdlet 'Get-AzureRmServiceBusKey'.

### <a name="new-azurermservicebusnamespaceauthorizationrule"></a>**New-AzureRmServiceBusNamespaceAuthorizationRule**
- Se ha eliminado el cmdlet 'New-AzureRmServiceBusNamespaceAuthorizationRule'. Use el cmdlet 'Get-AzureRmServiceBusAuthorizationRule'.

### <a name="remove-azurermservicebusnamespaceauthorizationrule"></a>**Remove-AzureRmServiceBusNamespaceAuthorizationRule**
- Se ha eliminado el cmdlet 'Remove-AzureRmServiceBusNamespaceAuthorizationRule'. Use el cmdlet 'Remove-AzureRmServiceBusAuthorizationRule'.

### <a name="set-azurermservicebusnamespaceauthorizationrule"></a>**Set-AzureRmServiceBusNamespaceAuthorizationRule**
- Se ha eliminado el cmdlet 'Set-AzureRmServiceBusNamespaceAuthorizationRule'. Use el cmdlet 'Set-AzureRmServiceBusAuthorizationRule'.

### <a name="type-namespaceattributes"></a>**Tipo NamespaceAttributes**
- Se han quitado las siguientes propiedades
    - habilitado
    - Status
   
```powershell
# Old
# The $namespace has Status and Enabled property 
$namespace = Get-AzureRmServiceBusNamespace <parameters>
$namespace.Status
$namespace.Enabled

# New
# The call remains the same, but the returned values NameSpace object will not have the Enabled and Status properties    
$namespace = Get-AzureRmServiceBusNamespace <parameters>
```

### <a name="type-queueattribute"></a>**Tipo QueueAttribute**
- Las siguientes propiedades se marcan como obsoletas:
    - EnableBatchedOperations
    - EntityAvailabilityStatus
    - IsAnonymousAccessible
    - SupportOrdering

```powershell
# Old
# The $queue has EntityAvailabilityStatus, EnableBatchedOperations, IsAnonymousAccessible and SupportOrdering properties
$queue = Get-AzureRmServiceBusQueue <parameters>
$queue.EntityAvailabilityStatus
$queue.EnableBatchedOperations
$queue.IsAnonymousAccessible
$queue.SupportOrdering  

# New
# The call remains the same, but the returned values Queue object will not have the EntityAvailabilityStatus, EnableBatchedOperations, IsAnonymousAccessible and SupportOrdering properties    
$queue = Get-AzureRmServiceBusQueue <parameters>
```
   
### <a name="type-topicattribute"></a>**Tipo TopicAttribute**
- Las siguientes propiedades se marcan como obsoletas:
    - Ubicación
    - IsExpress
    - IsAnonymousAccessible
    - FilteringMessagesBeforePublishing
    - EnableSubscriptionPartitioning
    - EntityAvailabilityStatus

```powershell
# Old
# The $topic has EntityAvailabilityStatus, EnableSubscriptionPartitioning, IsAnonymousAccessible, IsExpress, Location and FilteringMessagesBeforePublishing properties
$topic = Get-AzureRmServiceBusTopic <parameters>
$topic.EntityAvailabilityStatus
$topic.EnableSubscriptionPartitioning
$topic.IsAnonymousAccessible
$topic.IsExpress
$topic.FilteringMessagesBeforePublishing
$topic.Location

# New
# The call remains the same, but the returned values Topic object will not have the EntityAvailabilityStatus, EnableBatchedOperations, IsAnonymousAccessible and SupportOrdering properties    
$topic = Get-AzureRmServiceBusTopic <parameters>
```
   
### <a name="type-subscriptionattribute"></a>**Tipo SubscriptionAttribute**
- Las siguientes propiedades se marcan como obsoletas
    - DeadLetteringOnFilterEvaluationExceptions
    - EntityAvailabilityStatus
    - IsReadOnly
    - Ubicación
   
```powershell
# Old
# The $subscription has EntityAvailabilityStatus, EnableSubscriptionPartitioning, IsAnonymousAccessible, IsExpress, Location and FilteringMessagesBeforePublishing properties
$subscription = Get-AzureRmServiceBussubscription <parameters>
$subscription.EntityAvailabilityStatus
$subscription.EnableSubscriptionPartitioning
$subscription.IsAnonymousAccessible
$subscription.IsExpress
$subscription.FilteringMessagesBeforePublishing
$subscription.Location

# New
# The call remains the same, but the returned values Topic object will not have the EntityAvailabilityStatus, EnableBatchedOperations, IsAnonymousAccessible and SupportOrdering properties    
$subscription = Get-AzureRmServiceBussubscription <parameters>
```