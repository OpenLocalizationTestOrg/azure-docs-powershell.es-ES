---
title: Introducción a Azure PowerShell | Microsoft Docs
description: ''
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: get-started-article
ms.date: 11/15/2017
ms.openlocfilehash: 5f1bd0c780b027b2b5779c70fa3145c5dfdc3bb4
ms.sourcegitcommit: 4ebdeea3c472d94c1aedb10b9d85bf2e76826e83
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2018
---
# <a name="getting-started-with-azure-powershell"></a><span data-ttu-id="33572-102">Introducción a Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="33572-102">Getting started with Azure PowerShell</span></span>

<span data-ttu-id="33572-103">Azure PowerShell está diseñado para administrar recursos de Azure desde la línea de comandos y para generar scripts de automatización que funcionan con Azure Resource Manager.</span><span class="sxs-lookup"><span data-stu-id="33572-103">Azure PowerShell is designed for managing and administering Azure resources from the command line, and for building automation scripts that work against the Azure Resource Manager.</span></span> <span data-ttu-id="33572-104">Se puede usar en el explorador con [Azure Cloud Shell](/azure/cloud-shell/overview), o lo puede instalar en el equipo local y usarlo en cualquier sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="33572-104">You can use it in your browser with [Azure Cloud Shell](/azure/cloud-shell/overview), or you can install it on your local machine and use it in any PowerShell session.</span></span> <span data-ttu-id="33572-105">Este artículo le ayuda a empezar a usarlo y explica los conceptos básicos que hay detrás.</span><span class="sxs-lookup"><span data-stu-id="33572-105">This article helps get you started using it, and teaches you the core concepts behind it.</span></span>

## <a name="connect"></a><span data-ttu-id="33572-106">Conectar</span><span class="sxs-lookup"><span data-stu-id="33572-106">Connect</span></span>

<span data-ttu-id="33572-107">La manera más sencilla de empezar es [iniciar Cloud Shell](/azure/cloud-shell/quickstart).</span><span class="sxs-lookup"><span data-stu-id="33572-107">The simplest way to get started is to [launch Cloud Shell](/azure/cloud-shell/quickstart).</span></span>

1. <span data-ttu-id="33572-108">Inicie Cloud Shell en la navegación superior de Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="33572-108">Launch Cloud Shell from the top navigation of the Azure portal.</span></span>

   ![Icono de Shell](~/media/get-started-azureps/shell-icon.png)

2. <span data-ttu-id="33572-110">Elija la suscripción que desea utilizar y cree una cuenta de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="33572-110">Choose the subscription you want to use and create a storage account.</span></span>

   ![Crear una cuenta de almacenamiento](~/media/get-started-azureps/storage-prompt.png)

<span data-ttu-id="33572-112">Una vez que se haya creado el almacenamiento, Cloud Shell abrirá una sesión de PowerShell en el explorador.</span><span class="sxs-lookup"><span data-stu-id="33572-112">Once your storage has been created, the Cloud Shell will open a PowerShell session in the browser.</span></span>

![Cloud Shell para PowerShell](~/media/get-started-azureps/cloud-powershell.png)

<span data-ttu-id="33572-114">También puede instalar Azure PowerShell y usarlo de forma local en una sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="33572-114">You can also install Azure PowerShell and use it locally in a PowerShell session.</span></span>

## <a name="install-azure-powershell"></a><span data-ttu-id="33572-115">Instalar Azure Powershell</span><span class="sxs-lookup"><span data-stu-id="33572-115">Install Azure PowerShell</span></span>

<span data-ttu-id="33572-116">El primer paso es asegurarse de que está instalada la versión más reciente de Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="33572-116">The first step is to make sure you have the latest version of the Azure PowerShell installed.</span></span> <span data-ttu-id="33572-117">Para más información sobre la versión más reciente, consulte las [notas de la versión](./release-notes-azureps.md).</span><span class="sxs-lookup"><span data-stu-id="33572-117">For information about the latest release, see the [release notes](./release-notes-azureps.md).</span></span>

