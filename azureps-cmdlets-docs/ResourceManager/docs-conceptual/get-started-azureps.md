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
ms.date: 03/30/2017
ms.openlocfilehash: f1c13317f0b42b547166a8130dd8c29bed5759c9
ms.sourcegitcommit: db5c50de90764a9bdc7c1f1dbca3aed5bfeb05fa
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2017
---
# <a name="getting-started-with-azure-powershell"></a><span data-ttu-id="641e7-102">Introducción a Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="641e7-102">Getting started with Azure PowerShell</span></span>

<span data-ttu-id="641e7-103">Azure PowerShell está diseñado para administrar recursos de Azure desde la línea de comandos y para generar scripts de automatización que funcionan con Azure Resource Manager.</span><span class="sxs-lookup"><span data-stu-id="641e7-103">Azure PowerShell is designed for managing and administering Azure resources from the command line, and for building automation scripts that work against the Azure Resource Manager.</span></span> <span data-ttu-id="641e7-104">Este artículo le ayuda a empezar a usarlo y explica los conceptos básicos que hay detrás.</span><span class="sxs-lookup"><span data-stu-id="641e7-104">This article helps get you started using it, and teaches you the core concepts behind it.</span></span>

## <a name="install-azure-powershell"></a><span data-ttu-id="641e7-105">Instalar Azure Powershell</span><span class="sxs-lookup"><span data-stu-id="641e7-105">Install Azure PowerShell</span></span>

<span data-ttu-id="641e7-106">El primer paso es asegurarse de que está instalada la versión más reciente de Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="641e7-106">The first step is to make sure you have the latest version of the Azure PowerShell installed.</span></span> <span data-ttu-id="641e7-107">Para más información sobre la versión más reciente, consulte las [notas de la versión](./release-notes-azureps.md).</span><span class="sxs-lookup"><span data-stu-id="641e7-107">For information about the latest release, see the [release notes](./release-notes-azureps.md).</span></span>

1. <span data-ttu-id="641e7-108">[Instale Azure PowerShell](install-azurerm-ps.md).</span><span class="sxs-lookup"><span data-stu-id="641e7-108">[Install Azure PowerShell](install-azurerm-ps.md).</span></span>
2. <span data-ttu-id="641e7-109">Para comprobar que la instalación se realizó correctamente, ejecute `Get-Module AzureRM` desde la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="641e7-109">To verify the installation was successful, run `Get-Module AzureRM` from your command line.</span></span>

## <a name="log-in-to-azure"></a><span data-ttu-id="641e7-110">Inicie sesión en Azure.</span><span class="sxs-lookup"><span data-stu-id="641e7-110">Log in to Azure</span></span>

<span data-ttu-id="641e7-111">Inicie sesión de forma interactiva:</span><span class="sxs-lookup"><span data-stu-id="641e7-111">Sign on interactively:</span></span>

1. <span data-ttu-id="641e7-112">Escriba `Login-AzureRmAccount`.</span><span class="sxs-lookup"><span data-stu-id="641e7-112">Type `Login-AzureRmAccount`.</span></span> <span data-ttu-id="641e7-113">Aparecerá un cuadro de diálogo que le pide sus credenciales de Azure.</span><span class="sxs-lookup"><span data-stu-id="641e7-113">You will get dialog box asking for your Azure credentials.</span></span> <span data-ttu-id="641e7-114">La opción "-EnvironmentName" puede permitirle iniciar sesión en Azure China o Azure Alemania.</span><span class="sxs-lookup"><span data-stu-id="641e7-114">Option '-EnvironmentName' can let you login in Azure China or Azure Germany.</span></span>

   <span data-ttu-id="641e7-115">Por ejemplo, Login-AzureRmAccount -EnvironmentName AzureChinaCloud</span><span class="sxs-lookup"><span data-stu-id="641e7-115">e.g. Login-AzureRmAccount -EnvironmentName AzureChinaCloud</span></span>

2. <span data-ttu-id="641e7-116">Escriba la dirección de correo electrónico y la contraseña asociadas a su cuenta.</span><span class="sxs-lookup"><span data-stu-id="641e7-116">Type the email address and password associated with your account.</span></span> <span data-ttu-id="641e7-117">Azure autentica y guarda las credenciales y, luego, cierra la ventana.</span><span class="sxs-lookup"><span data-stu-id="641e7-117">Azure authenticates and saves the credential information, and then closes the window.</span></span>

