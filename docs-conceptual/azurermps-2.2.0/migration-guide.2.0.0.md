# <a name="table-of-contents"></a><span data-ttu-id="2c0d9-101">Tabla de contenido</span><span class="sxs-lookup"><span data-stu-id="2c0d9-101">Table of Contents</span></span>
1. [<span data-ttu-id="2c0d9-102">Eliminación de los parámetros Force</span><span class="sxs-lookup"><span data-stu-id="2c0d9-102">Removal of Force parameters</span></span>](#removal-of-force-parameters)
2. [<span data-ttu-id="2c0d9-103">Cambio de los parámetros Tag</span><span class="sxs-lookup"><span data-stu-id="2c0d9-103">Change of Tag parameters</span></span>](#change-of-tag-parameters)
3. [<span data-ttu-id="2c0d9-104">Cambios substanciales en cmdlets de Storage</span><span class="sxs-lookup"><span data-stu-id="2c0d9-104">Breaking changes to Storage cmdlets</span></span>](#breaking-changes-to-storage-cmdlets)
4. [<span data-ttu-id="2c0d9-105">Cambios sustanciales en los cmdlets de AD</span><span class="sxs-lookup"><span data-stu-id="2c0d9-105">Breaking changes to AD cmdlets</span></span>](#breaking-changes-to-ad-cmdlets)

## <a name="removal-of-force-parameters"></a><span data-ttu-id="2c0d9-106">Eliminación de los parámetros Force</span><span class="sxs-lookup"><span data-stu-id="2c0d9-106">Removal of Force parameters</span></span>

<span data-ttu-id="2c0d9-107">En esta versión hemos eliminado todos los parámetros `Force` obsoletos de cmdlets y las advertencias correspondientes de que el parámetro se quitará en futuras versiones.</span><span class="sxs-lookup"><span data-stu-id="2c0d9-107">This release, we removed all Obsolete `Force` parameters from cmdlets and the corresponding warnings that the parameter would be removed in a future release.</span></span>

<span data-ttu-id="2c0d9-108">Este cambio afecta a los siguientes cmdlets:</span><span class="sxs-lookup"><span data-stu-id="2c0d9-108">The following cmdlets are affected by this change:</span></span>

<span data-ttu-id="2c0d9-109">**ApiManagement**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-109">**ApiManagement**</span></span>
- <span data-ttu-id="2c0d9-110">Remove-AzureRmApiManagement</span><span class="sxs-lookup"><span data-stu-id="2c0d9-110">Remove-AzureRmApiManagement</span></span>
- <span data-ttu-id="2c0d9-111">Remove-AzureRmApiManagementApi</span><span class="sxs-lookup"><span data-stu-id="2c0d9-111">Remove-AzureRmApiManagementApi</span></span>
- <span data-ttu-id="2c0d9-112">Remove-AzureRmApiManagementGroup</span><span class="sxs-lookup"><span data-stu-id="2c0d9-112">Remove-AzureRmApiManagementGroup</span></span>
- <span data-ttu-id="2c0d9-113">Remove-AzureRmApiManagementLogger</span><span class="sxs-lookup"><span data-stu-id="2c0d9-113">Remove-AzureRmApiManagementLogger</span></span>
- <span data-ttu-id="2c0d9-114">Remove-AzureRmApiManagementOpenIdConnectProvider</span><span class="sxs-lookup"><span data-stu-id="2c0d9-114">Remove-AzureRmApiManagementOpenIdConnectProvider</span></span>
- <span data-ttu-id="2c0d9-115">Remove-AzureRmApiManagementOperation</span><span class="sxs-lookup"><span data-stu-id="2c0d9-115">Remove-AzureRmApiManagementOperation</span></span>
- <span data-ttu-id="2c0d9-116">Remove-AzureRmApiManagementPolicy</span><span class="sxs-lookup"><span data-stu-id="2c0d9-116">Remove-AzureRmApiManagementPolicy</span></span>
- <span data-ttu-id="2c0d9-117">Remove-AzureRmApiManagementProduct</span><span class="sxs-lookup"><span data-stu-id="2c0d9-117">Remove-AzureRmApiManagementProduct</span></span>
- <span data-ttu-id="2c0d9-118">Remove-AzureRmApiManagementProperty</span><span class="sxs-lookup"><span data-stu-id="2c0d9-118">Remove-AzureRmApiManagementProperty</span></span>
- <span data-ttu-id="2c0d9-119">Remove-AzureRmApiManagementSubscription</span><span class="sxs-lookup"><span data-stu-id="2c0d9-119">Remove-AzureRmApiManagementSubscription</span></span>
- <span data-ttu-id="2c0d9-120">Remove-AzureRmApiManagementUser</span><span class="sxs-lookup"><span data-stu-id="2c0d9-120">Remove-AzureRmApiManagementUser</span></span>

<span data-ttu-id="2c0d9-121">**Automation**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-121">**Automation**</span></span>
- <span data-ttu-id="2c0d9-122">Remove-AzureRmAutomationCertificate</span><span class="sxs-lookup"><span data-stu-id="2c0d9-122">Remove-AzureRmAutomationCertificate</span></span>
- <span data-ttu-id="2c0d9-123">Remove-AzureRmAutomationCredential</span><span class="sxs-lookup"><span data-stu-id="2c0d9-123">Remove-AzureRmAutomationCredential</span></span>
- <span data-ttu-id="2c0d9-124">Remove-AzureRmAutomationVariable</span><span class="sxs-lookup"><span data-stu-id="2c0d9-124">Remove-AzureRmAutomationVariable</span></span>
- <span data-ttu-id="2c0d9-125">Remove-AzureRmAutomationWebhook</span><span class="sxs-lookup"><span data-stu-id="2c0d9-125">Remove-AzureRmAutomationWebhook</span></span>

<span data-ttu-id="2c0d9-126">**Batch**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-126">**Batch**</span></span>
- <span data-ttu-id="2c0d9-127">Remove-AzureBatchCertificate</span><span class="sxs-lookup"><span data-stu-id="2c0d9-127">Remove-AzureBatchCertificate</span></span>
- <span data-ttu-id="2c0d9-128">Remove-AzureBatchComputeNode</span><span class="sxs-lookup"><span data-stu-id="2c0d9-128">Remove-AzureBatchComputeNode</span></span>
- <span data-ttu-id="2c0d9-129">Remove-AzureBatchComputeNodeUser</span><span class="sxs-lookup"><span data-stu-id="2c0d9-129">Remove-AzureBatchComputeNodeUser</span></span>

<span data-ttu-id="2c0d9-130">**DataFactories**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-130">**DataFactories**</span></span>
- <span data-ttu-id="2c0d9-131">Resume-AzureRmDataFactoryPipeline</span><span class="sxs-lookup"><span data-stu-id="2c0d9-131">Resume-AzureRmDataFactoryPipeline</span></span>
- <span data-ttu-id="2c0d9-132">Set-AzureRmDataFactoryPipelineActivePeriod</span><span class="sxs-lookup"><span data-stu-id="2c0d9-132">Set-AzureRmDataFactoryPipelineActivePeriod</span></span>
- <span data-ttu-id="2c0d9-133">Suspend-AzureRmDataFactoryPipeline</span><span class="sxs-lookup"><span data-stu-id="2c0d9-133">Suspend-AzureRmDataFactoryPipeline</span></span>

<span data-ttu-id="2c0d9-134">**DataLakeStore**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-134">**DataLakeStore**</span></span>
- <span data-ttu-id="2c0d9-135">Remove-AzureRmDataLakeStoreItemAclEntry</span><span class="sxs-lookup"><span data-stu-id="2c0d9-135">Remove-AzureRmDataLakeStoreItemAclEntry</span></span>
- <span data-ttu-id="2c0d9-136">Set-AzureRmDataLakeStoreItemAcl</span><span class="sxs-lookup"><span data-stu-id="2c0d9-136">Set-AzureRmDataLakeStoreItemAcl</span></span>
- <span data-ttu-id="2c0d9-137">Set-AzureRmDataLakeStoreItemAclEntry</span><span class="sxs-lookup"><span data-stu-id="2c0d9-137">Set-AzureRmDataLakeStoreItemAclEntry</span></span>
- <span data-ttu-id="2c0d9-138">Set-AzureRmDataLakeStoreItemOwner</span><span class="sxs-lookup"><span data-stu-id="2c0d9-138">Set-AzureRmDataLakeStoreItemOwner</span></span>

<span data-ttu-id="2c0d9-139">**OperationalInsights**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-139">**OperationalInsights**</span></span>
- <span data-ttu-id="2c0d9-140">Remove-AzureRmOperationalInsightsSavedSearch</span><span class="sxs-lookup"><span data-stu-id="2c0d9-140">Remove-AzureRmOperationalInsightsSavedSearch</span></span>

<span data-ttu-id="2c0d9-141">**Perfil**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-141">**Profile**</span></span>
- <span data-ttu-id="2c0d9-142">Remove-AzureRmEnvironment</span><span class="sxs-lookup"><span data-stu-id="2c0d9-142">Remove-AzureRmEnvironment</span></span>

<span data-ttu-id="2c0d9-143">**RedisCache**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-143">**RedisCache**</span></span>
- <span data-ttu-id="2c0d9-144">Remove-AzureRmRedisCacheDiagnostics</span><span class="sxs-lookup"><span data-stu-id="2c0d9-144">Remove-AzureRmRedisCacheDiagnostics</span></span>

<span data-ttu-id="2c0d9-145">**Recursos**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-145">**Resources**</span></span>
- <span data-ttu-id="2c0d9-146">Register-AzureRmProviderFeature</span><span class="sxs-lookup"><span data-stu-id="2c0d9-146">Register-AzureRmProviderFeature</span></span>
- <span data-ttu-id="2c0d9-147">Register-AzureRmResourceProvider</span><span class="sxs-lookup"><span data-stu-id="2c0d9-147">Register-AzureRmResourceProvider</span></span>
- <span data-ttu-id="2c0d9-148">Remove-AzureRmADServicePrincipal</span><span class="sxs-lookup"><span data-stu-id="2c0d9-148">Remove-AzureRmADServicePrincipal</span></span>
- <span data-ttu-id="2c0d9-149">Remove-AzureRmPolicyAssignment</span><span class="sxs-lookup"><span data-stu-id="2c0d9-149">Remove-AzureRmPolicyAssignment</span></span>
- <span data-ttu-id="2c0d9-150">Remove-AzureRmResourceGroupDeployment</span><span class="sxs-lookup"><span data-stu-id="2c0d9-150">Remove-AzureRmResourceGroupDeployment</span></span>
- <span data-ttu-id="2c0d9-151">Remove-AzureRmRoleAssignment</span><span class="sxs-lookup"><span data-stu-id="2c0d9-151">Remove-AzureRmRoleAssignment</span></span>
- <span data-ttu-id="2c0d9-152">Stop-AzureRmResourceGroupDeployment</span><span class="sxs-lookup"><span data-stu-id="2c0d9-152">Stop-AzureRmResourceGroupDeployment</span></span>
- <span data-ttu-id="2c0d9-153">Unregister-AzureRmResourceProvider</span><span class="sxs-lookup"><span data-stu-id="2c0d9-153">Unregister-AzureRmResourceProvider</span></span>

<span data-ttu-id="2c0d9-154">**Storage**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-154">**Storage**</span></span>
- <span data-ttu-id="2c0d9-155">Remove-AzureStorageContainerStoredAccessPolicy</span><span class="sxs-lookup"><span data-stu-id="2c0d9-155">Remove-AzureStorageContainerStoredAccessPolicy</span></span>
- <span data-ttu-id="2c0d9-156">Remove-AzureStorageQueueStoredAccessPolicy</span><span class="sxs-lookup"><span data-stu-id="2c0d9-156">Remove-AzureStorageQueueStoredAccessPolicy</span></span>
- <span data-ttu-id="2c0d9-157">Remove-AzureStorageShareStoredAccessPolicy</span><span class="sxs-lookup"><span data-stu-id="2c0d9-157">Remove-AzureStorageShareStoredAccessPolicy</span></span>
- <span data-ttu-id="2c0d9-158">Remove-AzureStorageTableStoredAccessPolicy</span><span class="sxs-lookup"><span data-stu-id="2c0d9-158">Remove-AzureStorageTableStoredAccessPolicy</span></span>

<span data-ttu-id="2c0d9-159">**StreamAnalytics**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-159">**StreamAnalytics**</span></span>
- <span data-ttu-id="2c0d9-160">Remove-AzureRmStreamAnalyticsFunction</span><span class="sxs-lookup"><span data-stu-id="2c0d9-160">Remove-AzureRmStreamAnalyticsFunction</span></span>
- <span data-ttu-id="2c0d9-161">Remove-AzureRmStreamAnalyticsInput</span><span class="sxs-lookup"><span data-stu-id="2c0d9-161">Remove-AzureRmStreamAnalyticsInput</span></span>
- <span data-ttu-id="2c0d9-162">Remove-AzureRmStreamAnalyticsJob</span><span class="sxs-lookup"><span data-stu-id="2c0d9-162">Remove-AzureRmStreamAnalyticsJob</span></span>
- <span data-ttu-id="2c0d9-163">Remove-AzureRmStreamAnalyticsOutput</span><span class="sxs-lookup"><span data-stu-id="2c0d9-163">Remove-AzureRmStreamAnalyticsOutput</span></span>

<span data-ttu-id="2c0d9-164">**Tag**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-164">**Tag**</span></span>
- <span data-ttu-id="2c0d9-165">Remove-AzureRmTag</span><span class="sxs-lookup"><span data-stu-id="2c0d9-165">Remove-AzureRmTag</span></span>

<br>

<span data-ttu-id="2c0d9-166">Si tiene un script que utiliza cualquiera de los cmdlets anteriores, el cambio se puede corregir quitando el parámetro `Force`.</span><span class="sxs-lookup"><span data-stu-id="2c0d9-166">If you have a script that uses any of the above cmdlets, the breaking change can be fixed by simply removing the `Force` parameter.</span></span>

```powershell
# Old
New-AzureRmResourceGroup -Name $resourceGroupName -Location $location -Force

# New
New-AzureRmResourceGroup -Name $resourceGroupName -Location $location
```

<br>

## <a name="change-of-tag-parameters"></a><span data-ttu-id="2c0d9-167">Cambio de los parámetros Tag</span><span class="sxs-lookup"><span data-stu-id="2c0d9-167">Change of Tag parameters</span></span>

<span data-ttu-id="2c0d9-168">En esta versión, el nombre de parámetro `Tags` se ha cambiado a `Tag` y el tipo se ha cambiado de `Hashtable[]` a `Hashtable`, lo que cambia el formato de los pares clave-valor.</span><span class="sxs-lookup"><span data-stu-id="2c0d9-168">This release, the `Tags` parameter name was changed to `Tag`, and the type was changed from `Hashtable[]` to `Hashtable`, changing the format of the key-value pairings.</span></span>

<span data-ttu-id="2c0d9-169">Anteriormente, cada entrada de `Hashtable[]` representaba un par de clave-valor individual:</span><span class="sxs-lookup"><span data-stu-id="2c0d9-169">Previously, each entry in the `Hashtable[]` represented a single key-value pairing:</span></span>

```powershell
$tags = @{ Name = "test1"; Value = "testval1" }, @{ Name = "test2", Value = "testval2" }
$tags[0].Name  # Key for the first entry, "test1"
$tags[0].Value # Value for the first entry, "testval1"
$tags[1].Name  # Key for the second entry, "test2"
$tags[1].Value # Value for the second entry, "testval2"
```

<span data-ttu-id="2c0d9-170">Ahora, `Name` y `Value` ya no son necesarios, lo que permite crear pares clave-valor mediante la asignación de `Key = "Value"` en `Hashtable`:</span><span class="sxs-lookup"><span data-stu-id="2c0d9-170">Now, `Name` and `Value` are no longer necessary, allowing for key-value pairings to be created by assigning `Key = "Value"` in the `Hashtable`:</span></span>

```powershell
$tag = @{ test1 = "testval1"; test2 = "testval2" }
$tag["test1"] # Gets the value associated with the key "test1"
$tag["test2"] # Gets the value associated with the key "test2"
```

<span data-ttu-id="2c0d9-171">Este cambio afecta a los siguientes cmdlets:</span><span class="sxs-lookup"><span data-stu-id="2c0d9-171">The following cmdlets are affected by this change:</span></span>

<span data-ttu-id="2c0d9-172">**Batch**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-172">**Batch**</span></span>
- <span data-ttu-id="2c0d9-173">Get-AzureRmBatchAccount</span><span class="sxs-lookup"><span data-stu-id="2c0d9-173">Get-AzureRmBatchAccount</span></span>
- <span data-ttu-id="2c0d9-174">New-AzureRmBatchAccount</span><span class="sxs-lookup"><span data-stu-id="2c0d9-174">New-AzureRmBatchAccount</span></span>
- <span data-ttu-id="2c0d9-175">Set-AzureRmBatchAccount</span><span class="sxs-lookup"><span data-stu-id="2c0d9-175">Set-AzureRmBatchAccount</span></span>

<span data-ttu-id="2c0d9-176">**Proceso**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-176">**Compute**</span></span>
- <span data-ttu-id="2c0d9-177">New-AzureRmVM</span><span class="sxs-lookup"><span data-stu-id="2c0d9-177">New-AzureRmVM</span></span>
- <span data-ttu-id="2c0d9-178">Update-AzureRmVM</span><span class="sxs-lookup"><span data-stu-id="2c0d9-178">Update-AzureRmVM</span></span>

<span data-ttu-id="2c0d9-179">**DataLakeAnalytics**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-179">**DataLakeAnalytics**</span></span>
- <span data-ttu-id="2c0d9-180">New-AzureRmDataLakeAnalyticsAccount</span><span class="sxs-lookup"><span data-stu-id="2c0d9-180">New-AzureRmDataLakeAnalyticsAccount</span></span>
- <span data-ttu-id="2c0d9-181">Set-AzureRmDataLakeAnalyticsAccount</span><span class="sxs-lookup"><span data-stu-id="2c0d9-181">Set-AzureRmDataLakeAnalyticsAccount</span></span>

<span data-ttu-id="2c0d9-182">**DataLakeStore**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-182">**DataLakeStore**</span></span>
- <span data-ttu-id="2c0d9-183">New-AzureRmDataLakeStoreAccount</span><span class="sxs-lookup"><span data-stu-id="2c0d9-183">New-AzureRmDataLakeStoreAccount</span></span>
- <span data-ttu-id="2c0d9-184">Set-AzureRmDataLakeStoreAccount</span><span class="sxs-lookup"><span data-stu-id="2c0d9-184">Set-AzureRmDataLakeStoreAccount</span></span>

<span data-ttu-id="2c0d9-185">**Dns**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-185">**Dns**</span></span>
- <span data-ttu-id="2c0d9-186">New-AzureRmDnsZone</span><span class="sxs-lookup"><span data-stu-id="2c0d9-186">New-AzureRmDnsZone</span></span>
- <span data-ttu-id="2c0d9-187">Set-AzureRmDnsZone</span><span class="sxs-lookup"><span data-stu-id="2c0d9-187">Set-AzureRmDnsZone</span></span>

<span data-ttu-id="2c0d9-188">**KeyVault**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-188">**KeyVault**</span></span>
- <span data-ttu-id="2c0d9-189">Get-AzureRmKeyVault</span><span class="sxs-lookup"><span data-stu-id="2c0d9-189">Get-AzureRmKeyVault</span></span>
- <span data-ttu-id="2c0d9-190">New-AzureRmKeyVault</span><span class="sxs-lookup"><span data-stu-id="2c0d9-190">New-AzureRmKeyVault</span></span>

<span data-ttu-id="2c0d9-191">**Red**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-191">**Network**</span></span>
- <span data-ttu-id="2c0d9-192">New-AzureRmApplicationGateway</span><span class="sxs-lookup"><span data-stu-id="2c0d9-192">New-AzureRmApplicationGateway</span></span>
- <span data-ttu-id="2c0d9-193">New-AzureRmExpressRouteCircuit</span><span class="sxs-lookup"><span data-stu-id="2c0d9-193">New-AzureRmExpressRouteCircuit</span></span>
- <span data-ttu-id="2c0d9-194">New-AzureRmLoadBalancer</span><span class="sxs-lookup"><span data-stu-id="2c0d9-194">New-AzureRmLoadBalancer</span></span>
- <span data-ttu-id="2c0d9-195">New-AzureRmLocalNetworkGateway</span><span class="sxs-lookup"><span data-stu-id="2c0d9-195">New-AzureRmLocalNetworkGateway</span></span>
- <span data-ttu-id="2c0d9-196">New-AzureRmNetworkInterface</span><span class="sxs-lookup"><span data-stu-id="2c0d9-196">New-AzureRmNetworkInterface</span></span>
- <span data-ttu-id="2c0d9-197">New-AzureRmNetworkSecurityGroup</span><span class="sxs-lookup"><span data-stu-id="2c0d9-197">New-AzureRmNetworkSecurityGroup</span></span>
- <span data-ttu-id="2c0d9-198">New-AzureRmPublicIpAddress</span><span class="sxs-lookup"><span data-stu-id="2c0d9-198">New-AzureRmPublicIpAddress</span></span>
- <span data-ttu-id="2c0d9-199">New-AzureRmRouteTable</span><span class="sxs-lookup"><span data-stu-id="2c0d9-199">New-AzureRmRouteTable</span></span>
- <span data-ttu-id="2c0d9-200">New-AzureRmVirtualNetwork</span><span class="sxs-lookup"><span data-stu-id="2c0d9-200">New-AzureRmVirtualNetwork</span></span>
- <span data-ttu-id="2c0d9-201">New-AzureRmVirtualNetworkGateway</span><span class="sxs-lookup"><span data-stu-id="2c0d9-201">New-AzureRmVirtualNetworkGateway</span></span>
- <span data-ttu-id="2c0d9-202">New-AzureRmVirtualNetworkGatewayConnection</span><span class="sxs-lookup"><span data-stu-id="2c0d9-202">New-AzureRmVirtualNetworkGatewayConnection</span></span>
- <span data-ttu-id="2c0d9-203">New-AzureRmVirtualNetworkPeering</span><span class="sxs-lookup"><span data-stu-id="2c0d9-203">New-AzureRmVirtualNetworkPeering</span></span>

<span data-ttu-id="2c0d9-204">**Recursos**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-204">**Resources**</span></span>
- <span data-ttu-id="2c0d9-205">Find-AzureRmResource</span><span class="sxs-lookup"><span data-stu-id="2c0d9-205">Find-AzureRmResource</span></span>
- <span data-ttu-id="2c0d9-206">Find-AzureRmResourceGroup</span><span class="sxs-lookup"><span data-stu-id="2c0d9-206">Find-AzureRmResourceGroup</span></span>
- <span data-ttu-id="2c0d9-207">New-AzureRmResource</span><span class="sxs-lookup"><span data-stu-id="2c0d9-207">New-AzureRmResource</span></span>
- <span data-ttu-id="2c0d9-208">New-AzureRmResourceGroup</span><span class="sxs-lookup"><span data-stu-id="2c0d9-208">New-AzureRmResourceGroup</span></span>
- <span data-ttu-id="2c0d9-209">Set-AzureRmResource</span><span class="sxs-lookup"><span data-stu-id="2c0d9-209">Set-AzureRmResource</span></span>
- <span data-ttu-id="2c0d9-210">Set-AzureRmResourceGroup</span><span class="sxs-lookup"><span data-stu-id="2c0d9-210">Set-AzureRmResourceGroup</span></span>

<span data-ttu-id="2c0d9-211">**SQL**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-211">**SQL**</span></span>
- <span data-ttu-id="2c0d9-212">New-AzureRmSqlDatabase</span><span class="sxs-lookup"><span data-stu-id="2c0d9-212">New-AzureRmSqlDatabase</span></span>
- <span data-ttu-id="2c0d9-213">New-AzureRmSqlDatabaseCopy</span><span class="sxs-lookup"><span data-stu-id="2c0d9-213">New-AzureRmSqlDatabaseCopy</span></span>
- <span data-ttu-id="2c0d9-214">New-AzureRmSqlDatabaseSecondary</span><span class="sxs-lookup"><span data-stu-id="2c0d9-214">New-AzureRmSqlDatabaseSecondary</span></span>
- <span data-ttu-id="2c0d9-215">New-AzureRmSqlElasticPool</span><span class="sxs-lookup"><span data-stu-id="2c0d9-215">New-AzureRmSqlElasticPool</span></span>
- <span data-ttu-id="2c0d9-216">New-AzureRmSqlServer</span><span class="sxs-lookup"><span data-stu-id="2c0d9-216">New-AzureRmSqlServer</span></span>
- <span data-ttu-id="2c0d9-217">Set-AzureRmSqlDatabase</span><span class="sxs-lookup"><span data-stu-id="2c0d9-217">Set-AzureRmSqlDatabase</span></span>
- <span data-ttu-id="2c0d9-218">Set-AzureRmSqlElasticPool</span><span class="sxs-lookup"><span data-stu-id="2c0d9-218">Set-AzureRmSqlElasticPool</span></span>
- <span data-ttu-id="2c0d9-219">Set-AzureRmSqlServer</span><span class="sxs-lookup"><span data-stu-id="2c0d9-219">Set-AzureRmSqlServer</span></span>

<span data-ttu-id="2c0d9-220">**Storage**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-220">**Storage**</span></span>
- <span data-ttu-id="2c0d9-221">New-AzureRmStorageAccount</span><span class="sxs-lookup"><span data-stu-id="2c0d9-221">New-AzureRmStorageAccount</span></span>
- <span data-ttu-id="2c0d9-222">Set-AzureRmStorageAccount</span><span class="sxs-lookup"><span data-stu-id="2c0d9-222">Set-AzureRmStorageAccount</span></span>

<span data-ttu-id="2c0d9-223">**TrafficManager**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-223">**TrafficManager**</span></span>
- <span data-ttu-id="2c0d9-224">New-AzureRmTrafficManagerProfile</span><span class="sxs-lookup"><span data-stu-id="2c0d9-224">New-AzureRmTrafficManagerProfile</span></span>

<br>

<span data-ttu-id="2c0d9-225">Si tiene un script que utiliza cualquiera de los cmdlets anteriores, el cambio se puede corregir cambiando el parámetro `Tags` a `Tag`, así como cambiando `Tag` al formato nuevo.</span><span class="sxs-lookup"><span data-stu-id="2c0d9-225">If you have a script that uses any of the above cmdlets, the breaking change can be fixed by changing the `Tags` parameter to `Tag`, as well as changing the `Tag` to the new format.</span></span>

```powershell
# Old
New-AzureRmResourceGroup -Name $resourceGroupName -Location -location -Tags @{ Name = "testtag"; Value = "testval" }

# New
New-AzureRmResourceGroup -Name $resourceGroupName -Location -location -Tag @{ testtag = "testval" }
```

<br>

## <a name="breaking-changes-to-storage-cmdlets"></a><span data-ttu-id="2c0d9-226">Cambios sustanciales en los cmdlets de Storage</span><span class="sxs-lookup"><span data-stu-id="2c0d9-226">Breaking changes to Storage cmdlets</span></span>

<span data-ttu-id="2c0d9-227">Los siguientes cmdlets han resultado afectados en esta versión:</span><span class="sxs-lookup"><span data-stu-id="2c0d9-227">The following cmdlets were affected this release:</span></span>

<span data-ttu-id="2c0d9-228">**Get-AzureRmStorageAccountKey**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-228">**Get-AzureRmStorageAccountKey**</span></span>
- <span data-ttu-id="2c0d9-229">Ahora, el cmdlet devuelve una lista de claves, en lugar de un objeto con propiedades para cada clave</span><span class="sxs-lookup"><span data-stu-id="2c0d9-229">The cmdlet now returns a list of keys, rather than an object with properties for each key</span></span>

```powershell
# Old
$key = (Get-AzureRmStorageAccountKey -ResourceGroupName $resourceGroupName -Name $accountName).Key1

# New
$key = (Get-AzureRmStorageAccountKey -ResourceGroupName $resourceGroupName -Name $accountName)[0].Value
```

<span data-ttu-id="2c0d9-230">**New-AzureRmStorageAccountKey**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-230">**New-AzureRmStorageAccountKey**</span></span>
- <span data-ttu-id="2c0d9-231">El nombre del campo `StorageAccountRegenerateKeyResponse` del resultado de este cmdlet cambia a `StorageAccountListKeysResults`, que ahora es una lista de claves, en lugar de un objeto con propiedades para cada clave</span><span class="sxs-lookup"><span data-stu-id="2c0d9-231">`StorageAccountRegenerateKeyResponse` field in output of this cmdlet is renamed to `StorageAccountListKeysResults`, which is now a list of keys rather than an object with properties for each key</span></span>

```powershell
# Old
$key = (New-AzureRmStorageAccountKey -ResourceGroupName $resourceGroupName -Name $accountName).StorageAccountKeys.Key1

# New
$key = (New-AzureRmStorageAccountKey -ResourceGroupName $resourceGroupName -Name $accountName).Keys[0].Value
```

<span data-ttu-id="2c0d9-232">**New/Get/Set-AzureRmStorageAccount**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-232">**New/Get/Set-AzureRmStorageAccount**</span></span>
- <span data-ttu-id="2c0d9-233">El nombre del campo `AccountType` del resultado de este cmdlet cambia a `Sku.Name`</span><span class="sxs-lookup"><span data-stu-id="2c0d9-233">`AccountType` field in output of this cmdlet is renamed to `Sku.Name`</span></span>
- <span data-ttu-id="2c0d9-234">El tipo de salida del blob, tabla, cola, archivo de PrimaryEndpoints y SecondaryEndpoints ha cambiado de `Uri` a `String`</span><span class="sxs-lookup"><span data-stu-id="2c0d9-234">Output type for PrimaryEndpoints/Secondary endpoints blob/table/queue/file changed from `Uri` to `String`</span></span>

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

## <a name="breaking-changes-to-ad-cmdlets"></a><span data-ttu-id="2c0d9-235">Cambios sustanciales en los cmdlets de AD</span><span class="sxs-lookup"><span data-stu-id="2c0d9-235">Breaking changes to AD cmdlets</span></span>

<span data-ttu-id="2c0d9-236">Los siguientes cmdlets han resultado afectados en esta versión:</span><span class="sxs-lookup"><span data-stu-id="2c0d9-236">The following cmdlets were affected this release:</span></span>

<span data-ttu-id="2c0d9-237">**Get-AzureRMADServicePrincipal**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-237">**Get-AzureRMADServicePrincipal**</span></span>
- <span data-ttu-id="2c0d9-238">El nombre del campo `ServicePrincipalName` del resultado de este cmdlet cambia a `ServicePrincipalNames` y ahora es una colección.</span><span class="sxs-lookup"><span data-stu-id="2c0d9-238">`ServicePrincipalName` field in output of this cmdlet is renamed to `ServicePrincipalNames` and is now a collection.</span></span> <span data-ttu-id="2c0d9-239">Ahora muestra `ApplicationId` también como uno de los SPN, junto con identifierUri.</span><span class="sxs-lookup"><span data-stu-id="2c0d9-239">It now displays `ApplicationId` also as one of the SPN, along with the identifierUri.</span></span>

```powershell
# Old
$servicePrincipals = Get-AzureRmADServicePrincipal -SearchString $displayName
$spn = $servicePrincipals[0].ServicePrincipalName

# New
$servicePrincipals = Get-AzureRmADServicePrincipal -SearchString $displayName
$spn = $servicePrincipals[0].ServicePrincipalNames[0]
```

<span data-ttu-id="2c0d9-240">**Get-AzureRmADApplication**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-240">**Get-AzureRmADApplication**</span></span>
- <span data-ttu-id="2c0d9-241">El nombre del parámetro `ApplicationObjectId` ha cambiado a `ObjectId`.</span><span class="sxs-lookup"><span data-stu-id="2c0d9-241">Parameter `ApplicationObjectId` is renamed to `ObjectId`.</span></span>
- <span data-ttu-id="2c0d9-242">En la salida de este cdmlet, el nombre de `ApplicationObjectId` se cambia a `ObjectId`.</span><span class="sxs-lookup"><span data-stu-id="2c0d9-242">In output of this cmdlet, `ApplicationObjectId` is renamed to `ObjectId`.</span></span>

```powershell
# Old
$app = Get-AzureRmADApplication -ApplicationObjectId $applicationObjectId
$objectId = $app.ApplicationObjectId

# New
$app = Get-AzureRmADApplication -ObjectId $objectId
$objectId = $app.ObjectId
```

<span data-ttu-id="2c0d9-243">**Remove-AzureRmADApplication**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-243">**Remove-AzureRmADApplication**</span></span>
- <span data-ttu-id="2c0d9-244">El nombre del parámetro `ApplicationObjectId` ha cambiado a `ObjectId`.</span><span class="sxs-lookup"><span data-stu-id="2c0d9-244">Parameter `ApplicationObjectId` is renamed to `ObjectId`.</span></span>

```powershell
# Old
$app = Remove-AzureRmADApplication -ApplicationObjectId $applicationObjectId -Force

# New
$app = Remove-AzureRmADApplication -ObjectId $objectId -Force
```

<span data-ttu-id="2c0d9-245">**New-AzureRmADApplication**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-245">**New-AzureRmADApplication**</span></span>
- <span data-ttu-id="2c0d9-246">En la salida de este cdmlet, el nombre de `ApplicationObjectId` se cambia a `ObjectId`.</span><span class="sxs-lookup"><span data-stu-id="2c0d9-246">In output of this cmdlet, `ApplicationObjectId` is renamed to `ObjectId`.</span></span>
- <span data-ttu-id="2c0d9-247">Se quitan los parámetros `KeyValue`, `KeyUsage`, `KeyType`.</span><span class="sxs-lookup"><span data-stu-id="2c0d9-247">`KeyValue`, `KeyUsage`, `KeyType` parameters are removed.</span></span>

```powershell
# Old
$app = New-AzureRmADApplication -DisplayName $displayName -HomePage $homePage -IdentifierUris $identifierUris -KeyValue $kv -KeyType $kt -KeyUsage $ku
$id = $app.ApplicationObjectId

# New
$app = New-AzureRmADApplication -DisplayName $displayName -HomePage $homePage -IdentifierUris $identifierUris
$id = $app.ObjectId
New-AzureRmADAppCredential -ObjectId $id -Password $kv
```

<span data-ttu-id="2c0d9-248">**Get-AzureRmADGroup**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-248">**Get-AzureRmADGroup**</span></span>
- <span data-ttu-id="2c0d9-249">El campo `Mail` se ha quitado de la salida.</span><span class="sxs-lookup"><span data-stu-id="2c0d9-249">`Mail` field is removed from the output.</span></span>

<span data-ttu-id="2c0d9-250">**Get-AzureRmADUser**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-250">**Get-AzureRmADUser**</span></span>
- <span data-ttu-id="2c0d9-251">El campo `Mail` se ha quitado de la salida.</span><span class="sxs-lookup"><span data-stu-id="2c0d9-251">`Mail` field is removed from the output.</span></span>

<span data-ttu-id="2c0d9-252">**New-AzureRmADServicePrincipal**</span><span class="sxs-lookup"><span data-stu-id="2c0d9-252">**New-AzureRmADServicePrincipal**</span></span>
- <span data-ttu-id="2c0d9-253">El parámetro `DisableAccount` se ha eliminado.</span><span class="sxs-lookup"><span data-stu-id="2c0d9-253">Removed `DisableAccount` parameter.</span></span>

```powershell
# Old
$servicePrincipal = New-AzureRmADServicePrincipal -DisplayName $displayName -Password $password -DisableAccount true

# New
$servicePrincipal = New-AzureRmADServicePrincipal -DisplayName $displayName -Password $password
Remove-AzureRmADServicePrincipal -ObjectId $servicePrincipal.ObjectId
```