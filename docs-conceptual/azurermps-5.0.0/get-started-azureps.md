---
title: "Introducción a Azure PowerShell | Microsoft Docs"
description: 
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: get-started-article
ms.date: 08/31/2017
ms.openlocfilehash: 2cd3fc8e955ae826471dceee79d5e6b70070d416
ms.sourcegitcommit: b256bf48e15ee98865de0fae50e7b81878b03a54
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/03/2017
---
# <a name="getting-started-with-azure-powershell"></a>Introducción a Azure PowerShell

Azure PowerShell está diseñado para administrar recursos de Azure desde la línea de comandos y para generar scripts de automatización que funcionan con Azure Resource Manager. Se puede usar en el explorador con [Azure Cloud Shell](/azure/cloud-shell/overview), o lo puede instalar en el equipo local y usarlo en cualquier sesión de PowerShell. Este artículo le ayuda a empezar a usarlo y explica los conceptos básicos que hay detrás.

## <a name="connect"></a>Conectar

La manera más sencilla de empezar es [iniciar Cloud Shell](/azure/cloud-shell/quickstart).

1. Inicie Cloud Shell en la navegación superior de Azure Portal.

   ![Icono de Shell](~/media/get-started-azureps/shell-icon.png)

2. Elija la suscripción que desea utilizar y cree una cuenta de almacenamiento.

   ![Crear una cuenta de almacenamiento](~/media/get-started-azureps/storage-prompt.png)

Una vez que se haya creado el almacenamiento, Cloud Shell abrirá una sesión de PowerShell en el explorador.

![Cloud Shell para PowerShell](~/media/get-started-azureps/cloud-powershell.png)

También puede instalar Azure PowerShell y usarlo de forma local en una sesión de PowerShell.

## <a name="install-azure-powershell"></a>Azure PowerShell

El primer paso es asegurarse de que está instalada la versión más reciente de Azure PowerShell. Para más información sobre la versión más reciente, consulte las [notas de la versión](./release-notes-azureps.md).

1. [Instale Azure PowerShell](install-azurerm-ps.md).

2. Para comprobar que la instalación se realizó correctamente, ejecute `Get-Module AzureRM` desde la línea de comandos.

## <a name="log-in-to-azure"></a>Inicie sesión en Azure.

Inicie sesión de forma interactiva:

1. Escriba `Login-AzureRmAccount`. Aparecerá un cuadro de diálogo que le pide sus credenciales de Azure. La opción "-EnvironmentName" puede permitirle iniciar sesión en Azure China o Azure Alemania.

   Por ejemplo, Login-AzureRmAccount -EnvironmentName AzureChinaCloud

2. Escriba la dirección de correo electrónico y la contraseña asociadas a su cuenta. Azure autentica y guarda las credenciales y, luego, cierra la ventana.

Una vez que haya iniciado sesión en una cuenta de Azure, puede usar los cmdlets de Azure PowerShell para acceder y administrar los recursos de la suscripción.

## <a name="create-a-resource-group"></a>Crear un grupo de recursos

Ahora que todo está configurado, vamos a usar Azure PowerShell para crear recursos en Azure.

En primer lugar, cree un grupo de recursos. En Azure, los grupos de recursos proporcionan una manera de administrar varios recursos que se desean agrupar lógicamente. Por ejemplo, puede crear un grupo de recursos para una aplicación o un proyecto, y agregar una máquina virtual, una base de datos y un servicio de CDN en él.

Vamos a crear un grupo de recursos denominado "MyResourceGroup" en la región europaoccidental de Azure. Para ello, escriba el siguiente comando:

```powershell
New-AzureRmResourceGroup -Name 'myResourceGroup' -Location 'westeurope'
```

```Output
ResourceGroupName : myResourceGroup
Location          : westeurope
ProvisioningState : Succeeded
Tags              :
ResourceId        : /subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/myResourceGroup
```

## <a name="create-a-windows-virtual-machine"></a>Creación de una máquina virtual Windows

