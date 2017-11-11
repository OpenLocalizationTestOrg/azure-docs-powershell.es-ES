---
title: "Conservación de inicios de sesión de usuario entre sesiones de PowerShell"
description: "Este artículo explica las nuevas características de Azure PowerShell que le permiten volver a usar las credenciales y el resto de la información de usuario en varias sesiones de PowerShell."
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 08/31/2017
ms.openlocfilehash: 8ef20796b64b16c78a653e293a57d5e752d89710
ms.sourcegitcommit: b256bf48e15ee98865de0fae50e7b81878b03a54
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/03/2017
---
# <a name="persisting-user-logins-across-powershell-sessions"></a>Conservación de inicios de sesión de usuario entre sesiones de PowerShell

En la versión de septiembre de 2017 de Azure PowerShell, los cmdlets de Azure Resource Manager presentan una nueva característica, **Azure Context Autosave**. Esta característica permite varios escenarios de usuario nuevos entre los que cabe destacar:

- Retención de la información de inicio de sesión para volverla a usar en nuevas sesiones de PowerShell.
- Uso más fácil de tareas en segundo plano para ejecutar cmdlets de larga duración.
- Cambio entre cuentas, suscripciones y entornos sin tener que volver a escribir una información de inicio de sesión aparte.
- Ejecución simultánea de tareas mediante diferentes credenciales y suscripciones, desde la misma sesión de PowerShell.

## <a name="azure-contexts-defined"></a>Contextos de Azure definidos

Un *contexto Azure* es un conjunto de información que define el destino de los cmdlets de Azure PowerShell. El contexto se compone de cinco partes:

- Una *cuenta*: los valores de UserName o ServicePrincipal usados para autenticar las comunicaciones con Azure
- Una *suscripción*: la suscripción de Azure que contiene los recursos sobre los que se va a actuar.
- Un *inquilino*: el inquilino de Azure Active Directory que contiene la suscripción. Los inquilinos son más importantes para la autenticación de ServicePrincipal.
- Un *entorno*: la nube de Azure específica de destino, normalmente la nube global de Azure.
  No obstante, la configuración del entorno también le permite usar las nubes National, Government y locales (Azure Stack) como destino.
- *Credenciales*: la información utilizada por Azure para verificar su identidad y garantizar la autorización para acceder a los recursos de Azure

En versiones anteriores, el contexto de Azure se tenía que crear cada vez que se abría una nueva sesión de PowerShell. A partir de Azure PowerShell v4.4.0, puede habilitar el guardado automático y la reutilización de contextos de Azure cada vez que abre una nueva sesión de PowerShell.

## <a name="automatically-saving-the-context-for-the-next-login"></a>Guardar automáticamente el contexto para el siguiente inicio de sesión

De forma predeterminada, Azure PowerShell descarta la información de contexto siempre que cierra la sesión de PowerShell.

Para permitir que Azure PowerShell recuerde el contexto después de cerrar la sesión de PowerShell, use `Enable-AzureRmContextAutosave`. La información de contexto y de las credenciales se guarda automáticamente en una carpeta oculta especial del directorio del usuario (`%AppData%\Roaming\Windows Azure PowerShell`).
Posteriormente, cada nueva sesión de PowerShell usa como destino el contexto utilizado en la última sesión.

Para configurar PowerShell para que olvide su contexto y las credenciales, utilice `Disable-AzureRmContextAutoSave`. Debe iniciar sesión en Azure cada vez que abre una sesión de PowerShell.

