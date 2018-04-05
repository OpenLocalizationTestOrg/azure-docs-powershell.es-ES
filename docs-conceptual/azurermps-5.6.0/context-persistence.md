---
title: Conservación de inicios de sesión de usuario entre sesiones de PowerShell
description: Este artículo explica las nuevas características de Azure PowerShell que le permiten volver a usar las credenciales y el resto de la información de usuario en varias sesiones de PowerShell.
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 08/31/2017
ms.openlocfilehash: 4b2b3b690a8c5d6951b24d49091154c6fb479fe3
ms.sourcegitcommit: 8376e0bc5f862d382d7283ba72990e3707591e7b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/30/2018
---
# <a name="persisting-user-logins-across-powershell-sessions"></a><span data-ttu-id="671f0-103">Conservación de inicios de sesión de usuario entre sesiones de PowerShell</span><span class="sxs-lookup"><span data-stu-id="671f0-103">Persisting user logins across PowerShell sessions</span></span>

<span data-ttu-id="671f0-104">En la versión de septiembre de 2017 de Azure PowerShell, los cmdlets de Azure Resource Manager presentan una nueva característica, **Azure Context Autosave**.</span><span class="sxs-lookup"><span data-stu-id="671f0-104">In the September 2017 release of Azure PowerShell, Azure Resource Manager cmdlets introduce a new feature, **Azure Context Autosave**.</span></span> <span data-ttu-id="671f0-105">Esta característica permite varios escenarios de usuario nuevos entre los que cabe destacar:</span><span class="sxs-lookup"><span data-stu-id="671f0-105">This feature enables several new user scenarios, including:</span></span>

- <span data-ttu-id="671f0-106">Retención de la información de inicio de sesión para volverla a usar en nuevas sesiones de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="671f0-106">Retention of login information for reuse in new PowerShell sessions.</span></span>
- <span data-ttu-id="671f0-107">Uso más fácil de tareas en segundo plano para ejecutar cmdlets de larga duración.</span><span class="sxs-lookup"><span data-stu-id="671f0-107">Easier use of background tasks for executing long-running cmdlets.</span></span>
- <span data-ttu-id="671f0-108">Cambio entre cuentas, suscripciones y entornos sin tener que volver a escribir una información de inicio de sesión aparte.</span><span class="sxs-lookup"><span data-stu-id="671f0-108">Switch between accounts, subscriptions, and environments without a separate login.</span></span>
- <span data-ttu-id="671f0-109">Ejecución simultánea de tareas mediante diferentes credenciales y suscripciones, desde la misma sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="671f0-109">Execution of tasks using different credentials and subscriptions, simultaneously, from the same PowerShell session.</span></span>

## <a name="azure-contexts-defined"></a><span data-ttu-id="671f0-110">Contextos de Azure definidos</span><span class="sxs-lookup"><span data-stu-id="671f0-110">Azure contexts defined</span></span>

<span data-ttu-id="671f0-111">Un *contexto Azure* es un conjunto de información que define el destino de los cmdlets de Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="671f0-111">An *Azure context* is a set of information that defines the target of Azure PowerShell cmdlets.</span></span> <span data-ttu-id="671f0-112">El contexto se compone de cinco partes:</span><span class="sxs-lookup"><span data-stu-id="671f0-112">The context consists of five parts:</span></span>

