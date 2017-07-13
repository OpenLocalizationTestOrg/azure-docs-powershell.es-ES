---
title: "<span data-ttu-id=\"9e468-101\">Aplicación de formato a los resultados de la consulta | Microsoft Docs</span><span class=\"sxs-lookup\"><span data-stu-id=\"9e468-101\">Formatting query results | Microsoft Docs</span></span>"
description: "<span data-ttu-id=\"9e468-102\">Cómo consultar los recursos de Azure y dar formato a los resultados.</span><span class=\"sxs-lookup\"><span data-stu-id=\"9e468-102\">How to query for resources in Azure and format the results.</span></span>"
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/30/2017
ms.openlocfilehash: 2b23af1ef84b7c91abdcbe0738b29b068f82fd32
ms.sourcegitcommit: 226527be7cb647acfe2ea9ab151185053ab3c6db
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2017
---
# <span data-ttu-id="9e468-103">Aplicación de formato a los resultados de la consulta</span><span class="sxs-lookup"><span data-stu-id="9e468-103">Formatting query results</span></span>
<a id="formatting-query-results" class="xliff"></a>

<span data-ttu-id="9e468-104">De forma predeterminada cada cmdlet de PowerShell tiene un formato de salida predefinido, lo que facilita la lectura.</span><span class="sxs-lookup"><span data-stu-id="9e468-104">By default each PowerShell cmdlet has predefined formatting of output making it easy to read.</span></span>  <span data-ttu-id="9e468-105">PowerShell también proporciona la flexibilidad de ajustar la salida o de convertir la salida del cmdlet en un formato diferente con los cmdlets siguientes:</span><span class="sxs-lookup"><span data-stu-id="9e468-105">PowerShell also provides the flexibility to adjust the output or convert the cmdlet output to a different format with the following cmdlets:</span></span>

| <span data-ttu-id="9e468-106">Aplicación de formato</span><span class="sxs-lookup"><span data-stu-id="9e468-106">Formatting</span></span>      | <span data-ttu-id="9e468-107">Conversión</span><span class="sxs-lookup"><span data-stu-id="9e468-107">Conversion</span></span>       |
|-----------------|------------------|
| `Format-Custom` | `ConvertTo-Csv`  |
| `Format-List`   | `ConvertTo-Html` |
| `Format-Table`  | `ConvertTo-Json` |
| `Format-Wide`   | `ConvertTo-Xml`  |

## <span data-ttu-id="9e468-108">Ejemplos de formato</span><span class="sxs-lookup"><span data-stu-id="9e468-108">Formatting examples</span></span>
<a id="formatting-examples" class="xliff"></a>

<span data-ttu-id="9e468-109">En este ejemplo, obtenemos una lista de máquinas virtuales de Azure en nuestra suscripción predeterminada.</span><span class="sxs-lookup"><span data-stu-id="9e468-109">In this example we get a list of Azure VMs in our default subscription.</span></span>  <span data-ttu-id="9e468-110">De forma predeterminada el comando Get-AzureRmVM emite la salida en un formato de tabla.</span><span class="sxs-lookup"><span data-stu-id="9e468-110">The Get-AzureRmVM command defaults output into a table format.</span></span>

```powershell
Get-AzureRmVM
```

```
ResourceGroupName          Name   Location          VmSize  OsType              NIC ProvisioningState
-----------------          ----   --------          ------  ------              --- -----------------
MYWESTEURG        MyUnbuntu1610 westeurope Standard_DS1_v2   Linux myunbuntu1610980         Succeeded
MYWESTEURG          MyWin2016VM westeurope Standard_DS1_v2 Windows   mywin2016vm880         Succeeded
```

<span data-ttu-id="9e468-111">Si desea limitar las columnas devueltas, puede usar el cmdlet `Format-Table`.</span><span class="sxs-lookup"><span data-stu-id="9e468-111">If you would like to limit the columns returned you can use the `Format-Table` cmdlet.</span></span> <span data-ttu-id="9e468-112">En el ejemplo siguiente, se obtiene la misma lista de máquinas virtuales pero se restringe la salida a solo el nombre de la máquina virtual, el grupo de recursos y la ubicación de la máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="9e468-112">In the following example we get the same list of virtual machines but restrict the output to just the name of the VM, the resource group, and the location of the VM.</span></span>  <span data-ttu-id="9e468-113">El parámetro `-Autosize` adapta el tamaño de las columnas según el tamaño de los datos.</span><span class="sxs-lookup"><span data-stu-id="9e468-113">The `-Autosize` parameter sizes the columns according to the size of the data.</span></span>

