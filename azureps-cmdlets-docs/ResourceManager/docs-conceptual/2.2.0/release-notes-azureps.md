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
ms.openlocfilehash: 143d92384fd270711378f6741ba59e88c12833d1
ms.sourcegitcommit: 226527be7cb647acfe2ea9ab151185053ab3c6db
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2017
---
# <span data-ttu-id="49eba-103">Notas de la versión</span><span class="sxs-lookup"><span data-stu-id="49eba-103">Release notes</span></span>
<a id="release-notes" class="xliff"></a>

<span data-ttu-id="49eba-104">Esta es una lista de los cambios realizados en esta versión de Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="49eba-104">This is a list of changes made to Azure PowerShell in this release.</span></span>

## <span data-ttu-id="49eba-105">Versión 2.2.0</span><span class="sxs-lookup"><span data-stu-id="49eba-105">Version 2.2.0</span></span>
<a id="version-220" class="xliff"></a>
* <span data-ttu-id="49eba-106">Proceso</span><span class="sxs-lookup"><span data-stu-id="49eba-106">Compute</span></span>
  - <span data-ttu-id="49eba-107">Incorporación de compatibilidad con la consulta del estado de cifrado desde la extensión de AzureDiskEncryptionForLinux</span><span class="sxs-lookup"><span data-stu-id="49eba-107">Add support for querying encryption status from the AzureDiskEncryptionForLinux extension</span></span>
* <span data-ttu-id="49eba-108">DataFactory</span><span class="sxs-lookup"><span data-stu-id="49eba-108">DataFactory</span></span>
  - <span data-ttu-id="49eba-109">Incorporación de un nuevo cmdlet para enumerar las ventanas de la actividad</span><span class="sxs-lookup"><span data-stu-id="49eba-109">Added new cmdlet for listing activity windows</span></span>
    + <span data-ttu-id="49eba-110">Get-AzureRmDataFactoryActivityWindow</span><span class="sxs-lookup"><span data-stu-id="49eba-110">Get-AzureRmDataFactoryActivityWindow</span></span>
* <span data-ttu-id="49eba-111">DataLake</span><span class="sxs-lookup"><span data-stu-id="49eba-111">DataLake</span></span>
  - <span data-ttu-id="49eba-112">Cambio del parámetro `Host` a `DatabaseHost` e incorporación de un alias para `Host`</span><span class="sxs-lookup"><span data-stu-id="49eba-112">Changed parameter `Host` to `DatabaseHost` and added alias to `Host`</span></span>
    + <span data-ttu-id="49eba-113">New-AzureRmDataLakeAnalyticsCatalogSecret</span><span class="sxs-lookup"><span data-stu-id="49eba-113">New-AzureRmDataLakeAnalyticsCatalogSecret</span></span>
    + <span data-ttu-id="49eba-114">Set-AzureRmDataLakeAnalyticsCatalogSecret</span><span class="sxs-lookup"><span data-stu-id="49eba-114">Set-AzureRmDataLakeAnalyticsCatalogSecret</span></span>
  - <span data-ttu-id="49eba-115">Incorporación de compatibilidad con ACL y eliminación de la ACL predeterminada</span><span class="sxs-lookup"><span data-stu-id="49eba-115">Add support for ACL and Default ACL removal</span></span>
  - <span data-ttu-id="49eba-116">Incorporación de compatibilidad con la obtención y la configuración de permisos sin nombre para archivos y carpetas</span><span class="sxs-lookup"><span data-stu-id="49eba-116">Add support for getting and setting unnamed permissions on files and folders</span></span>
