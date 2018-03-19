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
ms.date: 11/15/2017
ms.openlocfilehash: af1eccfffed551e6025014e2fd9287f3e6ebf425
ms.sourcegitcommit: 20af779cd523c758d40e23d60eb989a4ef982d5c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2018
---
# <a name="getting-started-with-azure-powershell"></a><span data-ttu-id="96e7d-102">Introducción a Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="96e7d-102">Getting started with Azure PowerShell</span></span>

<span data-ttu-id="96e7d-103">Azure PowerShell está diseñado para administrar recursos de Azure desde la línea de comandos y para generar scripts de automatización que funcionan con Azure Resource Manager.</span><span class="sxs-lookup"><span data-stu-id="96e7d-103">Azure PowerShell is designed for managing and administering Azure resources from the command line, and for building automation scripts that work against the Azure Resource Manager.</span></span> <span data-ttu-id="96e7d-104">Se puede usar en el explorador con [Azure Cloud Shell](/azure/cloud-shell/overview), o lo puede instalar en el equipo local y usarlo en cualquier sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="96e7d-104">You can use it in your browser with [Azure Cloud Shell](/azure/cloud-shell/overview), or you can install it on your local machine and use it in any PowerShell session.</span></span> <span data-ttu-id="96e7d-105">Este artículo le ayuda a empezar a usarlo y explica los conceptos básicos que hay detrás.</span><span class="sxs-lookup"><span data-stu-id="96e7d-105">This article helps get you started using it, and teaches you the core concepts behind it.</span></span>

## <a name="connect"></a><span data-ttu-id="96e7d-106">Conectar</span><span class="sxs-lookup"><span data-stu-id="96e7d-106">Connect</span></span>

<span data-ttu-id="96e7d-107">La manera más sencilla de empezar es [iniciar Cloud Shell](/azure/cloud-shell/quickstart).</span><span class="sxs-lookup"><span data-stu-id="96e7d-107">The simplest way to get started is to [launch Cloud Shell](/azure/cloud-shell/quickstart).</span></span>

1. <span data-ttu-id="96e7d-108">Inicie Cloud Shell en la navegación superior de Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="96e7d-108">Launch Cloud Shell from the top navigation of the Azure portal.</span></span>

   ![Icono de Shell](~/media/get-started-azureps/shell-icon.png)

2. <span data-ttu-id="96e7d-110">Elija la suscripción que desea utilizar y cree una cuenta de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="96e7d-110">Choose the subscription you want to use and create a storage account.</span></span>

   ![Crear una cuenta de almacenamiento](~/media/get-started-azureps/storage-prompt.png)

<span data-ttu-id="96e7d-112">Una vez que se haya creado el almacenamiento, Cloud Shell abrirá una sesión de PowerShell en el explorador.</span><span class="sxs-lookup"><span data-stu-id="96e7d-112">Once your storage has been created, the Cloud Shell will open a PowerShell session in the browser.</span></span>

![Cloud Shell para PowerShell](~/media/get-started-azureps/cloud-powershell.png)

<span data-ttu-id="96e7d-114">También puede instalar Azure PowerShell y usarlo de forma local en una sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="96e7d-114">You can also install Azure PowerShell and use it locally in a PowerShell session.</span></span>

## <a name="install-azure-powershell"></a><span data-ttu-id="96e7d-115">Instalar Azure Powershell</span><span class="sxs-lookup"><span data-stu-id="96e7d-115">Install Azure PowerShell</span></span>

<span data-ttu-id="96e7d-116">El primer paso es asegurarse de que está instalada la versión más reciente de Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="96e7d-116">The first step is to make sure you have the latest version of the Azure PowerShell installed.</span></span> <span data-ttu-id="96e7d-117">Para más información sobre la versión más reciente, consulte las [notas de la versión](./release-notes-azureps.md).</span><span class="sxs-lookup"><span data-stu-id="96e7d-117">For information about the latest release, see the [release notes](./release-notes-azureps.md).</span></span>

1. <span data-ttu-id="96e7d-118">[Instale Azure PowerShell](install-azurerm-ps.md).</span><span class="sxs-lookup"><span data-stu-id="96e7d-118">[Install Azure PowerShell](install-azurerm-ps.md).</span></span>