Los cmdlets que le permiten administrar contextos de Azure también permiten un control minucioso. Si desea que los cambios se apliquen solo a la sesión actual de PowerShell (ámbito `Process`) o a todas las sesiones de PowerShell (ámbito `CurrentUser`). Estas opciones se describen con detalle en [Uso de ámbitos de contexto](#Using-Context-Scopes).

## <a name="running-azure-powershell-cmdlets-as-background-jobs"></a>Ejecución de cmdlets de Azure PowerShell como trabajos en segundo plano

La característica **Azure Context Autosave** también le permite compartir el contexto con trabajos en segundo plano de PowerShell. PowerShell le permite iniciar y supervisar tareas de larga duración como trabajos en segundo plano sin tener que esperar a que las tareas se completen. Puede compartir las credenciales con los trabajos en segundo plano de dos maneras diferentes:

- Pasar el contexto como un argumento

  La mayoría de los cmdlets AzureRM le permiten pasar el contexto como un parámetro al cmdlet. Puede pasar un contexto a un trabajo en segundo plano como se muestra en el ejemplo siguiente:

  ```powershell
  PS C:\> $job = Start-Job { param ($ctx) New-AzureRmVm -AzureRmContext $ctx [... Additional parameters ...]} -ArgumentList (Get-AzureRmContext)
  ```

- Usar el contexto predeterminado con Autosave habilitado

  Si ha habilitado **Context Autosave**, los trabajos en segundo plano utilizarán automáticamente el contexto predeterminado guardado.

  ```powershell
  PS C:\> $job = Start-Job { New-AzureRmVm [... Additional parameters ...]}
  ```

Si necesita saber el resultado de la tarea en segundo plano, utilice `Get-Job` para comprobar el estado del trabajo y `Wait-Job` para esperar a que el trabajo finalice. Use `Receive-Job` para capturar o mostrar la salida del trabajo en segundo plano. Para más información, consulte [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs) (Acerca de los trabajos).

## <a name="creating-selecting-renaming-and-removing-contexts"></a>Creación, selección, cambio de nombre y eliminación de contextos

Para crear un contexto debe haber iniciado sesión en Azure. El cmdlet `Add-AzureRmAccount` (o su alias, `Login-AzureRmAccount`) permite establecer el contexto predeterminado utilizado por los cmdlets posteriores de Azure PowerShell y le permite acceder a todos los inquilinos o suscripciones permitidas por sus credenciales de inicio de sesión.

Para agregar un nuevo contexto después de iniciar sesión, use `Set-AzureRmContext` (o su alias, `Select-AzureRmSubscription`).

```powershell
PS C:\> Set-AzureRMContext -Subscription "Contoso Subscription 1" -Name "Contoso1"
```

En el ejemplo anterior se agrega un nuevo contexto que tiene como destino "Contoso suscripción 1" que usa las credenciales actuales. El nuevo contexto se denomina "Contoso1". Si no proporciona un nombre para el contexto, se utilizará un nombre predeterminado creado mediante el identificador de la cuenta y el de la suscripción.

Para cambiar el nombre de un contexto existente, use el cmdlet `Rename-AzureRmContext`. Por ejemplo:

```powershell
PS C:\> Rename-AzureRmContext '[user1@contoso.org; 123456-7890-1234-564321]` 'Contoso2'
```

Este ejemplo cambia el nombre automático del contexto `[user1@contoso.org; 123456-7890-1234-564321]` al nombre simple "Contoso2". Los cmdlets que administran contextos también usan la finalización con tabulación, que le permite seleccionar rápidamente el contexto.

Por último, para quitar un contexto, use el cmdlet `Remove-AzureRmContext`.  Por ejemplo:

```powershell
PS C:\> Remove-AzureRmContext Contoso2
```

Olvida el contexto denominado "Contoso2". Puede volver a crear este contexto posteriormente mediante `Set-AzureRmContext`

## <a name="removing-credentials"></a>Eliminación de credenciales

Puede quitar todas las credenciales y los contextos asociados de un usuario o una entidad de servicio mediante `Remove-AzureRmAccount` (también conocido como `Logout-AzureRmAccount`). Cuando se ejecuta sin parámetros, el cmdlet `Remove-AzureRmAccount` elimina todas las credenciales y contextos asociados al usuario o la entidad de servicio del contexto actual. Puede pasar un nombre de usuario, nombre de entidad de seguridad de servicio o contexto para que tenga como destino una determinada entidad de seguridad.

```powershell
Remove-AzureRmAccount user1@contoso.org
```

## <a name="using-context-scopes"></a>Uso de ámbitos de contexto

En ocasiones, puede que desee seleccionar, cambiar o quitar un contexto de una sesión de PowerShell sin que afecte a otras sesiones. Para cambiar el comportamiento predeterminado de los cmdlets de contexto, use el parámetro `Scope`. El ámbito `Process` invalida el comportamiento predeterminado haciendo que se aplique solo a la sesión actual. Por el contrario, el ámbito `CurrentUser` cambia el contexto en todas las sesiones, en lugar de simplemente en la sesión actual.

Por ejemplo, para cambiar el contexto predeterminado en la sesión actual de PowerShell, sin que afecte a otras ventanas, o el contexto que se utilizará la siguiente vez que se abra una sesión, use:

```powershell
PS C:\> Select-AzureRmContext Contoso1 -Scope Process
```

## <a name="how-the-context-autosave-setting-is-remembered"></a>Conservación de la configuración de Context Autosave

La configuración de Context Autosave se guarda en el directorio del usuario de Azure PowerShell (`%AppData%\Roaming\Windows Azure PowerShell`). Algunos tipos de cuentas de equipo no pueden acceder a este directorio. Para estos escenarios, puede usar la variable de entorno

```powershell
$env:AzureRmContextAutoSave="true" | "false"
```

Si se establece en "true", el contexto se guarda automáticamente. Si se establece en "false", el contexto no se guarda.

## <a name="changes-to-the-azurermprofile-module"></a>Cambios realizados en el módulo AzureRM.Profile

Nuevos cmdlets para la administración de contexto

- [Enable-AzureRmContextAutosave][enable]: permite guardar el contexto entre sesiones de PowerShell.
  Todos los cambios modificarán el contexto global.
- [Disable-AzureRmContextAutosave][disable]: desactiva el guardado automático del contexto. Tendrá que iniciar sesión de nuevo con cada nueva sesión de PowerShell.
- [Select-AzureRmContext][select]: selecciona un contexto como el predeterminado. Todos los cmdlets posteriores usarán las credenciales de este contexto para la autenticación.
- [Remove-AzureRmAccount][remove-cred]: elimina todas las credenciales y contextos asociados a una cuenta.
- [Remove-AzureRmContext][remove-context]: elimina un contexto con nombre.
- [Rename-AzureRmContext][rename]: cambia el nombre de un contexto existente.

Cambios en los cmdlets de perfil existentes

- [Add-AzureRmAccount][login]: permite el ámbito del inicio de sesión para el proceso o usuario actuales.
  Permite nombrar el contexto predeterminado después de iniciar sesión.
- [Import-AzureRmContext][import]: permite el ámbito del inicio de sesión para el proceso o usuario actuales.
- [Set-AzureRmContext][set-context]: permite la selección de los contextos con nombre existentes y los cambios de ámbito para el proceso o usuario actuales.

<!-- Hyperlinks -->
[enable]: /powershell/module/azurerm.profile/Enable-AzureRmContextAutosave
[disable]: /powershell/module/azurerm.profile/Disable-AzureRmContextAutosave
[select]: /powershell/module/azurerm.profile/Select-AzureRmContext
[remove-cred]: /powershell/module/azurerm.profile/Remove-AzureRmAccount
[remove-context]: /powershell/module/azurerm.profile/Remove-AzureRmContext
[rename]: /powershell/module/azurerm.profile/Rename-AzureRmContext

<!-- Updated cmdlets -->
[login]: /powershell/module/azurerm.profile/Add-AzureRmAccount
[import]: /powershell/module/azurerm.profile/Import-AzureRmAccount
[set-context]: /powershell/module/azurerm.profile/Import-AzureRmContext