- <span data-ttu-id="671f0-113">Una *cuenta*: los valores de UserName o ServicePrincipal usados para autenticar las comunicaciones con Azure</span><span class="sxs-lookup"><span data-stu-id="671f0-113">An *Account* - the UserName or Service Principal used to authenticate communications with Azure</span></span>
- <span data-ttu-id="671f0-114">Una *suscripción*: la suscripción de Azure que contiene los recursos sobre los que se va a actuar.</span><span class="sxs-lookup"><span data-stu-id="671f0-114">A *Subscription* - The Azure Subscription containing the Resources being acted upon.</span></span>
- <span data-ttu-id="671f0-115">Un *inquilino*: el inquilino de Azure Active Directory que contiene la suscripción.</span><span class="sxs-lookup"><span data-stu-id="671f0-115">A *Tenant* - The Azure Active Directory tenant that contains your subscription.</span></span> <span data-ttu-id="671f0-116">Los inquilinos son más importantes para la autenticación de ServicePrincipal.</span><span class="sxs-lookup"><span data-stu-id="671f0-116">Tenants are more important to ServicePrincipal authentication.</span></span>
- <span data-ttu-id="671f0-117">Un *entorno*: la nube de Azure específica de destino, normalmente la nube global de Azure.</span><span class="sxs-lookup"><span data-stu-id="671f0-117">An *Environment* - The particular Azure Cloud being targeted, usually the Azure global Cloud.</span></span>
  <span data-ttu-id="671f0-118">No obstante, la configuración del entorno también le permite usar las nubes National, Government y locales (Azure Stack) como destino.</span><span class="sxs-lookup"><span data-stu-id="671f0-118">However, the environment setting allows you to target National, Government, and on-premises (Azure Stack) clouds as well.</span></span>
- <span data-ttu-id="671f0-119">*Credenciales*: la información utilizada por Azure para verificar su identidad y garantizar la autorización para acceder a los recursos de Azure</span><span class="sxs-lookup"><span data-stu-id="671f0-119">*Credentials* - The information used by Azure to verify your identity and ensure your authorization to access resources in Azure</span></span>

<span data-ttu-id="671f0-120">En versiones anteriores, el contexto de Azure se tenía que crear cada vez que se abría una nueva sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="671f0-120">In previous releases, your Azure Context had to be created each time you opened a new PowerShell session.</span></span> <span data-ttu-id="671f0-121">A partir de Azure PowerShell v4.4.0, puede habilitar el guardado automático y la reutilización de contextos de Azure cada vez que abre una nueva sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="671f0-121">Beginning with Azure PowerShell v4.4.0, you can enable the automatic saving and reuse of Azure Contexts whenever you open a new PowerShell session.</span></span>

## <a name="automatically-saving-the-context-for-the-next-login"></a><span data-ttu-id="671f0-122">Guardar automáticamente el contexto para el siguiente inicio de sesión</span><span class="sxs-lookup"><span data-stu-id="671f0-122">Automatically saving the context for the next login</span></span>

<span data-ttu-id="671f0-123">De forma predeterminada, Azure PowerShell descarta la información de contexto siempre que cierra la sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="671f0-123">By default, Azure PowerShell discards your context information whenever you close the PowerShell session.</span></span>

<span data-ttu-id="671f0-124">Para permitir que Azure PowerShell recuerde el contexto después de cerrar la sesión de PowerShell, use `Enable-AzureRmContextAutosave`.</span><span class="sxs-lookup"><span data-stu-id="671f0-124">To allow Azure PowerShell to remember your context after the PowerShell session is closed, use `Enable-AzureRmContextAutosave`.</span></span> <span data-ttu-id="671f0-125">La información de contexto y de las credenciales se guarda automáticamente en una carpeta oculta especial del directorio del usuario (`%AppData%\Roaming\Windows Azure PowerShell`).</span><span class="sxs-lookup"><span data-stu-id="671f0-125">Context and credential information are automatically saved in a special hidden folder in your user directory (`%AppData%\Roaming\Windows Azure PowerShell`).</span></span>
<span data-ttu-id="671f0-126">Posteriormente, cada nueva sesión de PowerShell usa como destino el contexto utilizado en la última sesión.</span><span class="sxs-lookup"><span data-stu-id="671f0-126">Subsequently, each new PowerShell session targets the context used in your last session.</span></span>

