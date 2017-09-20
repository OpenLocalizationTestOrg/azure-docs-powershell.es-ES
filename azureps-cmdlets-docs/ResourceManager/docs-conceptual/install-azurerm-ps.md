---
title: "Instalación y configuración de Azure PowerShell | Microsoft Docs"
description: "Instalación y configuración de Azure PowerShell para usarlo por primera vez."
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 05/17/2017
ms.openlocfilehash: 8f99855c88240c6c5aeb6dd3b1ba5d9ddc8aefd1
ms.sourcegitcommit: 202ec2df66c40a60f47ea06b30a6701ad444d229
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/08/2017
---
# <a name="install-and-configure-azure-powershell"></a>Instale y configure Azure PowerShell.

En este artículo se explican los pasos para instalar los módulos de Azure PowerShell en un entorno de Windows.
Si quiere usar Azure PowerShell en macOS o Linux, consulte el siguiente artículo: [Instalación y configuración de Azure PowerShell en macOS y Linux](install-azureps-maclinux.md).

La instalación de Azure PowerShell desde la Galería de PowerShell es el método de instalación preferido.

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

Si no tiene instalado PowerShellGet, consulte la sección [Cómo obtener PowerShellGet](#how-to-get-powershellget) de este artículo.

> [!NOTE]
> El uso de PowerShellGet requiere una directiva de ejecución que permita ejecutar scripts. Para más información sobre la directiva de ejecución de PowerShell, consulte [About Execution Policies](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_execution_policies) (Acerca de las directivas de ejecución).

## <a name="step-2-install-azure-powershell"></a>Paso 2: Instalación de Azure PowerShell

La instalación de Azure PowerShell desde la Galería de PowerShell requiere privilegios elevados. Ejecute el siguiente comando desde una sesión de PowerShell con privilegios elevados:

```powershell
# Install the Azure Resource Manager modules from the PowerShell Gallery
Install-Module AzureRM
```

De forma predeterminada, la Galería de PowerShell no está configurada como un repositorio de confianza para PowerShellGet. La primera vez que use PSGallery verá el siguiente mensaje:

```
Untrusted repository

You are installing the modules from an untrusted repository. If you trust this repository, change
its InstallationPolicy value by running the Set-PSRepository cmdlet.

Are you sure you want to install the modules from 'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): Y
```

Responda "Sí" o "Sí a todo" para continuar con la instalación.

> [!NOTE]
> Si tiene una versión de NuGet anterior a la 2.8.5.201, se le pedirá que descargue e instale la versión más reciente de NuGet.

AzureRM es un módulo consolidado para los cmdlets de Azure Resource Manager. Al instalar el módulo AzureRM, los módulos de Azure PowerShell que no se hayan instalado anteriormente se descargan de la Galería de PowerShell.

Si tiene instalada una versión anterior de Azure PowerShell, puede que reciba un error. Para resolver este problema, consulte la sección [Actualización a una nueva versión de Azure PowerShell](#update-azps) de este artículo.

## <a name="step-3-load-the-azurerm-module"></a>Paso 3: Carga del módulo AzureRM
Una vez que se instala, debe cargarse en la sesión de PowerShell. Esta acción debe hacerse en una sesión de PowerShell normal (sin privilegios elevados). Los módulos se cargan mediante el cmdlet, `Import-Module` como se indica a continuación:

```powershell
Import-Module AzureRM
```

## <a name="next-steps"></a>Pasos siguientes

Para más información sobre el uso de Azure PowerShell, consulte los siguientes artículos:

* [Introducción a Azure PowerShell](get-started-azureps.md)

## <a name="reporting-issues-and-feedback"></a>Notificación de problemas y comentarios

Si aparecen errores al usar la herramienta, envíe un problema en la sección [Issues](https://github.com/Azure/azure-powershell/issues) (Problemas) del repositorio de GitHub. Para proporcionar comentarios desde la línea de comandos, use el cmdlet `Send-Feedback`.

## <a name="frequently-asked-questions"></a>Preguntas más frecuentes

### <a name="how-to-get-powershellget"></a>Cómo obtener PowerShellGet

|Versión del SO.|Instrucciones de instalación|
|---|---|
|Tengo Windows 10 o Windows Server 2016|Integrado en Windows Management Framework (WMF) 5.0 incluido en el sistema operativo|
|Quiero actualizar a PowerShell 5|[Instalar la versión más reciente de WMF](https://www.microsoft.com/en-us/download/details.aspx?id=54616)|
|Uso una versión de Windows con PowerShell 3 o PowerShell 4|[Obtener los módulos PackageManagement](http://go.microsoft.com/fwlink/?LinkID=746217)|

<a id="helpmechoose"></a>
### <a name="checking-the-version-of-azure-powershell"></a>Comprobación de la versión de Azure PowerShell

Si bien se recomienda que actualice a la versión más reciente lo antes posible, se admiten varias versiones de Azure PowerShell. Para determinar la versión de Azure PowerShell instalada, ejecute `Get-Module AzureRM` desde la línea de comandos.

```powershell
Get-Module AzureRM -list | Select-Object Name,Version,Path
```

### <a name="support-for-classic-deployment-methods"></a>Compatibilidad con métodos de implementación clásicos

Si dispone de implementaciones que usan el modelo de implementación clásica, puede instalar la versión de Service Management de Azure PowerShell. Para más información, consulte [Install the Azure PowerShell Service Management module](/powershell/azure/servicemanagement/install-azure-ps) (Instalación del módulo Service Management de Azure PowerShell). Los módulos Azure y AzureRM comparten dependencias comunes. Si usa los módulos Azure y AzureRM, debe instalar la misma versión de cada paquete.

### <a id="update-azps"></a>Actualización a una nueva versión de Azure PowerShell

Si tiene instalada una versión anterior de Azure PowerShell que incluye el módulo Service Management, puede recibir el error siguiente:

```
PackageManagement\Install-Package : A command with name 'Get-AzureStorageContainerAcl' is already
available on this system. This module 'Azure.Storage' may override the existing commands. If you
still want to install this module 'Azure.Storage', use -AllowClobber parameter.

At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1772 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], Exception
    + FullyQualifiedErrorId : CommandAlreadyAvailable,Validate-ModuleCommandAlreadyAvailable,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage
```

Como indica el mensaje de error, debe usar el parámetro - AllowClobber para instalar el módulo. Use el comando siguiente:

```powershell
# Install the Azure Resource Manager modules from the PowerShell Gallery
Install-Module AzureRM -AllowClobber
```

Para más información, consulte el tema de ayuda de [Install-Module](https://msdn.microsoft.com/powershell/reference/5.1/PowerShellGet/install-module).

### <a name="installing-module-versions-side-by-side"></a>Instalación de versiones de módulo en paralelo

El método de instalación PowerShellGet es el único método que admite la instalación de varias versiones. Por ejemplo, puede tener scripts escritos con una versión anterior de Azure PowerShell que no tenga tiempo de actualizar o recursos para hacerlo. Los comandos siguientes muestran cómo instalar varias versiones de Azure PowerShell:

```powershell
Install-Module -Name AzureRM -RequiredVersion 3.7.0
Install-Module -Name AzureRM -RequiredVersion 1.2.9
```

Solo una versión del módulo se puede cargar en una sesión de PowerShell. Debe abrir una nueva ventana de PowerShell y usar `Import-Module` para importar una versión específica de los cmdlets de AzureRM:

```powershell
Import-Module AzureRM -RequiredVersion 1.2.9
```

> [!NOTE]
> La versión 2.1.0 y la versión 1.2.6 son las primeras versiones de módulos diseñadas para instalarse y usarse en paralelo. Al cargar una versión anterior de Azure PowerShell, se cargan versiones incompatibles del módulo **AzureRM.Profile**. Como resultado, cada vez que ejecuta un cmdlet se le pide que inicie sesión.

### <a name="other-installation-methods"></a>Otros métodos de instalación

Para más información sobre la instalación mediante el Instalador de plataforma web o el paquete MSI, consulte [Otros métodos de instalación](other-install.md)
