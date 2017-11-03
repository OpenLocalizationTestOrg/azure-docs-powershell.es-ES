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
# <a name="release-notes"></a>Notas de la versión

Esta es una lista de los cambios realizados en esta versión de Azure PowerShell.

## <a name="version-220"></a>Versión 2.2.0
* Proceso
  - Incorporación de compatibilidad con la consulta del estado de cifrado desde la extensión de AzureDiskEncryptionForLinux
* DataFactory
  - Incorporación de un nuevo cmdlet para enumerar las ventanas de la actividad
    + Get-AzureRmDataFactoryActivityWindow
* DataLake
  - Cambio del parámetro `Host` a `DatabaseHost` e incorporación de un alias para `Host`
    + New-AzureRmDataLakeAnalyticsCatalogSecret
    + Set-AzureRmDataLakeAnalyticsCatalogSecret
  - Incorporación de compatibilidad con ACL y eliminación de la ACL predeterminada
  - Incorporación de compatibilidad con la obtención y la configuración de permisos sin nombre para archivos y carpetas
* KeyVault
  - Incorporación de compatibilidad con certificados
    + Add-AzureKeyVaultCertificate
    + Add-AzureKeyVaultCertificateContact
    + Get-AzureKeyVaultCertificate
    + Get-AzureKeyVaultCertificateContact
    + Get-AzureKeyVaultCertificateIssuer
    + Get-AzureKeyVaultCertificateOperation
    + Get-AzureKeyVaultCertificatePolicy
    + Import-AzureKeyVaultCertificate
    + New-AzureKeyVaultCertificateAdministratorDetails
    + New-AzureKeyVaultCertificateOrganizationDetails
    + New-AzureKeyVaultCertificatePolicy
    + Remove-AzureKeyVaultCertificate
    + Remove-AzureKeyVaultCertificateContact
    + Remove-AzureKeyVaultCertificateIssuer
    + Remove-AzureKeyVaultCertificateOperation
    + Set-AzureKeyVaultCertificateAttribute
    + Set-AzureKeyVaultCertificateIssuer
    + Set-AzureKeyVaultCertificatePolicy
    + Stop-AzureKeyVaultCertificateOperation
* Red

  - Incorporación de un nuevo parámetro modificador +New-AzureRmNetworkInterface -EnableAcceleratedNetworking para que la interfaz de red habilite o deshabilite las redes aceleradas.
  - Habilitación de los cmdlets de PowerShell de característica de puerta de enlace Active-Active
    + Add-AzureRmVirtualNetworkGatewayIpConfig
    + Remove-AzureRmVirtualNetworkGatewayIpConfig
  - Incorporación de un cmdlet nuevo
    + Test-AzureRmPrivateIpAddressAvailability
* Recursos
  - Zonas de compatibilidad en los cmdlets de proveedor y recurso
    + Get-AzureRmProvider
    + New-AzureRmResource
    + Set-AzureRmResource
* Sql
  - Incorporación de cmdlets nuevos para la administración de directivas de detección de amenazas de Azure SQL en el nivel de servidor
    + Get-AzureRmSqlServerThreatDetectionPolicy
    + Remove-AzureRmSqlServerThreatDetectionPolicy
    + Set-AzureRmSqlServerThreatDetectionPolicy
  - Incorporación de cmdlets nuevos para permitir la compatibilidad con la habilitación o la deshabilitación de GeoBackupPolicy para los almacenes de datos de SQL Azure
    + Get-AzureRmSqlDatabaseGeoBackupPolicy
    + Set-AzureRmSqlDatabaseGeoBackupPolicy
  - Incorporación de cmdlets nuevos para Azure Sql Advisors y API de acciones recomendadas
    + Get-AzureRmSqlDatabaseAdvisor
    + Get-AzureRmSqlElasticPoolAdvisor
    + Get-AzureRmSqlServerAdvisor
    + Get-AzureRmSqlDatabaseRecommendedActions
    + Get-AzureRmSqlElasticPoolRecommendedActions
    + Get-AzureRmSqlServerRecommendedActions
    + Set-AzureRmSqlDatabaseAdvisorAutoExecuteStatus
    + Set-AzureRmSqlElasticPoolAdvisorAutoExecuteStatus
    + Set-AzureRmSqlServerAdvisorAutoExecuteStatus
    + Set-AzureRmSqlDatabaseRecommendedActionState
    + Set-AzureRmSqlElasticPoolRecommendedActionState
    + Set-AzureRmSqlServerRecommendedActionState