Ahora que tenemos nuestro grupo de recursos, vamos a crear una máquina virtual Windows en él. Para crear una nueva máquina virtual primero debemos crear los otros recursos necesarios y asignarles a una configuración. A continuación, podemos usar esa configuración para crear la máquina virtual.

### <a name="create-the-required-network-resources"></a>Creación de los recursos de red necesarios

Primero se debe crear una configuración de subred que se utilizará durante el proceso de creación de la red virtual. También se creará una dirección IP pública para que podamos conectarnos a esta máquina virtual. Se creará un grupo de seguridad de red para proteger el acceso a la dirección pública. Por último, se creará la NIC virtual con todos los recursos anteriores.

```powershell
# Variables for common values
$resourceGroup = "myResourceGroup"
$location = "westeurope"
$vmName = "myWindowsVM"

# Create a subnet configuration
$subnetConfig = New-AzureRmVirtualNetworkSubnetConfig -Name mySubnet1 -AddressPrefix 192.168.1.0/24

# Create a virtual network
$vnet = New-AzureRmVirtualNetwork -ResourceGroupName $resourceGroup -Location $location `
  -Name MYvNET1 -AddressPrefix 192.168.0.0/16 -Subnet $subnetConfig

# Create a public IP address and specify a DNS name
$publicIp = New-AzureRmPublicIpAddress -ResourceGroupName $resourceGroup -Location $location `
  -Name "mypublicdns$(Get-Random)" -AllocationMethod Static -IdleTimeoutInMinutes 4
$publicIp | Select-Object Name,IpAddress

# Create an inbound network security group rule for port 3389
$nsgRuleRDP = New-AzureRmNetworkSecurityRuleConfig -Name myNetworkSecurityGroupRuleRDP  -Protocol Tcp `
  -Direction Inbound -Priority 1000 -SourceAddressPrefix * -SourcePortRange * -DestinationAddressPrefix * `
  -DestinationPortRange 3389 -Access Allow

# Create a network security group
$nsg = New-AzureRmNetworkSecurityGroup -ResourceGroupName $resourceGroup -Location $location `
  -Name myNetworkSecurityGroup1 -SecurityRules $nsgRuleRDP

# Create a virtual network card and associate with public IP address and NSG
$nic = New-AzureRmNetworkInterface -Name myNic1 -ResourceGroupName $resourceGroup -Location $location `
  -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $publicIp.Id -NetworkSecurityGroupId $nsg.Id
```

### <a name="create-the-virtual-machine"></a>Creación de la máquina virtual

En primer lugar, necesitamos un conjunto de credenciales para el sistema operativo.

```powershell
# Create user object
$cred = Get-Credential -Message "Enter a username and password for the virtual machine."
```

Ahora que tenemos los recursos necesarios, podemos crear la máquina virtual. Para este paso, se creará un objeto de configuración de máquina virtual y, a continuación, se utilizará la configuración para crear la máquina virtual.

```powershell
# Create a virtual machine configuration
$vmConfig = New-AzureRmVMConfig -VMName $vmName -VMSize Standard_D1 |
  Set-AzureRmVMOperatingSystem -Windows -ComputerName $vmName -Credential $cred |
  Set-AzureRmVMSourceImage -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version latest |
  Add-AzureRmVMNetworkInterface -Id $nic.Id

# Create a virtual machine
New-AzureRmVM -ResourceGroupName $resourceGroup -Location $location -VM $vmConfig
```

El comando `New-AzureRmVM` devuelve los resultados una vez que la máquina virtual se haya creado completamente y que esté lista para usarla.

```Output
RequestId IsSuccessStatusCode StatusCode ReasonPhrase
--------- ------------------- ---------- ------------
                         True         OK OK
```

A continuación, inicie sesión en la máquina virtual con Windows Server recién creada mediante el Escritorio remoto y la dirección IP pública de la máquina virtual. El comando siguiente muestra la dirección IP pública que se creó en el script anterior.

```powershell
$publicIp | Select-Object Name,IpAddress
```