* <span data-ttu-id="49eba-117">KeyVault</span><span class="sxs-lookup"><span data-stu-id="49eba-117">KeyVault</span></span>
  - <span data-ttu-id="49eba-118">Incorporación de compatibilidad con certificados</span><span class="sxs-lookup"><span data-stu-id="49eba-118">Add support for certificates</span></span>
    + <span data-ttu-id="49eba-119">Add-AzureKeyVaultCertificate</span><span class="sxs-lookup"><span data-stu-id="49eba-119">Add-AzureKeyVaultCertificate</span></span>
    + <span data-ttu-id="49eba-120">Add-AzureKeyVaultCertificateContact</span><span class="sxs-lookup"><span data-stu-id="49eba-120">Add-AzureKeyVaultCertificateContact</span></span>
    + <span data-ttu-id="49eba-121">Get-AzureKeyVaultCertificate</span><span class="sxs-lookup"><span data-stu-id="49eba-121">Get-AzureKeyVaultCertificate</span></span>
    + <span data-ttu-id="49eba-122">Get-AzureKeyVaultCertificateContact</span><span class="sxs-lookup"><span data-stu-id="49eba-122">Get-AzureKeyVaultCertificateContact</span></span>
    + <span data-ttu-id="49eba-123">Get-AzureKeyVaultCertificateIssuer</span><span class="sxs-lookup"><span data-stu-id="49eba-123">Get-AzureKeyVaultCertificateIssuer</span></span>
    + <span data-ttu-id="49eba-124">Get-AzureKeyVaultCertificateOperation</span><span class="sxs-lookup"><span data-stu-id="49eba-124">Get-AzureKeyVaultCertificateOperation</span></span>
    + <span data-ttu-id="49eba-125">Get-AzureKeyVaultCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="49eba-125">Get-AzureKeyVaultCertificatePolicy</span></span>
    + <span data-ttu-id="49eba-126">Import-AzureKeyVaultCertificate</span><span class="sxs-lookup"><span data-stu-id="49eba-126">Import-AzureKeyVaultCertificate</span></span>
    + <span data-ttu-id="49eba-127">New-AzureKeyVaultCertificateAdministratorDetails</span><span class="sxs-lookup"><span data-stu-id="49eba-127">New-AzureKeyVaultCertificateAdministratorDetails</span></span>
    + <span data-ttu-id="49eba-128">New-AzureKeyVaultCertificateOrganizationDetails</span><span class="sxs-lookup"><span data-stu-id="49eba-128">New-AzureKeyVaultCertificateOrganizationDetails</span></span>
    + <span data-ttu-id="49eba-129">New-AzureKeyVaultCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="49eba-129">New-AzureKeyVaultCertificatePolicy</span></span>
    + <span data-ttu-id="49eba-130">Remove-AzureKeyVaultCertificate</span><span class="sxs-lookup"><span data-stu-id="49eba-130">Remove-AzureKeyVaultCertificate</span></span>
    + <span data-ttu-id="49eba-131">Remove-AzureKeyVaultCertificateContact</span><span class="sxs-lookup"><span data-stu-id="49eba-131">Remove-AzureKeyVaultCertificateContact</span></span>
    + <span data-ttu-id="49eba-132">Remove-AzureKeyVaultCertificateIssuer</span><span class="sxs-lookup"><span data-stu-id="49eba-132">Remove-AzureKeyVaultCertificateIssuer</span></span>
    + <span data-ttu-id="49eba-133">Remove-AzureKeyVaultCertificateOperation</span><span class="sxs-lookup"><span data-stu-id="49eba-133">Remove-AzureKeyVaultCertificateOperation</span></span>
    + <span data-ttu-id="49eba-134">Set-AzureKeyVaultCertificateAttribute</span><span class="sxs-lookup"><span data-stu-id="49eba-134">Set-AzureKeyVaultCertificateAttribute</span></span>
    + <span data-ttu-id="49eba-135">Set-AzureKeyVaultCertificateIssuer</span><span class="sxs-lookup"><span data-stu-id="49eba-135">Set-AzureKeyVaultCertificateIssuer</span></span>
    + <span data-ttu-id="49eba-136">Set-AzureKeyVaultCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="49eba-136">Set-AzureKeyVaultCertificatePolicy</span></span>
    + <span data-ttu-id="49eba-137">Stop-AzureKeyVaultCertificateOperation</span><span class="sxs-lookup"><span data-stu-id="49eba-137">Stop-AzureKeyVaultCertificateOperation</span></span>