2. <span data-ttu-id="96e7d-119">Para comprobar que la instalación se realizó correctamente, ejecute `Get-Module AzureRM -ListAvailable` desde la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="96e7d-119">To verify the installation was successful, run `Get-Module AzureRM -ListAvailable` from your command line.</span></span>

## <a name="log-in-to-azure"></a><span data-ttu-id="96e7d-120">Inicio de sesión en Azure</span><span class="sxs-lookup"><span data-stu-id="96e7d-120">Log in to Azure</span></span>

<span data-ttu-id="96e7d-121">Inicie sesión de forma interactiva:</span><span class="sxs-lookup"><span data-stu-id="96e7d-121">Sign on interactively:</span></span>

1. <span data-ttu-id="96e7d-122">Escriba `Login-AzureRmAccount`.</span><span class="sxs-lookup"><span data-stu-id="96e7d-122">Type `Login-AzureRmAccount`.</span></span> <span data-ttu-id="96e7d-123">Aparecerá un cuadro de diálogo que le pide sus credenciales de Azure.</span><span class="sxs-lookup"><span data-stu-id="96e7d-123">You will get dialog box asking for your Azure credentials.</span></span> <span data-ttu-id="96e7d-124">La opción "-EnvironmentName" puede permitirle iniciar sesión en Azure China o Azure Alemania.</span><span class="sxs-lookup"><span data-stu-id="96e7d-124">Option '-EnvironmentName' can let you login in Azure China or Azure Germany.</span></span>

   <span data-ttu-id="96e7d-125">Por ejemplo, Login-AzureRmAccount -EnvironmentName AzureChinaCloud</span><span class="sxs-lookup"><span data-stu-id="96e7d-125">e.g. Login-AzureRmAccount -EnvironmentName AzureChinaCloud</span></span>

2. <span data-ttu-id="96e7d-126">Escriba la dirección de correo electrónico y la contraseña asociadas a su cuenta.</span><span class="sxs-lookup"><span data-stu-id="96e7d-126">Type the email address and password associated with your account.</span></span> <span data-ttu-id="96e7d-127">Azure autentica y guarda las credenciales y, luego, cierra la ventana.</span><span class="sxs-lookup"><span data-stu-id="96e7d-127">Azure authenticates and saves the credential information, and then closes the window.</span></span>

<span data-ttu-id="96e7d-128">Una vez que haya iniciado sesión en una cuenta de Azure, puede usar los cmdlets de Azure PowerShell para acceder y administrar los recursos de la suscripción.</span><span class="sxs-lookup"><span data-stu-id="96e7d-128">Once you have signed in to an Azure account, you can use the Azure PowerShell cmdlets to access and manager the resources in your subscription.</span></span>

## <a name="create-a-windows-virtual-machine-using-simple-defaults"></a><span data-ttu-id="96e7d-129">Creación de una máquina virtual Windows con valores predeterminados sencillos</span><span class="sxs-lookup"><span data-stu-id="96e7d-129">Create a Windows virtual machine using simple defaults</span></span>

<span data-ttu-id="96e7d-130">El cmdlet `New-AzureRmVM` proporciona una sintaxis simplificada que facilita el proceso de creación de una nueva máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="96e7d-130">The `New-AzureRmVM` cmdlet provides a simplified syntax making it easy to create a new virtual machine.</span></span> <span data-ttu-id="96e7d-131">Solo tiene que proporcionar dos valores de parámetro: el nombre de la máquina virtual y un conjunto de credenciales para la cuenta de administrador local en la máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="96e7d-131">There are only two parameter values you must provide: the name of the VM and a set of credentials for the local administrator account on the VM.</span></span>

<span data-ttu-id="96e7d-132">En primer lugar, cree el objeto de credenciales.</span><span class="sxs-lookup"><span data-stu-id="96e7d-132">First, create the credential object.</span></span>

```powershell
$cred = Get-Credential -Message "Enter a username and password for the virtual machine."
```

```Output
Windows PowerShell credential request.
Enter a username and password for the virtual machine.
User: localAdmin
Password for user localAdmin: *********
```
<span data-ttu-id="96e7d-133">Después, cree la máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="96e7d-133">Next, create the VM.</span></span>

```powershell
New-AzureRmVM -Name SampleVM -Credential $cred
```

