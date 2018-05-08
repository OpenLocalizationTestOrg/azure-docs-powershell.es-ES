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
ms.date: 05/18/2017
ms.openlocfilehash: 04f89e8d47d0825d46cb1b8817efbcc0cafa0acd
ms.sourcegitcommit: b256bf48e15ee98865de0fae50e7b81878b03a54
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/03/2017
---
# <a name="release-notes"></a><span data-ttu-id="a3bd4-103">Notas de la versión</span><span class="sxs-lookup"><span data-stu-id="a3bd4-103">Release notes</span></span>

<span data-ttu-id="a3bd4-104">Esta es una lista de los cambios realizados en esta versión de Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a3bd4-104">This is a list of changes made to Azure PowerShell in this release.</span></span>

## <a name="version-380"></a><span data-ttu-id="a3bd4-105">Versión 3.8.0</span><span class="sxs-lookup"><span data-stu-id="a3bd4-105">Version 3.8.0</span></span>
* <span data-ttu-id="a3bd4-106">Proceso</span><span class="sxs-lookup"><span data-stu-id="a3bd4-106">Compute</span></span>
  - <span data-ttu-id="a3bd4-107">Corrección del error de los cmdlets Get-* para permitir la recuperación de varias páginas de datos (más de 120 elementos)</span><span class="sxs-lookup"><span data-stu-id="a3bd4-107">Fix bug in Get-* cmdlets, to allow retrieving multiple pages of data (more than 120 items)</span></span>
* <span data-ttu-id="a3bd4-108">DataLakeAnalytics</span><span class="sxs-lookup"><span data-stu-id="a3bd4-108">DataLakeAnalytics</span></span>
  - <span data-ttu-id="a3bd4-109">Corrección de la ayuda para que algunos comandos tengan la sintaxis y los ejemplos apropiados.</span><span class="sxs-lookup"><span data-stu-id="a3bd4-109">Fix help for some commands to have the proper verbage and examples.</span></span>
* <span data-ttu-id="a3bd4-110">DataLakeStore</span><span class="sxs-lookup"><span data-stu-id="a3bd4-110">DataLakeStore</span></span>
  - <span data-ttu-id="a3bd4-111">Incorporación de compatibilidad de encabezado y cola para el cmdlet `Get-AzureRMDataLakeStoreItemContent`.</span><span class="sxs-lookup"><span data-stu-id="a3bd4-111">Add support for head and tail to the `Get-AzureRMDataLakeStoreItemContent` cmdlet.</span></span> <span data-ttu-id="a3bd4-112">Esto permite mostrar las filas delimitadas de N líneas nuevas al principio o al final que se devuelven.</span><span class="sxs-lookup"><span data-stu-id="a3bd4-112">This enables returning the top N or last N new line delimited rows to be displayed.</span></span>
* <span data-ttu-id="a3bd4-113">HDInsight</span><span class="sxs-lookup"><span data-stu-id="a3bd4-113">HDInsight</span></span>
  - <span data-ttu-id="a3bd4-114">Incorporación de compatibilidad con el tipo de clúster RServer</span><span class="sxs-lookup"><span data-stu-id="a3bd4-114">Added support for RServer cluster type</span></span>
    + <span data-ttu-id="a3bd4-115">Se puede especificar el tamaño de máquina virtual del nodo perimetral para el clúster RServer en New-AzureRmHDInsightCluster o New-AzureRmHDInsightClusterConfig</span><span class="sxs-lookup"><span data-stu-id="a3bd4-115">Edgenode VM size can be specified for RServer cluster in New-AzureRmHDInsightCluster or New-AzureRmHDInsightClusterConfig</span></span>
    + <span data-ttu-id="a3bd4-116">RServer es ahora una opción de configuración en Add-AzureRmHDInsightConfigValues.</span><span class="sxs-lookup"><span data-stu-id="a3bd4-116">RServer is now a configuration option in Add-AzureRmHDInsightConfigValues.</span></span> <span data-ttu-id="a3bd4-117">Permite la configuración de la etiqueta RStudio para indicar que se debe realizar la instalación de R Studio.</span><span class="sxs-lookup"><span data-stu-id="a3bd4-117">It allows for RStudio flag to be set to indicate that R Studio installation should be done.</span></span>
* <span data-ttu-id="a3bd4-118">LogicApp</span><span class="sxs-lookup"><span data-stu-id="a3bd4-118">LogicApp</span></span>
  - <span data-ttu-id="a3bd4-119">Se ha corregido el problema de contentlink de los cmdlets Set-AzureRmIntegrationAccountSchema y Set-AzureRmIntegrationAccountMap (la configuración de content y contentlink derivaba en un error de actualización).</span><span class="sxs-lookup"><span data-stu-id="a3bd4-119">Set-AzureRmIntegrationAccountSchema and Set-AzureRmIntegrationAccountMap cmdlets are fixed for the contentlink issue(Both content and contentlink were set resulting in update failure).</span></span>
