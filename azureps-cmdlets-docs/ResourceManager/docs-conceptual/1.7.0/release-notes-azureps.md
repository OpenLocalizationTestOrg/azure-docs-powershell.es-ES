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
ms.openlocfilehash: 0a3f152751fee569d3ac5fba6bcff8c1737f7b8c
ms.sourcegitcommit: 226527be7cb647acfe2ea9ab151185053ab3c6db
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2017
---
# <span data-ttu-id="2d641-103">Notas de la versión</span><span class="sxs-lookup"><span data-stu-id="2d641-103">Release notes</span></span>
<a id="release-notes" class="xliff"></a>

<span data-ttu-id="2d641-104">Esta es una lista de los cambios realizados en esta versión de Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2d641-104">This is a list of changes made to Azure PowerShell in this release.</span></span>

## <span data-ttu-id="2d641-105">Versión 1.7.0</span><span class="sxs-lookup"><span data-stu-id="2d641-105">Version 1.7.0</span></span>
<a id="version-170" class="xliff"></a>

* <span data-ttu-id="2d641-106">**Cambio de comportamiento de los parámetros -Force, –Confirm y $ConfirmPreference en todos los cmdlets. Esta implementación se cambia para ir en línea con las directrices de PowerShell. Para la mayoría de cmdlets, esto significa la eliminación del parámetro Force y la omisión del mensaje ShouldProcess; los usuarios tendrán que incluir el parámetro "-Confirm:$false" en los scripts de PowerShell.**</span><span class="sxs-lookup"><span data-stu-id="2d641-106">**Behavioral change for -Force, –Confirm and $ConfirmPreference parameters for all cmdlets. We are changing this implementation to be in line with PowerShell guidelines. For most cmdlets, this means removing the Force parameter and to skip the ShouldProcess prompt, users will need to include the parameter: ‘-Confirm:$false’ in their PowerShell scripts.**</span></span> <span data-ttu-id="2d641-107">Este cambio soluciona los siguientes problemas:</span><span class="sxs-lookup"><span data-stu-id="2d641-107">This changes are addressing following issues:</span></span>
  - <span data-ttu-id="2d641-108">Implementación correcta de la funcionalidad –WhatIf, que permite a un usuario determinar los efectos de un script o cmdlet sin tener que realizar ningún cambio real</span><span class="sxs-lookup"><span data-stu-id="2d641-108">Correct implementation of –WhatIf functionality, allowing a user to determine the effects of a cmdlet or script without making any actual changes</span></span>
  - <span data-ttu-id="2d641-109">Control sobre los mensajes mediante un parámetro $ConfirmPreference de sesión, de manera que se pregunta al usuario en función del efecto de un posible cambio (según se indica en la configuración de ConfirmImpact en el cmdlet)</span><span class="sxs-lookup"><span data-stu-id="2d641-109">Control over prompting using a session-wide $ConfirmPreference, so that the user is prompted based on the impact of a prospective change (as reported in the ConfirmImpact setting in the cmdlet)</span></span>
  - <span data-ttu-id="2d641-110">Control de cmdlet específico sobre los mensajes de confirmación con el parámetro –Confirm</span><span class="sxs-lookup"><span data-stu-id="2d641-110">Cmdlet-specific control over confirmation prompts using the –Confirm parameter</span></span>
  - <span data-ttu-id="2d641-111">Uso coherente de ShouldContinue y el parámetro –Force en los cmdlets, solo para aquellas acciones que requieran preguntar al usuario por la naturaleza especial de los cambios (por ejemplo, la eliminación de archivos ocultos)</span><span class="sxs-lookup"><span data-stu-id="2d641-111">Consistent use of ShouldContinue and the –Force parameter across cmdlets, for only those actions that would require prompting from the user due to the special nature of the changes (for example, deleting hidden files)</span></span>
  - <span data-ttu-id="2d641-112">Coherencia con otros cmdlets de PowerShell, de manera que el conocimiento de scripts de PowerShell de otros cmdlets se aplique inmediatamente a los cmdlets de Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2d641-112">Consistency with other PowerShell cmdlets, so that PowerShell scripting knowledge from other cmdlets is immediately applicable to the Azure PowerShell cmdlets.</span></span>

