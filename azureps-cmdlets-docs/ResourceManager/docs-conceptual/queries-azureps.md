---
title: "Consulta de los recursos de Azure y aplicación de formato a los resultados | Microsoft Docs"
description: "Cómo consultar los recursos de Azure y dar formato a los resultados."
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/30/2017
ms.openlocfilehash: 369ecdca1ab0453847041de88d0765f1ae61ca9d
ms.sourcegitcommit: 226527be7cb647acfe2ea9ab151185053ab3c6db
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2017
---
# <a name="querying-for-azure-resources"></a><span data-ttu-id="93831-103">Consulta de los recursos de Azure</span><span class="sxs-lookup"><span data-stu-id="93831-103">Querying for Azure resources</span></span>

<span data-ttu-id="93831-104">La realización de consultas en PowerShell puede realizarse mediante cmdlets integrados.</span><span class="sxs-lookup"><span data-stu-id="93831-104">Querying in PowerShell can be completed by using built-in cmdlets.</span></span> <span data-ttu-id="93831-105">En PowerShell, los nombres de cmdlet adoptan la forma de **_verbo-nombre_**.</span><span class="sxs-lookup"><span data-stu-id="93831-105">In PowerShell, cmdlet names take the form of **_Verb-Noun_**.</span></span> <span data-ttu-id="93831-106">Los cmdlets con el verbo **_Get_** son los cmdlets de consulta.</span><span class="sxs-lookup"><span data-stu-id="93831-106">The cmdlets using the verb **_Get_** are the query cmdlets.</span></span> <span data-ttu-id="93831-107">Los nombres de cmdlet son los tipos de recursos de Azure sobre los que actúan los verbos de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="93831-107">The cmdlet nouns are the types of Azure resources that are acted upon by the cmdlet verbs.</span></span>


## <a name="selecting-simple-properties"></a><span data-ttu-id="93831-108">Selección de propiedades simples</span><span class="sxs-lookup"><span data-stu-id="93831-108">Selecting simple properties</span></span>

<span data-ttu-id="93831-109">Azure PowerShell tiene un formato predeterminado definido para cada cmdlet.</span><span class="sxs-lookup"><span data-stu-id="93831-109">Azure PowerShell has default formatting defined for each cmdlet.</span></span> <span data-ttu-id="93831-110">Las propiedades más comunes para cada tipo de recurso se muestran automáticamente en un formato de tabla o lista.</span><span class="sxs-lookup"><span data-stu-id="93831-110">The most common properties for each resource type are displayed in a table or list format automatically.</span></span> <span data-ttu-id="93831-111">Para más información acerca del formato de salida, consulte [Formatting query results](formatting-output.md) (Aplicación de formato a los resultados de la consulta).</span><span class="sxs-lookup"><span data-stu-id="93831-111">For more information about formatting output, see [Formatting query results](formatting-output.md).</span></span>

<span data-ttu-id="93831-112">Use el cmdlet `Get-AzureRmVM` para consultar una lista de máquinas virtuales en su cuenta.</span><span class="sxs-lookup"><span data-stu-id="93831-112">Use the `Get-AzureRmVM` cmdlet to query for a list of VMs in your account.</span></span>

```powershell
Get-AzureRmVM
```

<span data-ttu-id="93831-113">La salida predeterminada se convierte automáticamente en una tabla.</span><span class="sxs-lookup"><span data-stu-id="93831-113">The default output is automatically formatted as a table.</span></span>

```
ResourceGroupName          Name   Location          VmSize  OsType              NIC ProvisioningState
-----------------          ----   --------          ------  ------              --- -----------------
MYWESTEURG        MyUnbuntu1610 westeurope Standard_DS1_v2   Linux myunbuntu1610980         Succeeded
MYWESTEURG          MyWin2016VM westeurope Standard_DS1_v2 Windows   mywin2016vm880         Succeeded
```

<span data-ttu-id="93831-114">El cmdlet `Select-Object` puede usarse para seleccionar las propiedades específicas que pueden resultar interesantes.</span><span class="sxs-lookup"><span data-stu-id="93831-114">The `Select-Object` cmdlet can be used to select the specific properties that are interesting to you.</span></span>

```powershell
Get-AzureRmVM | Select-Object Name,ResourceGroupName,Location
```

```
Name          ResourceGroupName Location
----          ----------------- --------
MyUnbuntu1610 MYWESTEURG        westeurope
MyWin2016VM   MYWESTEURG        westeurope
```

## <a name="selecting-complex-nested-properties"></a><span data-ttu-id="93831-115">Selección de propiedades complejas anidadas</span><span class="sxs-lookup"><span data-stu-id="93831-115">Selecting complex nested properties</span></span>

<span data-ttu-id="93831-116">Si la propiedad que desea seleccionar está muy anidada en la salida JSON, debe proporcionar la ruta de acceso completa a la propiedad anidada.</span><span class="sxs-lookup"><span data-stu-id="93831-116">If the property you want to select is nested deep in the JSON output you need to supply the full path to that nested property.</span></span> <span data-ttu-id="93831-117">En el ejemplo siguiente se muestra cómo seleccionar el nombre de la máquina virtual y el tipo de sistema operativo en el cmdlet `Get-AzureRmVM`.</span><span class="sxs-lookup"><span data-stu-id="93831-117">The following example shows how to select the VM Name and the OS type from the `Get-AzureRmVM` cmdlet.</span></span>

```powershell
Get-AzureRmVM | Select-Object name,@{Name='OSType'; Expression={$_.StorageProfile.OSDisk.OSType}}
```

```
Name           OSType
----           ------
MyUnbuntu1610   Linux
MyWin2016VM   Windows
```

## <a name="filter-result-using-the-where-object-cmdlet"></a><span data-ttu-id="93831-118">Filtrado del resultado con el cmdlet Where-Object</span><span class="sxs-lookup"><span data-stu-id="93831-118">Filter result using the Where-Object cmdlet</span></span>

<span data-ttu-id="93831-119">El cmdlet `Where-Object` le permite filtrar el resultado en función de los valores de propiedad.</span><span class="sxs-lookup"><span data-stu-id="93831-119">The `Where-Object` cmdlet allows you to filter the result based on any property value.</span></span> <span data-ttu-id="93831-120">En el ejemplo siguiente, el filtro selecciona solo las máquinas virtuales con el texto "RGD" en su nombre.</span><span class="sxs-lookup"><span data-stu-id="93831-120">In the following example, the filter selects only VMs that have the text "RGD" in their name.</span></span>

```powershell
Get-AzureRmVM | Where-Object ResourceGroupName -like "RGD*" | Select-Object ResourceGroupName,Name
```

```
ResourceGroupName  Name
-----------------  ----
RGDEMO001          KBDemo001VM
RGDEMO001          KBDemo020
```

<span data-ttu-id="93831-121">En el ejemplo siguiente, los resultados devolverán las máquinas virtuales que tengan el vmSize 'Standard_DS1_V2'.</span><span class="sxs-lookup"><span data-stu-id="93831-121">With the next example, the results will return the VMs that have the vmSize 'Standard_DS1_V2'.</span></span>

```powershell
Get-AzureRmVM | Where-Object vmSize -eq 'Standard_DS1_V2'
```

```
ResourceGroupName          Name     Location          VmSize  OsType              NIC ProvisioningState
-----------------          ----     --------          ------  ------              --- -----------------
MYWESTEURG        MyUnbuntu1610   westeurope Standard_DS1_v2   Linux myunbuntu1610980         Succeeded
MYWESTEURG          MyWin2016VM   westeurope Standard_DS1_v2 Windows   mywin2016vm880         Succeeded
```