<span data-ttu-id="641e7-118">Una vez que haya iniciado sesión en una cuenta de Azure, puede usar los cmdlets de Azure PowerShell para acceder y administrar los recursos de la suscripción.</span><span class="sxs-lookup"><span data-stu-id="641e7-118">Once you have signed in to an Azure account, you can use the Azure PowerShell cmdlets to access and manager the resources in your subscription.</span></span>

## <a name="create-a-resource-group"></a><span data-ttu-id="641e7-119">Crear un grupo de recursos</span><span class="sxs-lookup"><span data-stu-id="641e7-119">Create a resource group</span></span>

<span data-ttu-id="641e7-120">Ahora que todo está configurado, vamos a usar Azure PowerShell para crear recursos en Azure.</span><span class="sxs-lookup"><span data-stu-id="641e7-120">Now that we've got everything set up, let's use Azure PowerShell to create resources within Azure.</span></span>

<span data-ttu-id="641e7-121">En primer lugar, cree un grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="641e7-121">First, create a Resource Group.</span></span> <span data-ttu-id="641e7-122">En Azure, los grupos de recursos proporcionan una manera de administrar varios recursos que se desean agrupar lógicamente.</span><span class="sxs-lookup"><span data-stu-id="641e7-122">Resource Groups in Azure provide a way to manage multiple resources that you want to logically group together.</span></span> <span data-ttu-id="641e7-123">Por ejemplo, puede crear un grupo de recursos para una aplicación o un proyecto, y agregar una máquina virtual, una base de datos y un servicio de CDN en él.</span><span class="sxs-lookup"><span data-stu-id="641e7-123">For example, you might create a Resource Group for an application or project and add a virtual machine, a database and a CDN service within it.</span></span>

<span data-ttu-id="641e7-124">Vamos a crear un grupo de recursos denominado "MyResourceGroup" en la región europaoccidental de Azure.</span><span class="sxs-lookup"><span data-stu-id="641e7-124">Let's create a resource group named "MyResourceGroup" in the westeurope region of Azure.</span></span> <span data-ttu-id="641e7-125">Para ello, escriba el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="641e7-125">To do so type the following command:</span></span>

```powershell
New-AzureRmResourceGroup -Name 'myResourceGroup' -Location 'westeurope'
```

```
ResourceGroupName : myResourceGroup
Location          : westeurope
ProvisioningState : Succeeded
Tags              :
ResourceId        : /subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/myResourceGroup
```

## <a name="create-a-windows-virtual-machine"></a><span data-ttu-id="641e7-126">Creación de una máquina virtual Windows</span><span class="sxs-lookup"><span data-stu-id="641e7-126">Create a Windows Virtual Machine</span></span>

<span data-ttu-id="641e7-127">Ahora que tenemos nuestro grupo de recursos, vamos a crear una máquina virtual Windows en él.</span><span class="sxs-lookup"><span data-stu-id="641e7-127">Now that we have our resource group, let's create a Windows VM within it.</span></span> <span data-ttu-id="641e7-128">Para crear una nueva máquina virtual primero debemos crear los otros recursos necesarios y asignarles a una configuración.</span><span class="sxs-lookup"><span data-stu-id="641e7-128">To create a new VM we must first create the other required resources and assign them to a configuration.</span></span> <span data-ttu-id="641e7-129">A continuación, podemos usar esa configuración para crear la máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="641e7-129">Then we can use that configuration to create the VM.</span></span>

### <a name="create-the-required-network-resources"></a><span data-ttu-id="641e7-130">Creación de los recursos de red necesarios</span><span class="sxs-lookup"><span data-stu-id="641e7-130">Create the required network resources</span></span>

<span data-ttu-id="641e7-131">Primero se debe crear una configuración de subred que se utilizará durante el proceso de creación de la red virtual.</span><span class="sxs-lookup"><span data-stu-id="641e7-131">First we need to create a subnet configuration to be used with the virtual network creation process.</span></span> <span data-ttu-id="641e7-132">También se creará una dirección IP pública para que podamos conectarnos a esta máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="641e7-132">We also create a public IP address so that we can connect to this VM.</span></span> <span data-ttu-id="641e7-133">Se creará un grupo de seguridad de red para proteger el acceso a la dirección pública.</span><span class="sxs-lookup"><span data-stu-id="641e7-133">We create a network security group to secure access to the public address.</span></span> <span data-ttu-id="641e7-134">Por último, se creará la NIC virtual con todos los recursos anteriores.</span><span class="sxs-lookup"><span data-stu-id="641e7-134">Finally we create the virtual NIC using all of the previous resources.</span></span>

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