<span data-ttu-id="2d641-113">**Observe que ahora para *omitir automáticamente todos los mensajes en todas las circunstancias*, los cmdlets de Azure PowerShell requieren que el usuario proporcione dos parámetros:**</span><span class="sxs-lookup"><span data-stu-id="2d641-113">**Notice that now to *automatically skip all Prompts in all Circumstances* Azure PowerShell cmdlets require the user to supply two parameters:**</span></span>
```powershell
My-CmdletWithConfirmation –Confirm:$false -Force
```
* <span data-ttu-id="2d641-114">Azure Compute</span><span class="sxs-lookup"><span data-stu-id="2d641-114">Azure Compute</span></span>
  - <span data-ttu-id="2d641-115">Set-AzureRmVMADDomainExtension</span><span class="sxs-lookup"><span data-stu-id="2d641-115">Set-AzureRmVMADDomainExtension</span></span>
  - <span data-ttu-id="2d641-116">Get-AzureRmVMADDomainExtension</span><span class="sxs-lookup"><span data-stu-id="2d641-116">Get-AzureRmVMADDomainExtension</span></span>
  - <span data-ttu-id="2d641-117">Parámetro -Redeploy para Restart-AzureVM</span><span class="sxs-lookup"><span data-stu-id="2d641-117">-Redeploy parameter for Restart-AzureVM</span></span>
  - <span data-ttu-id="2d641-118">Parámetro -Validate para Move-AzureService, Move-AzureStorageAccount y Move-AzureVirtualNetwork</span><span class="sxs-lookup"><span data-stu-id="2d641-118">-Validate parameter for Move-AzureService, Move-AzureStorageAccount, and Move-AzureVirtualNetwork</span></span>
  - <span data-ttu-id="2d641-119">Los parámetros de nombre y versión para los cmdlets de extensión son opcionales, como antes.</span><span class="sxs-lookup"><span data-stu-id="2d641-119">Name and version parameters for extension cmdlets are optional as before.</span></span>
  - <span data-ttu-id="2d641-120">New-AzureVM puede obtener un tipo de licencia de objeto de máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="2d641-120">New-AzureVM can get a license type from VM object.</span></span>
* <span data-ttu-id="2d641-121">Almacenamiento de Azure</span><span class="sxs-lookup"><span data-stu-id="2d641-121">Azure Storage</span></span>
  - <span data-ttu-id="2d641-122">Cambio del parámetro Tags a Tag e incorporación del alias de parámetro Tags</span><span class="sxs-lookup"><span data-stu-id="2d641-122">Change Tags Parameter to Tag, and add parameter alias Tags</span></span>
    + <span data-ttu-id="2d641-123">New-AzureRmStorageAccount</span><span class="sxs-lookup"><span data-stu-id="2d641-123">New-AzureRmStorageAccount</span></span>
    + <span data-ttu-id="2d641-124">Set-AzureRmStorageAccount</span><span class="sxs-lookup"><span data-stu-id="2d641-124">Set-AzureRmStorageAccount</span></span>
* <span data-ttu-id="2d641-125">Red de Azure</span><span class="sxs-lookup"><span data-stu-id="2d641-125">Azure Network</span></span>
  - <span data-ttu-id="2d641-126">Incorporación de un nuevo cmdlet para el emparejamiento de redes virtuales</span><span class="sxs-lookup"><span data-stu-id="2d641-126">New cmdlet added for Virtual Network Peering</span></span>
* <span data-ttu-id="2d641-127">Caché en Redis de Azure</span><span class="sxs-lookup"><span data-stu-id="2d641-127">Azure Redis Cache</span></span>
  - <span data-ttu-id="2d641-128">Incorporación de un nuevo cmdlet para Reset-AzureRmRedisCache</span><span class="sxs-lookup"><span data-stu-id="2d641-128">New cmdlet added for Reset-AzureRmRedisCache</span></span>
  - <span data-ttu-id="2d641-129">Incorporación de un nuevo cmdlet para Export-AzureRmRedisCache</span><span class="sxs-lookup"><span data-stu-id="2d641-129">New cmdlet added for Export-AzureRmRedisCache</span></span>
  - <span data-ttu-id="2d641-130">Incorporación de un nuevo cmdlet para Import-AzureRmRedisCache</span><span class="sxs-lookup"><span data-stu-id="2d641-130">New cmdlet added for Import-AzureRmRedisCache</span></span>
  - <span data-ttu-id="2d641-131">Modificación del cmdlet New-AzureRmRedisCache para incluir el cambio de parámetro para la red virtual</span><span class="sxs-lookup"><span data-stu-id="2d641-131">Modified cmdlet New-AzureRmRedisCache to include parameter change for vNet</span></span>
