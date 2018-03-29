---
title: Consulta de los recursos de Azure y aplicación de formato a los resultados | Microsoft Docs
description: Cómo consultar los recursos de Azure y dar formato a los resultados.
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/30/2017
ms.openlocfilehash: 93a031ce90352286bb1a5e01dc65e6db7cbe5c7e
ms.sourcegitcommit: 15bf69bf95eceb936b3a429e741add95c308826a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/28/2018
---
# <a name="querying-for-azure-resources"></a>Consulta de los recursos de Azure

La realización de consultas en PowerShell puede realizarse mediante cmdlets integrados. En PowerShell, los nombres de cmdlet adoptan la forma de **_verbo-nombre_**. Los cmdlets con el verbo **_Get_** son los cmdlets de consulta. Los nombres de cmdlet son los tipos de recursos de Azure sobre los que actúan los verbos de cmdlet.


## <a name="selecting-simple-properties"></a>Selección de propiedades simples

Azure PowerShell tiene un formato predeterminado definido para cada cmdlet. Las propiedades más comunes para cada tipo de recurso se muestran automáticamente en un formato de tabla o lista. Para más información acerca del formato de salida, consulte [Formatting query results](formatting-output.md) (Aplicación de formato a los resultados de la consulta).

Use el cmdlet `Get-AzureRmVM` para consultar una lista de máquinas virtuales en su cuenta.

```powershell
Get-AzureRmVM
```

La salida predeterminada se convierte automáticamente en una tabla.

```
ResourceGroupName          Name   Location          VmSize  OsType              NIC ProvisioningState
-----------------          ----   --------          ------  ------              --- -----------------
MYWESTEURG        MyUnbuntu1610 westeurope Standard_DS1_v2   Linux myunbuntu1610980         Succeeded
MYWESTEURG          MyWin2016VM westeurope Standard_DS1_v2 Windows   mywin2016vm880         Succeeded
```

El cmdlet `Select-Object` puede usarse para seleccionar las propiedades específicas que pueden resultar interesantes.

```powershell
Get-AzureRmVM | Select Name,ResourceGroupName,Location
```

```
Name          ResourceGroupName Location
----          ----------------- --------
MyUnbuntu1610 MYWESTEURG        westeurope
MyWin2016VM   MYWESTEURG        westeurope
```

## <a name="selecting-complex-nested-properties"></a>Selección de propiedades complejas anidadas

Si la propiedad que desea seleccionar está muy anidada en la salida JSON, debe proporcionar la ruta de acceso completa a la propiedad anidada. En el ejemplo siguiente se muestra cómo seleccionar el nombre de la máquina virtual y el tipo de sistema operativo en el cmdlet `Get-AzureRmVM`.

```powershell
Get-AzureRmVM | Select Name,@{Name='OSType'; Expression={$_.StorageProfile.OSDisk.OSType}}
```

```
Name           OSType
----           ------
MyUnbuntu1610   Linux
MyWin2016VM   Windows
```

## <a name="filter-result-using-the-where-object-cmdlet"></a>Filtrado del resultado con el cmdlet Where-Object

El cmdlet `Where-Object` le permite filtrar el resultado en función de los valores de propiedad. En el ejemplo siguiente, el filtro selecciona solo las máquinas virtuales con el texto "RGD" en su nombre.

```powershell
Get-AzureRmVM | Where ResourceGroupName -like RGD* | Select ResourceGroupName,Name
```

```
ResourceGroupName  Name
-----------------  ----
RGDEMO001          KBDemo001VM
RGDEMO001          KBDemo020
```

En el ejemplo siguiente, los resultados devolverán las máquinas virtuales que tengan el vmSize 'Standard_DS1_V2'.

```powershell
Get-AzureRmVM | Where vmSize -eq Standard_DS1_V2
```

```
ResourceGroupName          Name     Location          VmSize  OsType              NIC ProvisioningState
-----------------          ----     --------          ------  ------              --- -----------------
MYWESTEURG        MyUnbuntu1610   westeurope Standard_DS1_v2   Linux myunbuntu1610980         Succeeded
MYWESTEURG          MyWin2016VM   westeurope Standard_DS1_v2 Windows   mywin2016vm880         Succeeded
```
