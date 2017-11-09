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
# <a name="release-notes"></a>Notas de la versión

Esta es una lista de los cambios realizados en esta versión de Azure PowerShell.

## <a name="version-380"></a>Versión 3.8.0
* Proceso
  - Corrección del error de los cmdlets Get-* para permitir la recuperación de varias páginas de datos (más de 120 elementos)
* DataLakeAnalytics
  - Corrección de la ayuda para que algunos comandos tengan la sintaxis y los ejemplos apropiados.
* DataLakeStore
  - Incorporación de compatibilidad de encabezado y cola para el cmdlet `Get-AzureRMDataLakeStoreItemContent`. Esto permite mostrar las filas delimitadas de N líneas nuevas al principio o al final que se devuelven.
* HDInsight
  - Incorporación de compatibilidad con el tipo de clúster RServer
    + Se puede especificar el tamaño de máquina virtual del nodo perimetral para el clúster RServer en New-AzureRmHDInsightCluster o New-AzureRmHDInsightClusterConfig
    + RServer es ahora una opción de configuración en Add-AzureRmHDInsightConfigValues. Permite la configuración de la etiqueta RStudio para indicar que se debe realizar la instalación de R Studio.
* LogicApp
  - Se ha corregido el problema de contentlink de los cmdlets Set-AzureRmIntegrationAccountSchema y Set-AzureRmIntegrationAccountMap (la configuración de content y contentlink derivaba en un error de actualización).
* Red
  - Incorporación de compatibilidad con nuevas características de firewall de aplicación web en puertas de enlace de aplicaciones
    + Incorporación de New-AzureRmApplicationGatewayFirewallDisabledRuleGroupConfig
    + Incorporación de Get-AzureRmApplicationGatewayAvailableWafRuleSets (alias: List-AzureRmApplicationGatewayAvailableWafRuleSets)
    + Actualización de New-AzureRmApplicationGatewayWebApplicationFirewallConfiguration: incorporación de los parámetros -RuleSetType, -RuleSetVersion y -DisabledRuleGroups
    + Actualización de Set-AzureRmApplicationGatewayWebApplicationFirewallConfiguration: incorporación de los parámetros -RuleSetType, -RuleSetVersion y -DisabledRuleGroups
  - Incorporación de compatibilidad con las directivas de IPSec en las conexiones de puerta de enlace de red virtual
  - Incorporación de New-AzureRmIpsecPolicy
  - Actualización de New-AzureRmVirtualNetworkGatewayConnection: incorporación de los parámetros -IpsecPolicies y -UsePolicyBasedTrafficSelectors
* Perfil
  - *Obsoleto*: se ha cambiado el nombre de Save-AzureRmProfile a Save-AzureRmContext, hay un alias al antiguo nombre del cmdlet, que se eliminará en la siguiente versión.
  - *Obsoleto*: se ha cambiado el nombre de Select-AzureRmProfile a Import-AzureRmContext, hay un alias al antiguo nombre del cmdlet, que se eliminará en la siguiente versión.
  - Los tipos de salida PSAzureContext PSAzureProfile de cmdlets de perfil se cambiarán en la siguiente versión.
  - El cmdlet Save-AzureRmContext no tendrá OutputType en la siguiente versión.
  - Corrección de errores en el código común del cmdlet para utilizar el algoritmo compatible con FIPS para los hash de datos: https://github.com/Azure/azure-powershell/issues/3651
* Sql
  - Correcciones de errores en los cmdlets del grupo de conmutación por error de Azure
  - Corrección para sondeo de operaciones
  - Corrección del valor de GracePeriodWithDataLossHour al establecer FailoverPolicy en Manual
* TrafficManager
  - Compatibilidad con el método de enrutamiento del tráfico geográfico
    + Nuevo valor de "Geographic" para el parámetro TrafficRoutingMethod de New-AzureRmTrafficManagerProfile
    + Nuevo parámetro "GeoMapping" para New-AzureRmTrafficManagerEndpoint y Add-AzureRmTrafficManagerEndpointConfig
    + Corrección de la canalización para Get-AzureRmTrafficManagerProfile cuando devuelve una colección de perfiles
* ServiceManagement
  - Restart-AzureVM: incorporación del parámetro InitiateMaintenance para realizar el mantenimiento durante el reinicio de la máquina virtual.
  - Get-AzureVM: incorporación del campo Maintenance Status.
  - Incorporación de nuevos cmdlets para admitir la actualización del almacén de Recovery Services
    + Test-AzureRecoveryServicesVaultUpgrade
    + Invoke-AzureRecoveryServicesVaultUpgrade