* <span data-ttu-id="49eba-138">Red</span><span class="sxs-lookup"><span data-stu-id="49eba-138">Network</span></span>

  - <span data-ttu-id="49eba-139">Incorporación de un nuevo parámetro modificador +New-AzureRmNetworkInterface -EnableAcceleratedNetworking para que la interfaz de red habilite o deshabilite las redes aceleradas.</span><span class="sxs-lookup"><span data-stu-id="49eba-139">New switch parameter added for network interface to enable/disable accelerated networking +New-AzureRmNetworkInterface -EnableAcceleratedNetworking</span></span>
  - <span data-ttu-id="49eba-140">Habilitación de los cmdlets de PowerShell de característica de puerta de enlace Active-Active</span><span class="sxs-lookup"><span data-stu-id="49eba-140">Enable Active-Active gateway feature PowerShell cmdlets</span></span>
    + <span data-ttu-id="49eba-141">Add-AzureRmVirtualNetworkGatewayIpConfig</span><span class="sxs-lookup"><span data-stu-id="49eba-141">Add-AzureRmVirtualNetworkGatewayIpConfig</span></span>
    + <span data-ttu-id="49eba-142">Remove-AzureRmVirtualNetworkGatewayIpConfig</span><span class="sxs-lookup"><span data-stu-id="49eba-142">Remove-AzureRmVirtualNetworkGatewayIpConfig</span></span>
  - <span data-ttu-id="49eba-143">Incorporación de un cmdlet nuevo</span><span class="sxs-lookup"><span data-stu-id="49eba-143">Added new cmdlet</span></span>
    + <span data-ttu-id="49eba-144">Test-AzureRmPrivateIpAddressAvailability</span><span class="sxs-lookup"><span data-stu-id="49eba-144">Test-AzureRmPrivateIpAddressAvailability</span></span>
* <span data-ttu-id="49eba-145">Recursos</span><span class="sxs-lookup"><span data-stu-id="49eba-145">Resources</span></span>
  - <span data-ttu-id="49eba-146">Zonas de compatibilidad en los cmdlets de proveedor y recurso</span><span class="sxs-lookup"><span data-stu-id="49eba-146">Support zones in provider and resource cmdlets</span></span>
    + <span data-ttu-id="49eba-147">Get-AzureRmProvider</span><span class="sxs-lookup"><span data-stu-id="49eba-147">Get-AzureRmProvider</span></span>
    + <span data-ttu-id="49eba-148">New-AzureRmResource</span><span class="sxs-lookup"><span data-stu-id="49eba-148">New-AzureRmResource</span></span>
    + <span data-ttu-id="49eba-149">Set-AzureRmResource</span><span class="sxs-lookup"><span data-stu-id="49eba-149">Set-AzureRmResource</span></span>
