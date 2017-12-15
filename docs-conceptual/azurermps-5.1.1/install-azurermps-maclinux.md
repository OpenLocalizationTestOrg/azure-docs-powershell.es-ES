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
ms.date: 09/06/2017
ms.openlocfilehash: 94b39c18acaca7a4b17b5207feed025442665acc
ms.sourcegitcommit: c42c7176276ec4e1cc3360a93e6b15d32083bf9f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2017
---
# <a name="install-and-configure-azure-powershell-on-macos-and-linux"></a>Instalación y configuración de Azure PowerShell en macOS y Linux

Ahora es posible instalar PowerShell 6 (beta) y Azure PowerShell en plataformas que no sean Windows.
El proceso de instalación de Azure PowerShell en macOS y Linux no es tan diferente al de Windows, sin embargo, primero se debe instalar PowerShell 6 (beta).

> [!NOTE]

> En este momento, tanto PowerShell 6 como Azure PowerShell para .NET Core están en versión beta.
> La compatibilidad con estos productos es limitada. Si tiene problemas o detecta errores, regístrelos en GitHub.
>
> * [Problemas de PowerShell 6 (beta)](https://github.com/PowerShell/PowerShell/issues)
> * [Problemas de Azure PowerShell](https://github.com/azure/azure-docs-powershell/issues)

## <a name="step-1-install-powershell-6-beta"></a>Paso 1: Instalación de PowerShell 6 (beta)

El proceso de instalación de PowerShell 6 (beta) varía según el sistema operativo de destino.
Aunque es posible instalar PowerShell 6 (beta) en Windows, este artículo se centra en macOS y Linux. Si quiere usar Azure PowerShell en Windows, consulte el artículo de [instalación](./install-azurerm-ps.md) para Windows.

Para instalar **PowerShell 6** (beta) en Linux o macOS, necesita:

1. Obtener PowerShell para el sistema operativo y la versión específicos, en [GitHub](https://github.com/powershell/powershell#get-powershell)
2. Seguir las instrucciones de instalación
   - [Linux](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md)
   - [macOS](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#macos-1012)

## <a name="step-2-install-azure-powershell-for-net-core"></a>Paso 2: Instalación de Azure PowerShell para .NET Core

PowerShell 6 (beta) viene con el módulo PowerShellGet ya instalado. Esto facilita la instalación de cualquier módulo que se publica en la Galería de PowerShell. Para instalar Azure PowerShell, abra una nueva sesión de PowerShell y ejecute el siguiente comando:

```powershell
Install-Module AzureRM.NetCore
```

## <a name="step-3-load-the-azurermnetcore-module"></a>Paso 3: Carga del módulo AzureRM.Netcore

Una vez que se instala, debe cargarse en la sesión de PowerShell. Los módulos se cargan mediante el cmdlet, `Import-Module` como se indica a continuación:

```powershell
Import-Module AzureRM.Netcore
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