```Output
Name                  IpAddress
----                  ---------
mypublicdns1400512543 xx.xx.xx.xx
```

Si se encuentra en un sistema basado en Windows, puede hacerlo desde la línea de comandos mediante el comando mstsc:

```powershell
mstsc /v:xx.xxx.xx.xxx
```

Especifique la misma combinación de nombre de usuario y contraseña que utilizó al crear la máquina virtual para iniciar sesión.

## <a name="create-a-linux-virtual-machine"></a>Creación de una máquina virtual Linux

Para crear una nueva máquina virtual Linux primero debemos crear los otros recursos necesarios y asignarles a una configuración. A continuación, podemos usar esa configuración para crear la máquina virtual. Se supone que ya ha creado el grupo de recursos como se explicó anteriormente. Además, debe haber una clave pública SSH llamada "`id_rsa.pub`" en el directorio .ssh del perfil de usuario.

### <a name="create-the-required-network-resources"></a>Creación de los recursos de red necesarios

Primero se debe crear una configuración de subred que se utilizará durante el proceso de creación de la red virtual. También se creará una dirección IP pública para que podamos conectarnos a esta máquina virtual. Se creará un grupo de seguridad de red para proteger el acceso a la dirección pública. Por último, se creará la NIC virtual con todos los recursos anteriores.

```powershell
# Variables for common values
$resourceGroup = "myResourceGroup"
$location = "westeurope"
$vmName = "myLinuxVM"

# Definer user name and blank password
$securePassword = ConvertTo-SecureString ' ' -AsPlainText -Force
$cred = New-Object System.Management.Automation.PSCredential ("azureuser", $securePassword)

# Create a subnet configuration
$subnetConfig = New-AzureRmVirtualNetworkSubnetConfig -Name mySubnet2 -AddressPrefix 192.168.2.0/24

# Create a virtual network
$vnet = New-AzureRmVirtualNetwork -ResourceGroupName $resourceGroup -Location $location `
  -Name MYvNET2 -AddressPrefix 192.168.0.0/16 -Subnet $subnetConfig

# Create a public IP address and specify a DNS name
$publicIp = New-AzureRmPublicIpAddress -ResourceGroupName $resourceGroup -Location $location `
  -Name "mypublicdns$(Get-Random)" -AllocationMethod Static -IdleTimeoutInMinutes 4
$publicIp | Select-Object Name,IpAddress

# Create an inbound network security group rule for port 22
$nsgRuleSSH = New-AzureRmNetworkSecurityRuleConfig -Name myNetworkSecurityGroupRuleSSH  -Protocol Tcp `
  -Direction Inbound -Priority 1000 -SourceAddressPrefix * -SourcePortRange * -DestinationAddressPrefix * `
  -DestinationPortRange 22 -Access Allow

# Create a network security group
$nsg = New-AzureRmNetworkSecurityGroup -ResourceGroupName $resourceGroup -Location $location `
  -Name myNetworkSecurityGroup2 -SecurityRules $nsgRuleSSH

# Create a virtual network card and associate with public IP address and NSG
$nic = New-AzureRmNetworkInterface -Name myNic2 -ResourceGroupName $resourceGroup -Location $location `
  -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $publicIp.Id -NetworkSecurityGroupId $nsg.Id
```

### <a name="create-the-virtual-machine"></a>Creación de la máquina virtual

Ahora que tenemos los recursos necesarios, podemos crear la máquina virtual. Para este paso, se creará un objeto de configuración de máquina virtual y, a continuación, se utilizará la configuración para crear la máquina virtual.

