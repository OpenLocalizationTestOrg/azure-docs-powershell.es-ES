# <a name="breaking-changes-for-microsoft-azure-powershell-300"></a><span data-ttu-id="67c6a-101">Cambios sustanciales en Microsoft Azure PowerShell 3.0.0.</span><span class="sxs-lookup"><span data-stu-id="67c6a-101">Breaking changes for Microsoft Azure PowerShell 3.0.0.</span></span>

<span data-ttu-id="67c6a-102">Este documento sirve no solo como notificación de los cambios sustanciales, sino también como guía de migración para los consumidores de los cmdlets de Microsoft Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="67c6a-102">This document serves as both a breaking change notification and migration guide for consumers of the Microsoft Azure PowerShell cmdlets.</span></span>  <span data-ttu-id="67c6a-103">En todas las secciones se describen tanto el ímpetu del cambio como la ruta de acceso de la migración más sencilla.</span><span class="sxs-lookup"><span data-stu-id="67c6a-103">Each section describes both the impetus for the breaking change and the migration path of least resistance.</span></span>  <span data-ttu-id="67c6a-104">Para ver el contexto en profundidad, consulte la solicitud de incorporación de cambios asociada a cada cambio.</span><span class="sxs-lookup"><span data-stu-id="67c6a-104">For in-depth context, please refer to the pull request associated with each change.</span></span>