1. <span data-ttu-id="33572-118">[Instale Azure PowerShell](install-azurerm-ps.md).</span><span class="sxs-lookup"><span data-stu-id="33572-118">[Install Azure PowerShell](install-azurerm-ps.md).</span></span>

2. <span data-ttu-id="33572-119">Para comprobar que la instalación se realizó correctamente, ejecute `Get-Module AzureRM -ListAvailable` desde la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="33572-119">To verify the installation was successful, run `Get-Module AzureRM -ListAvailable` from your command line.</span></span>

## <a name="log-in-to-azure"></a><span data-ttu-id="33572-120">Inicio de sesión en Azure</span><span class="sxs-lookup"><span data-stu-id="33572-120">Log in to Azure</span></span>

<span data-ttu-id="33572-121">Inicie sesión de forma interactiva:</span><span class="sxs-lookup"><span data-stu-id="33572-121">Sign on interactively:</span></span>

1. <span data-ttu-id="33572-122">Escriba `Login-AzureRmAccount`.</span><span class="sxs-lookup"><span data-stu-id="33572-122">Type `Login-AzureRmAccount`.</span></span> <span data-ttu-id="33572-123">Aparecerá un cuadro de diálogo que le pide sus credenciales de Azure.</span><span class="sxs-lookup"><span data-stu-id="33572-123">You will get dialog box asking for your Azure credentials.</span></span> <span data-ttu-id="33572-124">La opción "-EnvironmentName" puede permitirle iniciar sesión en Azure China o Azure Alemania.</span><span class="sxs-lookup"><span data-stu-id="33572-124">Option '-EnvironmentName' can let you login in Azure China or Azure Germany.</span></span>

   <span data-ttu-id="33572-125">Por ejemplo, Login-AzureRmAccount -EnvironmentName AzureChinaCloud</span><span class="sxs-lookup"><span data-stu-id="33572-125">e.g. Login-AzureRmAccount -EnvironmentName AzureChinaCloud</span></span>

2. <span data-ttu-id="33572-126">Escriba la dirección de correo electrónico y la contraseña asociadas a su cuenta.</span><span class="sxs-lookup"><span data-stu-id="33572-126">Type the email address and password associated with your account.</span></span> <span data-ttu-id="33572-127">Azure autentica y guarda las credenciales y, luego, cierra la ventana.</span><span class="sxs-lookup"><span data-stu-id="33572-127">Azure authenticates and saves the credential information, and then closes the window.</span></span>

<span data-ttu-id="33572-128">Una vez que haya iniciado sesión en una cuenta de Azure, puede usar los cmdlets de Azure PowerShell para acceder y administrar los recursos de la suscripción.</span><span class="sxs-lookup"><span data-stu-id="33572-128">Once you have signed in to an Azure account, you can use the Azure PowerShell cmdlets to access and manager the resources in your subscription.</span></span>

## <a name="create-a-resource-group"></a><span data-ttu-id="33572-129">Crear un grupo de recursos</span><span class="sxs-lookup"><span data-stu-id="33572-129">Create a resource group</span></span>

<span data-ttu-id="33572-130">Ahora que todo está configurado, vamos a usar Azure PowerShell para crear recursos en Azure.</span><span class="sxs-lookup"><span data-stu-id="33572-130">Now that we've got everything set up, let's use Azure PowerShell to create resources within Azure.</span></span>

<span data-ttu-id="33572-131">En primer lugar, cree un grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="33572-131">First, create a Resource Group.</span></span> <span data-ttu-id="33572-132">En Azure, los grupos de recursos proporcionan una manera de administrar varios recursos que se desean agrupar lógicamente.</span><span class="sxs-lookup"><span data-stu-id="33572-132">Resource Groups in Azure provide a way to manage multiple resources that you want to logically group together.</span></span> <span data-ttu-id="33572-133">Por ejemplo, puede crear un grupo de recursos para una aplicación o un proyecto, y agregar una máquina virtual, una base de datos y un servicio de CDN en él.</span><span class="sxs-lookup"><span data-stu-id="33572-133">For example, you might create a Resource Group for an application or project and add a virtual machine, a database and a CDN service within it.</span></span>