```Output
ResourceGroupName        : SampleVM
Id                       : /subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/SampleVM/providers/Microsoft.Compute/virtualMachines/SampleVM
VmId                     : 43f6275d-ce50-49c8-a831-5d5974006e63
Name                     : SampleVM
Type                     : Microsoft.Compute/virtualMachines
Location                 : eastus
Tags                     : {}
HardwareProfile          : {VmSize}
NetworkProfile           : {NetworkInterfaces}
OSProfile                : {ComputerName, AdminUsername, WindowsConfiguration, Secrets}
ProvisioningState        : Succeeded
StorageProfile           : {ImageReference, OsDisk, DataDisks}
FullyQualifiedDomainName : samplevm-2c0867.eastus.cloudapp.azure.com
```

<span data-ttu-id="96e7d-134">Eso es fácil.</span><span class="sxs-lookup"><span data-stu-id="96e7d-134">That was easy.</span></span> <span data-ttu-id="96e7d-135">Sin embargo, quizás se pregunte qué más se crea y cómo se configura la máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="96e7d-135">But, you may wonder what else is created and how is the VM configured.</span></span> <span data-ttu-id="96e7d-136">Primero, echemos un vistazo a nuestro grupos de recursos.</span><span class="sxs-lookup"><span data-stu-id="96e7d-136">First, let's look at our resource groups.</span></span>

```powershell
Get-AzureRmResourceGroup | Select-Object ResourceGroupName,Location
```

```Output
ResourceGroupName          Location
-----------------          --------
cloud-shell-storage-westus westus
SampleVM                   eastus
```

<span data-ttu-id="96e7d-137">El grupo de recursos **cloud-shell-storage-westus** se crea la primera vez que se usa Cloud Shell.</span><span class="sxs-lookup"><span data-stu-id="96e7d-137">The **cloud-shell-storage-westus** resource group is created the first time you use the Cloud Shell.</span></span> <span data-ttu-id="96e7d-138">El grupo de recursos **SampleVM** se crea con el cmdlet `New-AzureRmVM`.</span><span class="sxs-lookup"><span data-stu-id="96e7d-138">The **SampleVM** resource group was created by the `New-AzureRmVM` cmdlet.</span></span>

<span data-ttu-id="96e7d-139">Ahora, ¿qué otros recursos se crearon en este nuevo grupo de recursos?</span><span class="sxs-lookup"><span data-stu-id="96e7d-139">Now, what other resources were created in this new resource group?</span></span>

```powershell
Get-AzureRmResource |
  Where ResourceGroupName -eq SampleVM |
    Select-Object ResourceGroupName,Location,ResourceType,Name
```

```Output
ResourceGroupName          Location ResourceType                            Name
-----------------          -------- ------------                            ----
SAMPLEVM                   eastus   Microsoft.Compute/disks                 SampleVM_OsDisk_1_9b286c54b168457fa1f8c47...
SampleVM                   eastus   Microsoft.Compute/virtualMachines       SampleVM
SampleVM                   eastus   Microsoft.Network/networkInterfaces     SampleVM
SampleVM                   eastus   Microsoft.Network/networkSecurityGroups SampleVM
SampleVM                   eastus   Microsoft.Network/publicIPAddresses     SampleVM
SampleVM                   eastus   Microsoft.Network/virtualNetworks       SampleVM
```

<span data-ttu-id="96e7d-140">Vamos a obtener más información acerca de la máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="96e7d-140">Let's get some more details about the VM.</span></span> <span data-ttu-id="96e7d-141">En este ejemplo se muestra cómo recuperar información acerca de la imagen de sistema operativo utilizada para crear la máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="96e7d-141">This examples shows how to retrieve information about the OS Image used to create the VM.</span></span>

```powershell
Get-AzureRmVM -Name SampleVM -ResourceGroupName SampleVM |
  Select-Object -ExpandProperty StorageProfile |
    Select-Object -ExpandProperty ImageReference
```

```Output
Publisher : MicrosoftWindowsServer
Offer     : WindowsServer
Sku       : 2016-Datacenter
Version   : latest
Id        :
```

## <a name="create-a-fully-configured-linux-virtual-machine"></a><span data-ttu-id="96e7d-142">Creación de una máquina virtual Linux completamente configurada</span><span class="sxs-lookup"><span data-stu-id="96e7d-142">Create a fully configured Linux Virtual Machine</span></span>