* <span data-ttu-id="49eba-150">Sql</span><span class="sxs-lookup"><span data-stu-id="49eba-150">Sql</span></span>
  - <span data-ttu-id="49eba-151">Incorporación de cmdlets nuevos para la administración de directivas de detección de amenazas de Azure SQL en el nivel de servidor</span><span class="sxs-lookup"><span data-stu-id="49eba-151">Added new cmdlets for Azure SQL threat detection policy management at server level</span></span>
    + <span data-ttu-id="49eba-152">Get-AzureRmSqlServerThreatDetectionPolicy</span><span class="sxs-lookup"><span data-stu-id="49eba-152">Get-AzureRmSqlServerThreatDetectionPolicy</span></span>
    + <span data-ttu-id="49eba-153">Remove-AzureRmSqlServerThreatDetectionPolicy</span><span class="sxs-lookup"><span data-stu-id="49eba-153">Remove-AzureRmSqlServerThreatDetectionPolicy</span></span>
    + <span data-ttu-id="49eba-154">Set-AzureRmSqlServerThreatDetectionPolicy</span><span class="sxs-lookup"><span data-stu-id="49eba-154">Set-AzureRmSqlServerThreatDetectionPolicy</span></span>
  - <span data-ttu-id="49eba-155">Incorporación de cmdlets nuevos para permitir la compatibilidad con la habilitación o la deshabilitación de GeoBackupPolicy para los almacenes de datos de SQL Azure</span><span class="sxs-lookup"><span data-stu-id="49eba-155">Added new cmdlets to support enabling/disabling GeoBackupPolicy for Sql Azure DataWarehouses</span></span>
    + <span data-ttu-id="49eba-156">Get-AzureRmSqlDatabaseGeoBackupPolicy</span><span class="sxs-lookup"><span data-stu-id="49eba-156">Get-AzureRmSqlDatabaseGeoBackupPolicy</span></span>
    + <span data-ttu-id="49eba-157">Set-AzureRmSqlDatabaseGeoBackupPolicy</span><span class="sxs-lookup"><span data-stu-id="49eba-157">Set-AzureRmSqlDatabaseGeoBackupPolicy</span></span>
  - <span data-ttu-id="49eba-158">Incorporación de cmdlets nuevos para Azure Sql Advisors y API de acciones recomendadas</span><span class="sxs-lookup"><span data-stu-id="49eba-158">Added new cmdlets for Azure Sql Advisors and Recommended Actions APIs</span></span>
    + <span data-ttu-id="49eba-159">Get-AzureRmSqlDatabaseAdvisor</span><span class="sxs-lookup"><span data-stu-id="49eba-159">Get-AzureRmSqlDatabaseAdvisor</span></span>
    + <span data-ttu-id="49eba-160">Get-AzureRmSqlElasticPoolAdvisor</span><span class="sxs-lookup"><span data-stu-id="49eba-160">Get-AzureRmSqlElasticPoolAdvisor</span></span>
    + <span data-ttu-id="49eba-161">Get-AzureRmSqlServerAdvisor</span><span class="sxs-lookup"><span data-stu-id="49eba-161">Get-AzureRmSqlServerAdvisor</span></span>
    + <span data-ttu-id="49eba-162">Get-AzureRmSqlDatabaseRecommendedActions</span><span class="sxs-lookup"><span data-stu-id="49eba-162">Get-AzureRmSqlDatabaseRecommendedActions</span></span>
    + <span data-ttu-id="49eba-163">Get-AzureRmSqlElasticPoolRecommendedActions</span><span class="sxs-lookup"><span data-stu-id="49eba-163">Get-AzureRmSqlElasticPoolRecommendedActions</span></span>
    + <span data-ttu-id="49eba-164">Get-AzureRmSqlServerRecommendedActions</span><span class="sxs-lookup"><span data-stu-id="49eba-164">Get-AzureRmSqlServerRecommendedActions</span></span>
    + <span data-ttu-id="49eba-165">Set-AzureRmSqlDatabaseAdvisorAutoExecuteStatus</span><span class="sxs-lookup"><span data-stu-id="49eba-165">Set-AzureRmSqlDatabaseAdvisorAutoExecuteStatus</span></span>
    + <span data-ttu-id="49eba-166">Set-AzureRmSqlElasticPoolAdvisorAutoExecuteStatus</span><span class="sxs-lookup"><span data-stu-id="49eba-166">Set-AzureRmSqlElasticPoolAdvisorAutoExecuteStatus</span></span>
    + <span data-ttu-id="49eba-167">Set-AzureRmSqlServerAdvisorAutoExecuteStatus</span><span class="sxs-lookup"><span data-stu-id="49eba-167">Set-AzureRmSqlServerAdvisorAutoExecuteStatus</span></span>
    + <span data-ttu-id="49eba-168">Set-AzureRmSqlDatabaseRecommendedActionState</span><span class="sxs-lookup"><span data-stu-id="49eba-168">Set-AzureRmSqlDatabaseRecommendedActionState</span></span>
    + <span data-ttu-id="49eba-169">Set-AzureRmSqlElasticPoolRecommendedActionState</span><span class="sxs-lookup"><span data-stu-id="49eba-169">Set-AzureRmSqlElasticPoolRecommendedActionState</span></span>
    + <span data-ttu-id="49eba-170">Set-AzureRmSqlServerRecommendedActionState</span><span class="sxs-lookup"><span data-stu-id="49eba-170">Set-AzureRmSqlServerRecommendedActionState</span></span>