<span data-ttu-id="33572-134">Vamos a crear un grupo de recursos denominado "MyResourceGroup" en la región europaoccidental de Azure.</span><span class="sxs-lookup"><span data-stu-id="33572-134">Let's create a resource group named "MyResourceGroup" in the westeurope region of Azure.</span></span> <span data-ttu-id="33572-135">Para ello, escriba el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="33572-135">To do so type the following command:</span></span>

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

## <a name="create-a-windows-virtual-machine"></a><span data-ttu-id="33572-136">Creación de una máquina virtual Windows</span><span class="sxs-lookup"><span data-stu-id="33572-136">Create a Windows Virtual Machine</span></span>

<span data-ttu-id="33572-137">Ahora que tenemos nuestro grupo de recursos, vamos a crear una máquina virtual Windows en él.</span><span class="sxs-lookup"><span data-stu-id="33572-137">Now that we have our resource group, let's create a Windows VM within it.</span></span> <span data-ttu-id="33572-138">Para crear una nueva máquina virtual primero debemos crear los otros recursos necesarios y asignarles a una configuración.</span><span class="sxs-lookup"><span data-stu-id="33572-138">To create a new VM we must first create the other required resources and assign them to a configuration.</span></span> <span data-ttu-id="33572-139">A continuación, podemos usar esa configuración para crear la máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="33572-139">Then we can use that configuration to create the VM.</span></span>

### <a name="create-the-required-network-resources"></a><span data-ttu-id="33572-140">Creación de los recursos de red necesarios</span><span class="sxs-lookup"><span data-stu-id="33572-140">Create the required network resources</span></span>

<span data-ttu-id="33572-141">Primero se debe crear una configuración de subred que se utilizará durante el proceso de creación de la red virtual.</span><span class="sxs-lookup"><span data-stu-id="33572-141">First we need to create a subnet configuration to be used with the virtual network creation process.</span></span> <span data-ttu-id="33572-142">También se creará una dirección IP pública para que podamos conectarnos a esta máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="33572-142">We also create a public IP address so that we can connect to this VM.</span></span> <span data-ttu-id="33572-143">Se creará un grupo de seguridad de red para proteger el acceso a la dirección pública.</span><span class="sxs-lookup"><span data-stu-id="33572-143">We create a network security group to secure access to the public address.</span></span> <span data-ttu-id="33572-144">Por último, se creará la NIC virtual con todos los recursos anteriores.</span><span class="sxs-lookup"><span data-stu-id="33572-144">Finally we create the virtual NIC using all of the previous resources.</span></span>

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

### <a name="create-the-virtual-machine"></a><span data-ttu-id="33572-145">Creación de la máquina virtual</span><span class="sxs-lookup"><span data-stu-id="33572-145">Create the virtual machine</span></span>

<span data-ttu-id="33572-146">En primer lugar, necesitamos un conjunto de credenciales para el sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="33572-146">First we need a set of credentials for the OS.</span></span>

```powershell
# Create user object
$cred = Get-Credential -Message "Enter a username and password for the virtual machine."
```

<span data-ttu-id="33572-147">Ahora que tenemos los recursos necesarios, podemos crear la máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="33572-147">Now that we have the required resources we can create the VM.</span></span> <span data-ttu-id="33572-148">Para este paso, se creará un objeto de configuración de máquina virtual y, a continuación, se utilizará la configuración para crear la máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="33572-148">For this step, we create a VM configuration object, then we use the configuration to create the VM.</span></span>