```powershell
Get-AzureRmVM | Format-Table Name,ResourceGroupName,Location -AutoSize
```

```
Name          ResourceGroupName Location
----          ----------------- --------
MyUnbuntu1610 MYWESTEURG        westeurope
MyWin2016VM   MYWESTEURG        westeurope
```

<span data-ttu-id="9e468-114">Si lo prefiere, puede ver la información en formato de lista.</span><span class="sxs-lookup"><span data-stu-id="9e468-114">If you would prefer you can view information in a list format.</span></span> <span data-ttu-id="9e468-115">En el siguiente ejemplo se muestra el uso del cmdlet `Format-List`.</span><span class="sxs-lookup"><span data-stu-id="9e468-115">The following example shows this using the`Format-List` cmdlet.</span></span>

```powershell
Get-AzureVM | Format-List Name,VmId,Location,ResourceGroupName
```

```
Name              : MyUnbuntu1610
VmId              : 33422f9b-e339-4704-bad8-dbe094585496
Location          : westeurope
ResourceGroupName : MYWESTEURG

Name              : MyWin2016VM
VmId              : 4650c755-fc2b-4fc7-a5bc-298d5c00808f
Location          : westeurope
ResourceGroupName : MYWESTEURG
```

## <span data-ttu-id="9e468-116">Conversión en otros tipos de datos</span><span class="sxs-lookup"><span data-stu-id="9e468-116">Converting to other data types</span></span>
<a id="converting-to-other-data-types" class="xliff"></a>

<span data-ttu-id="9e468-117">PowerShell también ofrece varios formato de salida que se pueden utilizar para adaptarse a sus necesidades.</span><span class="sxs-lookup"><span data-stu-id="9e468-117">PowerShell also offers multiple output format you can use to meet your needs.</span></span>  <span data-ttu-id="9e468-118">En el ejemplo siguiente se utiliza el cmdlet `Select-Object` para obtener los atributos de las máquinas virtuales de la suscripción y convertir el resultado en formato CSV para una importación sencilla en una base de datos u hoja de cálculo.</span><span class="sxs-lookup"><span data-stu-id="9e468-118">In the following example we use the `Select-Object` cmdlet to get attributes of the virtual machines in our subscription and and convert the output to CSV format for easy import into a database or spreadsheet.</span></span>

```powershell
Get-AzureRmVM | Select-Object ResourceGroupName,Id,VmId,Name,Location,ProvisioningState | ConvertTo-Csv -NoTypeInformation
```

```
"ResourceGroupName","Id","VmId","Name","Location","ProvisioningState"
"MYWESTUERG","/subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/MYWESTUERG/providers/Microsoft.Compute/virtualMachines/MyUnbuntu1610","33422f9b-e339-4704-bad8-dbe094585496","MyUnbuntu1610","westeurope","Succeeded"
"MYWESTUERG","/subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/MYWESTUERG/providers/Microsoft.Compute/virtualMachines/MyWin2016VM","4650c755-fc2b-4fc7-a5bc-298d5c00808f","MyWin2016VM","westeurope","Succeeded"
```

<span data-ttu-id="9e468-119">También puede convertir la salida en formato JSON.</span><span class="sxs-lookup"><span data-stu-id="9e468-119">You can also convert the output into JSON format.</span></span>  <span data-ttu-id="9e468-120">En el ejemplo siguiente se crea la misma lista de máquinas virtuales, pero se cambia el formato de salida a JSON.</span><span class="sxs-lookup"><span data-stu-id="9e468-120">The following example creates the same list of VMs but changes the output format to JSON.</span></span>

```powershell
Get-AzureRmVM | Select-Object ResourceGroupName,Id,VmId,Name,Location,ProvisioningState | ConvertTo-Json
```

```
[
    {
        "ResourceGroupName":  "MYWESTEURG",
        "Id":  "/subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/MYWESTEURG/providers/Microsoft.Compute/virtualMachines/MyUnbuntu1610",
        "VmId":  "33422f9b-e339-4704-bad8-dbe094585496",
        "Name":  "MyUnbuntu1610",
        "Location":  "westeurope",
        "ProvisioningState":  "Succeeded"
    },
    {
        "ResourceGroupName":  "MYWESTEURG",
        "Id":  "/subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/MYWESTEURG/providers/Microsoft.Compute/virtualMachines/MyWin2016VM",
        "VmId":  "4650c755-fc2b-4fc7-a5bc-298d5c00808f",
        "Name":  "MyWin2016VM",
        "Location":  "westeurope",
        "ProvisioningState":  "Succeeded"
    }
]
```