## <a name="table-of-contents"></a><span data-ttu-id="67c6a-105">Tabla de contenido</span><span class="sxs-lookup"><span data-stu-id="67c6a-105">Table of Contents</span></span>
1. [<span data-ttu-id="67c6a-106">Cambios sustanciales en cmdlets de Data Lake Store</span><span class="sxs-lookup"><span data-stu-id="67c6a-106">Breaking changes to Data Lake Store cmdlets</span></span>](#breaking-changes-to-data-lake-store-cmdlets)
2. [<span data-ttu-id="67c6a-107">Cambios sustanciales en cmdlets de ApiManagement</span><span class="sxs-lookup"><span data-stu-id="67c6a-107">Breaking changes to ApiManagement cmdlets</span></span>](#breaking-changes-to-apimanagement-cmdlets)
3. [<span data-ttu-id="67c6a-108">Cambios substanciales en cmdlets de Network</span><span class="sxs-lookup"><span data-stu-id="67c6a-108">Breaking changes to Network cmdlets</span></span>](#breaking-changes-to-network-cmdlets)

## <a name="breaking-changes-to-data-lake-store-cmdlets"></a><span data-ttu-id="67c6a-109">Cambios sustanciales en cmdlets de Data Lake Store</span><span class="sxs-lookup"><span data-stu-id="67c6a-109">Breaking changes to Data Lake Store cmdlets</span></span>

<span data-ttu-id="67c6a-110">Los siguientes cmdlets han resultado afectados en esta versión ([PR 2965](https://github.com/Azure/azure-powershell/pull/2965)):</span><span class="sxs-lookup"><span data-stu-id="67c6a-110">The following cmdlets were affected this release ([PR 2965](https://github.com/Azure/azure-powershell/pull/2965)):</span></span>

<span data-ttu-id="67c6a-111">**Get-AzureRmDataLakeStoreItemAcl (Get-AdlStoreItemAcl)**</span><span class="sxs-lookup"><span data-stu-id="67c6a-111">**Get-AzureRmDataLakeStoreItemAcl (Get-AdlStoreItemAcl)**</span></span>
- <span data-ttu-id="67c6a-112">Este cmdlet se ha reemplazado por ``Get-AzureRmDataLakeStoreItemAclEntry (Get-AdlStoreItemAclEntry)``.</span><span class="sxs-lookup"><span data-stu-id="67c6a-112">This cmdlet was removed and replaced with ``Get-AzureRmDataLakeStoreItemAclEntry (Get-AdlStoreItemAclEntry)``.</span></span>
- <span data-ttu-id="67c6a-113">El cmdlet anterior devuelve un objeto complejo que representa la lista de control de acceso (ACL).</span><span class="sxs-lookup"><span data-stu-id="67c6a-113">The old cmdlet returned a complex object representing the access control list (ACL).</span></span> <span data-ttu-id="67c6a-114">El nuevo cmdlet devuelve una lista simple de entradas de la ACL de la ruta de acceso elegida.</span><span class="sxs-lookup"><span data-stu-id="67c6a-114">The new cmdlet returns a simple list of entries in the chosen path's ACL.</span></span>

```powershell
# Old
Get-AdlStoreItemAcl -Account myadlsaccount -Path /foo

# New
Get-AdlStoreItemAclEntry -Account myadlsaccount -Path /foo
```

<span data-ttu-id="67c6a-115">**Get-AzureRmDataLakeStoreItemAclEntry (Get-AdlStoreItemAclEntry)**</span><span class="sxs-lookup"><span data-stu-id="67c6a-115">**Get-AzureRmDataLakeStoreItemAclEntry (Get-AdlStoreItemAclEntry)**</span></span>
- <span data-ttu-id="67c6a-116">Este cmdlet reemplaza el cmdlet anterior ``Get-AzureRmDataLakeStoreItemAcl (Get-AdlStoreItemAcl)``.</span><span class="sxs-lookup"><span data-stu-id="67c6a-116">This cmdlet replaces the old cmdlet ``Get-AzureRmDataLakeStoreItemAcl (Get-AdlStoreItemAcl)``.</span></span>
- <span data-ttu-id="67c6a-117">Este nuevo cmdlet devuelve una lista simple de entradas de la ACL de la ruta de acceso elegida con el tipo ``DataLakeStoreItemAce[]``.</span><span class="sxs-lookup"><span data-stu-id="67c6a-117">This new cmdlet returns a simple list of entries in the chosen path's ACL, with type ``DataLakeStoreItemAce[]``.</span></span>
- <span data-ttu-id="67c6a-118">La salida de este cmdlet se puede pasar al parámetro ``-Acl`` de los siguientes cmdlets:</span><span class="sxs-lookup"><span data-stu-id="67c6a-118">The output of this cmdlet can be passed in to the ``-Acl`` parameter of the following cmdlets:</span></span>
   - ``Remove-AzureRmDataLakeStoreItemAcl``
   - ``Set-AzureRmDataLakeStoreItemAcl``
   - ``Set-AzureRmDataLakeStoreItemAclEntry``

```powershell
# Old
Get-AdlStoreItemAcl -Account myadlsaccount -Path /foo

# New
Get-AdlStoreItemAclEntry -Account myadlsaccount -Path /foo
```

<span data-ttu-id="67c6a-119">**Remove-AzureRmDataLakeStoreItemAcl (Remove-AdlStoreItemAcl)**, **Set-AzureRmDataLakeStoreItemAcl (Set-AdlStoreItemAcl)**, **Set-AzureRmDataLakeStoreItemAclEntry (Set-AdlStoreItemAclEntry)**</span><span class="sxs-lookup"><span data-stu-id="67c6a-119">**Remove-AzureRmDataLakeStoreItemAcl (Remove-AdlStoreItemAcl)**, **Set-AzureRmDataLakeStoreItemAcl (Set-AdlStoreItemAcl)**, **Set-AzureRmDataLakeStoreItemAclEntry (Set-AdlStoreItemAclEntry)**</span></span>
- <span data-ttu-id="67c6a-120">Estos cmdlets ahora aceptan ``DataLakeStoreItemAce[]`` para el parámetro ``-Acl``.</span><span class="sxs-lookup"><span data-stu-id="67c6a-120">These cmdlets now accept ``DataLakeStoreItemAce[]`` for the ``-Acl`` parameter.</span></span>
- <span data-ttu-id="67c6a-121">``DataLakeStoreItemAce[]`` lo devuelve ``Get-AzureRmDataLakeStoreItemAclEntry (Get-AdlStoreItemAclEntry)``.</span><span class="sxs-lookup"><span data-stu-id="67c6a-121">``DataLakeStoreItemAce[]`` is returned by ``Get-AzureRmDataLakeStoreItemAclEntry (Get-AdlStoreItemAclEntry)``.</span></span>

```powershell
# Old
$acl = Get-AdlStoreItemAcl -Account myadlsaccount -Path /foo
Set-AdlStoreItemAcl -Account myadlsaccount -Path /foo -Acl $acl

# New
$aclEntries = Get-AdlStoreItemAclEntry -Account myadlsaccount -Path /foo
Set-AdlStoreItemAcl -Account myadlsaccount -Path /foo -Acl $aclEntries
```

## <a name="breaking-changes-to-apimanagement-cmdlets"></a><span data-ttu-id="67c6a-122">Cambios sustanciales en los cmdlets de ApiManagement</span><span class="sxs-lookup"><span data-stu-id="67c6a-122">Breaking changes to ApiManagement cmdlets</span></span>

<span data-ttu-id="67c6a-123">Los siguientes cmdlets han resultado afectados en esta versión ([PR 2971](https://github.com/Azure/azure-powershell/pull/2971)):</span><span class="sxs-lookup"><span data-stu-id="67c6a-123">The following cmdlets were affected this release ([PR 2971](https://github.com/Azure/azure-powershell/pull/2971)):</span></span>

<span data-ttu-id="67c6a-124">**New-AzureRmApiManagementVirtualNetwork**</span><span class="sxs-lookup"><span data-stu-id="67c6a-124">**New-AzureRmApiManagementVirtualNetwork**</span></span>
- <span data-ttu-id="67c6a-125">Los parámetros necesarios para hacer referencia a una red virtual ha cambiado de requerir SubnetName y VnetId para SubnetResourceId en formato ``/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.ClassicNetwork/virtualNetworks/{virtualNetworkName}/subnets/{subnetName}``</span><span class="sxs-lookup"><span data-stu-id="67c6a-125">The required parameters to reference a virtual network changed from requiring SubnetName and VnetId to SubnetResourceId in format ``/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.ClassicNetwork/virtualNetworks/{virtualNetworkName}/subnets/{subnetName}``</span></span>

```powershell
# Old
$virtualNetwork = New-AzureRmApiManagementVirtualNetwork -Location <String> -SubnetName <String> -VnetId <Guid>

# New
$virtualNetwork = New-AzureRmApiManagementVirtualNetwork -Location <String> -SubnetResourceId <String>

```

<span data-ttu-id="67c6a-126">**Cmdlet Set-AzureRmApiManagementVirtualNetworks en desuso**</span><span class="sxs-lookup"><span data-stu-id="67c6a-126">**Deprecating Cmdlet Set-AzureRmApiManagementVirtualNetworks**</span></span>
- <span data-ttu-id="67c6a-127">El cmdlet ha dejado de usarse, ya que había más de una forma de porque se produjo que más de una manera de establecer la red virtual asociada a la implementación de ApiManagement.</span><span class="sxs-lookup"><span data-stu-id="67c6a-127">The Cmdlet is getting deprecated as there was more than one way to Set Virtual Network associated to ApiManagement deployment.</span></span>

```powershell
# Old
$networksList = @()
$networksList += New-AzureRmApiManagementVirtualNetwork -Location $vnetLocation -VnetId $vnetId -SubnetName $subnetName
Set-AzureRmApiManagementVirtualNetworks -ResourceGroupName "ContosoGroup" -Name "ContosoApi" -VirtualNetworks $networksList

# New
$masterRegionVirtualNetwork = New-AzureRmApiManagementVirtualNetwork -Location <String> -SubnetResourceId <String>
Update-AzureRmApiManagementDeployment -ResourceGroupName "ContosoGroup" -Name "ContosoApi" -VirtualNetwork $masterRegionVirtualNetwork
```

## <a name="breaking-changes-to-network-cmdlets"></a><span data-ttu-id="67c6a-128">Cambios sustanciales en los cmdlets de Network</span><span class="sxs-lookup"><span data-stu-id="67c6a-128">Breaking changes to Network cmdlets</span></span>

<span data-ttu-id="67c6a-129">Los siguientes cmdlets han resultado afectados en esta versión ([PR 2982](https://github.com/Azure/azure-powershell/pull/2982)):</span><span class="sxs-lookup"><span data-stu-id="67c6a-129">The following cmdlets were affected this release ([PR 2982](https://github.com/Azure/azure-powershell/pull/2982)):</span></span>

<span data-ttu-id="67c6a-130">**New-AzureRmVirtualNetworkGateway**</span><span class="sxs-lookup"><span data-stu-id="67c6a-130">**New-AzureRmVirtualNetworkGateway**</span></span>
- <span data-ttu-id="67c6a-131">Se ha eliminado la descripción de lo que ha cambiado ``:- Bool parameter:-ActiveActive`` y se agrega ``SwitchParameter:-EnableActiveActiveFeature`` para habilitar la característica Active-Active en la puerta de enlace de red virtual recién creada.</span><span class="sxs-lookup"><span data-stu-id="67c6a-131">Description of what has changed ``:- Bool parameter:-ActiveActive`` is removed and ``SwitchParameter:-EnableActiveActiveFeature`` is added for enabling Active-Active feature on newly creating virtual network gateway.</span></span>

```powershell
# Old 
# Sample of how the cmdlet was previously called
New-AzureRmVirtualNetworkGateway -ResourceGroupName $rgname -name $rname -Location $location -IpConfigurations $vnetIpConfig1,$vnetIpConfig2 -GatewayType Vpn -VpnType RouteBased -EnableBgp $false -GatewaySku HighPerformance -ActiveActive $true

# New
# Sample of how the cmdlet should now be called
New-AzureRmVirtualNetworkGateway -ResourceGroupName $rgname -name $rname -Location $location -IpConfigurations $vnetIpConfig1,$vnetIpConfig2 -GatewayType Vpn -VpnType RouteBased -EnableBgp $false -GatewaySku HighPerformance -EnableActiveActiveFeature
```

<span data-ttu-id="67c6a-132">Set-AzureRmVirtualNetworkGateway</span><span class="sxs-lookup"><span data-stu-id="67c6a-132">Set-AzureRmVirtualNetworkGateway</span></span>
- <span data-ttu-id="67c6a-133">Se ha eliminado la descripción de lo que ha cambiado ``:- Bool parameter:-ActiveActive`` y se agregan 2 ``SwitchParameters:-EnableActiveActiveFeature`` / ``DisableActiveActiveFeature`` para habilitar y deshabilitar la característica Active-Active en una puerta de enlace de red virtual.</span><span class="sxs-lookup"><span data-stu-id="67c6a-133">Description of what has changed ``:- Bool parameter:-ActiveActive`` is removed and 2 ``SwitchParameters:-EnableActiveActiveFeature`` / ``DisableActiveActiveFeature`` are added for enabling and disabling Active-Active feature on virtual network gateway.</span></span>

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