```powershell
# Create a virtual machine configuration
$vmConfig = New-AzureRmVMConfig -VMName $vmName -VMSize Standard_D1 |
  Set-AzureRmVMOperatingSystem -Windows -ComputerName $vmName -Credential $cred |
  Set-AzureRmVMSourceImage -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version latest |
  Add-AzureRmVMNetworkInterface -Id $nic.Id

# Create a virtual machine
New-AzureRmVM -ResourceGroupName $resourceGroup -Location $location -VM $vmConfig
```

<span data-ttu-id="33572-149">El comando `New-AzureRmVM` devuelve los resultados una vez que la máquina virtual se haya creado completamente y que esté lista para usarla.</span><span class="sxs-lookup"><span data-stu-id="33572-149">The `New-AzureRmVM` command outputs results once the VM has been fully created and is ready to be used.</span></span>

```Output
RequestId IsSuccessStatusCode StatusCode ReasonPhrase
--------- ------------------- ---------- ------------
                         True         OK OK
```

<span data-ttu-id="33572-150">A continuación, inicie sesión en la máquina virtual con Windows Server recién creada mediante el Escritorio remoto y la dirección IP pública de la máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="33572-150">Now log on to your newly created Windows Server VM using Remote Desktop and the public IP address of the VM.</span></span> <span data-ttu-id="33572-151">El comando siguiente muestra la dirección IP pública que se creó en el script anterior.</span><span class="sxs-lookup"><span data-stu-id="33572-151">The following command displays the public IP address created in the previous script.</span></span>

```powershell
$publicIp | Select-Object Name,IpAddress
```

```Output
Name                  IpAddress
----                  ---------
mypublicdns1400512543 xx.xx.xx.xx
```

<span data-ttu-id="33572-152">Si se encuentra en un sistema basado en Windows, puede hacerlo desde la línea de comandos mediante el comando mstsc:</span><span class="sxs-lookup"><span data-stu-id="33572-152">If you are on a Windows-based system, you can do this from the command line using the mstsc command:</span></span>

```powershell
mstsc /v:xx.xxx.xx.xxx
```

<span data-ttu-id="33572-153">Especifique la misma combinación de nombre de usuario y contraseña que utilizó al crear la máquina virtual para iniciar sesión.</span><span class="sxs-lookup"><span data-stu-id="33572-153">Supply the same username/password combination you used when creating the VM to log in.</span></span>

## <a name="create-a-linux-virtual-machine"></a><span data-ttu-id="33572-154">Creación de una máquina virtual Linux</span><span class="sxs-lookup"><span data-stu-id="33572-154">Create a Linux Virtual Machine</span></span>

<span data-ttu-id="33572-155">Para crear una nueva máquina virtual Linux primero debemos crear los otros recursos necesarios y asignarles a una configuración.</span><span class="sxs-lookup"><span data-stu-id="33572-155">To create a new Linux VM we must first create the other required resources and assign them to a configuration.</span></span> <span data-ttu-id="33572-156">A continuación, podemos usar esa configuración para crear la máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="33572-156">Then we can use that configuration to create the VM.</span></span> <span data-ttu-id="33572-157">Se supone que ya ha creado el grupo de recursos como se explicó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="33572-157">This assumes that you have already created the resource group as previously shown.</span></span> <span data-ttu-id="33572-158">Además, debe haber una clave pública SSH llamada "`id_rsa.pub`" en el directorio .ssh del perfil de usuario.</span><span class="sxs-lookup"><span data-stu-id="33572-158">Also, you will need to have an SSH public key named `id_rsa.pub` in the .ssh directory of your user profile.</span></span>

### <a name="create-the-required-network-resources"></a><span data-ttu-id="33572-159">Creación de los recursos de red necesarios</span><span class="sxs-lookup"><span data-stu-id="33572-159">Create the required network resources</span></span>