```powershell
# Create a virtual machine configuration
$vmConfig = New-AzureRmVMConfig -VMName $vmName -VMSize Standard_D1 |
  Set-AzureRmVMOperatingSystem -Linux -ComputerName $vmName -Credential $cred -DisablePasswordAuthentication |
  Set-AzureRmVMSourceImage -PublisherName Canonical -Offer UbuntuServer -Skus 14.04.2-LTS -Version latest |
  Add-AzureRmVMNetworkInterface -Id $nic.Id

# Configure SSH Keys
$sshPublicKey = Get-Content "$env:USERPROFILE\.ssh\id_rsa.pub"
Add-AzureRmVMSshPublicKey -VM $vmConfig -KeyData $sshPublicKey -Path "/home/azureuser/.ssh/authorized_keys"

# Create a virtual machine
New-AzureRmVM -ResourceGroupName $resourceGroup -Location $location -VM $vmConfig
```

Una vez creada la máquina virtual, puede iniciar sesión en la nueva máquina virtual Linux mediante SSH con la dirección IP pública de la máquina virtual que ha creado:

```bash
ssh xx.xxx.xxx.xxx
```

```Output
Welcome to Ubuntu 14.04.4 LTS (GNU/Linux 3.19.0-65-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

  System information as of Sun Feb 19 00:32:28 UTC 2017

  System load: 0.31              Memory usage: 3%   Processes:       89
  Usage of /:  39.6% of 1.94GB   Swap usage:   0%   Users logged in: 0

  Graph this data and manage this system at:
    https://landscape.canonical.com/

  Get cloud support with Ubuntu Advantage Cloud Guest:
    http://www.ubuntu.com/business/services/cloud

0 packages can be updated.
0 updates are security updates.



The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

my-login@MyLinuxVM:../../..$
```

## <a name="creating-other-resources-in-azure"></a>Creación de otros recursos en Azure

Ya se ha visto cómo se crean un grupo de recursos, una máquina virtual Linux y una VM con Windows Server. Sin embargo, también se pueden crear muchos otros tipos de recursos de Azure.

Por ejemplo, para crear un equilibrador de carga de red de Azure que luego se pueda asociar con las máquinas virtuales recién creadas, se puede utilizar el siguiente comando create:

```powershell
New-AzureRmLoadBalancer -Name MyLoadBalancer -ResourceGroupName myResourceGroup -Location westeurope
```

También se puede crear una red virtual privada nueva (que se suele denominar "Virtual Network" en Azure) para nuestra infraestructura con el siguiente comando:

```powershell
$subnetConfig = New-AzureRmVirtualNetworkSubnetConfig -Name mySubnet2 -AddressPrefix 10.0.0.0/16
$vnet = New-AzureRmVirtualNetwork -ResourceGroupName myResourceGroup -Location westeurope `
  -Name MYvNET3 -AddressPrefix 10.0.0.0/16 -Subnet $subnetConfig
```

Lo que hace que tanto Azure como Azure PowerShell sean muy eficaces, es que se pueden usar no solo para obtener una infraestructura en la nube, sino también para crear servicios de plataforma administrados. Los servicios de plataforma administrados también se pueden combinar con una infraestructura para compilar soluciones aún más eficaces.

Por ejemplo, Azure PowerShell se puede utilizar para crear una instancia de Azure App Service. Azure App Service es un servicio de plataforma administrado que proporciona una manera excelente de hospedar aplicaciones web sin tener que preocuparse de la infraestructura. Después de crear la instancia de Azure App Service, se pueden crear dos nuevas instancias de Azure Web Apps en App Service mediante los siguientes comandos:

```powershell
# Create an Azure AppService that we can host any number of web apps within
New-AzureRmAppServicePlan -Name MyAppServicePlan -Tier Basic -NumberofWorkers 2 -WorkerSize Small -ResourceGroupName myResourceGroup -Location westeurope

# Create Two Web Apps within the AppService (note: name param must be a unique DNS entry)
New-AzureRmWebApp -Name MyWebApp43432 -AppServicePlan MyAppServicePlan -ResourceGroupName myResourceGroup -Location westeurope
New-AzureRmWebApp -Name MyWebApp43433 -AppServicePlan MyAppServicePlan -ResourceGroupName myResourceGroup -Location westeurope
```

## <a name="listing-deployed-resources"></a>Lista de los recursos implementados

Puede usar el cmdlet `Get-AzureRmResource` para enumerar los recursos que se ejecutan en Azure. En el ejemplo siguiente se muestran los recursos que acabamos de crear en el nuevo grupo de recursos.

```powershell
Get-AzureRmResource |
  Where-Object ResourceGroupName -eq myResourceGroup |
    Select-Object Name,Location,ResourceType