<span data-ttu-id="96e7d-143">En el ejemplo anterior, se utilizaban los valores de parámetro predeterminados y la sintaxis simplificada para crear una máquina virtual Windows.</span><span class="sxs-lookup"><span data-stu-id="96e7d-143">The previous example used the simplified syntax and default parameter values to create a Windows virtual machine.</span></span> <span data-ttu-id="96e7d-144">En este ejemplo, proporcionamos los valores de todas las opciones de la máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="96e7d-144">In this example, we provide values for all options of the virtual machine.</span></span>

### <a name="create-a-resource-group"></a><span data-ttu-id="96e7d-145">Crear un grupo de recursos</span><span class="sxs-lookup"><span data-stu-id="96e7d-145">Create a resource group</span></span>

<span data-ttu-id="96e7d-146">Para este ejemplo, queremos crear un grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="96e7d-146">For this example we want to create a Resource Group.</span></span> <span data-ttu-id="96e7d-147">En Azure, los grupos de recursos proporcionan una manera de administrar varios recursos que se desean agrupar lógicamente.</span><span class="sxs-lookup"><span data-stu-id="96e7d-147">Resource Groups in Azure provide a way to manage multiple resources that you want to logically group together.</span></span> <span data-ttu-id="96e7d-148">Por ejemplo, puede crear un grupo de recursos para una aplicación o un proyecto, y agregar una máquina virtual, una base de datos y un servicio de CDN en él.</span><span class="sxs-lookup"><span data-stu-id="96e7d-148">For example, you might create a Resource Group for an application or project and add a virtual machine, a database and a CDN service within it.</span></span>

<span data-ttu-id="96e7d-149">Vamos a crear un grupo de recursos denominado "MyResourceGroup" en la región europaoccidental de Azure.</span><span class="sxs-lookup"><span data-stu-id="96e7d-149">Let's create a resource group named "MyResourceGroup" in the westeurope region of Azure.</span></span> <span data-ttu-id="96e7d-150">Para ello, escriba el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="96e7d-150">To do so type the following command:</span></span>

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

<span data-ttu-id="96e7d-151">Este nuevo grupo de recursos se utilizará para contener todos los recursos necesarios para la nueva máquina virtual que creemos.</span><span class="sxs-lookup"><span data-stu-id="96e7d-151">This new resource group will be used to contain all of the resources needed for the new VM we create.</span></span> <span data-ttu-id="96e7d-152">Para crear una nueva máquina virtual Linux primero debemos crear los otros recursos necesarios y asignarles a una configuración.</span><span class="sxs-lookup"><span data-stu-id="96e7d-152">To create a new Linux VM we must first create the other required resources and assign them to a configuration.</span></span> <span data-ttu-id="96e7d-153">A continuación, podemos usar esa configuración para crear la máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="96e7d-153">Then we can use that configuration to create the VM.</span></span> <span data-ttu-id="96e7d-154">Además, debe haber una clave pública SSH llamada "`id_rsa.pub`" en el directorio .ssh del perfil de usuario.</span><span class="sxs-lookup"><span data-stu-id="96e7d-154">Also, you will need to have an SSH public key named `id_rsa.pub` in the .ssh directory of your user profile.</span></span>

#### <a name="create-the-required-network-resources"></a><span data-ttu-id="96e7d-155">Creación de los recursos de red necesarios</span><span class="sxs-lookup"><span data-stu-id="96e7d-155">Create the required network resources</span></span>

<span data-ttu-id="96e7d-156">Primero se debe crear una configuración de subred que se utilizará durante el proceso de creación de la red virtual.</span><span class="sxs-lookup"><span data-stu-id="96e7d-156">First we need to create a subnet configuration to be used with the virtual network creation process.</span></span> <span data-ttu-id="96e7d-157">También se creará una dirección IP pública para que podamos conectarnos a esta máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="96e7d-157">We also create a public IP address so that we can connect to this VM.</span></span> <span data-ttu-id="96e7d-158">Se creará un grupo de seguridad de red para proteger el acceso a la dirección pública.</span><span class="sxs-lookup"><span data-stu-id="96e7d-158">We create a network security group to secure access to the public address.</span></span> <span data-ttu-id="96e7d-159">Por último, se creará la NIC virtual con todos los recursos anteriores.</span><span class="sxs-lookup"><span data-stu-id="96e7d-159">Finally we create the virtual NIC using all of the previous resources.</span></span>

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