### <a name="create-the-virtual-machine"></a><span data-ttu-id="641e7-135">Creación de la máquina virtual</span><span class="sxs-lookup"><span data-stu-id="641e7-135">Create the virtual machine</span></span>

<span data-ttu-id="641e7-136">En primer lugar, necesitamos un conjunto de credenciales para el sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="641e7-136">First we need a set of credentials for the OS.</span></span>

```powershell
# Create user object
$cred = Get-Credential -Message "Enter a username and password for the virtual machine."
```

<span data-ttu-id="641e7-137">Ahora que tenemos los recursos necesarios, podemos crear la máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="641e7-137">Now that we have the required resources we can create the VM.</span></span> <span data-ttu-id="641e7-138">Para este paso, se creará un objeto de configuración de máquina virtual y, a continuación, se utilizará la configuración para crear la máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="641e7-138">For this step, we create a VM configuration object, then we use the configuration to create the VM.</span></span>

```powershell
# Create a virtual machine configuration
$vmConfig = New-AzureRmVMConfig -VMName $vmName -VMSize Standard_D1 |
  Set-AzureRmVMOperatingSystem -Windows -ComputerName $vmName -Credential $cred |
  Set-AzureRmVMSourceImage -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version latest |
  Add-AzureRmVMNetworkInterface -Id $nic.Id

# Create a virtual machine
New-AzureRmVM -ResourceGroupName $resourceGroup -Location $location -VM $vmConfig
```

<span data-ttu-id="641e7-139">El comando `New-AzureRmVM` devuelve los resultados una vez que la máquina virtual se haya creado completamente y que esté lista para usarla.</span><span class="sxs-lookup"><span data-stu-id="641e7-139">The `New-AzureRmVM` command outputs results once the VM has been fully created and is ready to be used.</span></span>

```
RequestId IsSuccessStatusCode StatusCode ReasonPhrase
--------- ------------------- ---------- ------------
                         True         OK OK
```

<span data-ttu-id="641e7-140">A continuación, inicie sesión en la máquina virtual con Windows Server recién creada mediante el Escritorio remoto y la dirección IP pública de la máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="641e7-140">Now log on to your newly created Windows Server VM using Remote Desktop and the public IP address of the VM.</span></span> <span data-ttu-id="641e7-141">El comando siguiente muestra la dirección IP pública que se creó en el script anterior.</span><span class="sxs-lookup"><span data-stu-id="641e7-141">The following command displays the public IP address created in the previous script.</span></span>

```powershell
$publicIp | Select-Object Name,IpAddress
```

```
Name                  IpAddress
----                  ---------
mypublicdns1400512543 xx.xx.xx.xx
```

<span data-ttu-id="641e7-142">Si se encuentra en un sistema basado en Windows, puede hacerlo desde la línea de comandos mediante el comando mstsc:</span><span class="sxs-lookup"><span data-stu-id="641e7-142">If you are on a Windows-based system, you can do this from the command line using the mstsc command:</span></span>

```
mstsc /v:xx.xxx.xx.xxx
```

<span data-ttu-id="641e7-143">Especifique la misma combinación de nombre de usuario y contraseña que utilizó al crear la máquina virtual para iniciar sesión.</span><span class="sxs-lookup"><span data-stu-id="641e7-143">Supply the same username/password combination you used when creating the VM to log in.</span></span>


## <a name="create-a-linux-virtual-machine"></a><span data-ttu-id="641e7-144">Creación de una máquina virtual Linux</span><span class="sxs-lookup"><span data-stu-id="641e7-144">Create a Linux Virtual Machine</span></span>

<span data-ttu-id="641e7-145">Para crear una nueva máquina virtual Linux primero debemos crear los otros recursos necesarios y asignarles a una configuración.</span><span class="sxs-lookup"><span data-stu-id="641e7-145">To create a new Linux VM we must first create the other required resources and assign them to a configuration.</span></span> <span data-ttu-id="641e7-146">A continuación, podemos usar esa configuración para crear la máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="641e7-146">Then we can use that configuration to create the VM.</span></span> <span data-ttu-id="641e7-147">Se supone que ya ha creado el grupo de recursos como se explicó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="641e7-147">This assumes that you have already created the resource group as previously shown.</span></span> <span data-ttu-id="641e7-148">Además, debe haber una clave pública SSH llamada "`id_rsa.pub`" en el directorio .ssh del perfil de usuario.</span><span class="sxs-lookup"><span data-stu-id="641e7-148">Also, you will need to have an SSH public key named `id_rsa.pub` in the .ssh directory of your user profile.</span></span>

