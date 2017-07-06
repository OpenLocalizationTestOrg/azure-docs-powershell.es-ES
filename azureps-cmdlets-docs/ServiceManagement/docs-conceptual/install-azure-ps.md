---
title: "Instalación y configuración del módulo Service Management de Azure PowerShell | Microsoft Docs"
description: "Instalación y configuración de Azure PowerShell para usarlo por primera vez"
services: azure
author: sdwheeler
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/06/2017
ms.openlocfilehash: c51c727c1cb022eca59f819c7f24d8e058c677da
ms.sourcegitcommit: 226527be7cb647acfe2ea9ab151185053ab3c6db
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2017
---
# <a name="installing-the-azure-powershell-service-management-module"></a>Instalación del módulo Service Management de Azure PowerShell

La instalación de Azure PowerShell desde la [Galería de PowerShell](https://www.powershellgallery.com/) es el método de instalación preferido.

## <a name="step-1-install-powershellget"></a>Paso 1: Instalación de PowerShellGet

La instalación de elementos de la Galería de PowerShell requiere el módulo PowerShellGet. Asegúrese de que tiene la versión adecuada de PowerShellGet y otros requisitos del sistema. Ejecute el siguiente comando para ver si tiene instalado PowerShellGet en el sistema.

```powershell
Get-Module PowerShellGet -list | Select-Object Name,Version,Path
```

Debería ver algo parecido a los siguiente:

```
Name          Version Path
----          ------- ----
PowerShellGet 1.0.0.1 C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PowerShellGet.psd1
```

Si no tiene instalado PowerShellGet, consulte la sección [Cómo obtener PowerShellGet](install-azurerm-ps.md#how-to-get-powershellget).

## <a name="step-2-install-azure-powershell"></a>Paso 2: Instalación de Azure PowerShell

Ejecute el siguiente comando desde la consola de Windows PowerShell como administrador:

```powershell
Install-Module Azure
```

El módulo de Azure es un módulo consolidado para los cmdlets de Azure Resource Manager. Cuando se instala el módulo de AzureRM, los restantes módulos de Azure que no se hayan instalado anteriormente se descargarán de la Galería de PowerShell y se instalarán.

El módulo Azure Service Management comparte dependencias con los módulos de Resource Manager de Azure PowerShell. Si ha instalado los módulos de Resource Manager de Azure PowerShell, será preciso que agregue el parámetro `-AllowClobber` al comando de instalación, ya que ello permite que se actualicen las dependencias compartidas existentes. Sin este parámetro, no se puede realizar la instalación del módulo.

```powershell
Install-Module Azure -AllowClobber
```

Después de instalar el módulo, para importarlo debe ejecutar el siguiente comando:

```powershell
Import-Module Azure
```

## <a name="to-use-the-cmdlets"></a>Uso de los cmdlets

Para empezar a trabajar con los cmdlets de Azure Service Management, antes debe iniciar sesión en su cuenta de Azure. Para ello, ejecute el siguiente comando:

```powershell
Add-AzureAccount
```

Tras iniciar sesión en Azure, Azure PowerShell crea un contexto para la sesión determinada. Dicho contexto contiene el entorno, la cuenta, el inquilino y la suscripción de Azure PowerShell que se utilizarán para todos los cmdlets de dicha sesión. Ya está listo para usar los siguientes módulos.

## <a name="azure-service-management-cmdlets"></a>Cmdlets de Azure Service Management

Los módulos de Azure PowerShell se actualizan con frecuencia. Si observa que la ayuda en línea del cmdlet incluye cmdlets o parámetros que no están en el módulo, descargue e instale la versión más reciente del mismo. Para buscar la versión de un módulo, escriba: `(Get-Module Azure).Version`.

Para ver scripts de ejemplo que pueden ayudarle a automatizar algunas de las tareas comunes de Azure, consulte el [Centro de scripts de Microsoft Azure](http://www.windowsazure.com/documentation/scripts/).

Para obtener información general acerca de cómo instalar, aprendizaje, usar y personalizar Windows PowerShell, consulte [Scripting con Windows PowerShell](http://go.microsoft.com/fwlink/p/?linkid=320210) (Scripting con Windows PowerShell).