### <a name="create-the-vm-configuration"></a><span data-ttu-id="96e7d-160">Creación de la configuración de máquina virtual</span><span class="sxs-lookup"><span data-stu-id="96e7d-160">Create the VM configuration</span></span>

<span data-ttu-id="96e7d-161">Ahora que tenemos los recursos necesarios, podemos crear el objeto de configuración de máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="96e7d-161">Now that we have the required resources we can create the VM configuration oboject.</span></span>

```powershell
# Create a virtual machine configuration
$vmConfig = New-AzureRmVMConfig -VMName $vmName -VMSize Standard_D1 |
  Set-AzureRmVMOperatingSystem -Linux -ComputerName $vmName -Credential $cred -DisablePasswordAuthentication |
  Set-AzureRmVMSourceImage -PublisherName Canonical -Offer UbuntuServer -Skus 14.04.2-LTS -Version latest |
  Add-AzureRmVMNetworkInterface -Id $nic.Id

# Configure SSH Keys
$sshPublicKey = Get-Content "$env:USERPROFILE\.ssh\id_rsa.pub"
Add-AzureRmVMSshPublicKey -VM $vmConfig -KeyData $sshPublicKey -Path "/home/azureuser/.ssh/authorized_keys"
```

### <a name="create-the-virtual-machine"></a><span data-ttu-id="96e7d-162">Creación de la máquina virtual</span><span class="sxs-lookup"><span data-stu-id="96e7d-162">Create the virtual machine</span></span>

<span data-ttu-id="96e7d-163">Ahora podemos crear la máquina virtual con el objeto de configuración de máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="96e7d-163">Now we can create the VM using the VM configuration object.</span></span>

```powershell
New-AzureRmVM -ResourceGroupName $resourceGroup -Location $location -VM $vmConfig
```

<span data-ttu-id="96e7d-164">Una vez creada la máquina virtual, puede iniciar sesión en la nueva máquina virtual Linux mediante SSH con la dirección IP pública de la máquina virtual que ha creado:</span><span class="sxs-lookup"><span data-stu-id="96e7d-164">Now that the VM has been created, you can log on to your new Linux VM using SSH with the public IP address of the VM you created:</span></span>

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

## <a name="creating-other-resources-in-azure"></a><span data-ttu-id="96e7d-165">Creación de otros recursos en Azure</span><span class="sxs-lookup"><span data-stu-id="96e7d-165">Creating other resources in Azure</span></span>

<span data-ttu-id="96e7d-166">Ya se ha visto cómo se crean un grupo de recursos, una máquina virtual Linux y una VM con Windows Server.</span><span class="sxs-lookup"><span data-stu-id="96e7d-166">We've now walked through how to create a Resource Group, a Linux VM, and a Windows Server VM.</span></span> <span data-ttu-id="96e7d-167">Sin embargo, también se pueden crear muchos otros tipos de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="96e7d-167">You can create many other types of Azure resources as well.</span></span>

<span data-ttu-id="96e7d-168">Por ejemplo, para crear un equilibrador de carga de red de Azure que luego se pueda asociar con las máquinas virtuales recién creadas, se puede utilizar el siguiente comando create:</span><span class="sxs-lookup"><span data-stu-id="96e7d-168">For example, to create an Azure Network Load Balancer that we could then associate with our newly created VMs, we can use the following create command:</span></span>

```powershell
New-AzureRmLoadBalancer -Name MyLoadBalancer -ResourceGroupName myResourceGroup -Location westeurope
```

<span data-ttu-id="96e7d-169">También se puede crear una red virtual privada nueva (que se suele denominar "Virtual Network" en Azure) para nuestra infraestructura con el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="96e7d-169">We could also create a new private Virtual Network (commonly referred to as a "VNet" within Azure) for our infrastructure using the following command:</span></span>

```powershell
$subnetConfig = New-AzureRmVirtualNetworkSubnetConfig -Name mySubnet2 -AddressPrefix 10.0.0.0/16
$vnet = New-AzureRmVirtualNetwork -ResourceGroupName myResourceGroup -Location westeurope `
  -Name MYvNET3 -AddressPrefix 10.0.0.0/16 -Subnet $subnetConfig