### <a name="create-the-required-network-resources"></a><span data-ttu-id="641e7-149">Creación de los recursos de red necesarios</span><span class="sxs-lookup"><span data-stu-id="641e7-149">Create the required network resources</span></span>

<span data-ttu-id="641e7-150">Primero se debe crear una configuración de subred que se utilizará durante el proceso de creación de la red virtual.</span><span class="sxs-lookup"><span data-stu-id="641e7-150">First we need to create a subnet configuration to be used with the virtual network creation process.</span></span> <span data-ttu-id="641e7-151">También se creará una dirección IP pública para que podamos conectarnos a esta máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="641e7-151">We also create a public IP address so that we can connect to this VM.</span></span> <span data-ttu-id="641e7-152">Se creará un grupo de seguridad de red para proteger el acceso a la dirección pública.</span><span class="sxs-lookup"><span data-stu-id="641e7-152">We create a network security group to secure access to the public address.</span></span> <span data-ttu-id="641e7-153">Por último, se creará la NIC virtual con todos los recursos anteriores.</span><span class="sxs-lookup"><span data-stu-id="641e7-153">Finally we create the virtual NIC using all of the previous resources.</span></span>

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

### <a name="create-the-virtual-machine"></a><span data-ttu-id="641e7-154">Creación de la máquina virtual</span><span class="sxs-lookup"><span data-stu-id="641e7-154">Create the virtual machine</span></span>

<span data-ttu-id="641e7-155">Ahora que tenemos los recursos necesarios, podemos crear la máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="641e7-155">Now that we have the required resources we can create the VM.</span></span> <span data-ttu-id="641e7-156">Para este paso, se creará un objeto de configuración de máquina virtual y, a continuación, se utilizará la configuración para crear la máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="641e7-156">For this step, we create a VM configuration object, then we use the configuration to create the VM.</span></span>

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

<span data-ttu-id="641e7-157">Una vez creada la máquina virtual, puede iniciar sesión en la nueva máquina virtual Linux mediante SSH con la dirección IP pública de la máquina virtual que ha creado:</span><span class="sxs-lookup"><span data-stu-id="641e7-157">Now that the VM has been created, you can log on to your new Linux VM using SSH with the public IP address of the VM you created:</span></span>

```bash
ssh xx.xxx.xxx.xxx
```

```
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

my-login@MyLinuxVM:~$
```

## <a name="creating-other-resources-in-azure"></a><span data-ttu-id="641e7-158">Creación de otros recursos en Azure</span><span class="sxs-lookup"><span data-stu-id="641e7-158">Creating other resources in Azure</span></span>

<span data-ttu-id="641e7-159">Ya se ha visto cómo se crean un grupo de recursos, una máquina virtual Linux y una VM con Windows Server.</span><span class="sxs-lookup"><span data-stu-id="641e7-159">We've now walked through how to create a Resource Group, a Linux VM, and a Windows Server VM.</span></span> <span data-ttu-id="641e7-160">Sin embargo, también se pueden crear muchos otros tipos de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="641e7-160">You can create many other types of Azure resources as well.</span></span>

<span data-ttu-id="641e7-161">Por ejemplo, para crear un equilibrador de carga de red de Azure que luego se pueda asociar con las máquinas virtuales recién creadas, se puede utilizar el siguiente comando create:</span><span class="sxs-lookup"><span data-stu-id="641e7-161">For example, to create an Azure Network Load Balancer that we could then associate with our newly created VMs, we can use the following create command:</span></span>

```powershell
New-AzureRmLoadBalancer -Name MyLoadBalancer -ResourceGroupName myResourceGroup -Location westeurope
```

<span data-ttu-id="641e7-162">También se puede crear una red virtual privada nueva (que se suele denominar "Red virtual" en Azure) para nuestra infraestructura con el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="641e7-162">We could also create a new private Virtual Network (commonly referred to as a "VNet" within Azure) for our infrastructure using the following command:</span></span>

