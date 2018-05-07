# <a name="breaking-changes-for-microsoft-azure-powershell-300"></a>Cambios sustanciales en Microsoft Azure PowerShell 3.0.0.

Este documento sirve no solo como notificación de los cambios sustanciales, sino también como guía de migración para los consumidores de los cmdlets de Microsoft Azure PowerShell.  En todas las secciones se describen tanto el ímpetu del cambio como la ruta de acceso de la migración más sencilla.  Para ver el contexto en profundidad, consulte la solicitud de incorporación de cambios asociada a cada cambio.

## <a name="table-of-contents"></a>Tabla de contenido
1. [Cambios sustanciales en cmdlets de Data Lake Store](#breaking-changes-to-data-lake-store-cmdlets)
2. [Cambios sustanciales en cmdlets de ApiManagement](#breaking-changes-to-apimanagement-cmdlets)
3. [Cambios substanciales en cmdlets de Network](#breaking-changes-to-network-cmdlets)

## <a name="breaking-changes-to-data-lake-store-cmdlets"></a>Cambios sustanciales en cmdlets de Data Lake Store

Los siguientes cmdlets han resultado afectados en esta versión ([PR 2965](https://github.com/Azure/azure-powershell/pull/2965)):

**Get-AzureRmDataLakeStoreItemAcl (Get-AdlStoreItemAcl)**
- Este cmdlet se ha reemplazado por ``Get-AzureRmDataLakeStoreItemAclEntry (Get-AdlStoreItemAclEntry)``.
- El cmdlet anterior devuelve un objeto complejo que representa la lista de control de acceso (ACL). El nuevo cmdlet devuelve una lista simple de entradas de la ACL de la ruta de acceso elegida.

```powershell
# Old
Get-AdlStoreItemAcl -Account myadlsaccount -Path /foo

# New
Get-AdlStoreItemAclEntry -Account myadlsaccount -Path /foo
```

**Get-AzureRmDataLakeStoreItemAclEntry (Get-AdlStoreItemAclEntry)**
- Este cmdlet reemplaza el cmdlet anterior ``Get-AzureRmDataLakeStoreItemAcl (Get-AdlStoreItemAcl)``.
- Este nuevo cmdlet devuelve una lista simple de entradas de la ACL de la ruta de acceso elegida con el tipo ``DataLakeStoreItemAce[]``.
- La salida de este cmdlet se puede pasar al parámetro ``-Acl`` de los siguientes cmdlets:
   - ``Remove-AzureRmDataLakeStoreItemAcl``
   - ``Set-AzureRmDataLakeStoreItemAcl``
   - ``Set-AzureRmDataLakeStoreItemAclEntry``

```powershell
# Old
Get-AdlStoreItemAcl -Account myadlsaccount -Path /foo

# New
Get-AdlStoreItemAclEntry -Account myadlsaccount -Path /foo
```

**Remove-AzureRmDataLakeStoreItemAcl (Remove-AdlStoreItemAcl)**, **Set-AzureRmDataLakeStoreItemAcl (Set-AdlStoreItemAcl)**, **Set-AzureRmDataLakeStoreItemAclEntry (Set-AdlStoreItemAclEntry)**
- Estos cmdlets ahora aceptan ``DataLakeStoreItemAce[]`` para el parámetro ``-Acl``.
- ``DataLakeStoreItemAce[]`` lo devuelve ``Get-AzureRmDataLakeStoreItemAclEntry (Get-AdlStoreItemAclEntry)``.

```powershell
# Old
$acl = Get-AdlStoreItemAcl -Account myadlsaccount -Path /foo
Set-AdlStoreItemAcl -Account myadlsaccount -Path /foo -Acl $acl

# New
$aclEntries = Get-AdlStoreItemAclEntry -Account myadlsaccount -Path /foo
Set-AdlStoreItemAcl -Account myadlsaccount -Path /foo -Acl $aclEntries
```

## <a name="breaking-changes-to-apimanagement-cmdlets"></a>Cambios sustanciales en los cmdlets de ApiManagement

Los siguientes cmdlets han resultado afectados en esta versión ([PR 2971](https://github.com/Azure/azure-powershell/pull/2971)):

**New-AzureRmApiManagementVirtualNetwork**
- Los parámetros necesarios para hacer referencia a una red virtual ha cambiado de requerir SubnetName y VnetId para SubnetResourceId en formato ``/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.ClassicNetwork/virtualNetworks/{virtualNetworkName}/subnets/{subnetName}``

```powershell
# Old
$virtualNetwork = New-AzureRmApiManagementVirtualNetwork -Location <String> -SubnetName <String> -VnetId <Guid>

# New
$virtualNetwork = New-AzureRmApiManagementVirtualNetwork -Location <String> -SubnetResourceId <String>

```

**Cmdlet Set-AzureRmApiManagementVirtualNetworks en desuso**
- El cmdlet ha dejado de usarse, ya que había más de una forma de porque se produjo que más de una manera de establecer la red virtual asociada a la implementación de ApiManagement.

```powershell
# Old
$networksList = @()
$networksList += New-AzureRmApiManagementVirtualNetwork -Location $vnetLocation -VnetId $vnetId -SubnetName $subnetName
Set-AzureRmApiManagementVirtualNetworks -ResourceGroupName "ContosoGroup" -Name "ContosoApi" -VirtualNetworks $networksList

# New
$masterRegionVirtualNetwork = New-AzureRmApiManagementVirtualNetwork -Location <String> -SubnetResourceId <String>
Update-AzureRmApiManagementDeployment -ResourceGroupName "ContosoGroup" -Name "ContosoApi" -VirtualNetwork $masterRegionVirtualNetwork
```

## <a name="breaking-changes-to-network-cmdlets"></a>Cambios sustanciales en los cmdlets de Network

Los siguientes cmdlets han resultado afectados en esta versión ([PR 2982](https://github.com/Azure/azure-powershell/pull/2982)):

**New-AzureRmVirtualNetworkGateway**
- Se ha eliminado la descripción de lo que ha cambiado ``:- Bool parameter:-ActiveActive`` y se agrega ``SwitchParameter:-EnableActiveActiveFeature`` para habilitar la característica Active-Active en la puerta de enlace de red virtual recién creada.

```powershell
# Old 
# Sample of how the cmdlet was previously called
New-AzureRmVirtualNetworkGateway -ResourceGroupName $rgname -name $rname -Location $location -IpConfigurations $vnetIpConfig1,$vnetIpConfig2 -GatewayType Vpn -VpnType RouteBased -EnableBgp $false -GatewaySku HighPerformance -ActiveActive $true

# New
# Sample of how the cmdlet should now be called
New-AzureRmVirtualNetworkGateway -ResourceGroupName $rgname -name $rname -Location $location -IpConfigurations $vnetIpConfig1,$vnetIpConfig2 -GatewayType Vpn -VpnType RouteBased -EnableBgp $false -GatewaySku HighPerformance -EnableActiveActiveFeature
```

Set-AzureRmVirtualNetworkGateway
- Se ha eliminado la descripción de lo que ha cambiado ``:- Bool parameter:-ActiveActive`` y se agregan 2 ``SwitchParameters:-EnableActiveActiveFeature`` / ``DisableActiveActiveFeature`` para habilitar y deshabilitar la característica Active-Active en una puerta de enlace de red virtual.

```powershell
# Old
# Sample of how the cmdlet was previously called
Set-AzureRmVirtualNetworkGateway -VirtualNetworkGateway $gw -ActiveActive $true
Set-AzureRmVirtualNetworkGateway -VirtualNetworkGateway $gw -ActiveActive $false  

# New
# Sample of how the cmdlet should now be called
Set-AzureRmVirtualNetworkGateway -VirtualNetworkGateway $gw -EnableActiveActiveFeature
Set-AzureRmVirtualNetworkGateway -VirtualNetworkGateway $gw -DisableActiveActiveFeature
```