<span data-ttu-id="33572-160">Primero se debe crear una configuración de subred que se utilizará durante el proceso de creación de la red virtual.</span><span class="sxs-lookup"><span data-stu-id="33572-160">First we need to create a subnet configuration to be used with the virtual network creation process.</span></span> <span data-ttu-id="33572-161">También se creará una dirección IP pública para que podamos conectarnos a esta máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="33572-161">We also create a public IP address so that we can connect to this VM.</span></span> <span data-ttu-id="33572-162">Se creará un grupo de seguridad de red para proteger el acceso a la dirección pública.</span><span class="sxs-lookup"><span data-stu-id="33572-162">We create a network security group to secure access to the public address.</span></span> <span data-ttu-id="33572-163">Por último, se creará la NIC virtual con todos los recursos anteriores.</span><span class="sxs-lookup"><span data-stu-id="33572-163">Finally we create the virtual NIC using all of the previous resources.</span></span>

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

### <a name="create-the-virtual-machine"></a><span data-ttu-id="33572-164">Creación de la máquina virtual</span><span class="sxs-lookup"><span data-stu-id="33572-164">Create the virtual machine</span></span>

<span data-ttu-id="33572-165">Ahora que tenemos los recursos necesarios, podemos crear la máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="33572-165">Now that we have the required resources we can create the VM.</span></span> <span data-ttu-id="33572-166">Para este paso, se creará un objeto de configuración de máquina virtual y, a continuación, se utilizará la configuración para crear la máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="33572-166">For this step, we create a VM configuration object, then we use the configuration to create the VM.</span></span>

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

<span data-ttu-id="33572-167">Una vez creada la máquina virtual, puede iniciar sesión en la nueva máquina virtual Linux mediante SSH con la dirección IP pública de la máquina virtual que ha creado:</span><span class="sxs-lookup"><span data-stu-id="33572-167">Now that the VM has been created, you can log on to your new Linux VM using SSH with the public IP address of the VM you created:</span></span>

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

## <a name="creating-other-resources-in-azure"></a><span data-ttu-id="33572-168">Creación de otros recursos en Azure</span><span class="sxs-lookup"><span data-stu-id="33572-168">Creating other resources in Azure</span></span>

<span data-ttu-id="33572-169">Ya se ha visto cómo se crean un grupo de recursos, una máquina virtual Linux y una VM con Windows Server.</span><span class="sxs-lookup"><span data-stu-id="33572-169">We've now walked through how to create a Resource Group, a Linux VM, and a Windows Server VM.</span></span> <span data-ttu-id="33572-170">Sin embargo, también se pueden crear muchos otros tipos de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="33572-170">You can create many other types of Azure resources as well.</span></span>

<span data-ttu-id="33572-171">Por ejemplo, para crear un equilibrador de carga de red de Azure que luego se pueda asociar con las máquinas virtuales recién creadas, se puede utilizar el siguiente comando create:</span><span class="sxs-lookup"><span data-stu-id="33572-171">For example, to create an Azure Network Load Balancer that we could then associate with our newly created VMs, we can use the following create command:</span></span>

```powershell
New-AzureRmLoadBalancer -Name MyLoadBalancer -ResourceGroupName myResourceGroup -Location westeurope
```

<span data-ttu-id="33572-172">También se puede crear una red virtual privada nueva (que se suele denominar "Virtual Network" en Azure) para nuestra infraestructura con el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="33572-172">We could also create a new private Virtual Network (commonly referred to as a "VNet" within Azure) for our infrastructure using the following command:</span></span>

```powershell
$subnetConfig = New-AzureRmVirtualNetworkSubnetConfig -Name mySubnet2 -AddressPrefix 10.0.0.0/16
$vnet = New-AzureRmVirtualNetwork -ResourceGroupName myResourceGroup -Location westeurope `
  -Name MYvNET3 -AddressPrefix 10.0.0.0/16 -Subnet $subnetConfig