```powershell
$subnetConfig = New-AzureRmVirtualNetworkSubnetConfig -Name mySubnet2 -AddressPrefix 10.0.0.0/16
$vnet = New-AzureRmVirtualNetwork -ResourceGroupName myResourceGroup -Location westeurope `
  -Name MYvNET3 -AddressPrefix 10.0.0.0/16 -Subnet $subnetConfig
```

<span data-ttu-id="641e7-163">Lo que hace que tanto Azure como Azure PowerShell sean muy eficaces, es que se pueden usar no solo para obtener una infraestructura en la nube, sino también para crear servicios de plataforma administrados.</span><span class="sxs-lookup"><span data-stu-id="641e7-163">What makes Azure and the Azure PowerShell powerful is that we can use it not just to get cloud-based infrastructure but also to create managed platform services.</span></span> <span data-ttu-id="641e7-164">Los servicios de plataforma administrados también se pueden combinar con una infraestructura para compilar soluciones aún más eficaces.</span><span class="sxs-lookup"><span data-stu-id="641e7-164">The managed platform services can also be combined with infrastructure to build even more powerful solutions.</span></span>

<span data-ttu-id="641e7-165">Por ejemplo, Azure PowerShell se puede utilizar para crear una instancia de Azure App Service.</span><span class="sxs-lookup"><span data-stu-id="641e7-165">For example, you can use the Azure PowerShell to create an Azure AppService.</span></span> <span data-ttu-id="641e7-166">Azure App Service es un servicio de plataforma administrado que proporciona una manera excelente de hospedar aplicaciones web sin tener que preocuparse de la infraestructura.</span><span class="sxs-lookup"><span data-stu-id="641e7-166">Azure AppService is a managed platform service that provides a great way to host web apps without having to worry about infrastructure.</span></span> <span data-ttu-id="641e7-167">Después de crear la instancia de Azure App Service, se pueden crear dos nuevas instancias de Azure Web Apps en App Service mediante los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="641e7-167">After creating the Azure AppService, you can create two new Azure Web Apps within the AppService using the following commands:</span></span>

```powershell
# Create an Azure AppService that we can host any number of web apps within
New-AzureRmAppServicePlan -Name MyAppServicePlan -Tier Basic -NumberofWorkers 2 -WorkerSize Small -ResourceGroupName myResourceGroup -Location westeurope

# Create Two Web Apps within the AppService (note: name param must be a unique DNS entry)
New-AzureRmWebApp -Name MyWebApp43432 -AppServicePlan MyAppServicePlan -ResourceGroupName myResourceGroup -Location westeurope
New-AzureRmWebApp -Name MyWebApp43433 -AppServicePlan MyAppServicePlan -ResourceGroupName myResourceGroup -Location westeurope
```

## <a name="listing-deployed-resources"></a><span data-ttu-id="641e7-168">Lista de los recursos implementados</span><span class="sxs-lookup"><span data-stu-id="641e7-168">Listing deployed resources</span></span>

<span data-ttu-id="641e7-169">Puede usar el cmdlet `Get-AzureRmResource` para enumerar los recursos que se ejecutan en Azure.</span><span class="sxs-lookup"><span data-stu-id="641e7-169">You can use the `Get-AzureRmResource` cmdlet to list the resources running in Azure.</span></span> <span data-ttu-id="641e7-170">En el ejemplo siguiente se muestran los recursos que acabamos de crear en el nuevo grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="641e7-170">The following example shows the resources we just created in the new resource group.</span></span>

```powershell
Get-AzureRmResource |
  Where-Object ResourceGroupName -eq myResourceGroup |
    Select-Object Name,Location,ResourceType
```

```
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

## <a name="deleting-resources"></a><span data-ttu-id="641e7-171">Eliminación de recursos</span><span class="sxs-lookup"><span data-stu-id="641e7-171">Deleting resources</span></span>

<span data-ttu-id="641e7-172">Para limpiar su cuenta de Azure, debe quitar los recursos que se han creado en este ejemplo.</span><span class="sxs-lookup"><span data-stu-id="641e7-172">To clean up your Azure account, you want to remove the resources we created in this example.</span></span> <span data-ttu-id="641e7-173">Puede usar los cmdlets `Remove-AzureRm*` para eliminar los recursos que ya no necesita.</span><span class="sxs-lookup"><span data-stu-id="641e7-173">You can use the `Remove-AzureRm*` cmdlets to delete the resources you no longer need.</span></span> <span data-ttu-id="641e7-174">Para quitar la máquina virtual Windows que se creó, use el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="641e7-174">To remove the Windows VM we created, using the following command:</span></span>

