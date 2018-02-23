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
ms.date: 09/06/2017
ms.openlocfilehash: 8a88cce312b4cca002c342c04e1f97b966ae3d2f
ms.sourcegitcommit: 7e77fe7ecd2112d6b4515517509c5c723e750e27
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2018
---
# <a name="other-installation-methods"></a>Otros métodos de instalación

Azure PowerShell tiene varios métodos de instalación. El método preferido es usar PowerShellGet con la Galería de PowerShell. Azure PowerShell se puede instalar en Windows mediante el Instalador de plataforma web (WebPI) o por medio del archivo MSI disponible en GitHub. También se puede instalar en un contenedor de Docker.

## <a name="install-on-windows-using-the-web-platform-installer"></a>Instalación en Windows mediante el Instalador de plataforma web

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

## <a name="install-on-windows-using-the-msi-package"></a>Instalación en Windows mediante el paquete MSI

Azure PowerShell puede instalarse con el archivo MSI disponible en [GitHub](https://aka.ms/azps-release). Si ha instalado versiones anteriores de los módulos de Azure, el instalador las quita automáticamente. El paquete MSI instala los módulos en `$env:ProgramFiles\WindowsPowerShell\Modules`, pero no crea carpetas específicas de versión.

## <a name="install-in-a-docker-container"></a>Instalación en un contenedor de Docker

Mantenemos una imagen de Docker preconfigurada con Azure PowerShell.

Ejecute el contenedor con `docker run`.

```powershell
docker run azuresdk/azure-powershell
```

Además, mantenemos un subconjunto de cmdlets como un contenedor de PowerShell Core.

Para Mac/Linux, use la imagen `latest`.

```bash
docker run azuresdk/azure-powershell-core:latest
```

Para Windows, use la imagen `nanoserver`.

```powershell
docker run azuresdk/azure-powershell-core:nanoserver
```

Azure PowerShell se instala en la imagen a través de `Install-Module` desde la [Galería de PowerShell](https://www.powershellgallery.com/).