```

```Output
Name                                                  Location   ResourceType
----                                                  --------   ------------
myLinuxVM_OsDisk_1_36ca038791f642ba91270879088c249a   westeurope Microsoft.Compute/disks
myWindowsVM_OsDisk_1_f627e6e2bb454c72897d72e9632adf9a westeurope Microsoft.Compute/disks
myLinuxVM                                             westeurope Microsoft.Compute/virtualMachines
myWindowsVM                                           westeurope Microsoft.Compute/virtualMachines
myWindowsVM/BGInfo                                    westeurope Microsoft.Compute/virtualMachines/extensions
myNic1                                                westeurope Microsoft.Network/networkInterfaces
myNic2                                                westeurope Microsoft.Network/networkInterfaces
myNetworkSecurityGroup1                               westeurope Microsoft.Network/networkSecurityGroups
myNetworkSecurityGroup2                               westeurope Microsoft.Network/networkSecurityGroups
mypublicdns245369171                                  westeurope Microsoft.Network/publicIPAddresses
mypublicdns779537141                                  westeurope Microsoft.Network/publicIPAddresses
MYvNET1                                               westeurope Microsoft.Network/virtualNetworks
MYvNET2                                               westeurope Microsoft.Network/virtualNetworks
micromyresomywi032907510                              westeurope Microsoft.Storage/storageAccounts
```

## <a name="deleting-resources"></a>Eliminación de recursos

Para limpiar su cuenta de Azure, debe quitar los recursos que se han creado en este ejemplo. Puede usar los cmdlets `Remove-AzureRm*` para eliminar los recursos que ya no necesita. Para quitar la máquina virtual Windows que se creó, use el siguiente comando:

```powershell
Remove-AzureRmVM -Name myWindowsVM -ResourceGroupName myResourceGroup
```

Se le pedirá que confirme que desea eliminar el recurso.

```Output
Confirm
Are you sure you want to remove resource group 'myResourceGroup'
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
```

Puede también utilizar la eliminación de muchos recursos al mismo tiempo. Por ejemplo, el siguiente comando permite eliminar todo el grupo de recursos "MyResourceGroup" que hemos usado en todos los ejemplos de este tutorial de introducción. Esto eliminará el grupo de recursos y todos los recursos que contiene.

```powershell
Remove-AzureRmResourceGroup -Name myResourceGroup
```

```Output
Confirm
Are you sure you want to remove resource group 'myResourceGroup'
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
```

Este proceso puede tardar varios minutos en completarse.

## <a name="get-samples"></a>Ejemplos

Para más información sobre cómo usar Azure PowerShell, consulte nuestros scripts más comunes para [máquinas virtuales Linux](/azure/virtual-machines/virtual-machines-linux-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [máquinas virtuales Windows](/azure/virtual-machines/virtual-machines-windows-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [Web Apps](/azure/app-service-web/app-service-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json) y [SQL Database](/azure/sql-database/sql-database-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json).

## <a name="next-steps"></a>Pasos siguientes

* [Inicio de sesión con Azure PowerShell](authenticate-azureps.md)
* [Administración de suscripciones de Azure con Azure PowerShell](manage-subscriptions-azureps.md)
* [Creación de entidades de servicio en Azure con Azure PowerShell](create-azure-service-principal-azureps.md)
* Lea las notas de la versión sobre la migración desde una versión anterior: [https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes](https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes).
* Consiga ayuda de la comunidad:
  * [Foro de Azure en MSDN](http://go.microsoft.com/fwlink/p/?LinkId=320212)
  * [stackoverflow](http://go.microsoft.com/fwlink/?LinkId=320213)