* <span data-ttu-id="2d641-132">Copia de seguridad/restauración de la base de datos de Azure SQL</span><span class="sxs-lookup"><span data-stu-id="2d641-132">Azure SQL DB Backup/Restore</span></span>
  - <span data-ttu-id="2d641-133">Cmdlets para la característica de copia de seguridad LTR (retención a largo plazo)</span><span class="sxs-lookup"><span data-stu-id="2d641-133">Cmdlets for LTR (Long Term Retention) backup feature</span></span>
  - <span data-ttu-id="2d641-134">Get-AzureRmSqlServerBackupLongTermRetentionVault</span><span class="sxs-lookup"><span data-stu-id="2d641-134">Get-AzureRmSqlServerBackupLongTermRetentionVault</span></span>
  - <span data-ttu-id="2d641-135">Get-AzureRmSqlDatabaseBackupLongTermRetentionPolicy</span><span class="sxs-lookup"><span data-stu-id="2d641-135">Get-AzureRmSqlDatabaseBackupLongTermRetentionPolicy</span></span>
  - <span data-ttu-id="2d641-136">Set-AzureRmSqlServerBackupLongTermRetentionVault</span><span class="sxs-lookup"><span data-stu-id="2d641-136">Set-AzureRmSqlServerBackupLongTermRetentionVault</span></span>
  - <span data-ttu-id="2d641-137">Set-AzureRmSqlDatabaseBackupLongTermRetentionPolicy</span><span class="sxs-lookup"><span data-stu-id="2d641-137">Set-AzureRmSqlDatabaseBackupLongTermRetentionPolicy</span></span>
  - <span data-ttu-id="2d641-138">Restore-AzureRmSqlDatabase es ahora compatible con la restauración a un momento dado de una base de datos eliminada</span><span class="sxs-lookup"><span data-stu-id="2d641-138">Restore-AzureRmSqlDatabase now supports point-in-time restore of a deleted database</span></span>
  - <span data-ttu-id="2d641-139">Restore-AzureRmSqlDatabase es ahora compatible con la restauración de una copia de seguridad con retención a largo plazo</span><span class="sxs-lookup"><span data-stu-id="2d641-139">Restore-AzureRmSqlDatabase now supports restoring from a Long Term Retention backup</span></span>
