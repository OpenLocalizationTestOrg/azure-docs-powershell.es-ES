# <a name="breaking-changes-for-microsoft-azure-powershell-500"></a><span data-ttu-id="609cd-101">Cambios sustanciales en Microsoft Azure PowerShell 5.0.0</span><span class="sxs-lookup"><span data-stu-id="609cd-101">Breaking changes for Microsoft Azure PowerShell 5.0.0</span></span>

<span data-ttu-id="609cd-102">Este documento sirve no solo como notificación de los cambios sustanciales, sino también como guía de migración para los consumidores de los cmdlets de Microsoft Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="609cd-102">This document serves as both a breaking change notification and migration guide for consumers of the Microsoft Azure PowerShell cmdlets.</span></span> <span data-ttu-id="609cd-103">En todas las secciones se describen tanto el ímpetu del cambio como la ruta de acceso de la migración más sencilla.</span><span class="sxs-lookup"><span data-stu-id="609cd-103">Each section describes both the impetus for the breaking change and the migration path of least resistance.</span></span> <span data-ttu-id="609cd-104">Para ver el contexto en profundidad, consulte la solicitud de incorporación de cambios asociada a cada cambio.</span><span class="sxs-lookup"><span data-stu-id="609cd-104">For in-depth context, please refer to the pull request associated with each change.</span></span>

## <a name="table-of-contents"></a><span data-ttu-id="609cd-105">Tabla de contenido</span><span class="sxs-lookup"><span data-stu-id="609cd-105">Table of Contents</span></span>