* <span data-ttu-id="a3bd4-120">Red</span><span class="sxs-lookup"><span data-stu-id="a3bd4-120">Network</span></span>
  - <span data-ttu-id="a3bd4-121">Incorporación de compatibilidad con nuevas características de firewall de aplicación web en puertas de enlace de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="a3bd4-121">Added support for new web application firewall features to Application Gateways</span></span>
    + <span data-ttu-id="a3bd4-122">Incorporación de New-AzureRmApplicationGatewayFirewallDisabledRuleGroupConfig</span><span class="sxs-lookup"><span data-stu-id="a3bd4-122">Added New-AzureRmApplicationGatewayFirewallDisabledRuleGroupConfig</span></span>
    + <span data-ttu-id="a3bd4-123">Incorporación de Get-AzureRmApplicationGatewayAvailableWafRuleSets (alias: List-AzureRmApplicationGatewayAvailableWafRuleSets)</span><span class="sxs-lookup"><span data-stu-id="a3bd4-123">Added Get-AzureRmApplicationGatewayAvailableWafRuleSets (Alias: List-AzureRmApplicationGatewayAvailableWafRuleSets)</span></span>
    + <span data-ttu-id="a3bd4-124">Actualización de New-AzureRmApplicationGatewayWebApplicationFirewallConfiguration: incorporación de los parámetros -RuleSetType, -RuleSetVersion y -DisabledRuleGroups</span><span class="sxs-lookup"><span data-stu-id="a3bd4-124">Updated New-AzureRmApplicationGatewayWebApplicationFirewallConfiguration: Added parameter -RuleSetType -RuleSetVersion and -DisabledRuleGroups</span></span>
    + <span data-ttu-id="a3bd4-125">Actualización de Set-AzureRmApplicationGatewayWebApplicationFirewallConfiguration: incorporación de los parámetros -RuleSetType, -RuleSetVersion y -DisabledRuleGroups</span><span class="sxs-lookup"><span data-stu-id="a3bd4-125">Updated Set-AzureRmApplicationGatewayWebApplicationFirewallConfiguration: Added parameter -RuleSetType -RuleSetVersion and -DisabledRuleGroups</span></span>
  - <span data-ttu-id="a3bd4-126">Incorporación de compatibilidad con las directivas de IPSec en las conexiones de puerta de enlace de red virtual</span><span class="sxs-lookup"><span data-stu-id="a3bd4-126">Added support for IPSec policies to Virtual Network Gateway Connections</span></span>
  - <span data-ttu-id="a3bd4-127">Incorporación de New-AzureRmIpsecPolicy</span><span class="sxs-lookup"><span data-stu-id="a3bd4-127">Added New-AzureRmIpsecPolicy</span></span>
  - <span data-ttu-id="a3bd4-128">Actualización de New-AzureRmVirtualNetworkGatewayConnection: incorporación de los parámetros -IpsecPolicies y -UsePolicyBasedTrafficSelectors</span><span class="sxs-lookup"><span data-stu-id="a3bd4-128">Updated New-AzureRmVirtualNetworkGatewayConnection: Added parameter -IpsecPolicies and -UsePolicyBasedTrafficSelectors</span></span>
* <span data-ttu-id="a3bd4-129">Perfil</span><span class="sxs-lookup"><span data-stu-id="a3bd4-129">Profile</span></span>
  - <span data-ttu-id="a3bd4-130">*Obsoleto*: se ha cambiado el nombre de Save-AzureRmProfile a Save-AzureRmContext, hay un alias al antiguo nombre del cmdlet, que se eliminará en la siguiente versión.</span><span class="sxs-lookup"><span data-stu-id="a3bd4-130">*Obsolete*: Save-AzureRmProfile is renamed to Save-AzureRmContext, there is an alias to the old cmdlet name, the alias will be removed in the next release.</span></span>
  - <span data-ttu-id="a3bd4-131">*Obsoleto*: se ha cambiado el nombre de Select-AzureRmProfile a Import-AzureRmContext, hay un alias al antiguo nombre del cmdlet, que se eliminará en la siguiente versión.</span><span class="sxs-lookup"><span data-stu-id="a3bd4-131">*Obsolete*: Select-AzureRmProfile is renamed to Import-AzureRmContext, there is an alias to the old cmdlet name, the alias will be removed in the next release.</span></span>
  - <span data-ttu-id="a3bd4-132">Los tipos de salida PSAzureContext PSAzureProfile de cmdlets de perfil se cambiarán en la siguiente versión.</span><span class="sxs-lookup"><span data-stu-id="a3bd4-132">The PSAzureContext and PSAzureProfile output types of profile cmdlets will be changed in the next release.</span></span>
  - <span data-ttu-id="a3bd4-133">El cmdlet Save-AzureRmContext no tendrá OutputType en la siguiente versión.</span><span class="sxs-lookup"><span data-stu-id="a3bd4-133">The Save-AzureRmContext cmdlet will have no OutputType in the next release.</span></span>
  - <span data-ttu-id="a3bd4-134">Corrección de errores en el código común del cmdlet para utilizar el algoritmo compatible con FIPS para los hash de datos: https://github.com/Azure/azure-powershell/issues/3651</span><span class="sxs-lookup"><span data-stu-id="a3bd4-134">Fix bug in cmdlet common code to use FIPS-compliant algorithm for data hashes: https://github.com/Azure/azure-powershell/issues/3651</span></span>