* <span data-ttu-id="2d641-140">Azure LogicApp</span><span class="sxs-lookup"><span data-stu-id="2d641-140">Azure LogicApp</span></span>
  - <span data-ttu-id="2d641-141">Incorporación de cmdlets para las cuentas de integración de LogicApp.</span><span class="sxs-lookup"><span data-stu-id="2d641-141">Added LogicApp Integration accounts cmdlets.</span></span>
  - <span data-ttu-id="2d641-142">Get-AzureRmIntegrationAccountAgreement</span><span class="sxs-lookup"><span data-stu-id="2d641-142">Get-AzureRmIntegrationAccountAgreement</span></span>
  - <span data-ttu-id="2d641-143">Get-AzureRmIntegrationAccountCallbackUrl</span><span class="sxs-lookup"><span data-stu-id="2d641-143">Get-AzureRmIntegrationAccountCallbackUrl</span></span>
  - <span data-ttu-id="2d641-144">Get-AzureRmIntegrationAccountCertificate</span><span class="sxs-lookup"><span data-stu-id="2d641-144">Get-AzureRmIntegrationAccountCertificate</span></span>
  - <span data-ttu-id="2d641-145">Get-AzureRmIntegrationAccount</span><span class="sxs-lookup"><span data-stu-id="2d641-145">Get-AzureRmIntegrationAccount</span></span>
  - <span data-ttu-id="2d641-146">Get-AzureRmIntegrationAccountMap</span><span class="sxs-lookup"><span data-stu-id="2d641-146">Get-AzureRmIntegrationAccountMap</span></span>
  - <span data-ttu-id="2d641-147">Get-AzureRmIntegrationAccountPartner</span><span class="sxs-lookup"><span data-stu-id="2d641-147">Get-AzureRmIntegrationAccountPartner</span></span>
  - <span data-ttu-id="2d641-148">Get-AzureRmIntegrationAccountSchema</span><span class="sxs-lookup"><span data-stu-id="2d641-148">Get-AzureRmIntegrationAccountSchema</span></span>
  - <span data-ttu-id="2d641-149">New-AzureRmIntegrationAccountAgreement</span><span class="sxs-lookup"><span data-stu-id="2d641-149">New-AzureRmIntegrationAccountAgreement</span></span>
  - <span data-ttu-id="2d641-150">New-AzureRmIntegrationAccountCertificate</span><span class="sxs-lookup"><span data-stu-id="2d641-150">New-AzureRmIntegrationAccountCertificate</span></span>
  - <span data-ttu-id="2d641-151">New-AzureRmIntegrationAccount</span><span class="sxs-lookup"><span data-stu-id="2d641-151">New-AzureRmIntegrationAccount</span></span>
  - <span data-ttu-id="2d641-152">New-AzureRmIntegrationAccountMap</span><span class="sxs-lookup"><span data-stu-id="2d641-152">New-AzureRmIntegrationAccountMap</span></span>
  - <span data-ttu-id="2d641-153">New-AzureRmIntegrationAccountPartner</span><span class="sxs-lookup"><span data-stu-id="2d641-153">New-AzureRmIntegrationAccountPartner</span></span>
  - <span data-ttu-id="2d641-154">New-AzureRmIntegrationAccountSchema</span><span class="sxs-lookup"><span data-stu-id="2d641-154">New-AzureRmIntegrationAccountSchema</span></span>
  - <span data-ttu-id="2d641-155">Remove-AzureRmIntegrationAccountAgreement</span><span class="sxs-lookup"><span data-stu-id="2d641-155">Remove-AzureRmIntegrationAccountAgreement</span></span>
  - <span data-ttu-id="2d641-156">Remove-AzureRmIntegrationAccountCertificate</span><span class="sxs-lookup"><span data-stu-id="2d641-156">Remove-AzureRmIntegrationAccountCertificate</span></span>
  - <span data-ttu-id="2d641-157">Remove-AzureRmIntegrationAccount</span><span class="sxs-lookup"><span data-stu-id="2d641-157">Remove-AzureRmIntegrationAccount</span></span>
  - <span data-ttu-id="2d641-158">Remove-AzureRmIntegrationAccountMap</span><span class="sxs-lookup"><span data-stu-id="2d641-158">Remove-AzureRmIntegrationAccountMap</span></span>
  - <span data-ttu-id="2d641-159">Remove-AzureRmIntegrationAccountPartner</span><span class="sxs-lookup"><span data-stu-id="2d641-159">Remove-AzureRmIntegrationAccountPartner</span></span>
  - <span data-ttu-id="2d641-160">Remove-AzureRmIntegrationAccountSchema</span><span class="sxs-lookup"><span data-stu-id="2d641-160">Remove-AzureRmIntegrationAccountSchema</span></span>
  - <span data-ttu-id="2d641-161">Set-AzureRmIntegrationAccountAgreement</span><span class="sxs-lookup"><span data-stu-id="2d641-161">Set-AzureRmIntegrationAccountAgreement</span></span>
  - <span data-ttu-id="2d641-162">Set-AzureRmIntegrationAccountCertificate</span><span class="sxs-lookup"><span data-stu-id="2d641-162">Set-AzureRmIntegrationAccountCertificate</span></span>
  - <span data-ttu-id="2d641-163">Set-AzureRmIntegrationAccount</span><span class="sxs-lookup"><span data-stu-id="2d641-163">Set-AzureRmIntegrationAccount</span></span>
  - <span data-ttu-id="2d641-164">Set-AzureRmIntegrationAccountMap</span><span class="sxs-lookup"><span data-stu-id="2d641-164">Set-AzureRmIntegrationAccountMap</span></span>
  - <span data-ttu-id="2d641-165">Set-AzureRmIntegrationAccountPartner</span><span class="sxs-lookup"><span data-stu-id="2d641-165">Set-AzureRmIntegrationAccountPartner</span></span>
  - <span data-ttu-id="2d641-166">Set-AzureRmIntegrationAccountSchema</span><span class="sxs-lookup"><span data-stu-id="2d641-166">Set-AzureRmIntegrationAccountSchema</span></span>