<span data-ttu-id="671f0-127">Para configurar PowerShell para que olvide su contexto y las credenciales, utilice `Disable-AzureRmContextAutoSave`.</span><span class="sxs-lookup"><span data-stu-id="671f0-127">To set PowerShell to forget your context and credentials, use `Disable-AzureRmContextAutoSave`.</span></span> <span data-ttu-id="671f0-128">Debe iniciar sesión en Azure cada vez que abre una sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="671f0-128">You will need to log in to Azure every time you open a PowerShell session.</span></span>

<span data-ttu-id="671f0-129">Los cmdlets que le permiten administrar contextos de Azure también permiten un control minucioso.</span><span class="sxs-lookup"><span data-stu-id="671f0-129">The cmdlets that allow you to manage Azure contexts also allow you fine grained control.</span></span> <span data-ttu-id="671f0-130">Si desea que los cambios se apliquen solo a la sesión actual de PowerShell (ámbito `Process`) o a todas las sesiones de PowerShell (ámbito `CurrentUser`).</span><span class="sxs-lookup"><span data-stu-id="671f0-130">If you want changes to apply only to the current PowerShell session (`Process` scope) or every PowerShell session (`CurrentUser` scope).</span></span> <span data-ttu-id="671f0-131">Estas opciones se describen con detalle en [Uso de ámbitos de contexto](#Using-Context-Scopes).</span><span class="sxs-lookup"><span data-stu-id="671f0-131">These options are discussed in mode detail in [Using Context Scopes](#Using-Context-Scopes).</span></span>

## <a name="running-azure-powershell-cmdlets-as-background-jobs"></a><span data-ttu-id="671f0-132">Ejecución de cmdlets de Azure PowerShell como trabajos en segundo plano</span><span class="sxs-lookup"><span data-stu-id="671f0-132">Running Azure PowerShell cmdlets as background jobs</span></span>

<span data-ttu-id="671f0-133">La característica **Azure Context Autosave** también le permite compartir el contexto con trabajos en segundo plano de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="671f0-133">The **Azure Context Autosave** feature also allows you to share you context with PowerShell background jobs.</span></span> <span data-ttu-id="671f0-134">PowerShell le permite iniciar y supervisar tareas de larga duración como trabajos en segundo plano sin tener que esperar a que las tareas se completen.</span><span class="sxs-lookup"><span data-stu-id="671f0-134">PowerShell allows you to start and monitor long-executing tasks as background jobs without having to wait for the tasks to complete.</span></span> <span data-ttu-id="671f0-135">Puede compartir las credenciales con los trabajos en segundo plano de dos maneras diferentes:</span><span class="sxs-lookup"><span data-stu-id="671f0-135">You can share credentials with background jobs in two different ways:</span></span>

- <span data-ttu-id="671f0-136">Pasar el contexto como un argumento</span><span class="sxs-lookup"><span data-stu-id="671f0-136">Passing the context as an argument</span></span>

  <span data-ttu-id="671f0-137">La mayoría de los cmdlets AzureRM le permiten pasar el contexto como un parámetro al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="671f0-137">Most AzureRM cmdlets allow you to pass the context as a parameter to the cmdlet.</span></span> <span data-ttu-id="671f0-138">Puede pasar un contexto a un trabajo en segundo plano como se muestra en el ejemplo siguiente:</span><span class="sxs-lookup"><span data-stu-id="671f0-138">You can pass a context to a background job as shown in the following example:</span></span>

  ```powershell
  PS C:\> $job = Start-Job { param ($ctx) New-AzureRmVm -AzureRmContext $ctx [... Additional parameters ...]} -ArgumentList (Get-AzureRmContext)
  ```

- <span data-ttu-id="671f0-139">Usar el contexto predeterminado con Autosave habilitado</span><span class="sxs-lookup"><span data-stu-id="671f0-139">Using the default context with Autosave enabled</span></span>

  <span data-ttu-id="671f0-140">Si ha habilitado **Context Autosave**, los trabajos en segundo plano utilizarán automáticamente el contexto predeterminado guardado.</span><span class="sxs-lookup"><span data-stu-id="671f0-140">If you have enabled **Context Autosave**, background jobs automatically use the default saved context.</span></span>

  ```powershell
  PS C:\> $job = Start-Job { New-AzureRmVm [... Additional parameters ...]}
  ```

<span data-ttu-id="671f0-141">Si necesita saber el resultado de la tarea en segundo plano, utilice `Get-Job` para comprobar el estado del trabajo y `Wait-Job` para esperar a que el trabajo finalice.</span><span class="sxs-lookup"><span data-stu-id="671f0-141">When you need to know the outcome of the background task, use `Get-Job` to check the job status and `Wait-Job` to wait for the Job to complete.</span></span> <span data-ttu-id="671f0-142">Use `Receive-Job` para capturar o mostrar la salida del trabajo en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="671f0-142">Use `Receive-Job` to capture or display the output of the background job.</span></span> <span data-ttu-id="671f0-143">Para más información, consulte [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs) (Acerca de los trabajos).</span><span class="sxs-lookup"><span data-stu-id="671f0-143">For more information, see [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span></span>

## <a name="creating-selecting-renaming-and-removing-contexts"></a><span data-ttu-id="671f0-144">Creación, selección, cambio de nombre y eliminación de contextos</span><span class="sxs-lookup"><span data-stu-id="671f0-144">Creating, selecting, renaming, and removing contexts</span></span>

<span data-ttu-id="671f0-145">Para crear un contexto debe haber iniciado sesión en Azure.</span><span class="sxs-lookup"><span data-stu-id="671f0-145">To create a context, you must be logged in to Azure.</span></span> <span data-ttu-id="671f0-146">El cmdlet `Connect-AzureRmAccount` (o su alias, `Login-AzureRmAccount`) permite establecer el contexto predeterminado utilizado por los cmdlets posteriores de Azure PowerShell y le permite acceder a todos los inquilinos o suscripciones permitidas por sus credenciales de inicio de sesión.</span><span class="sxs-lookup"><span data-stu-id="671f0-146">The `Connect-AzureRmAccount` cmdlet (or its alias, `Login-AzureRmAccount`) sets the default context used by subsequent Azure PowerShell cmdlets, and allows you to access any tenants or subscriptions allowed by your login credentials.</span></span>

<span data-ttu-id="671f0-147">Para agregar un nuevo contexto después de iniciar sesión, use `Set-AzureRmContext` (o su alias, `Select-AzureRmSubscription`).</span><span class="sxs-lookup"><span data-stu-id="671f0-147">To add a new context after login, use `Set-AzureRmContext` (or its alias, `Select-AzureRmSubscription`).</span></span>

```powershell
PS C:\> Set-AzureRMContext -Subscription "Contoso Subscription 1" -Name "Contoso1"
```

<span data-ttu-id="671f0-148">En el ejemplo anterior se agrega un nuevo contexto que tiene como destino "Contoso suscripción 1" que usa las credenciales actuales.</span><span class="sxs-lookup"><span data-stu-id="671f0-148">The previous example adds a new context targeting 'Contoso Subscription 1' using your current credentials.</span></span> <span data-ttu-id="671f0-149">El nuevo contexto se denomina "Contoso1".</span><span class="sxs-lookup"><span data-stu-id="671f0-149">The new context is named 'Contoso1'.</span></span> <span data-ttu-id="671f0-150">Si no proporciona un nombre para el contexto, se utilizará un nombre predeterminado creado mediante el identificador de la cuenta y el de la suscripción.</span><span class="sxs-lookup"><span data-stu-id="671f0-150">If you do not provide a name for the context, a default name, using the account ID and subscription ID is used.</span></span>

<span data-ttu-id="671f0-151">Para cambiar el nombre de un contexto existente, use el cmdlet `Rename-AzureRmContext`.</span><span class="sxs-lookup"><span data-stu-id="671f0-151">To rename an existing context, use the `Rename-AzureRmContext` cmdlet.</span></span> <span data-ttu-id="671f0-152">Por ejemplo: </span><span class="sxs-lookup"><span data-stu-id="671f0-152">For example:</span></span>

```powershell
PS C:\> Rename-AzureRmContext '[user1@contoso.org; 123456-7890-1234-564321]` 'Contoso2'
```

<span data-ttu-id="671f0-153">Este ejemplo cambia el nombre automático del contexto `[user1@contoso.org; 123456-7890-1234-564321]` al nombre simple "Contoso2".</span><span class="sxs-lookup"><span data-stu-id="671f0-153">This example renames the context with automatic name `[user1@contoso.org; 123456-7890-1234-564321]` to the simple name 'Contoso2'.</span></span> <span data-ttu-id="671f0-154">Los cmdlets que administran contextos también usan la finalización con tabulación, que le permite seleccionar rápidamente el contexto.</span><span class="sxs-lookup"><span data-stu-id="671f0-154">Cmdlets that manage contexts also use tab completion, allowing you to quickly select the context.</span></span>

<span data-ttu-id="671f0-155">Por último, para quitar un contexto, use el cmdlet `Remove-AzureRmContext`.</span><span class="sxs-lookup"><span data-stu-id="671f0-155">Finally, to remove a context, use the `Remove-AzureRmContext` cmdlet.</span></span>  <span data-ttu-id="671f0-156">Por ejemplo: </span><span class="sxs-lookup"><span data-stu-id="671f0-156">For example:</span></span>

```powershell
PS C:\> Remove-AzureRmContext Contoso2
```

<span data-ttu-id="671f0-157">Olvida el contexto denominado "Contoso2".</span><span class="sxs-lookup"><span data-stu-id="671f0-157">Forgets the context that was named 'Contoso2'.</span></span> <span data-ttu-id="671f0-158">Puede volver a crear este contexto posteriormente mediante `Set-AzureRmContext`</span><span class="sxs-lookup"><span data-stu-id="671f0-158">You can recreate this context subsequently using `Set-AzureRmContext`</span></span>

## <a name="removing-credentials"></a><span data-ttu-id="671f0-159">Eliminación de credenciales</span><span class="sxs-lookup"><span data-stu-id="671f0-159">Removing credentials</span></span>

<span data-ttu-id="671f0-160">Puede quitar todas las credenciales y los contextos asociados de un usuario o una entidad de servicio mediante `Remove-AzureRmAccount` (también conocido como `Logout-AzureRmAccount`).</span><span class="sxs-lookup"><span data-stu-id="671f0-160">You can remove all credentials and associated contexts for a user or service principal using `Remove-AzureRmAccount` (also known as `Logout-AzureRmAccount`).</span></span> <span data-ttu-id="671f0-161">Cuando se ejecuta sin parámetros, el cmdlet `Remove-AzureRmAccount` elimina todas las credenciales y contextos asociados al usuario o la entidad de servicio del contexto actual.</span><span class="sxs-lookup"><span data-stu-id="671f0-161">When executed without parameters, the `Remove-AzureRmAccount` cmdlet removes all credentials and contexts associated with the User or Service Principal in the current context.</span></span> <span data-ttu-id="671f0-162">Puede pasar un nombre de usuario, nombre de entidad de seguridad de servicio o contexto para que tenga como destino una determinada entidad de seguridad.</span><span class="sxs-lookup"><span data-stu-id="671f0-162">You may pass in a Username, Service Principal Name, or context to target a particular principal.</span></span>

```powershell
Remove-AzureRmAccount user1@contoso.org
```

## <a name="using-context-scopes"></a><span data-ttu-id="671f0-163">Uso de ámbitos de contexto</span><span class="sxs-lookup"><span data-stu-id="671f0-163">Using context scopes</span></span>

<span data-ttu-id="671f0-164">En ocasiones, puede que desee seleccionar, cambiar o quitar un contexto de una sesión de PowerShell sin que afecte a otras sesiones.</span><span class="sxs-lookup"><span data-stu-id="671f0-164">Occasionally, you may want to select, change, or remove a context in a PowerShell session without impacting other sessions.</span></span> <span data-ttu-id="671f0-165">Para cambiar el comportamiento predeterminado de los cmdlets de contexto, use el parámetro `Scope`.</span><span class="sxs-lookup"><span data-stu-id="671f0-165">To change the default behavior of context cmdlets, use the `Scope` parameter.</span></span> <span data-ttu-id="671f0-166">El ámbito `Process` invalida el comportamiento predeterminado haciendo que se aplique solo a la sesión actual.</span><span class="sxs-lookup"><span data-stu-id="671f0-166">The `Process` scope overrides the default behavior by making it apply only for the current session.</span></span> <span data-ttu-id="671f0-167">Por el contrario, el ámbito `CurrentUser` cambia el contexto en todas las sesiones, en lugar de simplemente en la sesión actual.</span><span class="sxs-lookup"><span data-stu-id="671f0-167">Conversely `CurrentUser` scope changes the context in all sessions, instead of just the current session.</span></span>

<span data-ttu-id="671f0-168">Por ejemplo, para cambiar el contexto predeterminado en la sesión actual de PowerShell, sin que afecte a otras ventanas, o el contexto que se utilizará la siguiente vez que se abra una sesión, use:</span><span class="sxs-lookup"><span data-stu-id="671f0-168">As an example, to change the default context in the current PowerShell session without impacting other windows, or the context used the next time a session is opened, use:</span></span>

```powershell
PS C:\> Select-AzureRmContext Contoso1 -Scope Process
```

## <a name="how-the-context-autosave-setting-is-remembered"></a><span data-ttu-id="671f0-169">Conservación de la configuración de Context Autosave</span><span class="sxs-lookup"><span data-stu-id="671f0-169">How the context autosave setting is remembered</span></span>

<span data-ttu-id="671f0-170">La configuración de Context Autosave se guarda en el directorio del usuario de Azure PowerShell (`%AppData%\Roaming\Windows Azure PowerShell`).</span><span class="sxs-lookup"><span data-stu-id="671f0-170">The context AutoSave setting is saved to the user Azure PowerShell directory (`%AppData%\Roaming\Windows Azure PowerShell`).</span></span> <span data-ttu-id="671f0-171">Algunos tipos de cuentas de equipo no pueden acceder a este directorio.</span><span class="sxs-lookup"><span data-stu-id="671f0-171">Some kinds of computer accounts may not have access to this directory.</span></span> <span data-ttu-id="671f0-172">Para estos escenarios, puede usar la variable de entorno</span><span class="sxs-lookup"><span data-stu-id="671f0-172">For such scenarios, you can use the environment variable</span></span>

```powershell
$env:AzureRmContextAutoSave="true" | "false"
```

<span data-ttu-id="671f0-173">Si se establece en "true", el contexto se guarda automáticamente.</span><span class="sxs-lookup"><span data-stu-id="671f0-173">If set to 'true', the context is automatically saved.</span></span> <span data-ttu-id="671f0-174">Si se establece en "false", el contexto no se guarda.</span><span class="sxs-lookup"><span data-stu-id="671f0-174">If set to 'false', the context is not saved.</span></span>

## <a name="changes-to-the-azurermprofile-module"></a><span data-ttu-id="671f0-175">Cambios realizados en el módulo AzureRM.Profile</span><span class="sxs-lookup"><span data-stu-id="671f0-175">Changes to the AzureRM.Profile module</span></span>

<span data-ttu-id="671f0-176">Nuevos cmdlets para la administración de contexto</span><span class="sxs-lookup"><span data-stu-id="671f0-176">New cmdlets for managing context</span></span>

- <span data-ttu-id="671f0-177">[Enable-AzureRmContextAutosave][enable]: permite guardar el contexto entre sesiones de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="671f0-177">[Enable-AzureRmContextAutosave][enable] - Allow saving the context between powershell sessions.</span></span>
  <span data-ttu-id="671f0-178">Todos los cambios modificarán el contexto global.</span><span class="sxs-lookup"><span data-stu-id="671f0-178">Any changes alter the global context.</span></span>
- <span data-ttu-id="671f0-179">[Disable-AzureRmContextAutosave][disable]: desactiva el guardado automático del contexto.</span><span class="sxs-lookup"><span data-stu-id="671f0-179">[Disable-AzureRmContextAutosave][disable] - Turn off autosaving the context.</span></span> <span data-ttu-id="671f0-180">Tendrá que iniciar sesión de nuevo con cada nueva sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="671f0-180">Each new PowerShell session is required to log in again.</span></span>
- <span data-ttu-id="671f0-181">[Select-AzureRmContext][select]: selecciona un contexto como el predeterminado.</span><span class="sxs-lookup"><span data-stu-id="671f0-181">[Select-AzureRmContext][select] - Select a context as the default.</span></span> <span data-ttu-id="671f0-182">Todos los cmdlets posteriores usarán las credenciales de este contexto para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="671f0-182">All subsequent cmdlets use the credentials in this context for authentication.</span></span>
- <span data-ttu-id="671f0-183">[Remove-AzureRmAccount][remove-cred]: elimina todas las credenciales y contextos asociados a una cuenta.</span><span class="sxs-lookup"><span data-stu-id="671f0-183">[Remove-AzureRmAccount][remove-cred] - Remove all credentials and contexts associated with an account.</span></span>
- <span data-ttu-id="671f0-184">[Remove-AzureRmContext][remove-context]: elimina un contexto con nombre.</span><span class="sxs-lookup"><span data-stu-id="671f0-184">[Remove-AzureRmContext][remove-context] - Remove a named context.</span></span>
- <span data-ttu-id="671f0-185">[Rename-AzureRmContext][rename]: cambia el nombre de un contexto existente.</span><span class="sxs-lookup"><span data-stu-id="671f0-185">[Rename-AzureRmContext][rename] - Rename an existing context.</span></span>

<span data-ttu-id="671f0-186">Cambios en los cmdlets de perfil existentes</span><span class="sxs-lookup"><span data-stu-id="671f0-186">Changes to existing profile cmdlets</span></span>

- <span data-ttu-id="671f0-187">[Add-AzureRmAccount][login]: permite el ámbito del inicio de sesión para el proceso o usuario actuales.</span><span class="sxs-lookup"><span data-stu-id="671f0-187">[Add-AzureRmAccount][login] - Allow scoping of the login to the process or the current user.</span></span>
  <span data-ttu-id="671f0-188">Permite nombrar el contexto predeterminado después de iniciar sesión.</span><span class="sxs-lookup"><span data-stu-id="671f0-188">Allow naming the default context after login.</span></span>
- <span data-ttu-id="671f0-189">[Import-AzureRmContext][import]: permite el ámbito del inicio de sesión para el proceso o usuario actuales.</span><span class="sxs-lookup"><span data-stu-id="671f0-189">[Import-AzureRmContext][import] - Allow scoping of the login to the process or the current user.</span></span>
- <span data-ttu-id="671f0-190">[Set-AzureRmContext][set-context]: permite la selección de los contextos con nombre existentes y los cambios de ámbito para el proceso o usuario actuales.</span><span class="sxs-lookup"><span data-stu-id="671f0-190">[Set-AzureRmContext][set-context] - Allow selection of existing named contexts, and scope changes to the process or current user.</span></span>

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
