# <a name="breaking-changes-for-microsoft-azure-powershell-400"></a><span data-ttu-id="f214a-101">Cambios sustanciales en Microsoft Azure PowerShell 4.0.0</span><span class="sxs-lookup"><span data-stu-id="f214a-101">Breaking changes for Microsoft Azure PowerShell 4.0.0</span></span>

<span data-ttu-id="f214a-102">Este documento sirve no solo como notificación de los cambios sustanciales, sino también como guía de migración para los consumidores de los cmdlets de Microsoft Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f214a-102">This document serves as both a breaking change notification and migration guide for consumers of the Microsoft Azure PowerShell cmdlets.</span></span> <span data-ttu-id="f214a-103">En todas las secciones se describen tanto el ímpetu del cambio como la ruta de acceso de la migración más sencilla.</span><span class="sxs-lookup"><span data-stu-id="f214a-103">Each section describes both the impetus for the breaking change and the migration path of least resistance.</span></span> <span data-ttu-id="f214a-104">Para ver el contexto en profundidad, consulte la solicitud de incorporación de cambios asociada a cada cambio.</span><span class="sxs-lookup"><span data-stu-id="f214a-104">For in-depth context, please refer to the pull request associated with each change.</span></span>

## <a name="table-of-contents"></a><span data-ttu-id="f214a-105">Tabla de contenido</span><span class="sxs-lookup"><span data-stu-id="f214a-105">Table of Contents</span></span>