* <span data-ttu-id="2d641-167">Almacén de Azure Data Lake</span><span class="sxs-lookup"><span data-stu-id="2d641-167">Azure Data Lake Store</span></span>
  - <span data-ttu-id="2d641-168">Mejora considerable del rendimiento de carga y descarga de archivos y carpetas.</span><span class="sxs-lookup"><span data-stu-id="2d641-168">Drastically improve performance of file and folder upload and download.</span></span>
  - <span data-ttu-id="2d641-169">Esto incluye un pequeño cambio en los nombres de parámetro para la descarga y la inclusión de dos nuevos parámetros de carga:</span><span class="sxs-lookup"><span data-stu-id="2d641-169">This includes a slight change to the parameter names for download and inclusion of two new parameters for upload:</span></span>
    + <span data-ttu-id="2d641-170">NumThreads -> PerFileThreadCount, que indica el número de subprocesos para usar en un solo archivo</span><span class="sxs-lookup"><span data-stu-id="2d641-170">NumThreads -> PerFileThreadCount, used to indicate the number of threads to use in a single file</span></span>
    + <span data-ttu-id="2d641-171">ConcurrentFileCount, que indica el número de archivos para cargar o descargar en paralelo con la carga o descarga de carpetas.</span><span class="sxs-lookup"><span data-stu-id="2d641-171">ConcurrentFileCount, used to indicate the number of files to upload/download in parallel for folder upload/download.</span></span>
  - <span data-ttu-id="2d641-172">Los valores predeterminados de subprocesamiento ahora están diseñados para proporcionar un rendimiento mejor e integral para la mayoría de tamaños de archivo.</span><span class="sxs-lookup"><span data-stu-id="2d641-172">Default threading values are now designed to give a better all around throughput for most file sizes.</span></span> <span data-ttu-id="2d641-173">Si el rendimiento no es como lo desea, los valores indicados anteriormente se pueden modificar para adaptarlos.</span><span class="sxs-lookup"><span data-stu-id="2d641-173">If performance is not as desired, the values above can be modified to meet requirements.</span></span>
* <span data-ttu-id="2d641-174">Análisis con Azure Data Lake</span><span class="sxs-lookup"><span data-stu-id="2d641-174">Azure Data Lake Analytics</span></span>
  - <span data-ttu-id="2d641-175">Get-AzureRMDataLakeAnalyticsDataSource ahora devuelve todos los orígenes de datos cuando se realiza una llamada sin argumentos.</span><span class="sxs-lookup"><span data-stu-id="2d641-175">Get-AzureRMDataLakeAnalyticsDataSource now returns all data sources when called with no arguments.</span></span>
  - <span data-ttu-id="2d641-176">Este cambio también elimina el parámetro de tipo de origen de datos del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2d641-176">This change also removes the data source type parameter from the cmdlet.</span></span>
  - <span data-ttu-id="2d641-177">Este cambio produce un nuevo objeto que se devuelve para la operación de lista con las siguientes propiedades:</span><span class="sxs-lookup"><span data-stu-id="2d641-177">This change results in a new object being returned for the list operation with the following properties:</span></span>
    + <span data-ttu-id="2d641-178">Type, tipo del origen de los datos</span><span class="sxs-lookup"><span data-stu-id="2d641-178">Type, the type of data source</span></span>
    + <span data-ttu-id="2d641-179">Name, nombre del origen de los datos</span><span class="sxs-lookup"><span data-stu-id="2d641-179">Name, the name of the data source</span></span>
    + <span data-ttu-id="2d641-180">IsDefault, que se establece en true para el origen de datos predeterminado de la cuenta</span><span class="sxs-lookup"><span data-stu-id="2d641-180">IsDefault, set to true if this is the default data source for the account</span></span>
  - <span data-ttu-id="2d641-181">Corrección de Get-AzureRMDataLakeAnalyticsJob para que se enumeren ciertos valores de desplazamiento de hora de fecha al filtrar por submittedBefore y submittedAfter.</span><span class="sxs-lookup"><span data-stu-id="2d641-181">Get-AzureRMDataLakeAnalyticsJob fixed for list for certain date time offset values when filtering on submittedBefore and submittedAfter.</span></span>