```powershell
Remove-AzureRmVM -Name myWindowsVM -ResourceGroupName myResourceGroup
```

<span data-ttu-id="641e7-175">Se le pedirá que confirme que desea eliminar el recurso.</span><span class="sxs-lookup"><span data-stu-id="641e7-175">You will be prompted to confirm that you want to remove the resource.</span></span>

```
Confirm
Are you sure you want to remove resource group 'myResourceGroup'
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
```

<span data-ttu-id="641e7-176">Puede también utilizar la eliminación de muchos recursos al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="641e7-176">You can also use the delete many resources at one time.</span></span> <span data-ttu-id="641e7-177">Por ejemplo, el siguiente comando permite eliminar todo el grupo de recursos "MyResourceGroup" que hemos usado en todos los ejemplos de este tutorial de introducción.</span><span class="sxs-lookup"><span data-stu-id="641e7-177">For example, the following command deletes all the resource group "MyResourceGroup" that we've used for all the samples in this Get Started tutorial.</span></span> <span data-ttu-id="641e7-178">Esto eliminará el grupo de recursos y todos los recursos que contiene.</span><span class="sxs-lookup"><span data-stu-id="641e7-178">This removes the resource group and all of the resources in it.</span></span>

```powershell
Remove-AzureRmResourceGroup -Name myResourceGroup
```

```
Confirm
Are you sure you want to remove resource group 'myResourceGroup'
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
```

<span data-ttu-id="641e7-179">Este proceso puede tardar varios minutos en completarse.</span><span class="sxs-lookup"><span data-stu-id="641e7-179">This can take several minutes to complete.</span></span>

## <a name="get-samples"></a><span data-ttu-id="641e7-180">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="641e7-180">Get samples</span></span>

<span data-ttu-id="641e7-181">Para más información sobre cómo usar Azure PowerShell, consulte nuestros scripts más comunes para [máquinas virtuales Linux](/azure/virtual-machines/virtual-machines-linux-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [máquinas virtuales Windows](/azure/virtual-machines/virtual-machines-windows-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [aplicaciones web](/azure/app-service-web/app-service-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json) y [bases de datos de SQL Database](/azure/sql-database/sql-database-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json).</span><span class="sxs-lookup"><span data-stu-id="641e7-181">To learn more about ways to use the Azure PowerShell, check out our most common scripts for [Linux VMs](/azure/virtual-machines/virtual-machines-linux-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [Windows VMs](/azure/virtual-machines/virtual-machines-windows-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [Web Apps](/azure/app-service-web/app-service-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), and [SQL Databases](/azure/sql-database/sql-database-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json).</span></span>

## <a name="next-steps"></a><span data-ttu-id="641e7-182">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="641e7-182">Next steps</span></span>

* [<span data-ttu-id="641e7-183">Inicio de sesión con Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="641e7-183">Login with Azure PowerShell</span></span>](authenticate-azureps.md)
* [<span data-ttu-id="641e7-184">Administración de suscripciones de Azure con Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="641e7-184">Manage Azure subscriptions with Azure PowerShell</span></span>](manage-subscriptions-azureps.md)
* [<span data-ttu-id="641e7-185">Creación de entidades de servicio en Azure con Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="641e7-185">Create service principals in Azure using Azure PowerShell</span></span>](create-azure-service-principal-azureps.md)
* <span data-ttu-id="641e7-186">Lea las notas de la versión sobre la migración desde una versión anterior: [https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes](https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes).</span><span class="sxs-lookup"><span data-stu-id="641e7-186">Read the Release notes about migrating from an older release: [https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes](https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes).</span></span>
* <span data-ttu-id="641e7-187">Consiga ayuda de la comunidad:</span><span class="sxs-lookup"><span data-stu-id="641e7-187">Get help from the community:</span></span>
  + [<span data-ttu-id="641e7-188">Foro de Azure en MSDN</span><span class="sxs-lookup"><span data-stu-id="641e7-188">Azure forum on MSDN</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=320212)
  + [<span data-ttu-id="641e7-189">stackoverflow</span><span class="sxs-lookup"><span data-stu-id="641e7-189">stackoverflow</span></span>](http://go.microsoft.com/fwlink/?LinkId=320213)