- [<span data-ttu-id="609cd-106">Cambios sustanciales en cmdlets de ApiManagement</span><span class="sxs-lookup"><span data-stu-id="609cd-106">Breaking changes to ApiManagement cmdlets</span></span>](#breaking-changes-to-apimanagement-cmdlets)
- [<span data-ttu-id="609cd-107">Cambios sustanciales en los cmdlets de Batch</span><span class="sxs-lookup"><span data-stu-id="609cd-107">Breaking changes to Batch cmdlets</span></span>](#breaking-changes-to-batch-cmdlets)
- [<span data-ttu-id="609cd-108">Cambios substanciales en cmdlets de Compute</span><span class="sxs-lookup"><span data-stu-id="609cd-108">Breaking changes to Compute cmdlets</span></span>](#breaking-changes-to-compute-cmdlets)
- [<span data-ttu-id="609cd-109">Cambios substanciales en cmdlets de EventHub</span><span class="sxs-lookup"><span data-stu-id="609cd-109">Breaking changes to EventHub cmdlets</span></span>](#breaking-changes-to-eventhub-cmdlets)
- [<span data-ttu-id="609cd-110">Cambios substanciales en cmdlets de Insights</span><span class="sxs-lookup"><span data-stu-id="609cd-110">Breaking changes to Insights cmdlets</span></span>](#breaking-changes-to-insights-cmdlets)
- [<span data-ttu-id="609cd-111">Cambios substanciales en cmdlets de Network</span><span class="sxs-lookup"><span data-stu-id="609cd-111">Breaking changes to Network cmdlets</span></span>](#breaking-changes-to-network-cmdlets)
- [<span data-ttu-id="609cd-112">Cambios sustanciales en los cmdlets de Resources</span><span class="sxs-lookup"><span data-stu-id="609cd-112">Breaking changes to Resources cmdlets</span></span>](#breaking-changes-to-resources-cmdlets)
- [<span data-ttu-id="609cd-113">Cambios sustanciales en los cmdlets de ServiceBus</span><span class="sxs-lookup"><span data-stu-id="609cd-113">Breaking Changes to ServiceBus Cmdlets</span></span>](#breaking-changes-to-servicebus-cmdlets)

## <a name="breaking-changes-to-apimanagement-cmdlets"></a><span data-ttu-id="609cd-114">Cambios sustanciales en los cmdlets de ApiManagement</span><span class="sxs-lookup"><span data-stu-id="609cd-114">Breaking changes to ApiManagement cmdlets</span></span>

### <a name="new-azurermapimanagementbackendproxy"></a><span data-ttu-id="609cd-115">**New-AzureRmApiManagementBackendProxy**</span><span class="sxs-lookup"><span data-stu-id="609cd-115">**New-AzureRmApiManagementBackendProxy**</span></span>
- <span data-ttu-id="609cd-116">Los parámetros "UserName" y "Password" se han reemplazado en favor de PSCredential</span><span class="sxs-lookup"><span data-stu-id="609cd-116">Parameters "UserName" and "Password" are being replaced in favor of a PSCredential</span></span>

```powershell
# Old
New-AzureRmApiManagementBackendProxy [other required parameters] -UserName "plain-text string" -Password "plain-text string"

# New
New-AzureRmApiManagementBackendProxy [other required parameters] -Credential $PSCredentialVariable
```

### <a name="new-azurermapimanagementuser"></a><span data-ttu-id="609cd-117">**New-AzureRmApiManagementUser**</span><span class="sxs-lookup"><span data-stu-id="609cd-117">**New-AzureRmApiManagementUser**</span></span>
- <span data-ttu-id="609cd-118">El parámetro "Password" se ha reemplazar en favor de SecureString</span><span class="sxs-lookup"><span data-stu-id="609cd-118">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
New-AzureRmApiManagementUser [other required parameters] -Password "plain-text string"

# New
New-AzureRmApiManagementUser [other required parameters] -Password $SecureStringVariable
```

### <a name="set-azurermapimanagementuser"></a><span data-ttu-id="609cd-119">**Set-AzureRmApiManagementUser**</span><span class="sxs-lookup"><span data-stu-id="609cd-119">**Set-AzureRmApiManagementUser**</span></span>
- <span data-ttu-id="609cd-120">El parámetro "Password" se ha reemplazar en favor de SecureString</span><span class="sxs-lookup"><span data-stu-id="609cd-120">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
Set-AzureRmApiManagementUser [other required parameters] -Password "plain-text string"

# New
Set-AzureRmApiManagementUser [other required parameters] -Password $SecureStringVariable
```

## <a name="breaking-changes-to-batch-cmdlets"></a><span data-ttu-id="609cd-121">Cambios sustanciales en los cmdlets de Batch</span><span class="sxs-lookup"><span data-stu-id="609cd-121">Breaking changes to Batch cmdlets</span></span>

### <a name="new-azurebatchcertificate"></a><span data-ttu-id="609cd-122">**New-AzureBatchCertificate**</span><span class="sxs-lookup"><span data-stu-id="609cd-122">**New-AzureBatchCertificate**</span></span>
- <span data-ttu-id="609cd-123">El parámetro `Password` se ha sustituido en favor de SecureString</span><span class="sxs-lookup"><span data-stu-id="609cd-123">Parameter `Password` being replaced in favor of a Secure string</span></span>

```powershell
# Old
New-AzureBatchCertificate [other required parameters] -Password "plain-text string"

# New
New-AzureBatchCertificate [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurebatchcomputenodeuser"></a><span data-ttu-id="609cd-124">**New-AzureBatchComputeNodeUser**</span><span class="sxs-lookup"><span data-stu-id="609cd-124">**New-AzureBatchComputeNodeUser**</span></span>
- <span data-ttu-id="609cd-125">El parámetro `Password` se ha sustituido en favor de SecureString</span><span class="sxs-lookup"><span data-stu-id="609cd-125">Parameter `Password` being replaced in favor of a Secure string</span></span>

```powershell
# Old
New-AzureBatchComputeNodeUser [other required parameters] -Password "plain-text string"

# New
New-AzureBatchComputeNodeUser [other required parameters] -Password $SecureStringVariable
```

### <a name="set-azurermbatchcomputenodeuser"></a><span data-ttu-id="609cd-126">**Set-AzureRmBatchComputeNodeUser**</span><span class="sxs-lookup"><span data-stu-id="609cd-126">**Set-AzureRmBatchComputeNodeUser**</span></span>
- <span data-ttu-id="609cd-127">El parámetro `Password` se ha sustituido en favor de SecureString</span><span class="sxs-lookup"><span data-stu-id="609cd-127">Parameter `Password` being replaced in favor of a Secure string</span></span>

```powershell
# Old
Set-AzureRmBatchComputeNodeUser [other required parameters] -Password "plain-text string"

# New
Set-AzureRmBatchComputeNodeUser [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurebatchtask"></a><span data-ttu-id="609cd-128">**New-AzureBatchTask**</span><span class="sxs-lookup"><span data-stu-id="609cd-128">**New-AzureBatchTask**</span></span>
 - <span data-ttu-id="609cd-129">El modificador `RunElevated` se ha reemplazado por `UserIdentity`.</span><span class="sxs-lookup"><span data-stu-id="609cd-129">Removed the `RunElevated` switch and replaced it with `UserIdentity`.</span></span>

```powershell
# Old
New-AzureBatchTask -Id $taskId1 -JobId $jobId -CommandLine "cmd /c echo hello" -RunElevated $TRUE

# New
$autoUser = New-Object Microsoft.Azure.Commands.Batch.Models.PSAutoUserSpecification -ArgumentList @("Task", "Admin")
$userIdentity = New-Object Microsoft.Azure.Commands.Batch.Models.PSUserIdentity $autoUser
New-AzureBatchTask -Id $taskId1 -JobId $jobId -CommandLine "cmd /c echo hello" -UserIdentity $userIdentity
```

<span data-ttu-id="609cd-130">Adicionalmente, esto afecta a la propiedad `RunElevated` de `PSCloudTask`, `PSStartTask`, `PSJobManagerTask`, `PSJobPreparationTask` y `PSJobReleaseTask`.</span><span class="sxs-lookup"><span data-stu-id="609cd-130">This additionally impacts the `RunElevated` property on `PSCloudTask`, `PSStartTask`, `PSJobManagerTask`, `PSJobPreparationTask`, and `PSJobReleaseTask`.</span></span>

### <a name="psmultiinstancesettings"></a><span data-ttu-id="609cd-131">**PSMultiInstanceSettings**</span><span class="sxs-lookup"><span data-stu-id="609cd-131">**PSMultiInstanceSettings**</span></span>

- <span data-ttu-id="609cd-132">El constructor `PSMultiInstanceSettings` no toma un parámetro `numberOfInstances` requerido, sino que toma un parámetro `coordinationCommandLine` requerido.</span><span class="sxs-lookup"><span data-stu-id="609cd-132">`PSMultiInstanceSettings` constructor no longer takes a required `numberOfInstances` parameter, instead it takes a required `coordinationCommandLine` parameter.</span></span>

```powershell
# Old
$settings = New-Object Microsoft.Azure.Commands.Batch.Models.PSMultiInstanceSettings -ArgumentList @(2)
$settings.CoordinationCommandLine = "cmd /c echo hello"
New-AzureBatchTask [other parameters] -MultiInstanceSettings $settings

# New
$settings = New-Object Microsoft.Azure.Commands.Batch.Models.PSMultiInstanceSettings -ArgumentList @("cmd /c echo hello", 2)
New-AzureBatchTask [other parameters] -MultiInstanceSettings $settings
```

### <a name="get-azurebatchtask"></a><span data-ttu-id="609cd-133">**Get-AzureBatchTask**</span><span class="sxs-lookup"><span data-stu-id="609cd-133">**Get-AzureBatchTask**</span></span>
 - <span data-ttu-id="609cd-134">Se ha quitado la propiedad `RunElevated` en `PSCloudTask`.</span><span class="sxs-lookup"><span data-stu-id="609cd-134">Removed the `RunElevated` property on `PSCloudTask`.</span></span> <span data-ttu-id="609cd-135">Se ha agregado la propiedad `UserIdentity` para reemplazar a `RunElevated`.</span><span class="sxs-lookup"><span data-stu-id="609cd-135">The `UserIdentity` property has been added to replace `RunElevated`.</span></span>

```powershell
# Old
$task = Get-AzureBatchTask [parameters]
$task.RunElevated

# New
$task = Get-AzureBatchTask [parameters]
$task.UserIdentity.AutoUser.ElevationLevel
```

<span data-ttu-id="609cd-136">Adicionalmente, esto afecta a la propiedad `RunElevated` en `PSCloudTask`, `PSStartTask`, `PSJobManagerTask`, `PSJobPreparationTask` y `PSJobReleaseTask`.</span><span class="sxs-lookup"><span data-stu-id="609cd-136">This additionally impacts the `RunElevated` property on `PSCloudTask`, `PSStartTask`, `PSJobManagerTask`, `PSJobPreparationTask`, and `PSJobReleaseTask`.</span></span>

### <a name="multiple-types"></a><span data-ttu-id="609cd-137">**Tipos múltiples**</span><span class="sxs-lookup"><span data-stu-id="609cd-137">**Multiple types**</span></span>

- <span data-ttu-id="609cd-138">Se ha cambiado el nombre de la propiedad `SchedulingError` en `PSExitConditions` a `PreProcessingError`.</span><span class="sxs-lookup"><span data-stu-id="609cd-138">Renamed the `SchedulingError` property on `PSExitConditions` to `PreProcessingError`.</span></span>

```powershell
# Old
$task = Get-AzureBatchTask [parameters]
$task.ExitConditions.SchedulingError

# New
$task = Get-AzureBatchTask [parameters]
$task.ExitConditions.PreProcessingError
```

### <a name="multiple-types"></a><span data-ttu-id="609cd-139">**Tipos múltiples**</span><span class="sxs-lookup"><span data-stu-id="609cd-139">**Multiple types**</span></span>

- <span data-ttu-id="609cd-140">Se ha cambiado el nombre de la propiedad `SchedulingError` en `PSJobPreparationTaskExecutionInformation`, `PSJobReleaseTaskExecutionInformation`, `PSStartTaskInformation`, `PSSubtaskInformation` y `PSTaskExecutionInformation` a `FailureInformation`.</span><span class="sxs-lookup"><span data-stu-id="609cd-140">Renamed the `SchedulingError` property on `PSJobPreparationTaskExecutionInformation`, `PSJobReleaseTaskExecutionInformation`, `PSStartTaskInformation`, `PSSubtaskInformation`, and `PSTaskExecutionInformation` to `FailureInformation`.</span></span>
  - <span data-ttu-id="609cd-141">`FailureInformation`se devuelve alguna vez que se produzca un error en alguna tarea.</span><span class="sxs-lookup"><span data-stu-id="609cd-141">`FailureInformation` is returned any time there is a task failure.</span></span> <span data-ttu-id="609cd-142">Aquí se incluyen todos los casos de error de programación anteriores, así como los códigos de salida de tareas distintos de cero y los errores de carga de archivos de la nueva característica de archivos de salida.</span><span class="sxs-lookup"><span data-stu-id="609cd-142">This includes all previous scheduling error cases, as well as nonzero task exit codes, and file upload failures from the new output files feature.</span></span>
  - <span data-ttu-id="609cd-143">La estructura no varía, por lo que cuando se usa este tipo no es necesario realizar ningún cambio en el código.</span><span class="sxs-lookup"><span data-stu-id="609cd-143">This is structured the same as before, so no code change is needed when using this type.</span></span>

```powershell
# Old
$task = Get-AzureBatchTask [parameters]
$task.ExecutionInformation.SchedulingError

# New
$task = Get-AzureBatchTask [parameters]
$task.ExecutionInformation.FailureInformation
```

<span data-ttu-id="609cd-144">Afecta también a: Get-AzureBatchPool, Get-AzureBatchSubtask y Get-AzureBatchJobPreparationAndReleaseTaskStatus</span><span class="sxs-lookup"><span data-stu-id="609cd-144">This additionally impacts: Get-AzureBatchPool, Get-AzureBatchSubtask, and Get-AzureBatchJobPreparationAndReleaseTaskStatus</span></span>

### <a name="new-azurebatchpool"></a><span data-ttu-id="609cd-145">**New-AzureBatchPool**</span><span class="sxs-lookup"><span data-stu-id="609cd-145">**New-AzureBatchPool**</span></span>
 - <span data-ttu-id="609cd-146">`TargetDedicated` se ha reemplazado por `TargetDedicatedComputeNodes` y `TargetLowPriorityComputeNodes`.</span><span class="sxs-lookup"><span data-stu-id="609cd-146">Removed `TargetDedicated` and replaced it with `TargetDedicatedComputeNodes` and `TargetLowPriorityComputeNodes`.</span></span>
 - <span data-ttu-id="609cd-147">`TargetDedicatedComputeNodes` tiene un alias `TargetDedicated`.</span><span class="sxs-lookup"><span data-stu-id="609cd-147">`TargetDedicatedComputeNodes` has an alias `TargetDedicated`.</span></span>

```powershell
# Old
New-AzureBatchPool [other parameters] [-TargetDedicated <Int32>]

# New
New-AzureBatchPool [other parameters] [-TargetDedicatedComputeNodes <Int32>] [-TargetLowPriorityComputeNodes <Int32>]
```

<span data-ttu-id="609cd-148">Afecta también a: Start-AzureBatchPoolResize</span><span class="sxs-lookup"><span data-stu-id="609cd-148">This also impacts: Start-AzureBatchPoolResize</span></span>

### <a name="get-azurebatchpool"></a><span data-ttu-id="609cd-149">**Get-AzureBatchPool**</span><span class="sxs-lookup"><span data-stu-id="609cd-149">**Get-AzureBatchPool**</span></span>
 - <span data-ttu-id="609cd-150">Se ha cambiado el nombre de las propiedades `TargetDedicated` y `CurrentDedicated` de `PSCloudPool` a `TargetDedicatedComputeNodes` y `CurrentDedicatedComputeNodes`.</span><span class="sxs-lookup"><span data-stu-id="609cd-150">Renamed the `TargetDedicated` and `CurrentDedicated` properties on `PSCloudPool` to `TargetDedicatedComputeNodes` and `CurrentDedicatedComputeNodes`.</span></span>

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

### <a name="type-pscloudpool"></a><span data-ttu-id="609cd-151">**Tipo PSCloudPool**</span><span class="sxs-lookup"><span data-stu-id="609cd-151">**Type PSCloudPool**</span></span>

- <span data-ttu-id="609cd-152">Se ha cambiado el nombre de `ResizeError` a `ResizeErrors` en `PSCloudPool` y ahora es una colección.</span><span class="sxs-lookup"><span data-stu-id="609cd-152">Renamed `ResizeError` to `ResizeErrors` on `PSCloudPool`, and it is now a collection.</span></span>

```powershell
# Old
$pool = Get-AzureBatchPool [parameters]
$pool.ResizeError

# New
$pool = Get-AzureBatchPool [parameters]
$pool.ResizeErrors[0]
```

### <a name="new-azurebatchjob"></a><span data-ttu-id="609cd-153">**New-AzureBatchJob**</span><span class="sxs-lookup"><span data-stu-id="609cd-153">**New-AzureBatchJob**</span></span>
- <span data-ttu-id="609cd-154">Se ha cambiado el nombre de la propiedad `TargetDedicated` en `PSPoolSpecification` a `TargetDedicatedComputeNodes`.</span><span class="sxs-lookup"><span data-stu-id="609cd-154">Renamed the `TargetDedicated` property on `PSPoolSpecification` to `TargetDedicatedComputeNodes`.</span></span>

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

### <a name="get-azurebatchnodefile"></a><span data-ttu-id="609cd-155">**Get-AzureBatchNodeFile**</span><span class="sxs-lookup"><span data-stu-id="609cd-155">**Get-AzureBatchNodeFile**</span></span>
 - <span data-ttu-id="609cd-156">`Name` se ha reemplazado por `Path`.</span><span class="sxs-lookup"><span data-stu-id="609cd-156">Removed `Name` and replaced it with `Path`.</span></span>
 - <span data-ttu-id="609cd-157">`Path` tiene un alias `Name`.</span><span class="sxs-lookup"><span data-stu-id="609cd-157">`Path` has an alias `Name`.</span></span>

```powershell
# Old
Get-AzureBatchNodeFile [other parameters] [[-Name] <String>]

# New
Get-AzureBatchNodeFile [other parameters] [[-Path] <String>]
```

<span data-ttu-id="609cd-158">Afecta también a : Get-AzureBatchNodeFileContent y Remove-AzureBatchNodeFile</span><span class="sxs-lookup"><span data-stu-id="609cd-158">This also impacts: Get-AzureBatchNodeFileContent, Remove-AzureBatchNodeFile</span></span>

### <a name="type-psnodefile"></a><span data-ttu-id="609cd-159">Tipo **PSNodeFile**</span><span class="sxs-lookup"><span data-stu-id="609cd-159">Type **PSNodeFile**</span></span>

 - <span data-ttu-id="609cd-160">Se ha cambiado el nombre de la propiedad `Name` en `PSNodeFile` a `Path`.</span><span class="sxs-lookup"><span data-stu-id="609cd-160">Renamed the `Name` property on `PSNodeFile` to `Path`.</span></span>

```powershell
# Old
$file = Get-AzureBatchNodeFile [parameters]
$file.Name

# New
$file = Get-AzureBatchNodeFile [parameters]
$file.Path
```

### <a name="get-azurebatchsubtask"></a><span data-ttu-id="609cd-161">**Get-AzureBatchSubtask**</span><span class="sxs-lookup"><span data-stu-id="609cd-161">**Get-AzureBatchSubtask**</span></span>
- <span data-ttu-id="609cd-162">Las propiedades `PreviousState` y `State` de `PSSubtaskInformation` dejan de ser del tipo `TaskState`, ahora son del tipo `SubtaskState`.</span><span class="sxs-lookup"><span data-stu-id="609cd-162">The `PreviousState` and `State` properties of `PSSubtaskInformation` are no longer of type `TaskState`, instead they are of type `SubtaskState`.</span></span>
  - <span data-ttu-id="609cd-163">A diferencia de `TaskState`, `SubtaskState` no tiene ningún el valor `Active`, ya que no es posible que las subtareas estén en estado `Active`.</span><span class="sxs-lookup"><span data-stu-id="609cd-163">Unlike `TaskState`, `SubtaskState` has no `Active` value, since it is not possible for subtasks to be in an `Active` state.</span></span>

```powershell
# Old
$subtask = Get-AzureBatchSubtask [parameters]
if ($subtask.State -eq Microsoft.Azure.Batch.Common.TaskState.Running) { }

# New
$subtask = Get-AzureBatchSubtask [parameters]
if ($subtask.State -eq Microsoft.Azure.Batch.Common.SubtaskState.Running) { }
```

## <a name="breaking-changes-to-compute-cmdlets"></a><span data-ttu-id="609cd-164">Cambios substanciales en cmdlets de Compute</span><span class="sxs-lookup"><span data-stu-id="609cd-164">Breaking changes to Compute cmdlets</span></span>

### <a name="set-azurermvmaccessextension"></a><span data-ttu-id="609cd-165">**Set-AzureRmVMAccessExtension**</span><span class="sxs-lookup"><span data-stu-id="609cd-165">**Set-AzureRmVMAccessExtension**</span></span>
- <span data-ttu-id="609cd-166">Los parámetros "UserName" y "Password" se han reemplazado en favor de PSCredential</span><span class="sxs-lookup"><span data-stu-id="609cd-166">Parameters "UserName" and "Password" are being replaced in favor of a PSCredential</span></span>

```powershell
# Old
Set-AzureRmVMAccessExtension [other required parameters] -UserName "plain-text string" -Password "plain-text string"

# New
Set-AzureRmVMAccessExtension [other required parameters] -Credential $PSCredential
```

## <a name="breaking-changes-to-eventhub-cmdlets"></a><span data-ttu-id="609cd-167">Cambios sustanciales en los cmdlets de EventHub</span><span class="sxs-lookup"><span data-stu-id="609cd-167">Breaking changes to EventHub cmdlets</span></span>

### <a name="new-azurermeventhubnamespaceauthorizationrule"></a><span data-ttu-id="609cd-168">**New-AzureRmEventHubNamespaceAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="609cd-168">**New-AzureRmEventHubNamespaceAuthorizationRule**</span></span>
- <span data-ttu-id="609cd-169">Se ha eliminado el cmdlet 'New-AzureRmEventHubNamespaceAuthorizationRule'.</span><span class="sxs-lookup"><span data-stu-id="609cd-169">The 'New-AzureRmEventHubNamespaceAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="609cd-170">Use el cmdlet 'New-AzureRmEventHubAuthorizationRule'</span><span class="sxs-lookup"><span data-stu-id="609cd-170">Please use the 'New-AzureRmEventHubAuthorizationRule' cmdlet</span></span>
    
### <a name="get-azurermeventhubnamespaceauthorizationrule"></a><span data-ttu-id="609cd-171">**Get-AzureRmEventHubNamespaceAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="609cd-171">**Get-AzureRmEventHubNamespaceAuthorizationRule**</span></span>
- <span data-ttu-id="609cd-172">Se ha eliminado el cmdlet 'Get-AzureRmEventHubNamespaceAuthorizationRule'.</span><span class="sxs-lookup"><span data-stu-id="609cd-172">The 'Get-AzureRmEventHubNamespaceAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="609cd-173">Use el cmdlet 'Get-AzureRmEventHubAuthorizationRule'</span><span class="sxs-lookup"><span data-stu-id="609cd-173">Please use the 'Get-AzureRmEventHubAuthorizationRule' cmdlet</span></span>
    
### <a name="set-azurermeventhubnamespaceauthorizationrule"></a><span data-ttu-id="609cd-174">**Set-AzureRmEventHubNamespaceAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="609cd-174">**Set-AzureRmEventHubNamespaceAuthorizationRule**</span></span>
- <span data-ttu-id="609cd-175">Se ha eliminado el cmdlet 'Set-AzureRmEventHubNamespaceAuthorizationRule'.</span><span class="sxs-lookup"><span data-stu-id="609cd-175">The 'Set-AzureRmEventHubNamespaceAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="609cd-176">Use el cmdlet 'Set-AzureRmEventHubAuthorizationRule'</span><span class="sxs-lookup"><span data-stu-id="609cd-176">Please use the 'Set-AzureRmEventHubAuthorizationRule' cmdlet</span></span>
    
### <a name="remove-azurermeventhubnamespaceauthorizationrule"></a><span data-ttu-id="609cd-177">**Remove-AzureRmEventHubNamespaceAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="609cd-177">**Remove-AzureRmEventHubNamespaceAuthorizationRule**</span></span>
- <span data-ttu-id="609cd-178">Se ha eliminado el cmdlet 'Remove-AzureRmEventHubNamespaceAuthorizationRule'.</span><span class="sxs-lookup"><span data-stu-id="609cd-178">The 'Remove-AzureRmEventHubNamespaceAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="609cd-179">Use el cmdlet 'Remove-AzureRmEventHubAuthorizationRule'</span><span class="sxs-lookup"><span data-stu-id="609cd-179">Please use the 'Remove-AzureRmEventHubAuthorizationRule' cmdlet</span></span>
    
### <a name="new-azurermeventhubnamespacekey"></a><span data-ttu-id="609cd-180">**New-AzureRmEventHubNamespaceKey**</span><span class="sxs-lookup"><span data-stu-id="609cd-180">**New-AzureRmEventHubNamespaceKey**</span></span>
- <span data-ttu-id="609cd-181">Se ha eliminado el cmdlet 'New-AzureRmEventHubNamespaceKey'.</span><span class="sxs-lookup"><span data-stu-id="609cd-181">The 'New-AzureRmEventHubNamespaceKey' cmdlet has been removed.</span></span> <span data-ttu-id="609cd-182">Use el cmdlet 'New-AzureRmEventHubKey'</span><span class="sxs-lookup"><span data-stu-id="609cd-182">Please use the 'New-AzureRmEventHubKey' cmdlet</span></span>
    
### <a name="get-azurermeventhubnamespacekey"></a><span data-ttu-id="609cd-183">**Get-AzureRmEventHubNamespaceKey**</span><span class="sxs-lookup"><span data-stu-id="609cd-183">**Get-AzureRmEventHubNamespaceKey**</span></span>
- <span data-ttu-id="609cd-184">Se ha eliminado el cmdlet 'Get-AzureRmEventHubNamespaceKey'.</span><span class="sxs-lookup"><span data-stu-id="609cd-184">The 'Get-AzureRmEventHubNamespaceKey' cmdlet has been removed.</span></span> <span data-ttu-id="609cd-185">Use el cmdlet 'Get-AzureRmEventHubKey'</span><span class="sxs-lookup"><span data-stu-id="609cd-185">Please use the 'Get-AzureRmEventHubKey' cmdlet</span></span>
    
### <a name="new-azurermeventhubnamespace"></a><span data-ttu-id="609cd-186">**New-AzureRmEventHubNamespace**</span><span class="sxs-lookup"><span data-stu-id="609cd-186">**New-AzureRmEventHubNamespace**</span></span>
- <span data-ttu-id="609cd-187">Se quitarán las propiedades 'Status' y 'Enabled' de NamespceAttributes.</span><span class="sxs-lookup"><span data-stu-id="609cd-187">The property 'Status' and 'Enabled' from the NamespceAttributes will be removed.</span></span> 

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
    
### <a name="get-azurermeventhubnamespace"></a><span data-ttu-id="609cd-188">**Get-AzureRmEventHubNamespace**</span><span class="sxs-lookup"><span data-stu-id="609cd-188">**Get-AzureRmEventHubNamespace**</span></span>
- <span data-ttu-id="609cd-189">Se quitarán las propiedades 'Status' y 'Enabled' de NamespceAttributes.</span><span class="sxs-lookup"><span data-stu-id="609cd-189">The property 'Status' and 'Enabled' from the NamespceAttributes will be removed.</span></span> 

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
    
### <a name="set-azurermeventhubnamespace"></a><span data-ttu-id="609cd-190">**Set-AzureRmEventHubNamespace**</span><span class="sxs-lookup"><span data-stu-id="609cd-190">**Set-AzureRmEventHubNamespace**</span></span>
- <span data-ttu-id="609cd-191">Se quitarán las propiedades 'Status' y 'Enabled' de NamespceAttributes.</span><span class="sxs-lookup"><span data-stu-id="609cd-191">The property 'Status' and 'Enabled' from the NamespceAttributes will be removed.</span></span> 

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
  
### <a name="new-azurermeventhubconsumergroup"></a><span data-ttu-id="609cd-192">**New-AzureRmEventHubConsumerGroup**</span><span class="sxs-lookup"><span data-stu-id="609cd-192">**New-AzureRmEventHubConsumerGroup**</span></span>
- <span data-ttu-id="609cd-193">Se eliminará la propiedad 'EventHubPath' de ConsumerGroupAttributes.</span><span class="sxs-lookup"><span data-stu-id="609cd-193">The property 'EventHubPath' from the ConsumerGroupAttributes will be removed.</span></span>

```powershell
# Old
# The $consumergroup has EventHubPath property 
$consumergroup = New-AzureRmEventHubConsumerGroup <parameters>
$consumergroup.EventHubPath

# New
# The call remains the same, but the returned values ConsumerGroup object will not have the EventHubPath property    
$consumergroup = New-AzureRmEventHubConsumerGroup <parameters>
```
    
### <a name="set-azurermeventhubconsumergroup"></a><span data-ttu-id="609cd-194">**Set-AzureRmEventHubConsumerGroup**</span><span class="sxs-lookup"><span data-stu-id="609cd-194">**Set-AzureRmEventHubConsumerGroup**</span></span>
- <span data-ttu-id="609cd-195">Se eliminará la propiedad 'EventHubPath' de ConsumerGroupAttributes.</span><span class="sxs-lookup"><span data-stu-id="609cd-195">The property 'EventHubPath' from the ConsumerGroupAttributes will be removed.</span></span>

```powershell
# Old
# The $consumergroup has EventHubPath property 
$consumergroup = Set-AzureRmEventHubConsumerGroup <parameters>
$consumergroup.EventHubPath

# New
# The call remains the same, but the returned values ConsumerGroup object will not have the EventHubPath property    
$consumergroup = Set-AzureRmEventHubConsumerGroup <parameters>
```
    
### <a name="get-azurermeventhubconsumergroup"></a><span data-ttu-id="609cd-196">**Get-AzureRmEventHubConsumerGroup**</span><span class="sxs-lookup"><span data-stu-id="609cd-196">**Get-AzureRmEventHubConsumerGroup**</span></span>
- <span data-ttu-id="609cd-197">Se eliminará la propiedad 'EventHubPath' de ConsumerGroupAttributes.</span><span class="sxs-lookup"><span data-stu-id="609cd-197">The property 'EventHubPath' from the ConsumerGroupAttributes will be removed.</span></span>

```powershell
# Old
# The $consumergroup has EventHubPath property 
$consumergroup = Get-AzureRmEventHubConsumerGroup <parameters>
$consumergroup.EventHubPath

# New
# The call remains the same, but the returned values ConsumerGroup object will not have the EventHubPath property    
$consumergroup = Get-AzureRmEventHubConsumerGroup <parameters>
```

## <a name="breaking-changes-to-insights-cmdlets"></a><span data-ttu-id="609cd-198">Cambios sustanciales en los cmdlets de Insights</span><span class="sxs-lookup"><span data-stu-id="609cd-198">Breaking changes to Insights cmdlets</span></span>

### <a name="add-azurermlogalertrule"></a><span data-ttu-id="609cd-199">**Add-AzureRMLogAlertRule**</span><span class="sxs-lookup"><span data-stu-id="609cd-199">**Add-AzureRMLogAlertRule**</span></span>
- <span data-ttu-id="609cd-200">El cmdlet **Add-AzureRMLogAlertRule** está en desuso</span><span class="sxs-lookup"><span data-stu-id="609cd-200">The **Add-AzureRMLogAlertRule** cmdlet has been deprecated</span></span>
- <span data-ttu-id="609cd-201">A partir del 1 de octubre el uso de este cmdlet no tendrá ningún efecto, ya que esta funcionalidad se ha pasado a las alertas de registro de actividad.</span><span class="sxs-lookup"><span data-stu-id="609cd-201">After October 1st using this cmdlet will no longer have any effect as this functionality is being transitioned to Activity Log Alerts.</span></span> <span data-ttu-id="609cd-202">Para más información, consulte https://aka.ms/migratemealerts.</span><span class="sxs-lookup"><span data-stu-id="609cd-202">Please see https://aka.ms/migratemealerts for more information.</span></span>

### <a name="get-azurermusage"></a><span data-ttu-id="609cd-203">**Get-AzureRMUsage**</span><span class="sxs-lookup"><span data-stu-id="609cd-203">**Get-AzureRMUsage**</span></span>
- <span data-ttu-id="609cd-204">El cmdlet **AzureRMUsage Get** está en desuso</span><span class="sxs-lookup"><span data-stu-id="609cd-204">The **Get-AzureRMUsage** cmdlet has been deprecated</span></span>

### <a name="get-azurermalerthistory--get-azurermautoscalehistory--get-azurermlogs"></a><span data-ttu-id="609cd-205">**Get-AzureRmAlertHistory** / **Get-AzureRmAutoscaleHistory** / **Get-AzureRmLogs**</span><span class="sxs-lookup"><span data-stu-id="609cd-205">**Get-AzureRmAlertHistory** / **Get-AzureRmAutoscaleHistory** / **Get-AzureRmLogs**</span></span>
- <span data-ttu-id="609cd-206">Cambio de salida: el campo EventChannels del objeto EventData (que devuelven estos cmdlets) está en desuso, ya que ahora devuelve un valor constante (Admin, Operation).</span><span class="sxs-lookup"><span data-stu-id="609cd-206">Output change: The field EventChannels from the EventData object (returned by these cmdlets) is being deprecated since it now returns a constant value (Admin,Operation.)</span></span>

### <a name="get-azurermalertrule"></a><span data-ttu-id="609cd-207">**Get-AzureRmAlertRule**</span><span class="sxs-lookup"><span data-stu-id="609cd-207">**Get-AzureRmAlertRule**</span></span>
- <span data-ttu-id="609cd-208">Cambio de salida: la salida de este cmdlet se acoplará; es decir, se elimina el campo de propiedades para mejorar la experiencia del usuario.</span><span class="sxs-lookup"><span data-stu-id="609cd-208">Output change: The output of this cmdlet will be flattened, i.e. elimination of the properties field, to improve the user experience.</span></span>

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

### <a name="get-azurermautoscalesetting"></a><span data-ttu-id="609cd-209">**Get-AzureRmAutoscaleSetting**</span><span class="sxs-lookup"><span data-stu-id="609cd-209">**Get-AzureRmAutoscaleSetting**</span></span>
- <span data-ttu-id="609cd-210">Cambio de salida: el campo AutoscaleSettingResourceName dejará de utilizarse, ya que su valor es siempre el mismo que el del campo Name.</span><span class="sxs-lookup"><span data-stu-id="609cd-210">Output change: The AutoscaleSettingResourceName field will be deprecated since it always equals the Name field.</span></span>

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

### <a name="remove-azurermalertrule--remove-azurermlogprofile"></a><span data-ttu-id="609cd-211">**Remove-AzureRmAlertRule** / **Remove-AzureRmLogProfile**</span><span class="sxs-lookup"><span data-stu-id="609cd-211">**Remove-AzureRmAlertRule** / **Remove-AzureRmLogProfile**</span></span>
- <span data-ttu-id="609cd-212">Cambio de salida: el tipo de la salida cambiará para devolver un solo objeto que contiene el Id. de solicitud y el código de estado.</span><span class="sxs-lookup"><span data-stu-id="609cd-212">Output change: The type of the output will change to return a single object containing the request Id and the status code.</span></span>

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

## <a name="breaking-changes-to-network-cmdlets"></a><span data-ttu-id="609cd-213">Cambios sustanciales en los cmdlets de Network</span><span class="sxs-lookup"><span data-stu-id="609cd-213">Breaking changes to Network cmdlets</span></span>

### <a name="add-azurermapplicationgatewaysslcertificate"></a><span data-ttu-id="609cd-214">**Add-AzureRmApplicationGatewaySslCertificate**</span><span class="sxs-lookup"><span data-stu-id="609cd-214">**Add-AzureRmApplicationGatewaySslCertificate**</span></span>
- <span data-ttu-id="609cd-215">El parámetro "Password" se ha reemplazar en favor de SecureString</span><span class="sxs-lookup"><span data-stu-id="609cd-215">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
Add-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password "plain-text string"

# New
Add-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurermapplicationgatewaysslcertificate"></a><span data-ttu-id="609cd-216">**New-AzureRmApplicationGatewaySslCertificate**</span><span class="sxs-lookup"><span data-stu-id="609cd-216">**New-AzureRmApplicationGatewaySslCertificate**</span></span>
- <span data-ttu-id="609cd-217">El parámetro "Password" se ha reemplazar en favor de SecureString</span><span class="sxs-lookup"><span data-stu-id="609cd-217">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
New-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password "plain-text string"

# New
New-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password $SecureStringVariable
```

### <a name="set-azurermapplicationgatewaysslcertificate"></a><span data-ttu-id="609cd-218">**Set-AzureRmApplicationGatewaySslCertificate**</span><span class="sxs-lookup"><span data-stu-id="609cd-218">**Set-AzureRmApplicationGatewaySslCertificate**</span></span>
- <span data-ttu-id="609cd-219">El parámetro "Password" se ha reemplazar en favor de SecureString</span><span class="sxs-lookup"><span data-stu-id="609cd-219">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
Set-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password "plain-text string"

# New
Set-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password $SecureStringVariable
```

## <a name="breaking-changes-to-resources-cmdlets"></a><span data-ttu-id="609cd-220">Cambios sustanciales en los cmdlets de Resources</span><span class="sxs-lookup"><span data-stu-id="609cd-220">Breaking changes to Resources cmdlets</span></span>

### <a name="new-azurermadappcredential"></a><span data-ttu-id="609cd-221">**New-AzureRmADAppCredential**</span><span class="sxs-lookup"><span data-stu-id="609cd-221">**New-AzureRmADAppCredential**</span></span>
- <span data-ttu-id="609cd-222">El parámetro "Password" se ha reemplazar en favor de SecureString</span><span class="sxs-lookup"><span data-stu-id="609cd-222">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
New-AzureRmADAppCredential [other required parameters] -Password "plain-text string"

# New
New-AzureRmADAppCredential [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurermadapplication"></a><span data-ttu-id="609cd-223">**New-AzureRmADApplication**</span><span class="sxs-lookup"><span data-stu-id="609cd-223">**New-AzureRmADApplication**</span></span>
- <span data-ttu-id="609cd-224">El parámetro "Password" se ha reemplazar en favor de SecureString</span><span class="sxs-lookup"><span data-stu-id="609cd-224">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
New-AzureRmADApplication [other required parameters] -Password "plain-text string"

# New
New-AzureRmADApplication [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurermadserviceprincipal"></a><span data-ttu-id="609cd-225">**New-AzureRmADServicePrincipal**</span><span class="sxs-lookup"><span data-stu-id="609cd-225">**New-AzureRmADServicePrincipal**</span></span>
- <span data-ttu-id="609cd-226">El parámetro "Password" se ha reemplazar en favor de SecureString</span><span class="sxs-lookup"><span data-stu-id="609cd-226">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
New-AzureRmADServicePrincipal [other required parameters] -Password "plain-text string"

# New
New-AzureRmADServicePrincipal [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurermadspcredential"></a><span data-ttu-id="609cd-227">**New-AzureRmADSpCredential**</span><span class="sxs-lookup"><span data-stu-id="609cd-227">**New-AzureRmADSpCredential**</span></span>
- <span data-ttu-id="609cd-228">El parámetro "Password" se ha reemplazar en favor de SecureString</span><span class="sxs-lookup"><span data-stu-id="609cd-228">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
New-AzureRmADSpCredential [other required parameters] -Password "plain-text string"

# New
New-AzureRmADSpCredential [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurermaduser"></a><span data-ttu-id="609cd-229">**New-AzureRmADUser**</span><span class="sxs-lookup"><span data-stu-id="609cd-229">**New-AzureRmADUser**</span></span>
- <span data-ttu-id="609cd-230">El parámetro "Password" se ha reemplazar en favor de SecureString</span><span class="sxs-lookup"><span data-stu-id="609cd-230">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
New-AzureRmADUser [other required parameters] -Password "plain-text string"

# New
New-AzureRmADUser [other required parameters] -Password $SecureStringVariable
```

### <a name="set-azurermaduser"></a><span data-ttu-id="609cd-231">**Set-AzureRmADUser**</span><span class="sxs-lookup"><span data-stu-id="609cd-231">**Set-AzureRmADUser**</span></span>
- <span data-ttu-id="609cd-232">El parámetro "Password" se ha reemplazar en favor de SecureString</span><span class="sxs-lookup"><span data-stu-id="609cd-232">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
Set-AzureRmADUser [other required parameters] -Password "plain-text string"

# New
Set-AzureRmADUser [other required parameters] -Password $SecureStringVariable
```

## <a name="breaking-changes-to-servicebus-cmdlets"></a><span data-ttu-id="609cd-233">Cambios sustanciales en los cmdlets de ServiceBus</span><span class="sxs-lookup"><span data-stu-id="609cd-233">Breaking changes to ServiceBus cmdlets</span></span>

### <a name="get-azurermservicebustopicauthorizationrule"></a><span data-ttu-id="609cd-234">**Get-AzureRmServiceBusTopicAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="609cd-234">**Get-AzureRmServiceBusTopicAuthorizationRule**</span></span>
- <span data-ttu-id="609cd-235">Se ha eliminado el cmdlet 'Get-AzureRmServiceBusTopicAuthorizationRule'.</span><span class="sxs-lookup"><span data-stu-id="609cd-235">The 'Get-AzureRmServiceBusTopicAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="609cd-236">Use el cmdlet 'Get-AzureRmServiceBusAuthorizationRule'.</span><span class="sxs-lookup"><span data-stu-id="609cd-236">Please use the 'Get-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>    

### <a name="get-azurermservicebustopickey"></a><span data-ttu-id="609cd-237">**Get-AzureRmServiceBusTopicKey**</span><span class="sxs-lookup"><span data-stu-id="609cd-237">**Get-AzureRmServiceBusTopicKey**</span></span>
- <span data-ttu-id="609cd-238">Se ha eliminado el cmdlet 'Get-AzureRmServiceBusTopicKey'.</span><span class="sxs-lookup"><span data-stu-id="609cd-238">The 'Get-AzureRmServiceBusTopicKey' cmdlet has been removed.</span></span> <span data-ttu-id="609cd-239">Use el cmdlet 'Get-AzureRmServiceBusKey'.</span><span class="sxs-lookup"><span data-stu-id="609cd-239">Please use the 'Get-AzureRmServiceBusKey' cmdlet.</span></span>

### <a name="new-azurermservicebustopicauthorizationrule"></a><span data-ttu-id="609cd-240">**New-AzureRmServiceBusTopicAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="609cd-240">**New-AzureRmServiceBusTopicAuthorizationRule**</span></span>
- <span data-ttu-id="609cd-241">Se ha eliminado el cmdlet 'Get-AzureRmServiceBusTopicAuthorizationRule'.</span><span class="sxs-lookup"><span data-stu-id="609cd-241">The 'New-AzureRmServiceBusTopicAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="609cd-242">Use el cmdlet 'Get-AzureRmServiceBusAuthorizationRule'.</span><span class="sxs-lookup"><span data-stu-id="609cd-242">Please use the 'New-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>

### <a name="new-azurermservicebustopickey"></a><span data-ttu-id="609cd-243">**New-AzureRmServiceBusTopicKey**</span><span class="sxs-lookup"><span data-stu-id="609cd-243">**New-AzureRmServiceBusTopicKey**</span></span>
- <span data-ttu-id="609cd-244">Se ha eliminado el cmdlet 'New-AzureRmServiceBusTopicKey'.</span><span class="sxs-lookup"><span data-stu-id="609cd-244">The 'New-AzureRmServiceBusTopicKey' cmdlet has been removed.</span></span> <span data-ttu-id="609cd-245">Use el cmdlet 'Get-AzureRmServiceBusKey'.</span><span class="sxs-lookup"><span data-stu-id="609cd-245">Please use the 'New-AzureRmServiceBusKey' cmdlet.</span></span>

### <a name="remove-azurermservicebustopicauthorizationrule"></a><span data-ttu-id="609cd-246">**Remove-AzureRmServiceBusTopicAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="609cd-246">**Remove-AzureRmServiceBusTopicAuthorizationRule**</span></span>
- <span data-ttu-id="609cd-247">Se ha eliminado el cmdlet 'Remove-AzureRmServiceBusTopicAuthorizationRule'.</span><span class="sxs-lookup"><span data-stu-id="609cd-247">The 'Remove-AzureRmServiceBusTopicAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="609cd-248">Use el cmdlet 'Remove-AzureRmServiceBusAuthorizationRule'.</span><span class="sxs-lookup"><span data-stu-id="609cd-248">Please use the 'Remove-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>

### <a name="set-azurermservicebustopicauthorizationrule"></a><span data-ttu-id="609cd-249">**Set-AzureRmServiceBusTopicAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="609cd-249">**Set-AzureRmServiceBusTopicAuthorizationRule**</span></span>
- <span data-ttu-id="609cd-250">Se ha eliminado el cmdlet 'Set-AzureRmServiceBusTopicAuthorizationRule'.</span><span class="sxs-lookup"><span data-stu-id="609cd-250">The 'Set-AzureRmServiceBusTopicAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="609cd-251">Use el cmdlet 'Set-AzureRmServiceBusAuthorizationRule'.</span><span class="sxs-lookup"><span data-stu-id="609cd-251">Please use the 'Set-AzureRmServiceBusAuthorizationRule'cmdlet.</span></span>

### <a name="new-azurermservicebusnamespacekey"></a><span data-ttu-id="609cd-252">**New-AzureRmServiceBusNamespaceKey**</span><span class="sxs-lookup"><span data-stu-id="609cd-252">**New-AzureRmServiceBusNamespaceKey**</span></span>
- <span data-ttu-id="609cd-253">Se ha eliminado el cmdlet 'New-AzureRmServiceBusNamespaceKey'.</span><span class="sxs-lookup"><span data-stu-id="609cd-253">The 'New-AzureRmServiceBusNamespaceKey' cmdlet has been removed.</span></span> <span data-ttu-id="609cd-254">Use el cmdlet 'Get-AzureRmServiceBusKey'.</span><span class="sxs-lookup"><span data-stu-id="609cd-254">Please use the 'New-AzureRmServiceBusKey' cmdlet.</span></span>

### <a name="get-azurermservicebusqueueauthorizationrule"></a><span data-ttu-id="609cd-255">**Get-AzureRmServiceBusQueueAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="609cd-255">**Get-AzureRmServiceBusQueueAuthorizationRule**</span></span>
- <span data-ttu-id="609cd-256">Se ha eliminado el cmdlet 'Get-AzureRmServiceBusQueueAuthorizationRule'.</span><span class="sxs-lookup"><span data-stu-id="609cd-256">The 'Get-AzureRmServiceBusQueueAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="609cd-257">Use el cmdlet 'Get-AzureRmServiceBusAuthorizationRule'.</span><span class="sxs-lookup"><span data-stu-id="609cd-257">Please use the 'Get-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>

### <a name="get-azurermservicebusqueuekey"></a><span data-ttu-id="609cd-258">**Get-AzureRmServiceBusQueueKey**</span><span class="sxs-lookup"><span data-stu-id="609cd-258">**Get-AzureRmServiceBusQueueKey**</span></span>
- <span data-ttu-id="609cd-259">Se ha eliminado el cmdlet 'Get-AzureRmServiceBusQueueKey'.</span><span class="sxs-lookup"><span data-stu-id="609cd-259">The 'Get-AzureRmServiceBusQueueKey' cmdlet has been removed.</span></span> <span data-ttu-id="609cd-260">Use el cmdlet 'Get-AzureRmServiceBusKey'.</span><span class="sxs-lookup"><span data-stu-id="609cd-260">Please use the 'Get-AzureRmServiceBusKey' cmdlet.</span></span>

### <a name="new-azurermservicebusqueueauthorizationrule"></a><span data-ttu-id="609cd-261">**New-AzureRmServiceBusQueueAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="609cd-261">**New-AzureRmServiceBusQueueAuthorizationRule**</span></span>
- <span data-ttu-id="609cd-262">Se ha eliminado el cmdlet 'New-AzureRmServiceBusQueueAuthorizationRule'.</span><span class="sxs-lookup"><span data-stu-id="609cd-262">The 'New-AzureRmServiceBusQueueAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="609cd-263">Use el cmdlet 'Get-AzureRmServiceBusAuthorizationRule'.</span><span class="sxs-lookup"><span data-stu-id="609cd-263">Please use the 'New-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>

### <a name="new-azurermservicebusqueuekey"></a><span data-ttu-id="609cd-264">**New-AzureRmServiceBusQueueKey**</span><span class="sxs-lookup"><span data-stu-id="609cd-264">**New-AzureRmServiceBusQueueKey**</span></span>
- <span data-ttu-id="609cd-265">Se ha eliminado el cmdlet 'New-AzureRmServiceBusQueueKey'.</span><span class="sxs-lookup"><span data-stu-id="609cd-265">The 'New-AzureRmServiceBusQueueKey' cmdlet has been removed.</span></span> <span data-ttu-id="609cd-266">Use el cmdlet 'Get-AzureRmServiceBusKey'.</span><span class="sxs-lookup"><span data-stu-id="609cd-266">Please use the 'New-AzureRmServiceBusKey' cmdlet.</span></span>

### <a name="remove-azurermservicebusqueueauthorizationrule"></a><span data-ttu-id="609cd-267">**Remove-AzureRmServiceBusQueueAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="609cd-267">**Remove-AzureRmServiceBusQueueAuthorizationRule**</span></span>
- <span data-ttu-id="609cd-268">Se ha eliminado el cmdlet 'Remove-AzureRmServiceBusQueueAuthorizationRule'.</span><span class="sxs-lookup"><span data-stu-id="609cd-268">The 'Remove-AzureRmServiceBusQueueAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="609cd-269">Use el cmdlet 'GRemove-AzureRmServiceBusAuthorizationRule'.</span><span class="sxs-lookup"><span data-stu-id="609cd-269">Please use the 'GRemove-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>

### <a name="set-azurermservicebusqueueauthorizationrule"></a><span data-ttu-id="609cd-270">**Set-AzureRmServiceBusQueueAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="609cd-270">**Set-AzureRmServiceBusQueueAuthorizationRule**</span></span>
- <span data-ttu-id="609cd-271">Se ha eliminado el cmdlet 'Set-AzureRmServiceBusQueueAuthorizationRule'.</span><span class="sxs-lookup"><span data-stu-id="609cd-271">The 'Set-AzureRmServiceBusQueueAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="609cd-272">Use el cmdlet 'Set-AzureRmServiceBusAuthorizationRule'.</span><span class="sxs-lookup"><span data-stu-id="609cd-272">Please use the 'Set-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>

### <a name="get-azurermservicebusnamespaceauthorizationrule"></a><span data-ttu-id="609cd-273">**Get-AzureRmServiceBusNamespaceAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="609cd-273">**Get-AzureRmServiceBusNamespaceAuthorizationRule**</span></span>
- <span data-ttu-id="609cd-274">Se ha eliminado el cmdlet 'Get-AzureRmServiceBusNamespaceAuthorizationRule'.</span><span class="sxs-lookup"><span data-stu-id="609cd-274">The 'Get-AzureRmServiceBusNamespaceAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="609cd-275">Use el cmdlet 'Get-AzureRmServiceBusAuthorizationRule'.</span><span class="sxs-lookup"><span data-stu-id="609cd-275">Please use the 'Get-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>

### <a name="get-azurermservicebusnamespacekey"></a><span data-ttu-id="609cd-276">**Get-AzureRmServiceBusNamespaceKey**</span><span class="sxs-lookup"><span data-stu-id="609cd-276">**Get-AzureRmServiceBusNamespaceKey**</span></span>
- <span data-ttu-id="609cd-277">Se ha eliminado el cmdlet 'Get-AzureRmServiceBusNamespaceKey'.</span><span class="sxs-lookup"><span data-stu-id="609cd-277">The 'Get-AzureRmServiceBusNamespaceKey' cmdlet has been removed.</span></span> <span data-ttu-id="609cd-278">Use el cmdlet 'Get-AzureRmServiceBusKey'.</span><span class="sxs-lookup"><span data-stu-id="609cd-278">Please use the 'Get-AzureRmServiceBusKey' cmdlet.</span></span>

### <a name="new-azurermservicebusnamespaceauthorizationrule"></a><span data-ttu-id="609cd-279">**New-AzureRmServiceBusNamespaceAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="609cd-279">**New-AzureRmServiceBusNamespaceAuthorizationRule**</span></span>
- <span data-ttu-id="609cd-280">Se ha eliminado el cmdlet 'New-AzureRmServiceBusNamespaceAuthorizationRule'.</span><span class="sxs-lookup"><span data-stu-id="609cd-280">The 'New-AzureRmServiceBusNamespaceAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="609cd-281">Use el cmdlet 'Get-AzureRmServiceBusAuthorizationRule'.</span><span class="sxs-lookup"><span data-stu-id="609cd-281">Please use the 'New-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>

### <a name="remove-azurermservicebusnamespaceauthorizationrule"></a><span data-ttu-id="609cd-282">**Remove-AzureRmServiceBusNamespaceAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="609cd-282">**Remove-AzureRmServiceBusNamespaceAuthorizationRule**</span></span>
- <span data-ttu-id="609cd-283">Se ha eliminado el cmdlet 'Remove-AzureRmServiceBusNamespaceAuthorizationRule'.</span><span class="sxs-lookup"><span data-stu-id="609cd-283">The 'Remove-AzureRmServiceBusNamespaceAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="609cd-284">Use el cmdlet 'Remove-AzureRmServiceBusAuthorizationRule'.</span><span class="sxs-lookup"><span data-stu-id="609cd-284">Please use the 'Remove-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>

### <a name="set-azurermservicebusnamespaceauthorizationrule"></a><span data-ttu-id="609cd-285">**Set-AzureRmServiceBusNamespaceAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="609cd-285">**Set-AzureRmServiceBusNamespaceAuthorizationRule**</span></span>
- <span data-ttu-id="609cd-286">Se ha eliminado el cmdlet 'Set-AzureRmServiceBusNamespaceAuthorizationRule'.</span><span class="sxs-lookup"><span data-stu-id="609cd-286">The 'Set-AzureRmServiceBusNamespaceAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="609cd-287">Use el cmdlet 'Set-AzureRmServiceBusAuthorizationRule'.</span><span class="sxs-lookup"><span data-stu-id="609cd-287">Please use the 'Set-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>

### <a name="type-namespaceattributes"></a><span data-ttu-id="609cd-288">**Tipo NamespaceAttributes**</span><span class="sxs-lookup"><span data-stu-id="609cd-288">**Type NamespaceAttributes**</span></span>
- <span data-ttu-id="609cd-289">Se han quitado las siguientes propiedades</span><span class="sxs-lookup"><span data-stu-id="609cd-289">The following properties have been removed</span></span>
    - <span data-ttu-id="609cd-290">habilitado</span><span class="sxs-lookup"><span data-stu-id="609cd-290">Enabled</span></span>
    - <span data-ttu-id="609cd-291">Status</span><span class="sxs-lookup"><span data-stu-id="609cd-291">Status</span></span>
   
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

### <a name="type-queueattribute"></a><span data-ttu-id="609cd-292">**Tipo QueueAttribute**</span><span class="sxs-lookup"><span data-stu-id="609cd-292">**Type QueueAttribute**</span></span>
- <span data-ttu-id="609cd-293">Las siguientes propiedades se marcan como obsoletas:</span><span class="sxs-lookup"><span data-stu-id="609cd-293">The following properties are marked as obsolete:</span></span>
    - <span data-ttu-id="609cd-294">EnableBatchedOperations</span><span class="sxs-lookup"><span data-stu-id="609cd-294">EnableBatchedOperations</span></span>
    - <span data-ttu-id="609cd-295">EntityAvailabilityStatus</span><span class="sxs-lookup"><span data-stu-id="609cd-295">EntityAvailabilityStatus</span></span>
    - <span data-ttu-id="609cd-296">IsAnonymousAccessible</span><span class="sxs-lookup"><span data-stu-id="609cd-296">IsAnonymousAccessible</span></span>
    - <span data-ttu-id="609cd-297">SupportOrdering</span><span class="sxs-lookup"><span data-stu-id="609cd-297">SupportOrdering</span></span>

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
   
### <a name="type-topicattribute"></a><span data-ttu-id="609cd-298">**Tipo TopicAttribute**</span><span class="sxs-lookup"><span data-stu-id="609cd-298">**Type TopicAttribute**</span></span>
- <span data-ttu-id="609cd-299">Las siguientes propiedades se marcan como obsoletas:</span><span class="sxs-lookup"><span data-stu-id="609cd-299">The following properties are marked as obsolete:</span></span>
    - <span data-ttu-id="609cd-300">La ubicación</span><span class="sxs-lookup"><span data-stu-id="609cd-300">Location</span></span>
    - <span data-ttu-id="609cd-301">IsExpress</span><span class="sxs-lookup"><span data-stu-id="609cd-301">IsExpress</span></span>
    - <span data-ttu-id="609cd-302">IsAnonymousAccessible</span><span class="sxs-lookup"><span data-stu-id="609cd-302">IsAnonymousAccessible</span></span>
    - <span data-ttu-id="609cd-303">FilteringMessagesBeforePublishing</span><span class="sxs-lookup"><span data-stu-id="609cd-303">FilteringMessagesBeforePublishing</span></span>
    - <span data-ttu-id="609cd-304">EnableSubscriptionPartitioning</span><span class="sxs-lookup"><span data-stu-id="609cd-304">EnableSubscriptionPartitioning</span></span>
    - <span data-ttu-id="609cd-305">EntityAvailabilityStatus</span><span class="sxs-lookup"><span data-stu-id="609cd-305">EntityAvailabilityStatus</span></span>

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
   
### <a name="type-subscriptionattribute"></a><span data-ttu-id="609cd-306">**Tipo SubscriptionAttribute**</span><span class="sxs-lookup"><span data-stu-id="609cd-306">**Type SubscriptionAttribute**</span></span>
- <span data-ttu-id="609cd-307">Las siguientes propiedades se marcan como obsoletas</span><span class="sxs-lookup"><span data-stu-id="609cd-307">The following properties are marked as obsolete</span></span>
    - <span data-ttu-id="609cd-308">DeadLetteringOnFilterEvaluationExceptions</span><span class="sxs-lookup"><span data-stu-id="609cd-308">DeadLetteringOnFilterEvaluationExceptions</span></span>
    - <span data-ttu-id="609cd-309">EntityAvailabilityStatus</span><span class="sxs-lookup"><span data-stu-id="609cd-309">EntityAvailabilityStatus</span></span>
    - <span data-ttu-id="609cd-310">IsReadOnly</span><span class="sxs-lookup"><span data-stu-id="609cd-310">IsReadOnly</span></span>
    - <span data-ttu-id="609cd-311">La ubicación</span><span class="sxs-lookup"><span data-stu-id="609cd-311">Location</span></span>
   
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