* <span data-ttu-id="2d641-182">Web Apps</span><span class="sxs-lookup"><span data-stu-id="2d641-182">Web Apps</span></span>
  - <span data-ttu-id="2d641-183">Incorporación del cmdlet Swap-AzureRmWebAppSlot para el intercambio normal y el intercambio con vista previa</span><span class="sxs-lookup"><span data-stu-id="2d641-183">Add Swap-AzureRmWebAppSlot cmdlet for regular swap and swap with preview</span></span>
  - <span data-ttu-id="2d641-184">Extensión del cmdlet Set-AzureRmWebAppSlot para admitir el intercambio automático</span><span class="sxs-lookup"><span data-stu-id="2d641-184">Extend Set-AzureRmWebAppSlot cmdlet to support auto swap</span></span>
* <span data-ttu-id="2d641-185">Administración de API de Azure</span><span class="sxs-lookup"><span data-stu-id="2d641-185">Azure API Management</span></span>
  - <span data-ttu-id="2d641-186">Corrección de los cmdlets de implementación de Azure API Management para AzureChinaCloud.</span><span class="sxs-lookup"><span data-stu-id="2d641-186">Fixed Azure Api Management Deployment cmdlets for AzureChinaCloud.</span></span>
  - <span data-ttu-id="2d641-187">Eliminación de la habilitación de manera predeterminada del acceso de Git del cmdlet Set-AzureRmApiManagementTenantGitAccess.</span><span class="sxs-lookup"><span data-stu-id="2d641-187">Removed cmdlet Set-AzureRmApiManagementTenantGitAccess as Git Access is enabled by Default.</span></span>
* <span data-ttu-id="2d641-188">Copia de seguridad de Azure Recovery Services</span><span class="sxs-lookup"><span data-stu-id="2d641-188">Azure Recovery Services Backup</span></span>
  - <span data-ttu-id="2d641-189">Incorporación de compatibilidad con la carga de trabajo de Azure SQL</span><span class="sxs-lookup"><span data-stu-id="2d641-189">Added support for the Azure SQL workload</span></span>
  - <span data-ttu-id="2d641-190">Incorporación de compatibilidad con la copia de seguridad y la restauración de máquinas virtuales de Azure cifradas</span><span class="sxs-lookup"><span data-stu-id="2d641-190">Added support for backing up and restoring encrypted Azure VMs</span></span>
  - <span data-ttu-id="2d641-191">Backup-AzureRmRecoveryServicesBackupItem: incorporación de la característica de tiempo de retención opcional para los puntos de recuperación</span><span class="sxs-lookup"><span data-stu-id="2d641-191">Backup-AzureRmRecoveryServicesBackupItem - Added optional retention time feature for recovery points</span></span>
  - <span data-ttu-id="2d641-192">Correcciones de errores menores de filtrado en los cmdlets Get-AzureRmRecoveryServicesBackupContainer y Get-AzureRmRecoveryServicesBackupItem</span><span class="sxs-lookup"><span data-stu-id="2d641-192">Minor filter-related bug fixes in Get-AzureRmRecoveryServicesBackupContainer and Get-AzureRmRecoveryServicesBackupItem cmdlets</span></span>
* <span data-ttu-id="2d641-193">Automatización de Azure</span><span class="sxs-lookup"><span data-stu-id="2d641-193">Azure Automation</span></span>
  - <span data-ttu-id="2d641-194">Incorporación de Get-AzureRmAutomationHybridWorkerGroup</span><span class="sxs-lookup"><span data-stu-id="2d641-194">Added Get-AzureRmAutomationHybridWorkerGroup</span></span>