```

<span data-ttu-id="96e7d-170">Lo que hace que tanto Azure como Azure PowerShell sean muy eficaces, es que se pueden usar no solo para obtener una infraestructura en la nube, sino también para crear servicios de plataforma administrados.</span><span class="sxs-lookup"><span data-stu-id="96e7d-170">What makes Azure and the Azure PowerShell powerful is that we can use it not just to get cloud-based infrastructure but also to create managed platform services.</span></span> <span data-ttu-id="96e7d-171">Los servicios de plataforma administrados también se pueden combinar con una infraestructura para compilar soluciones aún más eficaces.</span><span class="sxs-lookup"><span data-stu-id="96e7d-171">The managed platform services can also be combined with infrastructure to build even more powerful solutions.</span></span>

<span data-ttu-id="96e7d-172">Por ejemplo, Azure PowerShell se puede utilizar para crear una instancia de Azure App Service.</span><span class="sxs-lookup"><span data-stu-id="96e7d-172">For example, you can use the Azure PowerShell to create an Azure AppService.</span></span> <span data-ttu-id="96e7d-173">Azure App Service es un servicio de plataforma administrado que proporciona una manera excelente de hospedar aplicaciones web sin tener que preocuparse de la infraestructura.</span><span class="sxs-lookup"><span data-stu-id="96e7d-173">Azure AppService is a managed platform service that provides a great way to host web apps without having to worry about infrastructure.</span></span> <span data-ttu-id="96e7d-174">Después de crear la instancia de Azure App Service, se pueden crear dos nuevas instancias de Azure Web Apps en App Service mediante los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="96e7d-174">After creating the Azure AppService, you can create two new Azure Web Apps within the AppService using the following commands:</span></span>

```powershell
# Create an Azure AppService that we can host any number of web apps within
New-AzureRmAppServicePlan -Name MyAppServicePlan -Tier Basic -NumberofWorkers 2 -WorkerSize Small -ResourceGroupName myResourceGroup -Location westeurope

