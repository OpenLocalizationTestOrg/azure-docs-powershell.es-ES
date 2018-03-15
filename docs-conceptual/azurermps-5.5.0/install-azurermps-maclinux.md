---
title: "Instalación y configuración de Azure PowerShell en macOS y Linux | Microsoft Docs"
description: "Instalación y configuración de Azure PowerShell para usarlo por primera vez en macOS y Linux."
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 01/12/2018
ms.openlocfilehash: 64a86dfd4af7f3f0a91501e9a096ff190f7100cb
ms.sourcegitcommit: 5fe9a579d2e0d1cb5a05aadaeba5db784f1b18fa
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/28/2018
---
# <a name="install-and-configure-azure-powershell-on-macos-and-linux"></a>Instalación y configuración de Azure PowerShell en macOS y Linux

Ya se pueden instalar PowerShell Core v6 y Azure PowerShell en plataformas distintas de Windows.
El proceso de instalación de Azure PowerShell en macOS y Linux no es tan distinto del de Windows; sin embargo, primero hay que instalar PowerShell Core v6.

> [!NOTE]

> Actualmente, tanto PowerShell 6 como Azure PowerShell para .NET Core están en versión beta.
> La compatibilidad con estos productos es limitada. Si tiene problemas o detecta errores, regístrelos en GitHub.
>
> * [Problemas de PowerShell Core v6](https://github.com/PowerShell/PowerShell/issues)
> * [Problemas de Azure PowerShell](https://github.com/azure/azure-docs-powershell/issues)

## <a name="step-1-install-powershell-core-v6"></a>Paso 1: Instalación de PowerShell Core v6

El proceso de instalación de PowerShell Core v6 varía en función del sistema operativo de destino.
Aunque PowerShell Core v6 se puede instalar en Windows, este artículo se centra en macOS y Linux. Si quiere usar Azure PowerShell en Windows, consulte el artículo de [instalación](./install-azurerm-ps.md) para Windows.

La instalación de **PowerShell Core v6** en Linux o macOS varía en función de la distribución de Linux y de la versión del sistema operativo.
En el siguiente artículo encontrará instrucciones detalladas para su instalación:

- [Instalación de PowerShell Core en macOS y Linux](/powershell/scripting/setup/installing-powershell-core-on-macos-and-linux)

## <a name="step-2-install-azure-powershell-for-net-core"></a>Paso 2: Instalación de Azure PowerShell para .NET Core

PowerShell Core v6 viene con el módulo PowerShellGet ya instalado. Esto facilita la instalación de cualquier módulo que se publica en la Galería de PowerShell. Para instalar Azure PowerShell, abra una nueva sesión de PowerShell y ejecute el siguiente comando:

```powershell
Install-Module AzureRM.NetCore
```

## <a name="step-3-load-the-azurermnetcore-module"></a>Paso 3: Carga del módulo AzureRM.Netcore

Una vez que se instala, debe cargarse en la sesión de PowerShell. Los módulos se cargan mediante el cmdlet, `Import-Module` como se indica a continuación:

```powershell
Import-Module AzureRM.Netcore
Import-Module AzureRM.Profile.Netcore
```

Cuando finalice la importación, puede probar su módulo recién instalado; para ello, intente iniciar sesión en Azure mediante el comando siguiente:

```powershell
Login-AzureRMAccount
```

El comando anterior debe solicitarle que vaya a `https://aka.ms/devicelogin` y escriba el código proporcionado.

## <a name="available-cmdlets"></a>Cmdlets disponibles

Los módulos de Azure PowerShell para .NET Standard se encuentran aún en desarrollo. Estos módulos no proporcionan el conjunto completo de cmdlets que están disponibles para la versión de Windows de los módulos. Las siguientes funciones se implementan en los módulos de AzureRM.Netcore:

* Administración de cuentas
  - Inicie sesión con la cuenta de Microsoft, la cuenta organizativa o la entidad de servicio mediante Microsoft Azure Active Directory.
  - Guarde las credenciales en el disco con Save-AzureRmContext y cargue las credenciales guardadas mediante Import-AzureRmContext.
* Environment
  - Obtenga los diferentes entornos de Microsoft Azure de uso inmediato.
  - Agregue, defina o quite entornos personalizados (como los entornos Azure Stack o Windows Azure Pack)
* Cmdlets del plano de administración para servicios de Azure que usan las interfaces de Resource Manager y Service Management.
  - Máquina virtual
  - App Service (Websites)
  - SQL Database
  - Storage
  - Red

## <a name="next-steps"></a>Pasos siguientes

Para más información sobre el uso de Azure PowerShell, consulte el artículo [Introducción a Azure PowerShell](get-started-azureps.md).