```

<span data-ttu-id="33572-173">Lo que hace que tanto Azure como Azure PowerShell sean muy eficaces, es que se pueden usar no solo para obtener una infraestructura en la nube, sino también para crear servicios de plataforma administrados.</span><span class="sxs-lookup"><span data-stu-id="33572-173">What makes Azure and the Azure PowerShell powerful is that we can use it not just to get cloud-based infrastructure but also to create managed platform services.</span></span> <span data-ttu-id="33572-174">Los servicios de plataforma administrados también se pueden combinar con una infraestructura para compilar soluciones aún más eficaces.</span><span class="sxs-lookup"><span data-stu-id="33572-174">The managed platform services can also be combined with infrastructure to build even more powerful solutions.</span></span>

<span data-ttu-id="33572-175">Por ejemplo, Azure PowerShell se puede utilizar para crear una instancia de Azure App Service.</span><span class="sxs-lookup"><span data-stu-id="33572-175">For example, you can use the Azure PowerShell to create an Azure AppService.</span></span> <span data-ttu-id="33572-176">Azure App Service es un servicio de plataforma administrado que proporciona una manera excelente de hospedar aplicaciones web sin tener que preocuparse de la infraestructura.</span><span class="sxs-lookup"><span data-stu-id="33572-176">Azure AppService is a managed platform service that provides a great way to host web apps without having to worry about infrastructure.</span></span> <span data-ttu-id="33572-177">Después de crear la instancia de Azure App Service, se pueden crear dos nuevas instancias de Azure Web Apps en App Service mediante los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="33572-177">After creating the Azure AppService, you can create two new Azure Web Apps within the AppService using the following commands:</span></span>

```powershell
# Create an Azure AppService that we can host any number of web apps within
New-AzureRmAppServicePlan -Name MyAppServicePlan -Tier Basic -NumberofWorkers 2 -WorkerSize Small -ResourceGroupName myResourceGroup -Location westeurope