# Create Two Web Apps within the AppService (note: name param must be a unique DNS entry)
New-AzureRmWebApp -Name MyWebApp43432 -AppServicePlan MyAppServicePlan -ResourceGroupName myResourceGroup -Location westeurope
New-AzureRmWebApp -Name MyWebApp43433 -AppServicePlan MyAppServicePlan -ResourceGroupName myResourceGroup -Location westeurope
```

## <a name="listing-deployed-resources"></a><span data-ttu-id="96e7d-175">Lista de los recursos implementados</span><span class="sxs-lookup"><span data-stu-id="96e7d-175">Listing deployed resources</span></span>

<span data-ttu-id="96e7d-176">Puede usar el cmdlet `Get-AzureRmResource` para enumerar los recursos que se ejecutan en Azure.</span><span class="sxs-lookup"><span data-stu-id="96e7d-176">You can use the `Get-AzureRmResource` cmdlet to list the resources running in Azure.</span></span> <span data-ttu-id="96e7d-177">En el ejemplo siguiente se muestran los recursos que acabamos de crear en el nuevo grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="96e7d-177">The following example shows the resources we just created in the new resource group.</span></span>

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

## <a name="deleting-resources"></a><span data-ttu-id="96e7d-178">Eliminación de recursos</span><span class="sxs-lookup"><span data-stu-id="96e7d-178">Deleting resources</span></span>

<span data-ttu-id="96e7d-179">Para limpiar su cuenta de Azure, debe quitar los recursos que se han creado en este ejemplo.</span><span class="sxs-lookup"><span data-stu-id="96e7d-179">To clean up your Azure account, you want to remove the resources we created in this example.</span></span> <span data-ttu-id="96e7d-180">Puede usar los cmdlets `Remove-AzureRm*` para eliminar los recursos que ya no necesita.</span><span class="sxs-lookup"><span data-stu-id="96e7d-180">You can use the `Remove-AzureRm*` cmdlets to delete the resources you no longer need.</span></span> <span data-ttu-id="96e7d-181">Para quitar la máquina virtual Windows que se creó, use el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="96e7d-181">To remove the Windows VM we created, using the following command:</span></span>

```powershell
Remove-AzureRmVM -Name myWindowsVM -ResourceGroupName myResourceGroup
```

<span data-ttu-id="96e7d-182">Se le pedirá que confirme que desea eliminar el recurso.</span><span class="sxs-lookup"><span data-stu-id="96e7d-182">You will be prompted to confirm that you want to remove the resource.</span></span>

```Output
Confirm
Are you sure you want to remove resource group 'myResourceGroup'
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
```

<span data-ttu-id="96e7d-183">Puede también utilizar la eliminación de muchos recursos al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="96e7d-183">You can also use the delete many resources at one time.</span></span> <span data-ttu-id="96e7d-184">Por ejemplo, el siguiente comando permite eliminar todo el grupo de recursos "MyResourceGroup" que hemos usado en todos los ejemplos de este tutorial de introducción.</span><span class="sxs-lookup"><span data-stu-id="96e7d-184">For example, the following command deletes all the resource group "MyResourceGroup" that we've used for all the samples in this Get Started tutorial.</span></span> <span data-ttu-id="96e7d-185">Esto eliminará el grupo de recursos y todos los recursos que contiene.</span><span class="sxs-lookup"><span data-stu-id="96e7d-185">This removes the resource group and all of the resources in it.</span></span>

```powershell
Remove-AzureRmResourceGroup -Name myResourceGroup
```

```Output
Confirm
Are you sure you want to remove resource group 'myResourceGroup'
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
```

<span data-ttu-id="96e7d-186">Este proceso puede tardar varios minutos en completarse.</span><span class="sxs-lookup"><span data-stu-id="96e7d-186">This can take several minutes to complete.</span></span>

## <a name="get-samples"></a><span data-ttu-id="96e7d-187">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="96e7d-187">Get samples</span></span>

<span data-ttu-id="96e7d-188">Para más información sobre cómo usar Azure PowerShell, consulte nuestros scripts más comunes para [máquinas virtuales Linux](/azure/virtual-machines/virtual-machines-linux-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [máquinas virtuales Windows](/azure/virtual-machines/virtual-machines-windows-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [Web Apps](/azure/app-service-web/app-service-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json) y [SQL Database](/azure/sql-database/sql-database-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json).</span><span class="sxs-lookup"><span data-stu-id="96e7d-188">To learn more about ways to use the Azure PowerShell, check out our most common scripts for [Linux VMs](/azure/virtual-machines/virtual-machines-linux-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [Windows VMs](/azure/virtual-machines/virtual-machines-windows-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [Web Apps](/azure/app-service-web/app-service-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), and [SQL Databases](/azure/sql-database/sql-database-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json).</span></span>

## <a name="next-steps"></a><span data-ttu-id="96e7d-189">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="96e7d-189">Next steps</span></span>

* [<span data-ttu-id="96e7d-190">Inicio de sesión con Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="96e7d-190">Login with Azure PowerShell</span></span>](authenticate-azureps.md)
* [<span data-ttu-id="96e7d-191">Administración de suscripciones de Azure con Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="96e7d-191">Manage Azure subscriptions with Azure PowerShell</span></span>](manage-subscriptions-azureps.md)
* [<span data-ttu-id="96e7d-192">Creación de entidades de servicio en Azure con Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="96e7d-192">Create service principals in Azure using Azure PowerShell</span></span>](create-azure-service-principal-azureps.md)
* <span data-ttu-id="96e7d-193">Consulte las notas de la versión sobre la migración desde una versión anterior: [https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes](https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes).</span><span class="sxs-lookup"><span data-stu-id="96e7d-193">Read the Release notes about migrating from an older release: [https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes](https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes).</span></span>
* <span data-ttu-id="96e7d-194">Consiga ayuda de la comunidad:</span><span class="sxs-lookup"><span data-stu-id="96e7d-194">Get help from the community:</span></span>
  * [<span data-ttu-id="96e7d-195">Foro de Azure en MSDN</span><span class="sxs-lookup"><span data-stu-id="96e7d-195">Azure forum on MSDN</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=320212)
  * [<span data-ttu-id="96e7d-196">stackoverflow</span><span class="sxs-lookup"><span data-stu-id="96e7d-196">stackoverflow</span></span>](http://go.microsoft.com/fwlink/?LinkId=320213)