- [<span data-ttu-id="f214a-106">Cambios substanciales en cmdlets de Compute</span><span class="sxs-lookup"><span data-stu-id="f214a-106">Breaking changes to Compute cmdlets</span></span>](#breaking-changes-to-compute-cmdlets)
- [<span data-ttu-id="f214a-107">Cambios substanciales en cmdlets de EventHub</span><span class="sxs-lookup"><span data-stu-id="f214a-107">Breaking changes to EventHub cmdlets</span></span>](#breaking-changes-to-eventhub-cmdlets)
- [<span data-ttu-id="f214a-108">Cambios substanciales en cmdlets de Insights</span><span class="sxs-lookup"><span data-stu-id="f214a-108">Breaking changes to Insights cmdlets</span></span>](#breaking-changes-to-insights-cmdlets)
- [<span data-ttu-id="f214a-109">Cambios substanciales en cmdlets de Network</span><span class="sxs-lookup"><span data-stu-id="f214a-109">Breaking changes to Network cmdlets</span></span>](#breaking-changes-to-network-cmdlets)
- [<span data-ttu-id="f214a-110">Cambios substanciales en cmdlets de ServiceBus</span><span class="sxs-lookup"><span data-stu-id="f214a-110">Breaking changes to ServiceBus cmdlets</span></span>](#breaking-changes-to-servicebus-cmdlets)
- [<span data-ttu-id="f214a-111">Cambios substanciales en cmdlets de Sql</span><span class="sxs-lookup"><span data-stu-id="f214a-111">Breaking changes to Sql cmdlets</span></span>](#breaking-changes-to-sql-cmdlets)
- [<span data-ttu-id="f214a-112">Cambios substanciales en cmdlets de Storage</span><span class="sxs-lookup"><span data-stu-id="f214a-112">Breaking changes to Storage cmdlets</span></span>](#breaking-changes-to-storage-cmdlets)
- [<span data-ttu-id="f214a-113">Cambios substanciales en cmdlets de Profile</span><span class="sxs-lookup"><span data-stu-id="f214a-113">Breaking Changes to Profile Cmdlets</span></span>](#breaking-changes-to-profile-cmdlets)
## <a name="breaking-changes-to-compute-cmdlets"></a><span data-ttu-id="f214a-114">Cambios substanciales en cmdlets de Compute</span><span class="sxs-lookup"><span data-stu-id="f214a-114">Breaking changes to Compute cmdlets</span></span>

<span data-ttu-id="f214a-115">Los siguientes tipos de salida han resultado afectados en esta versión:</span><span class="sxs-lookup"><span data-stu-id="f214a-115">The following output types were affected this release:</span></span>

### <a name="psvirtualmachine"></a><span data-ttu-id="f214a-116">PSVirtualMachine</span><span class="sxs-lookup"><span data-stu-id="f214a-116">PSVirtualMachine</span></span>
- <span data-ttu-id="f214a-117">Las propiedades de nivel superior `DataDiskNames` y `NetworkInterfaceIDs` del objeto `PSVirtualMachine` se han quitado del tipo de salida.</span><span class="sxs-lookup"><span data-stu-id="f214a-117">Top level properties `DataDiskNames` and `NetworkInterfaceIDs` of nthe `PSVirtualMachine` object have been removed from the output type.</span></span> <span data-ttu-id="f214a-118">Estas propiedades siempre han estado disponibles en las propiedades `StorageProfile` y `NetworkProfile` del objeto `PSVirtualMachine` y será la forma en que hay que acceder a ellas a partir de ahora.</span><span class="sxs-lookup"><span data-stu-id="f214a-118">These properties have always been available in the `StorageProfile` and `NetworkProfile` properties of the `PSVirtualMachine` object and will be the way they will need to be accessed going forward.</span></span>
- <span data-ttu-id="f214a-119">Este cambio afecta a los siguientes cmdlets:</span><span class="sxs-lookup"><span data-stu-id="f214a-119">This change affects the following cmdlets:</span></span>
    - `Add-AzureRmVMDataDisk`
    - `Add-AzureRmVMNetworkInterface`
    - `Get-AzureRmVM`
    - `Remove-AzureRmVMDataDisk`
    - `Remove-AzureRmVMNetworkInterface`
    - `Set-AzureRmVMDataDisk`

```powershell
# Old
$vm.DataDiskNames
$vm.NetworkInterfaceIDs

# New
$vm.StorageProfile.DataDisks | Select -Property Name
$vm.NetworkProfile.NetworkInterfaces | Select -Property Id
```

## <a name="breaking-changes-to-eventhub-cmdlets"></a><span data-ttu-id="f214a-120">Cambios sustanciales en los cmdlets de EventHub</span><span class="sxs-lookup"><span data-stu-id="f214a-120">Breaking changes to EventHub cmdlets</span></span>

<span data-ttu-id="f214a-121">Los siguientes cmdlets han resultado afectados en esta versión:</span><span class="sxs-lookup"><span data-stu-id="f214a-121">The following cmdlets were affected this release:</span></span>

### <a name="get-azurermeventhubnamespace"></a><span data-ttu-id="f214a-122">Get-AzureRmEventHubNamespace</span><span class="sxs-lookup"><span data-stu-id="f214a-122">Get-AzureRmEventHubNamespace</span></span>
- <span data-ttu-id="f214a-123">La propiedad `ResourceGroupName` se ha quitado del tipo de salida `NamespaceAttributes`</span><span class="sxs-lookup"><span data-stu-id="f214a-123">The property `ResourceGroupName` has been removed from the output type `NamespaceAttributes`</span></span>

### <a name="new-azurermeventhubnamespace"></a><span data-ttu-id="f214a-124">New-AzureRmEventHubNamespace</span><span class="sxs-lookup"><span data-stu-id="f214a-124">New-AzureRmEventHubNamespace</span></span>
- <span data-ttu-id="f214a-125">La propiedad `ResourceGroupName` se ha quitado del tipo de salida `NamespaceAttributes`</span><span class="sxs-lookup"><span data-stu-id="f214a-125">The property `ResourceGroupName` has been removed from the output type `NamespaceAttributes`</span></span>

## <a name="breaking-changes-to-insights-cmdlets"></a><span data-ttu-id="f214a-126">Cambios sustanciales en los cmdlets de Insights</span><span class="sxs-lookup"><span data-stu-id="f214a-126">Breaking changes to Insights cmdlets</span></span>

<span data-ttu-id="f214a-127">Los siguientes cmdlets han resultado afectados en esta versión:</span><span class="sxs-lookup"><span data-stu-id="f214a-127">The following cmdlets were affected this release:</span></span>
    
### <a name="get-azurermusage"></a><span data-ttu-id="f214a-128">Get-AzureRmUsage</span><span class="sxs-lookup"><span data-stu-id="f214a-128">Get-AzureRmUsage</span></span>
- <span data-ttu-id="f214a-129">Este cmdlet está en desuso.</span><span class="sxs-lookup"><span data-stu-id="f214a-129">This cmdlet has been deprecated.</span></span>

### <a name="remove-azurermalertrule"></a><span data-ttu-id="f214a-130">Remove-AzureRmAlertRule</span><span class="sxs-lookup"><span data-stu-id="f214a-130">Remove-AzureRmAlertRule</span></span>
- <span data-ttu-id="f214a-131">La salida de este cmdlet ha cambiado de una lista con un solo objeto a un solo objeto, que incluye Id. de solicitud y código de estado.</span><span class="sxs-lookup"><span data-stu-id="f214a-131">The output of this cmdlet has changed from a list with a single object to a single object; this object includes the requestId, and status code.</span></span>
    
```powershell
# Old  
$s1 = Remove-AzureRmAlertRule -ResourceGroup $resourceGroup -name chiricutin
if ($s1 -ne $null)
{
    $r = $s1(0).RequestId
    $s = $s1(0).StatusCode
}

# New
$s1 = Remove-AzureRmAlertRule -ResourceGroup $resourceGroup -name chiricutin
$r = $s1.RequestId
$s = $s1.StatusCode
```
    
### <a name="add-azurermlogalertrule"></a><span data-ttu-id="f214a-132">Add-AzureRmLogAlertRule</span><span class="sxs-lookup"><span data-stu-id="f214a-132">Add-AzureRmLogAlertRule</span></span>
- <span data-ttu-id="f214a-133">Este cmdlet está en desuso.</span><span class="sxs-lookup"><span data-stu-id="f214a-133">This cmdlet has been deprecated.</span></span>
    
### <a name="get-azurermalertrule"></a><span data-ttu-id="f214a-134">Get-AzureRmAlertRule</span><span class="sxs-lookup"><span data-stu-id="f214a-134">Get-AzureRmAlertRule</span></span>
- <span data-ttu-id="f214a-135">Todos los elementos de la salida (una lista de objetos) de este cmdlet están acoplados; en otras palabras, en lugar de devolver objetos con la estructura `{ Id, Location, Name, Tags, Properties }` devolverá objetos con la estructura `{ Id, Location, Name, Tags, Type, Description, IsEnabled, Condition, Actions, LastUpdatedTime, ...}`, que es todos los atributos de un recurso de Azure más todos los atributos de AlertRuleResource en el nivel superior.</span><span class="sxs-lookup"><span data-stu-id="f214a-135">Each element of the the output (a list of objects) of this cmdlet is flattened, i.e. instead of returning objects with the structure `{ Id, Location, Name, Tags, Properties }` it will return objects with the structure `{ Id, Location, Name, Tags, Type, Description, IsEnabled, Condition, Actions, LastUpdatedTime, ...}`, which is all of the attributes of an Azure Resource plus all of the attributes of an AlertRuleResource at the top level.</span></span>
    
```powershell
# Old
$rules = Get-AzureRmAlertRule -ResourceGroup $resourceGroup
if ($rules -and $rules.count -ge 1)
{
    Write-Host -fore red "Error updating alert rule"
      
    Write-Host $rules(0).Id
    Write-Host $rules(0).Properties.IsEnabled
    Write-Host $rules(0).Properties.Condition
}

# New
$rules = Get-AzureRmAlertRule -ResourceGroup $resourceGroup
if ($rules -and $rules.count -ge 1)
{
    Write-Host -fore red "Error updating alert rule"
 
    Write-Host $rules(0).Id
      
    # Properties will remain for a while
    Write-Host $rules(0).Properties.IsEnabled
      
    # But the properties will be at the top level too. Later Properties will be removed
    Write-Host $rules(0).IsEnabled
    Write-Host $rules(0).Condition
}
```
    
### <a name="get-azurermautoscalesetting"></a><span data-ttu-id="f214a-136">Get-AzureRmAutoscaleSetting</span><span class="sxs-lookup"><span data-stu-id="f214a-136">Get-AzureRmAutoscaleSetting</span></span>
- <span data-ttu-id="f214a-137">El campo `AutoscaleSettingResourceName` está en desuso, ya que siempre tiene el mismo valor que el campo `Name`.</span><span class="sxs-lookup"><span data-stu-id="f214a-137">The `AutoscaleSettingResourceName` field is deprecated since it always has the same value as the `Name` field.</span></span>

```powershell
# Old  
$s1 = Get-AzureRmAutoscaleSetting -ResourceGroup $resourceGroup -Name MySetting
if ($s1.AutoscaleSettingResourceName -ne $s1.Name)
{
    Write-Host "There is something wrong with the name"
}

# New
$s1 = Get-AzureRmAutoscaleSetting -ResourceGroup $resourceGroup -Name MySetting
    
# There won't be a AutoscaleSettingResourceName
Write-Host $s1.Name
```
    
### <a name="remove-azurermlogprofile"></a><span data-ttu-id="f214a-138">Remove-AzureRmLogProfile</span><span class="sxs-lookup"><span data-stu-id="f214a-138">Remove-AzureRmLogProfile</span></span>
- <span data-ttu-id="f214a-139">La salida de este cmdlet cambiará de `Boolean` a un objeto que contiene `RequestId` y `StatusCode`</span><span class="sxs-lookup"><span data-stu-id="f214a-139">The output of this cmdlet will change from `Boolean` to and object containing `RequestId` and `StatusCode`</span></span>

```powershell
# Old  
$s1 = Remove-AzureRmLogProfile -Name myLogProfile
if ($s1 -eq $true)
{
    Write-Host "Removed"
}
else
{
    Write-Host "Failed"
}

# New
$s1 = Remove-AzureRmLogProfile -Name myLogProfile
$r = $s1.RequestId
$s = $s1.StatusCode
```
    
### <a name="add-azurermlogprofile"></a><span data-ttu-id="f214a-140">Add-AzureRmLogProfile</span><span class="sxs-lookup"><span data-stu-id="f214a-140">Add-AzureRmLogProfile</span></span>
- <span data-ttu-id="f214a-141">La salida de este cmdlet cambiará de Id. de solicitud, código de estado y el recurso actualizado o recién creado</span><span class="sxs-lookup"><span data-stu-id="f214a-141">The output of this cmdlet will change from an object that includes the requestId, status code, and the updated or newly created resource</span></span>
    
```powershell
# Old  
$s1 = Add-AzureRmLogProfile -Name default -StorageAccountId /subscriptions/df602c9c-7aa0-407d-a6fb-eb20c8bd1192/resourceGroups/JohnKemTest/providers/Microsoft.Storage/storageAccounts/johnkemtest8162 -Locations Global -categ Delete, Write, Action -retention 3
$r = $s1.ServiceBusRuleId

# New
$s1 = Add-AzureRmLogProfile -Name default -StorageAccountId /subscriptions/df602c9c-7aa0-407d-a6fb-eb20c8bd1192/resourceGroups/JohnKemTest/providers/Microsoft.Storage/storageAccounts/johnkemtest8162 -Locations Global -categ Delete, Write, Action -retention 3
$r = $s1.RequestId
$s = $s1.StatusCode
$a = $s1.NewResource.ServiceBusRuleId
    
```
    
### <a name="set-azurermdiagnosticsettings"></a><span data-ttu-id="f214a-142">Set-AzureRmDiagnosticSettings</span><span class="sxs-lookup"><span data-stu-id="f214a-142">Set-AzureRmDiagnosticSettings</span></span>
- <span data-ttu-id="f214a-143">Se va a cambiar el nombre del comando a `Update-AzureRmDiagnsoticSettings`</span><span class="sxs-lookup"><span data-stu-id="f214a-143">The command is going to be renamed to `Update-AzureRmDiagnsoticSettings`</span></span>

```powershell
# Old
Set-AzureRmDiagnosticSettings

# New
Update-AzureRmDiagnosticSettings
```

## <a name="breaking-changes-to-network-cmdlets"></a><span data-ttu-id="f214a-144">Cambios sustanciales en los cmdlets de Network</span><span class="sxs-lookup"><span data-stu-id="f214a-144">Breaking changes to Network cmdlets</span></span>

<span data-ttu-id="f214a-145">Los siguientes cmdlets han resultado afectados en esta versión:</span><span class="sxs-lookup"><span data-stu-id="f214a-145">The following cmdlets were affected this release:</span></span>

### <a name="new-azurermvirtualnetworkgatewayconnection"></a><span data-ttu-id="f214a-146">New-AzureRmVirtualNetworkGatewayConnection</span><span class="sxs-lookup"><span data-stu-id="f214a-146">New-AzureRmVirtualNetworkGatewayConnection</span></span>
- <span data-ttu-id="f214a-147">El parámetro `EnableBgp` ha cambiado para usar una expresión `boolean`, en lugar de `string`</span><span class="sxs-lookup"><span data-stu-id="f214a-147">`EnableBgp` parameter has been changed to take a `boolean` instead of a `string`</span></span>

```powershell
# Old
New-AzureRmVirtualNetworkGatewayConnection -ResourceGroupName "RG" -name "conn1" -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localnetGateway -ConnectionType IPsec -SharedKey "key" -EnableBgp "true"

# New
New-AzureRmVirtualNetworkGatewayConnection -ResourceGroupName "RG" -name "conn1" -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localnetGateway -ConnectionType IPsec -SharedKey "key" -EnableBgp $true
```

## <a name="breaking-changes-to-servicebus-cmdlets"></a><span data-ttu-id="f214a-148">Cambios sustanciales en los cmdlets de ServiceBus</span><span class="sxs-lookup"><span data-stu-id="f214a-148">Breaking changes to ServiceBus cmdlets</span></span>

<span data-ttu-id="f214a-149">Los siguientes cmdlets han resultado afectados en esta versión:</span><span class="sxs-lookup"><span data-stu-id="f214a-149">The following cmdlets were affected this release:</span></span>

### <a name="get-azurermservicebusnamespace"></a><span data-ttu-id="f214a-150">Get-AzureRmServiceBusNamespace</span><span class="sxs-lookup"><span data-stu-id="f214a-150">Get-AzureRmServiceBusNamespace</span></span>
- <span data-ttu-id="f214a-151">La propiedad `ResourceGroupName` se ha quitado del tipo de salida `NamespaceAttributes`</span><span class="sxs-lookup"><span data-stu-id="f214a-151">The property `ResourceGroupName` has been removed from the output type `NamespaceAttributes`</span></span>

### <a name="new-azurermservicebusnamespace"></a><span data-ttu-id="f214a-152">New-AzureRmServiceBusNamespace</span><span class="sxs-lookup"><span data-stu-id="f214a-152">New-AzureRmServiceBusNamespace</span></span>

- <span data-ttu-id="f214a-153">La propiedad `ResourceGroupName` se ha quitado del tipo de salida `NamespaceAttributes`</span><span class="sxs-lookup"><span data-stu-id="f214a-153">The property `ResourceGroupName` has been removed from the output type `NamespaceAttributes`</span></span>

## <a name="breaking-changes-to-sql-cmdlets"></a><span data-ttu-id="f214a-154">Cambios sustanciales en los cmdlets de Sql</span><span class="sxs-lookup"><span data-stu-id="f214a-154">Breaking changes to Sql cmdlets</span></span>

<span data-ttu-id="f214a-155">Los siguientes cmdlets han resultado afectados en esta versión:</span><span class="sxs-lookup"><span data-stu-id="f214a-155">The following cmdlets were affected this release:</span></span>

### <a name="new-azurermsqldatabasefailovergroup"></a><span data-ttu-id="f214a-156">New-AzureRmSqlDatabaseFailoverGroup</span><span class="sxs-lookup"><span data-stu-id="f214a-156">New-AzureRmSqlDatabaseFailoverGroup</span></span>
- <span data-ttu-id="f214a-157">Se ha quitado el parámetro `Tag`</span><span class="sxs-lookup"><span data-stu-id="f214a-157">`Tag` parameter has been removed</span></span>
- <span data-ttu-id="f214a-158">Se ha cambiado el nombre del parámetro `GracePeriodWithDataLossHour` a `GracePeriodWithDataLossHours`</span><span class="sxs-lookup"><span data-stu-id="f214a-158">`GracePeriodWithDataLossHour` parameter has been renamed to `GracePeriodWithDataLossHours`</span></span>

```powershell
# Old
New-AzureRmSqlDatabaseFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -PartnerServerName server2 -FailoverPolicy Automatic -GracePeriodWithDataLossHour 1 -Tag @{ Environment="Test" }

# New
New-AzureRmSqlDatabaseFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -PartnerServerName server2 -FailoverPolicy Automatic -GracePeriodWithDataLossHours 1
```

### <a name="set-azurermsqldatabasefailovergroup"></a><span data-ttu-id="f214a-159">Set-AzureRmSqlDatabaseFailoverGroup</span><span class="sxs-lookup"><span data-stu-id="f214a-159">Set-AzureRmSqlDatabaseFailoverGroup</span></span>
- <span data-ttu-id="f214a-160">Se ha quitado el parámetro `Tag`</span><span class="sxs-lookup"><span data-stu-id="f214a-160">`Tag` parameter has been removed</span></span>
- <span data-ttu-id="f214a-161">Se ha cambiado el nombre del parámetro `GracePeriodWithDataLossHour` a `GracePeriodWithDataLossHours`</span><span class="sxs-lookup"><span data-stu-id="f214a-161">`GracePeriodWithDataLossHour` parameter has been renamed to `GracePeriodWithDataLossHours`</span></span>

```powershell
# Old
Set-AzureRmSqlDatabaseFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -FailoverPolicy Automatic -GracePeriodWithDataLossHour 1 -Tag @{ Environment="Test" }

# New
Set-AzureRmSqlDatabaseFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -FailoverPolicy Automatic -GracePeriodWithDataLossHours 1
```

### <a name="add-azurermsqldatabasetofailovergroup"></a><span data-ttu-id="f214a-162">Add-AzureRmSqlDatabaseToFailoverGroup</span><span class="sxs-lookup"><span data-stu-id="f214a-162">Add-AzureRmSqlDatabaseToFailoverGroup</span></span>
- <span data-ttu-id="f214a-163">Se ha quitado el parámetro `Tag`</span><span class="sxs-lookup"><span data-stu-id="f214a-163">`Tag` parameter has been removed</span></span>

```powershell
# Old
Add-AzureRmSqlDatabaseToFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -Database $db1 -Tag @{ Environment="Test" }

# New
Add-AzureRmSqlDatabaseToFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -Database $db1
```

###  <a name="remove-azurermsqldatabasefromfailovergroup"></a><span data-ttu-id="f214a-164">Remove-AzureRmSqlDatabaseFromFailoverGroup</span><span class="sxs-lookup"><span data-stu-id="f214a-164">Remove-AzureRmSqlDatabaseFromFailoverGroup</span></span>
- <span data-ttu-id="f214a-165">Se ha quitado el parámetro `Tag`</span><span class="sxs-lookup"><span data-stu-id="f214a-165">`Tag` parameter has been removed</span></span>

```powershell
# Old
Remove-AzureRmSqlDatabaseFromFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -Database $db1 -Tag @{ Environment="Test" }

# New
Remove-AzureRmSqlDatabaseFromFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -Database $db1
```

### <a name="remove-azurermsqldatabasefailovergroup"></a><span data-ttu-id="f214a-166">Remove-AzureRmSqlDatabaseFailoverGroup</span><span class="sxs-lookup"><span data-stu-id="f214a-166">Remove-AzureRmSqlDatabaseFailoverGroup</span></span>
- <span data-ttu-id="f214a-167">Se ha quitado el parámetro `PartnerResourceGroupName`</span><span class="sxs-lookup"><span data-stu-id="f214a-167">`PartnerResourceGroupName` parameter has been removed</span></span>
- <span data-ttu-id="f214a-168">Se ha quitado el parámetro `PartnerServerName`</span><span class="sxs-lookup"><span data-stu-id="f214a-168">`PartnerServerName` parameter has been removed</span></span>

```powershell
# Old
Remove-AzureRmSqlDatabaseFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -PartnerServerName server2 -PartnerResourceGroupName rg

# New
Remove-AzureRmSqlDatabaseFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg
```

### <a name="set-azurermsqldatabasethreatdetectionpolicy"></a><span data-ttu-id="f214a-169">Set-AzureRmSqlDatabaseThreatDetectionPolicy</span><span class="sxs-lookup"><span data-stu-id="f214a-169">Set-AzureRmSqlDatabaseThreatDetectionPolicy</span></span>
- <span data-ttu-id="f214a-170">El valor `Usage_Anomaly` ya no es válido para el parámetro `ExcludedDetectionType`</span><span class="sxs-lookup"><span data-stu-id="f214a-170">The value `Usage_Anomaly` is no longer valid for the parameter `ExcludedDetectionType`</span></span>

### <a name="set-azurermsqlserverthreatdetectionpolicy"></a><span data-ttu-id="f214a-171">Set-AzureRmSqlServerThreatDetectionPolicy</span><span class="sxs-lookup"><span data-stu-id="f214a-171">Set-AzureRmSqlServerThreatDetectionPolicy</span></span>
- <span data-ttu-id="f214a-172">El valor `Usage_Anomaly` ya no es válido para el parámetro `ExcludedDetectionType`</span><span class="sxs-lookup"><span data-stu-id="f214a-172">The value `Usage_Anomaly` is no longer valid for the parameter `ExcludedDetectionType`</span></span>

## <a name="breaking-changes-to-storage-cmdlets"></a><span data-ttu-id="f214a-173">Cambios sustanciales en los cmdlets de Storage</span><span class="sxs-lookup"><span data-stu-id="f214a-173">Breaking changes to Storage cmdlets</span></span>

<span data-ttu-id="f214a-174">Las siguientes propiedades del tipo de salida han resultado afectadas en esta versión:</span><span class="sxs-lookup"><span data-stu-id="f214a-174">The following output type properties were affected this release:</span></span>

### <a name="azurestorageblobicloudblobserviceclient"></a><span data-ttu-id="f214a-175">AzureStorageBlob.ICloudBlob.ServiceClient</span><span class="sxs-lookup"><span data-stu-id="f214a-175">AzureStorageBlob.ICloudBlob.ServiceClient</span></span>
- <span data-ttu-id="f214a-176">Las siguientes propiedades se han quitado de este tipo (_Nota_: Aún se pueden encontrar en la propiedad `DefaultRequestOptions`):</span><span class="sxs-lookup"><span data-stu-id="f214a-176">The following properties were removed from this type (_note_: they can still be found in `DefaultRequestOptions` property):</span></span>
    - `LocationMode`
    - `MaximumExecutionTime`
    - `ServerTimeout`
    - `ParallelOperationThreadCount`
    - `SingleBlobUploadThresholdInBytes`
- <span data-ttu-id="f214a-177">Este cambio afecta a los siguientes cmdlets:</span><span class="sxs-lookup"><span data-stu-id="f214a-177">This change affects the following cmdlets:</span></span>
    - `Get-AzureStorageBlob`
    - `Get-AzureStorageBlobContent`
    - `Get-AzureStorageBlobCopyState`
    - `Set-AzureStorageBlobContent`
    - `Start-AzureStorageBlobCopy`
    - `Stop-AzureStorageBlobCopy`
    
### <a name="azurestoragecontainercloudblobcontainerserviceclient"></a><span data-ttu-id="f214a-178">AzureStorageContainer.CloudBlobContainer.ServiceClient</span><span class="sxs-lookup"><span data-stu-id="f214a-178">AzureStorageContainer.CloudBlobContainer.ServiceClient</span></span>
- <span data-ttu-id="f214a-179">Las siguientes propiedades se han quitado de este tipo (_Nota_: Aún se pueden encontrar en la propiedad `DefaultRequestOptions`):</span><span class="sxs-lookup"><span data-stu-id="f214a-179">The following properties were removed from this type (_note_: they can still be found in the `DefaultRequestOptions` property):</span></span>
    - `LocationMode`
    - `MaximumExecutionTime`
    - `ServerTimeout`
    - `ParallelOperationThreadCount`
    - `SingleBlobUploadThresholdInBytes`
- <span data-ttu-id="f214a-180">Este cambio afecta a los siguientes cmdlets:</span><span class="sxs-lookup"><span data-stu-id="f214a-180">This change affects the following cmdlets:</span></span>
    - `Get-AzureStorageContainer`
    - `New-AzureStorageContainer`
    - `Set-AzureStorageContainerAcl`
    
### <a name="azurestoragequeuecloudqueueserviceclient"></a><span data-ttu-id="f214a-181">AzureStorageQueue.CloudQueue.ServiceClient</span><span class="sxs-lookup"><span data-stu-id="f214a-181">AzureStorageQueue.CloudQueue.ServiceClient</span></span>
- <span data-ttu-id="f214a-182">Las siguientes propiedades se han quitado de este tipo (_Nota_: Aún se pueden encontrar en la propiedad `DefaultRequestOptions`):</span><span class="sxs-lookup"><span data-stu-id="f214a-182">The following properties were removed from this type (_note_: they can still be found in the `DefaultRequestOptions` property):</span></span>
    - `LocationMode`
    - `MaximumExecutionTime`
    - `RetryPolicy`
    - `ServerTimeout`
- <span data-ttu-id="f214a-183">Este cambio afecta a los siguientes cmdlets:</span><span class="sxs-lookup"><span data-stu-id="f214a-183">This change affects the following cmdlets:</span></span>
    - `Get-AzureStorageQueue`
    - `New-AzureStorageQueue`
    
### <a name="azurestoragetablecloudtableserviceclient"></a><span data-ttu-id="f214a-184">AzureStorageTable.CloudTable.ServiceClient</span><span class="sxs-lookup"><span data-stu-id="f214a-184">AzureStorageTable.CloudTable.ServiceClient</span></span>
- <span data-ttu-id="f214a-185">Las siguientes propiedades se han quitado de este tipo (_Nota_: Aún se pueden encontrar en la propiedad `DefaultRequestOptions`):</span><span class="sxs-lookup"><span data-stu-id="f214a-185">The following properties were removed from this type (_note_: they can still be found in the `DefaultRequestOptions` property):</span></span>
    - `LocationMode`
    - `MaximumExecutionTime`
    - `PayloadFormat`
    - `RetryPolicy`
    - `ServerTimeout`
- <span data-ttu-id="f214a-186">Este cambio afecta a los siguientes cmdlets:</span><span class="sxs-lookup"><span data-stu-id="f214a-186">This change affects the following cmdlets:</span></span>
    - `Get-AzureStorageTable`
    - `New-AzureStorageTable`
    
```powershell
# Old
$LocationMode = (Get-AzureStorageBlob -Container $containername)[0].ICloudBlob.ServiceClient.LocationMode       
$ParallelOperationThreadCount = (Get-AzureStorageContainer -Container $containername).CloudBlobContainer.ServiceClient.ParallelOperationThreadCount
$PayloadFormat = (Get-AzureStorageTable -Name $tablename).CloudTable.ServiceClient.PayloadFormat
$RetryPolicy = (Get-AzureStorageQueue -Name $queuename).CloudQueue.ServiceClient.RetryPolicy

# New
$LocationMode = (Get-AzureStorageBlob -Container $containername)[0].ICloudBlob.ServiceClient.DefaultRequestOptions.LocationMode     
$ParallelOperationThreadCount = (Get-AzureStorageContainer -Container $containername).CloudBlobContainer.ServiceClient.DefaultRequestOptions.ParallelOperationThreadCount
$PayloadFormat = (Get-AzureStorageTable -Name $tablename).CloudTable.ServiceClient.DefaultRequestOptions.PayloadFormat
$RetryPolicy = (Get-AzureStorageQueue -Name $queuename).CloudQueue.ServiceClient.DefaultRequestOptions.RetryPolicy
```

## <a name="breaking-changes-to-profile-cmdlets"></a><span data-ttu-id="f214a-187">Cambios sustanciales en los cmdlets de Profile</span><span class="sxs-lookup"><span data-stu-id="f214a-187">Breaking Changes to Profile Cmdlets</span></span>

<span data-ttu-id="f214a-188">En esta versión se han cambiado los siguientes cmdlets y tipos de salida de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f214a-188">The following cmdlets and cmdlet output types were changed in this release.</span></span>

### <a name="add-azurermaccount-breaking-changes"></a><span data-ttu-id="f214a-189">Cambios sustanciales en Add-AzureRmAccount</span><span class="sxs-lookup"><span data-stu-id="f214a-189">Add-AzureRmAccount breaking changes</span></span>

- <span data-ttu-id="f214a-190">El parámetro ```EnvironmentName``` se ha reemplazado por ```Environment``` y ```Environment``` ahora usa una cadena, no un objeto ```AzureEnvironment```</span><span class="sxs-lookup"><span data-stu-id="f214a-190">```EnvironmentName``` parameter has been removed and replaced with ```Environment```, the ```Environment``` now takes a string and not an ```AzureEnvironment``` object</span></span>

```powershell
# Old
Add-AzureRmAccount -EnvironmentName AzureChinaCloud

# New
Add-AzureRmAccount -Environment AzureChinaCloud
```

### <a name="select-azurermprofile-was-renamed-to-import-azurermcontext"></a><span data-ttu-id="f214a-191">El nombre Select-AzureRmProfile se ha cambiado a Import-AzureRmContext</span><span class="sxs-lookup"><span data-stu-id="f214a-191">Select-AzureRmProfile was renamed to Import-AzureRmContext</span></span>

<span data-ttu-id="f214a-192">Se ha cambiado el nombre de ```Select-AzureRmProfile``` a ```Import-AzureRmContext```</span><span class="sxs-lookup"><span data-stu-id="f214a-192">```Select-AzureRmProfile``` was renamed to ```Import-AzureRmContext```</span></span>

```powershell
# Old
Select-AzureRmProfile -Path c:\mydir\myprofile.json

# New
Import-AzureRmContext -Path c:\mydir\myprofile.json
```

### <a name="save-azurermprofile-was-renamed-to-save-azurermcontext"></a><span data-ttu-id="f214a-193">El nombre Save-AzureRmProfile se ha cambiado a Save-AzureRmContext</span><span class="sxs-lookup"><span data-stu-id="f214a-193">Save-AzureRmProfile was renamed to Save-AzureRmContext</span></span>

<span data-ttu-id="f214a-194">Se ha cambiado el nombre de ```Save-AzureRmProfile``` a ```Save-AzureRmContext```</span><span class="sxs-lookup"><span data-stu-id="f214a-194">```Save-AzureRmProfile``` was renamed to ```Save-AzureRmContext```</span></span>

```powershell
# Old
Save-AzureRmProfile -Path c:\mydir\myprofile.json

# New
Save-AzureRmContext -Path c:\mydir\myprofile.json
```
### <a name="breaking-changes-to-output-psazurecontext-type"></a><span data-ttu-id="f214a-195">Cambios sustanciales en el tipo de salida de PSAzureContext</span><span class="sxs-lookup"><span data-stu-id="f214a-195">Breaking Changes to output PSAzureContext Type</span></span>

- <span data-ttu-id="f214a-196">La propiedad ```TokenCache``` ha cambiado a un tipo que implementa ```IAzureTokenCache```, en lugar de ```byte[]```</span><span class="sxs-lookup"><span data-stu-id="f214a-196">The ```TokenCache``` property changed to a type that implements ```IAzureTokenCache``` instead of a ```byte[]```</span></span>

```powershell
# Old
$bytes = (Get-AzureRmContext).TokenCache
$bytes = (Set-AzureRmContext -SubscriptionId xxx-xxx-xxx-xxx).TokenCache
$bytes = (Add-AzureRmAccount).Context.TokenCache

# New
$bytes = (Get-AzureRmContext).TokenCache.CacheData
$bytes = (Set-AzureRmContext -SubscriptionId xxx-xxx-xxx-xxx).TokenCache.CacheData
$bytes = (Add-AzureRmAccount).Context.TokenCache.CacheData
```

### <a name="breaking-changes-to-the-output-psazureaccount-type"></a><span data-ttu-id="f214a-197">Cambios sustanciales en el tipo de salida de PSAzureAccount</span><span class="sxs-lookup"><span data-stu-id="f214a-197">Breaking Changes to the output PSAzureAccount Type</span></span>

- <span data-ttu-id="f214a-198">La propiedad ```AccountType``` ha cambiado a ```Type```</span><span class="sxs-lookup"><span data-stu-id="f214a-198">The ```AccountType``` property was changed to ```Type```</span></span>

```powershell
# Old
$type = (Get-AzureRmContext).Account.AccountType
$type = (Set-AzureRmContext -SubscriptionId xxx-xxx-xxx-xxx).Account.AccountType
$type = (Add-AzureRmAccount).Context.Account.AccountType

# New 
$type = (Get-AzureRmContext).Account.Type
$type = (Set-AzureRmContext -SubscriptionId xxx-xxx-xxx-xxx).Account.Type
$type = (Add-AzureRmAccount).Context.Account.Type
```

### <a name="breaking-changes-to-the-output-psazuresubscription-type"></a><span data-ttu-id="f214a-199">Cambios sustanciales en el tipo de salida de PSAzureSubscription</span><span class="sxs-lookup"><span data-stu-id="f214a-199">Breaking Changes to the output PSAzureSubscription Type</span></span>
- <span data-ttu-id="f214a-200">La propiedad ```SubscriptionId``` ha cambiado a ```Id```</span><span class="sxs-lookup"><span data-stu-id="f214a-200">The ```SubscriptionId``` property was changed to ```Id```</span></span>

```powershell
# Old
$id =(Get-AzureRmSubscription -SubscriptionId xxxx-xxxx-xxxx-xxxx).SubscriptionId
$id =(Add-AzureRmAccount -SubscriptionId xxxx-xxxx-xxxx-xxxx).Context.Subscription.SubscriptionId
$id =(Get-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Subscription.SubscriptionId
$id =(Set-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Subscription.SubscriptionId

# New
$id =(Get-AzureRmSubscription -SubscriptionId xxxx-xxxx-xxxx-xxxx).Id
$id =(Add-AzureRmAccount -SubscriptionId xxxx-xxxx-xxxx-xxxx).Context.Subscription.Id
$id =(Get-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Subscription.Id
$id =(Set-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Subscription.Id
```

- <span data-ttu-id="f214a-201">La propiedad ```SubscriptionName``` ha cambiado a ```Name```</span><span class="sxs-lookup"><span data-stu-id="f214a-201">The ```SubscriptionName``` property was changed to ```Name```</span></span>

```powershell
# Old
$name =(Get-AzureRmSubscription -SubscriptionId xxxx-xxxx-xxxx-xxxx).SubscriptionName
$name =(Add-AzureRmAccount -SubscriptionId xxxx-xxxx-xxxx-xxxx).Context.Subscription.SubscriptionName
$name =(Get-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Subscription.SubscriptionName
$name =(Set-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Subscription.SubscriptionName

# New
$name =(Get-AzureRmSubscription -SubscriptionId xxxx-xxxx-xxxx-xxxx).Name
$name =(Add-AzureRmAccount -SubscriptionId xxxx-xxxx-xxxx-xxxx).Context.Subscription.Name
$name =(Get-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Subscription.Name
$name =(Set-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Subscription.Name
```

### <a name="breaking-changes-to-the-output-psazuretenant-type"></a><span data-ttu-id="f214a-202">Cambios sustanciales en el tipo de salida de PSAzureTenant</span><span class="sxs-lookup"><span data-stu-id="f214a-202">Breaking Changes to the output PSAzureTenant Type</span></span>

- <span data-ttu-id="f214a-203">La propiedad ```TenantId``` ha cambiado a ```Id```</span><span class="sxs-lookup"><span data-stu-id="f214a-203">The ```TenantId``` property was changed to ```Id```</span></span>

```powershell
# Old
$id =(Get-AzureRmTenant -TenantId xxxx-xxxx-xxxx-xxxx).TenantId
$id =(Add-AzureRmAccount -SubscriptionId xxxx-xxxx-xxxx-xxxx).Context.Tenant.TenantId
$id =(Get-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Tenant.TenantId
$id =(Set-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Tenant.TenantId

# New
$id =(Get-AzureRmTenant -TenantId xxxx-xxxx-xxxx-xxxx).Id
$id =(Add-AzureRmAccount -SubscriptionId xxxx-xxxx-xxxx-xxxx).Context.Tenant.Id
$id =(Get-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Tenant.Id
$id =(Set-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Tenant.Id
```

- <span data-ttu-id="f214a-204">La propiedad ```Domain``` ha cambiado a ```Directory```</span><span class="sxs-lookup"><span data-stu-id="f214a-204">The ```Domain``` property was changed to ```Directory```</span></span>

```powershell
# Old
$tenantName =(Get-AzureRmTenant -TenantId xxxx-xxxx-xxxx-xxxx).Domain

# New
$tenantName =(Get-AzureRmTenant -TenantId xxxx-xxxx-xxxx-xxxx).Directory
```