* <span data-ttu-id="a3bd4-135">Sql</span><span class="sxs-lookup"><span data-stu-id="a3bd4-135">Sql</span></span>
  - <span data-ttu-id="a3bd4-136">Correcciones de errores en los cmdlets del grupo de conmutación por error de Azure</span><span class="sxs-lookup"><span data-stu-id="a3bd4-136">Bug fixes on Azure Failover Group Cmdlets</span></span>
  - <span data-ttu-id="a3bd4-137">Corrección para sondeo de operaciones</span><span class="sxs-lookup"><span data-stu-id="a3bd4-137">Fix for operation polling</span></span>
  - <span data-ttu-id="a3bd4-138">Corrección del valor de GracePeriodWithDataLossHour al establecer FailoverPolicy en Manual</span><span class="sxs-lookup"><span data-stu-id="a3bd4-138">Fix GracePeriodWithDataLossHour value when setting FailoverPolicy to Manual</span></span>
* <span data-ttu-id="a3bd4-139">TrafficManager</span><span class="sxs-lookup"><span data-stu-id="a3bd4-139">TrafficManager</span></span>
  - <span data-ttu-id="a3bd4-140">Compatibilidad con el método de enrutamiento del tráfico geográfico</span><span class="sxs-lookup"><span data-stu-id="a3bd4-140">Support for the Geographic traffic routing method</span></span>
    + <span data-ttu-id="a3bd4-141">Nuevo valor de "Geographic" para el parámetro TrafficRoutingMethod de New-AzureRmTrafficManagerProfile</span><span class="sxs-lookup"><span data-stu-id="a3bd4-141">New value 'Geographic' for the TrafficRoutingMethod parameter of New-AzureRmTrafficManagerProfile</span></span>
    + <span data-ttu-id="a3bd4-142">Nuevo parámetro "GeoMapping" para New-AzureRmTrafficManagerEndpoint y Add-AzureRmTrafficManagerEndpointConfig</span><span class="sxs-lookup"><span data-stu-id="a3bd4-142">New parameter 'GeoMapping' for the New-AzureRmTrafficManagerEndpoint and Add-AzureRmTrafficManagerEndpointConfig</span></span>
    + <span data-ttu-id="a3bd4-143">Corrección de la canalización para Get-AzureRmTrafficManagerProfile cuando devuelve una colección de perfiles</span><span class="sxs-lookup"><span data-stu-id="a3bd4-143">Fix piping for Get-AzureRmTrafficManagerProfile when it returns a collection of profiles</span></span>
* <span data-ttu-id="a3bd4-144">ServiceManagement</span><span class="sxs-lookup"><span data-stu-id="a3bd4-144">ServiceManagement</span></span>
  - <span data-ttu-id="a3bd4-145">Restart-AzureVM: incorporación del parámetro InitiateMaintenance para realizar el mantenimiento durante el reinicio de la máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="a3bd4-145">Restart-AzureVM: Added InitiateMaintenance parameter for performing maintenance during VM restart.</span></span>
  - <span data-ttu-id="a3bd4-146">Get-AzureVM: incorporación del campo Maintenance Status.</span><span class="sxs-lookup"><span data-stu-id="a3bd4-146">Get-AzureVM: Added Maintenance Status field.</span></span>
  - <span data-ttu-id="a3bd4-147">Incorporación de nuevos cmdlets para admitir la actualización del almacén de Recovery Services</span><span class="sxs-lookup"><span data-stu-id="a3bd4-147">Added new cmdlets to support Recovery Services vault upgrade</span></span>
    + <span data-ttu-id="a3bd4-148">Test-AzureRecoveryServicesVaultUpgrade</span><span class="sxs-lookup"><span data-stu-id="a3bd4-148">Test-AzureRecoveryServicesVaultUpgrade</span></span>
    + <span data-ttu-id="a3bd4-149">Invoke-AzureRecoveryServicesVaultUpgrade</span><span class="sxs-lookup"><span data-stu-id="a3bd4-149">Invoke-AzureRecoveryServicesVaultUpgrade</span></span>
