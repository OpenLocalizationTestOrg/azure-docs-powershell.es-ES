---
title: Otras maneras de instalar Azure PowerShell | Microsoft Docs
description: "Cómo instalar Azure PowerShell con el paquete MSI o el Instalador de plataforma web."
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 05/15/2017
ms.openlocfilehash: 368404bcb5218814b4965bb1bcda1e2876441d2a
ms.sourcegitcommit: 226527be7cb647acfe2ea9ab151185053ab3c6db
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2017
---
# <a name="other-installation-methods"></a>Otros métodos de instalación

Azure PowerShell tiene varios métodos de instalación. El método preferido es usar PowerShellGet con la Galería de PowerShell. Azure PowerShell puede instalarse mediante el Instalador de plataforma web (WPI) o con el archivo MSI disponible en [GitHub](https://github.com/Azure/azure-powershell/releases/latest).

## <a name="install-using-the-web-platform-installer"></a>Instalación mediante el Instalador de plataforma web

La instalación de la versión más reciente de Azure PowerShell desde WebPI es igual al de las versiones anteriores.
Descargue el [paquete WebPI de Azure PowerShell](http://aka.ms/webpi-azps) e inicie la instalación.

> [!NOTE]
> Si ha instalado previamente módulos de Azure de la Galería de PowerShell, el instalador los quita automáticamente. Esto simplifica el entorno al garantizar que solo se instala una versión de Azure PowerShell. Sin embargo, puede haber escenarios en los que haya que tener varias versiones instaladas al mismo tiempo.
>
> Los módulos de la Galería de PowerShell instalan los módulos de `$env:ProgramFiles\WindowsPowerShell\Modules`. En cambio, el programa de instalación de WebPI instala los módulos de Azure en `$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\`.
>
> Si se produce un error durante la instalación, puede quitar manualmente las carpetas de Azure* de su carpeta `$env:ProgramFiles\WindowsPowerShell\Modules` e intentar la instalación de nuevo.

Una vez completada la instalación, la configuración `$env:PSModulePath` debe incluir los directorios que contienen los cmdlets de Azure PowerShell. El comando siguiente puede utilizarse para comprobar que Azure PowerShell está instalado correctamente.

```powershell
# To make sure the Azure PowerShell module is available after you install
Get-Module -ListAvailable Azure* | Select-Object Name, Version, Path
```

> [!NOTE]
> Existe un problema conocido que puede producirse cuando la instalación se realiza desde WebPI. Si el equipo requiere un reinicio debido a actualizaciones del sistema u otras instalaciones, puede hacer que las actualizaciones de `$env:PSModulePath` no incluyan la ruta de acceso donde está instalado Azure PowerShell.

Al intentar cargar o ejecutar cmdlets después de la instalación, puede recibir el mensaje de error siguiente:

```
PS C:\> Login-AzureRmAccount
Login-AzureRmAccount : The term 'Login-AzureRmAccount' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or if a path was
included, verify that the path is correct and try again.
At line:1 char:1
+ Login-AzureRmAccount
+ ~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Login-AzureRmAccount:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

Este error puede corregirse si se reinicia el equipo o se importa el módulo mediante la ruta de acceso completa. Por ejemplo:

```powershell
Import-Module "$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\AzureRM.psd1"
```

## <a name="install-using-the-msi-package"></a>Instalación mediante el paquete MSI

Azure PowerShell puede instalarse con el archivo MSI disponible en [GitHub](https://github.com/Azure/azure-powershell/releases/latest). Si ha instalado versiones anteriores de los módulos de Azure, el instalador las quita automáticamente. El paquete MSI instala los módulos en `$env:ProgramFiles\WindowsPowerShell\Modules`, pero no crea carpetas específicas de versión.