# Create Two Web Apps within the AppService (note: name param must be a unique DNS entry)
New-AzureRmWebApp -Name MyWebApp43432 -AppServicePlan MyAppServicePlan -ResourceGroupName myResourceGroup -Location westeurope
New-AzureRmWebApp -Name MyWebApp43433 -AppServicePlan MyAppServicePlan -ResourceGroupName myResourceGroup -Location westeurope
```

## <a name="listing-deployed-resources"></a><span data-ttu-id="33572-178">Lista de los recursos implementados</span><span class="sxs-lookup"><span data-stu-id="33572-178">Listing deployed resources</span></span>

<span data-ttu-id="33572-179">Puede usar el cmdlet `Get-AzureRmResource` para enumerar los recursos que se ejecutan en Azure.</span><span class="sxs-lookup"><span data-stu-id="33572-179">You can use the `Get-AzureRmResource` cmdlet to list the resources running in Azure.</span></span> <span data-ttu-id="33572-180">En el ejemplo siguiente se muestran los recursos que acabamos de crear en el nuevo grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="33572-180">The following example shows the resources we just created in the new resource group.</span></span>

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

## <a name="deleting-resources"></a><span data-ttu-id="33572-181">Eliminación de recursos</span><span class="sxs-lookup"><span data-stu-id="33572-181">Deleting resources</span></span>

<span data-ttu-id="33572-182">Para limpiar su cuenta de Azure, debe quitar los recursos que se han creado en este ejemplo.</span><span class="sxs-lookup"><span data-stu-id="33572-182">To clean up your Azure account, you want to remove the resources we created in this example.</span></span> <span data-ttu-id="33572-183">Puede usar los cmdlets `Remove-AzureRm*` para eliminar los recursos que ya no necesita.</span><span class="sxs-lookup"><span data-stu-id="33572-183">You can use the `Remove-AzureRm*` cmdlets to delete the resources you no longer need.</span></span> <span data-ttu-id="33572-184">Para quitar la máquina virtual Windows que se creó, use el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="33572-184">To remove the Windows VM we created, using the following command:</span></span>

```powershell
Remove-AzureRmVM -Name myWindowsVM -ResourceGroupName myResourceGroup
```

<span data-ttu-id="33572-185">Se le pedirá que confirme que desea eliminar el recurso.</span><span class="sxs-lookup"><span data-stu-id="33572-185">You will be prompted to confirm that you want to remove the resource.</span></span>

```Output
Confirm
Are you sure you want to remove resource group 'myResourceGroup'
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
```

<span data-ttu-id="33572-186">Puede también utilizar la eliminación de muchos recursos al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="33572-186">You can also use the delete many resources at one time.</span></span> <span data-ttu-id="33572-187">Por ejemplo, el siguiente comando permite eliminar todo el grupo de recursos "MyResourceGroup" que hemos usado en todos los ejemplos de este tutorial de introducción.</span><span class="sxs-lookup"><span data-stu-id="33572-187">For example, the following command deletes all the resource group "MyResourceGroup" that we've used for all the samples in this Get Started tutorial.</span></span> <span data-ttu-id="33572-188">Esto eliminará el grupo de recursos y todos los recursos que contiene.</span><span class="sxs-lookup"><span data-stu-id="33572-188">This removes the resource group and all of the resources in it.</span></span>

```powershell
Remove-AzureRmResourceGroup -Name myResourceGroup
```

```Output
Confirm
Are you sure you want to remove resource group 'myResourceGroup'
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
```

<span data-ttu-id="33572-189">Este proceso puede tardar varios minutos en completarse.</span><span class="sxs-lookup"><span data-stu-id="33572-189">This can take several minutes to complete.</span></span>

## <a name="get-samples"></a><span data-ttu-id="33572-190">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="33572-190">Get samples</span></span>

<span data-ttu-id="33572-191">Para más información sobre cómo usar Azure PowerShell, consulte nuestros scripts más comunes para [máquinas virtuales Linux](/azure/virtual-machines/virtual-machines-linux-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [máquinas virtuales Windows](/azure/virtual-machines/virtual-machines-windows-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [Web Apps](/azure/app-service-web/app-service-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json) y [SQL Database](/azure/sql-database/sql-database-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json).</span><span class="sxs-lookup"><span data-stu-id="33572-191">To learn more about ways to use the Azure PowerShell, check out our most common scripts for [Linux VMs](/azure/virtual-machines/virtual-machines-linux-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [Windows VMs](/azure/virtual-machines/virtual-machines-windows-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [Web Apps](/azure/app-service-web/app-service-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), and [SQL Databases](/azure/sql-database/sql-database-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json).</span></span>

## <a name="next-steps"></a><span data-ttu-id="33572-192">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="33572-192">Next steps</span></span>

* [<span data-ttu-id="33572-193">Inicio de sesión con Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="33572-193">Login with Azure PowerShell</span></span>](authenticate-azureps.md)
* [<span data-ttu-id="33572-194">Administración de suscripciones de Azure con Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="33572-194">Manage Azure subscriptions with Azure PowerShell</span></span>](manage-subscriptions-azureps.md)
* [<span data-ttu-id="33572-195">Creación de entidades de servicio en Azure con Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="33572-195">Create service principals in Azure using Azure PowerShell</span></span>](create-azure-service-principal-azureps.md)
* <span data-ttu-id="33572-196">Lea las notas de la versión sobre la migración desde una versión anterior: [https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes](https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes).</span><span class="sxs-lookup"><span data-stu-id="33572-196">Read the Release notes about migrating from an older release: [https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes](https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes).</span></span>
* <span data-ttu-id="33572-197">Consiga ayuda de la comunidad:</span><span class="sxs-lookup"><span data-stu-id="33572-197">Get help from the community:</span></span>
  * [<span data-ttu-id="33572-198">Foro de Azure en MSDN</span><span class="sxs-lookup"><span data-stu-id="33572-198">Azure forum on MSDN</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=320212)
  * [<span data-ttu-id="33572-199">stackoverflow</span><span class="sxs-lookup"><span data-stu-id="33572-199">stackoverflow</span></span>](http://go.microsoft.com/fwlink/?LinkId=320213)
