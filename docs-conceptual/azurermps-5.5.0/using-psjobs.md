---
title: "Ejecución de cmdlets en paralelo mediante trabajos de PowerShell"
description: "Ejecución de cmdlets en paralelo mediante el parámetro - AsJob."
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 12/11/2017
ms.openlocfilehash: 0a445a7db84c8deb6518b826b4096983669c5961
ms.sourcegitcommit: 20af779cd523c758d40e23d60eb989a4ef982d5c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2018
---
# <a name="running-cmdlets-in-parallel-using-powershell-jobs"></a><span data-ttu-id="bbf39-103">Ejecución de cmdlets en paralelo mediante trabajos de PowerShell</span><span class="sxs-lookup"><span data-stu-id="bbf39-103">Running cmdlets in parallel using PowerShell jobs</span></span>

<span data-ttu-id="bbf39-104">PowerShell admite la acción asincrónica en los [trabajos de PowerShell](/powershell/module/microsoft.powershell.core/about/about_jobs).</span><span class="sxs-lookup"><span data-stu-id="bbf39-104">PowerShell supports asynchronous action with [PowerShell Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span></span>
<span data-ttu-id="bbf39-105">Azure PowerShell depende en gran medida de la realización. y espera, de llamadas de red a Azure.</span><span class="sxs-lookup"><span data-stu-id="bbf39-105">Azure PowerShell is heavily dependent on making, and waiting for, network calls to Azure.</span></span> <span data-ttu-id="bbf39-106">Los programadores a menudo realizan varias llamadas sin bloqueo a Azure en un script o desea crear recursos de Azure en el REPL sin bloquear la sesión actual.</span><span class="sxs-lookup"><span data-stu-id="bbf39-106">As a developer, you may often find yourself looking to make multiple non-blocking calls to Azure in a script, or you may find that you want to create Azure resources in the REPL without blocking the current session.</span></span> <span data-ttu-id="bbf39-107">Para cubrir estas necesidades, Azure PowerShell ofrece compatibilidad con [PSJob](/powershell/module/microsoft.powershell.core/about/about_jobs) de primera clase.</span><span class="sxs-lookup"><span data-stu-id="bbf39-107">To address these needs, Azure PowerShell provides first-class [PSJob](/powershell/module/microsoft.powershell.core/about/about_jobs) support.</span></span>

## <a name="context-persistence-and-psjobs"></a><span data-ttu-id="bbf39-108">PSJobs y persistencia de contexto</span><span class="sxs-lookup"><span data-stu-id="bbf39-108">Context Persistence and PSJobs</span></span>

<span data-ttu-id="bbf39-109">Los PSJobs se ejecutan en procesos independientes, lo que significa que la información acerca de la conexión de Azure se debe compartir correctamente con los trabajos que se creen.</span><span class="sxs-lookup"><span data-stu-id="bbf39-109">PSJobs are run in separate processes, which means that information about your Azure connection must be properly shared with the jobs you create.</span></span> <span data-ttu-id="bbf39-110">Tras conectar su cuenta de Azure a su sesión de PowerShell con `Login-AzureRmAccount`, puede pasar el contexto a un trabajo.</span><span class="sxs-lookup"><span data-stu-id="bbf39-110">Upon connecting your Azure account to your PowerShell session with `Login-AzureRmAccount`, you can pass the context to a job.</span></span>

```powershell
$creds = Get-Credential
$job = Start-Job { param($context,$vmadmin) New-AzureRmVM -Name MyVm -AzureRmContext $context -Credential $vmadmin} -Arguments (Get-AzureRmContext),$creds
```

<span data-ttu-id="bbf39-111">Sin embargo, si ha elegido que el contexto se guarde automáticamente con `Enable-AzureRmContextAutosave`, el contexto se comparte automáticamente en todos los trabajos que cree.</span><span class="sxs-lookup"><span data-stu-id="bbf39-111">However, if you have chosen to have your context automatically saved with `Enable-AzureRmContextAutosave`, the context is automatically shared with any jobs you create.</span></span>

```powershell
Enable-AzureRmContextAutosave
$creds = Get-Credential
$job = Start-Job { param($vmadmin) New-AzureRmVM -Name MyVm -Credential $vmadmin} -Arguments $creds
```

## <a name="automatic-jobs-with--asjob"></a><span data-ttu-id="bbf39-112">Trabajos automáticos con `-AsJob`</span><span class="sxs-lookup"><span data-stu-id="bbf39-112">Automatic Jobs with `-AsJob`</span></span>

<span data-ttu-id="bbf39-113">Para su comodidad, Azure PowerShell también proporciona un modificador `-AsJob` en algunos cmdlets de larga duración.</span><span class="sxs-lookup"><span data-stu-id="bbf39-113">As a convenience, Azure PowerShell also provides an `-AsJob` switch on some long-running cmdlets.</span></span>
<span data-ttu-id="bbf39-114">El modificador `-AsJob` facilita aún más la creación de PSJobs.</span><span class="sxs-lookup"><span data-stu-id="bbf39-114">The `-AsJob` switch makes creating PSJobs even easier.</span></span>

```powershell
$creds = Get-Credential
$job = New-AzureRmVM -Name MyVm -Credential $creds -AsJob
```

<span data-ttu-id="bbf39-115">Puede inspeccionar el trabajo y el progreso en cualquier momento con `Get-Job` y `Get-AzureRmVM`.</span><span class="sxs-lookup"><span data-stu-id="bbf39-115">You can inspect the job and progress at any time with `Get-Job` and `Get-AzureRmVM`.</span></span>

```powershell
Get-Job $job
Get-AzureRmVM MyVm
```

```Output
Id Name                                       PSJobTypeName         State   HasMoreData Location  Command
-- ----                                       -------------         -----   ----------- --------  -------
1  Long Running Operation for 'New-AzureRmVM' AzureLongRunningJob`1 Running True        localhost New-AzureRmVM

ResourceGroupName    Name Location          VmSize  OsType     NIC ProvisioningState Zone
-----------------    ---- --------          ------  ------     --- ----------------- ----
MyVm                 MyVm   eastus Standard_DS1_v2 Windows    MyVm          Creating
```

<span data-ttu-id="bbf39-116">Posteriormente, cuando se complete, puede obtener el resultado del trabajo con `Receive-Job`.</span><span class="sxs-lookup"><span data-stu-id="bbf39-116">Subsequently, upon completion, you can obtain the result of the job with `Receive-Job`.</span></span>

> [!NOTE]
> <span data-ttu-id="bbf39-117">`Receive-Job` devuelve el resultado del cmdlet como si la marca `-AsJob` no estuviera.</span><span class="sxs-lookup"><span data-stu-id="bbf39-117">`Receive-Job` returns the result from the cmdlet as if the `-AsJob` flag were not present.</span></span>
> <span data-ttu-id="bbf39-118">Por ejemplo, el resultado `Receive-Job` de `Do-Action -AsJob` es del mismo tipo que el resultado de `Do-Action`.</span><span class="sxs-lookup"><span data-stu-id="bbf39-118">For example, the `Receive-Job` result of `Do-Action -AsJob` is of the same type as the result of `Do-Action`.</span></span>

```powershell
$vm = Receive-Job $job
$vm
```

```Output
ResourceGroupName        : MyVm
Id                       : /subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/MyVm/providers/Microsoft.Compute/virtualMachines/MyVm
VmId                     : dff1f79e-a8f7-4664-ab72-0ec28b9fbb5b
Name                     : MyVm
Type                     : Microsoft.Compute/virtualMachines
Location                 : eastus
Tags                     : {}
HardwareProfile          : {VmSize}
NetworkProfile           : {NetworkInterfaces}
OSProfile                : {ComputerName, AdminUsername, WindowsConfiguration, Secrets}
ProvisioningState        : Succeeded
StorageProfile           : {ImageReference, OsDisk, DataDisks}
FullyQualifiedDomainName : myvmmyvm.eastus.cloudapp.azure.com
```

## <a name="example-scenarios"></a><span data-ttu-id="bbf39-119">Escenarios de ejemplo</span><span class="sxs-lookup"><span data-stu-id="bbf39-119">Example Scenarios</span></span>

<span data-ttu-id="bbf39-120">Cree varias máquinas virtuales a la vez.</span><span class="sxs-lookup"><span data-stu-id="bbf39-120">Create multiple VMs at once.</span></span>

```powershell
$creds = Get-Credential
# Create 10 jobs.
for($k = 0; $k -lt 10; $k++) {
    New-AzureRmVm -Name MyVm$k  -Credential $creds -AsJob
}

# Get all jobs and wait on them.
Get-Job | Wait-Job
"All jobs completed"
Get-AzureRmVM
```

<span data-ttu-id="bbf39-121">En este ejemplo, el cmdlet `Wait-Job` hace que el script se detenga mientras se ejecutan trabajos.</span><span class="sxs-lookup"><span data-stu-id="bbf39-121">In this example, the `Wait-Job` cmdlet causes the script to pause while jobs run.</span></span> <span data-ttu-id="bbf39-122">La ejecución se reanuda una vez que se han completado todos los trabajos.</span><span class="sxs-lookup"><span data-stu-id="bbf39-122">The script continues executing once all of the jobs have completed.</span></span> <span data-ttu-id="bbf39-123">Esto permite crear varios trabajos que se ejecutan en paralelo y, luego, esperar a que se completen antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="bbf39-123">This allows you to create several jobs running in parallel then wait for completion before continuing.</span></span>

```Output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Long Running... AzureLongRun... Running       True            localhost            New-AzureRmVM
3      Long Running... AzureLongRun... Running       True            localhost            New-AzureRmVM
4      Long Running... AzureLongRun... Running       True            localhost            New-AzureRmVM
5      Long Running... AzureLongRun... Running       True            localhost            New-AzureRmVM
6      Long Running... AzureLongRun... Running       True            localhost            New-AzureRmVM
7      Long Running... AzureLongRun... Running       True            localhost            New-AzureRmVM
8      Long Running... AzureLongRun... Running       True            localhost            New-AzureRmVM
9      Long Running... AzureLongRun... Running       True            localhost            New-AzureRmVM
10     Long Running... AzureLongRun... Running       True            localhost            New-AzureRmVM
11     Long Running... AzureLongRun... Running       True            localhost            New-AzureRmVM
2      Long Running... AzureLongRun... Completed     True            localhost            New-AzureRmVM
3      Long Running... AzureLongRun... Completed     True            localhost            New-AzureRmVM
4      Long Running... AzureLongRun... Completed     True            localhost            New-AzureRmVM
5      Long Running... AzureLongRun... Completed     True            localhost            New-AzureRmVM
6      Long Running... AzureLongRun... Completed     True            localhost            New-AzureRmVM
7      Long Running... AzureLongRun... Completed     True            localhost            New-AzureRmVM
8      Long Running... AzureLongRun... Completed     True            localhost            New-AzureRmVM
9      Long Running... AzureLongRun... Completed     True            localhost            New-AzureRmVM
10     Long Running... AzureLongRun... Completed     True            localhost            New-AzureRmVM
11     Long Running... AzureLongRun... Completed     True            localhost            New-AzureRmVM
All Jobs completed.

ResourceGroupName        Name   Location          VmSize  OsType           NIC ProvisioningState Zone
-----------------        ----   --------          ------  ------           --- ----------------- ----
MYVM                     MyVm     eastus Standard_DS1_v2 Windows          MyVm         Succeeded
MYVM0                   MyVm0     eastus Standard_DS1_v2 Windows         MyVm0         Succeeded
MYVM1                   MyVm1     eastus Standard_DS1_v2 Windows         MyVm1         Succeeded
MYVM2                   MyVm2     eastus Standard_DS1_v2 Windows         MyVm2         Succeeded
MYVM3                   MyVm3     eastus Standard_DS1_v2 Windows         MyVm3         Succeeded
MYVM4                   MyVm4     eastus Standard_DS1_v2 Windows         MyVm4         Succeeded
MYVM5                   MyVm5     eastus Standard_DS1_v2 Windows         MyVm5         Succeeded
MYVM6                   MyVm6     eastus Standard_DS1_v2 Windows         MyVm6         Succeeded
MYVM7                   MyVm7     eastus Standard_DS1_v2 Windows         MyVm7         Succeeded
MYVM8                   MyVm8     eastus Standard_DS1_v2 Windows         MyVm8         Succeeded
MYVM9                   MyVm9     eastus Standard_DS1_v2 Windows         MyVm9         Succeeded
```
