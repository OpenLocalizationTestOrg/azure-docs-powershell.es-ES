---
title: "Uso de los módulos experimentales de Azure PowerShell"
description: "Filosofía y uso de los módulos experimentales de Azure PowerShell."
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 09/05/2017
ms.openlocfilehash: 4a8a74977440fa89b89843bbc95e43d622a58474
ms.sourcegitcommit: e6b7e20bbd04eda51416c56b13f867102b602d1a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2017
---
# <a name="using-experimental-azure-powershell-modules"></a><span data-ttu-id="cebc0-103">Uso de los módulos experimentales de Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="cebc0-103">Using experimental Azure PowerShell modules</span></span>

<span data-ttu-id="cebc0-104">Haciendo especial hincapié en las herramientas de desarrollador (especialmente las CLI) de Azure, el equipo de Azure PowerShell está realizando experimentos para mejorar la experiencia de este servicio.</span><span class="sxs-lookup"><span data-stu-id="cebc0-104">With the emphasis on developer tools (especially CLIs) in Azure, the Azure PowerShell team is experimenting with many improvements to the Azure PowerShell experience.</span></span>

## <a name="experimentation-methodology"></a><span data-ttu-id="cebc0-105">Metodología de experimentación</span><span class="sxs-lookup"><span data-stu-id="cebc0-105">Experimentation methodology</span></span>

<span data-ttu-id="cebc0-106">Para facilitar la experimentación, vamos a crear nuevos módulos de Azure PowerShell que implementan la funcionalidad de Azure SDK existente de nuevas y sencillas maneras.</span><span class="sxs-lookup"><span data-stu-id="cebc0-106">To facilitate experimentation, we are creating new Azure PowerShell modules that implement existing Azure SDK functionality in new, easier to use ways.</span></span> <span data-ttu-id="cebc0-107">En la mayoría de los casos los cmdlets son idénticos a los cmdlets existentes.</span><span class="sxs-lookup"><span data-stu-id="cebc0-107">In most cases, the cmdlets exactly mirror existing cmdlets.</span></span> <span data-ttu-id="cebc0-108">Sin embargo, los cmdlets experimentales proporcionan una notación abreviada y valores predeterminados más inteligentes que facilitan la creación y administración de los recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="cebc0-108">However, the experimental cmdlets provide a shorthand notation and smarter default values that make it easier to create and manage Azure resources.</span></span>

<span data-ttu-id="cebc0-109">Estos módulos se pueden instalar en paralelo con módulos de Azure PowerShell existentes.</span><span class="sxs-lookup"><span data-stu-id="cebc0-109">These modules can be installed side-by-side with existing Azure PowerShell modules.</span></span> <span data-ttu-id="cebc0-110">Los nombres de cmdlet se han abreviado para proporcionar nombres más cortos y evitar conflictos de nombres con los cmdlets no experimentales existentes.</span><span class="sxs-lookup"><span data-stu-id="cebc0-110">The cmdlet names have been shortened to provide shorter names and avoid name conflicts with existing, non-experimental cmdlets.</span></span>

<span data-ttu-id="cebc0-111">Los módulos experimentales utilizan la convención de nomenclatura siguiente:</span><span class="sxs-lookup"><span data-stu-id="cebc0-111">The experimental modules use the following naming convention:</span></span>

- <span data-ttu-id="cebc0-112">AzureRM.Compute.Experiments</span><span class="sxs-lookup"><span data-stu-id="cebc0-112">AzureRM.Compute.Experiments</span></span>
- <span data-ttu-id="cebc0-113">AzureRM.Websites.Experiments</span><span class="sxs-lookup"><span data-stu-id="cebc0-113">AzureRM.Websites.Experiments</span></span>

<span data-ttu-id="cebc0-114">Esta convención de nomenclatura es similar a la nomenclatura de los módulos de la versión preliminar: `AzureRM.*.Preview`.</span><span class="sxs-lookup"><span data-stu-id="cebc0-114">This naming convention is similar to the naming of Preview modules: `AzureRM.*.Preview`.</span></span> <span data-ttu-id="cebc0-115">Los módulos de la versión preliminar son diferentes a los módulos experimentales.</span><span class="sxs-lookup"><span data-stu-id="cebc0-115">Preview modules differ from experimental modules.</span></span> <span data-ttu-id="cebc0-116">Los módulos de la versión preliminar implementan la nueva funcionalidad de los servicios de Azure que solo está disponible como oferta en esta versión.</span><span class="sxs-lookup"><span data-stu-id="cebc0-116">Preview modules implement new functionality of Azure services that is only available as a Preview offering.</span></span> <span data-ttu-id="cebc0-117">Los módulos de la versión preliminar reemplazan los módulos de Azure PowerShell existentes y usan el mismo cmdlet y los mismos nombres de parámetro.</span><span class="sxs-lookup"><span data-stu-id="cebc0-117">Preview modules replace existing Azure PowerShell modules and use the same cmdlet and parameter names.</span></span>

## <a name="how-to-install-an-experimental-module"></a><span data-ttu-id="cebc0-118">Instalación de un módulo experimental</span><span class="sxs-lookup"><span data-stu-id="cebc0-118">How to install an experimental module</span></span>

<span data-ttu-id="cebc0-119">Los módulos experimentales se publican en la Galería de PowerShell al igual que los módulos de Azure PowerShell existentes.</span><span class="sxs-lookup"><span data-stu-id="cebc0-119">Experimental modules are published to the PowerShell Gallery just like the existing Azure PowerShell modules.</span></span> <span data-ttu-id="cebc0-120">Para instalar el módulo experimental, use los siguientes comandos desde una sesión de PowerShell con privilegios elevados:</span><span class="sxs-lookup"><span data-stu-id="cebc0-120">To install the experimental module, use the following commands from an elevated PowerShell session:</span></span>

```powershell
Install-Module AzureRM.Compute.Experiments
Install-Module AzureRM.Websites.Experiments
```

### <a name="documentation-and-support"></a><span data-ttu-id="cebc0-121">Documentación y soporte técnico</span><span class="sxs-lookup"><span data-stu-id="cebc0-121">Documentation and support</span></span>

<span data-ttu-id="cebc0-122">La documentación está incluida en el paquete de instalación y se accede a ella mediante el cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="cebc0-122">Documentation is included in the install package and is accessed using the `Get-Help` cmdlet.</span></span> <span data-ttu-id="cebc0-123">No se ha publicado ninguna documentación oficial para los módulos experimentales.</span><span class="sxs-lookup"><span data-stu-id="cebc0-123">No official documentation is published for experimental modules.</span></span>

<span data-ttu-id="cebc0-124">Le recomendamos que pruebe estos módulos.</span><span class="sxs-lookup"><span data-stu-id="cebc0-124">We encourage you to test these modules.</span></span> <span data-ttu-id="cebc0-125">Sus comentarios nos permiten mejorar la facilidad de uso y dar una respuesta mejor a sus necesidades.</span><span class="sxs-lookup"><span data-stu-id="cebc0-125">Your feedback allows us to improve usability and respond to your needs.</span></span> <span data-ttu-id="cebc0-126">Sin embargo, al ser experimental, el soporte técnico para estos módulos es limitado.</span><span class="sxs-lookup"><span data-stu-id="cebc0-126">However, being experimental, support for these modules is limited.</span></span> <span data-ttu-id="cebc0-127">Las preguntas o notificaciones de problemas se pueden enviar mediante la creación de un [problema](https://github.com/Azure/azure-powershell/issues) en el repositorio de GitHub.</span><span class="sxs-lookup"><span data-stu-id="cebc0-127">Questions or problem reports can be submitted by creating an [issue](https://github.com/Azure/azure-powershell/issues) in the GitHub repository.</span></span>

## <a name="experiments-and-areas-of-improvement"></a><span data-ttu-id="cebc0-128">Experimentos y áreas de mejora</span><span class="sxs-lookup"><span data-stu-id="cebc0-128">Experiments and areas of improvement</span></span>

<span data-ttu-id="cebc0-129">Estas mejoras se seleccionaron basándose en diferenciadores clave de productos de la competencia.</span><span class="sxs-lookup"><span data-stu-id="cebc0-129">These improvements were selected based on key differentiators in competing products.</span></span> <span data-ttu-id="cebc0-130">Por ejemplo, la CLI de Azure 2.0 ha hecho hincapié en basar los comandos en _escenarios_ en lugar de en _áreas expuestas de API_.</span><span class="sxs-lookup"><span data-stu-id="cebc0-130">For example, Azure CLI 2.0 has made a point of basing commands on _scenarios_ rather than _API surface area_.</span></span>
<span data-ttu-id="cebc0-131">La CLI de Azure 2.0 usa un cierto número de valores predeterminados inteligentes que hacen que los escenarios "introductorios" sean más fáciles para los usuarios finales.</span><span class="sxs-lookup"><span data-stu-id="cebc0-131">Azure CLI 2.0 use a number of smart defaults that make "getting started" scenarios easier for end users.</span></span>

### <a name="core-improvements"></a><span data-ttu-id="cebc0-132">Principales mejoras</span><span class="sxs-lookup"><span data-stu-id="cebc0-132">Core improvements</span></span>

<span data-ttu-id="cebc0-133">Las mejoras principales se consideran como de "sentido común" y basta con experimentar un poco para decidirse a la implementación de estas actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="cebc0-133">The core improvements are regarded as "common sense", and little experimentation is needed to move forward in implementing these updates.</span></span>

- <span data-ttu-id="cebc0-134">Cmdlets basados en escenarios: **todos* los cmdlets se deben designar en torno a escenarios, no en torno al servicio REST de Azure.</span><span class="sxs-lookup"><span data-stu-id="cebc0-134">Scenario-based Cmdlets - **All*- cmdlets should be designed around scenarios, not the Azure REST service.</span></span>

- <span data-ttu-id="cebc0-135">Nombres más cortos: incluye los nombres de los cmdlets (por ejemplo, `New-AzureRmVM` => `New-AzVm`) y los nombres de los parámetros (por ejemplo, `-ResourceGroupName` => `-Rg`).</span><span class="sxs-lookup"><span data-stu-id="cebc0-135">Shorter Names - Includes the names of cmdlets (for example, `New-AzureRmVM` => `New-AzVm`) and the names of parameters (for example, `-ResourceGroupName` => `-Rg`).</span></span> <span data-ttu-id="cebc0-136">Usa alias para una mejor compatibilidad con los cmdlets "anteriores".</span><span class="sxs-lookup"><span data-stu-id="cebc0-136">Use aliases for compatibility with "old" cmdlets.</span></span> <span data-ttu-id="cebc0-137">Proporciona conjuntos de parámetros _compatibles con versiones anteriores_.</span><span class="sxs-lookup"><span data-stu-id="cebc0-137">Provide _backwards compatible_ parameter sets.</span></span>

- <span data-ttu-id="cebc0-138">Valores predeterminados inteligentes: crea valores predeterminados inteligentes para rellenar los campos de información "obligatorios".</span><span class="sxs-lookup"><span data-stu-id="cebc0-138">Smart Defaults - Create smart defaults to fill in "required" information.</span></span> <span data-ttu-id="cebc0-139">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="cebc0-139">For example:</span></span>
  - <span data-ttu-id="cebc0-140">Grupo de recursos</span><span class="sxs-lookup"><span data-stu-id="cebc0-140">Resource Group</span></span>
  - <span data-ttu-id="cebc0-141">Ubicación</span><span class="sxs-lookup"><span data-stu-id="cebc0-141">Location</span></span>
  - <span data-ttu-id="cebc0-142">Recursos dependientes</span><span class="sxs-lookup"><span data-stu-id="cebc0-142">Dependent resources</span></span>

### <a name="experimental-improvements"></a><span data-ttu-id="cebc0-143">Mejoras experimentales</span><span class="sxs-lookup"><span data-stu-id="cebc0-143">Experimental improvements</span></span>

<span data-ttu-id="cebc0-144">Las mejoras experimentales presentan un cambio significativo que el equipo quiere validar a través de la experimentación.</span><span class="sxs-lookup"><span data-stu-id="cebc0-144">The experimental improvements present a significant change that the team wants to validate via experimentation.</span></span>

- <span data-ttu-id="cebc0-145">Tipos simples: la creación de escenarios se debe apartar de los tipos y objetos de configuración complejos.</span><span class="sxs-lookup"><span data-stu-id="cebc0-145">Simple types - Create scenarios should move away from complex types and config objects.</span></span> <span data-ttu-id="cebc0-146">Simplifique la configuración hasta uno o dos parámetros.</span><span class="sxs-lookup"><span data-stu-id="cebc0-146">Simplify the configuration down to one or two parameters.</span></span>

- <span data-ttu-id="cebc0-147">"Creación inteligente": todos los escenarios de creación que implementan la "creación inteligente" _no_ tienen parámetros obligatorios: Azure PowerShell elegirá toda la información necesaria de forma dogmática.</span><span class="sxs-lookup"><span data-stu-id="cebc0-147">"Smart Create" - All create scenarios implementing "Smart Create" would have _no_ required parameters: all necessary information would be chosen by Azure PowerShell in an opinionated fashion.</span></span>

- <span data-ttu-id="cebc0-148">Parámetros atenuados: en muchos casos, puede que algunos parámetros estén "atenuados" o sean parcialmente opcionales.</span><span class="sxs-lookup"><span data-stu-id="cebc0-148">Gray Parameters - In many cases, some parameters could be "gray" or semi-optional.</span></span> <span data-ttu-id="cebc0-149">Si el parámetro no se especifica, se pregunta al usuario si desea que el parámetro se genere en su lugar.</span><span class="sxs-lookup"><span data-stu-id="cebc0-149">If the parameter is not specified, the user is asked if they want the parameter generated for them.</span></span> <span data-ttu-id="cebc0-150">También es razonable que los parámetros atenuados deduzcan un valor basándose en el contexto con el consentimiento del usuario.</span><span class="sxs-lookup"><span data-stu-id="cebc0-150">It also makes sense for gray parameters to infer a value based on context with the user's consent.</span></span>
  <span data-ttu-id="cebc0-151">Por ejemplo, es razonable que los parámetros atenuados sugieran el valor usado más recientemente.</span><span class="sxs-lookup"><span data-stu-id="cebc0-151">For example, it may make sense to have the gray parameter suggest the most recently used value.</span></span>

- <span data-ttu-id="cebc0-152">Modificador `-Auto`: el modificador `-Auto` proporcionaría un modo de "participación" para que los usuarios obtengan los _valores predeterminados para todas las opciones_ al tiempo que se mantiene la integridad de los parámetros obligatorios en la ruta de acceso principal.</span><span class="sxs-lookup"><span data-stu-id="cebc0-152">`-Auto` Switch - The `-Auto` switch would provide an "opt-in" way for users to _default all the things_ while maintaining the integrity of required parameters in the mainline path.</span></span>

### <a name="feature-specific-switches"></a><span data-ttu-id="cebc0-153">Modificadores específicos de las características</span><span class="sxs-lookup"><span data-stu-id="cebc0-153">Feature-specific switches</span></span>

<span data-ttu-id="cebc0-154">Por ejemplo, el escenario de "Creación de aplicación web" podría tener un modificador `-Git` o `-AddRemote` que agregaría automáticamente un "azure" remoto a un repositorio de git existente.</span><span class="sxs-lookup"><span data-stu-id="cebc0-154">For example, the "Create web app" scenario might have a `-Git` or `-AddRemote` switch that would automatically add an "azure" remote to an existing git repository.</span></span>

- <span data-ttu-id="cebc0-155">Valores predeterminados configurables: los usuarios deben tener la capacidad de restablecer los valores predeterminados para ciertos parámetros ubicuos como `-ResourceGroupName` y `-Location`.</span><span class="sxs-lookup"><span data-stu-id="cebc0-155">Settable Defaults - Users should have the ability to default certain ubiquitous parameters like `-ResourceGroupName` and `-Location`.</span></span>

- <span data-ttu-id="cebc0-156">Valores predeterminados de tamaño: los "tamaños" de los recursos pueden ser confusos para los usuarios ya que muchos proveedores de recursos utilizan nombres diferentes (por ejemplo, "Standard\_DS1\_v2" o "S1").</span><span class="sxs-lookup"><span data-stu-id="cebc0-156">Size Defaults - Resource "sizes" can be confusing to users since many Resource Providers use different names (for example, "Standard\_DS1\_v2" or "S1").</span></span> <span data-ttu-id="cebc0-157">Sin embargo, la mayoría de los usuarios se preocupa más por el costo.</span><span class="sxs-lookup"><span data-stu-id="cebc0-157">However, most users care more about cost.</span></span> <span data-ttu-id="cebc0-158">Por lo tanto, tiene sentido definir tamaños "universales" basados en una programación de precios.</span><span class="sxs-lookup"><span data-stu-id="cebc0-158">Therefore, it makes sense to define "universal" sizes based on a pricing schedule.</span></span> <span data-ttu-id="cebc0-159">Los usuarios pueden elegir un tamaño específico o dejar que Azure PowerShell elija la _mejor opción_ en función del presupuesto de recursos.</span><span class="sxs-lookup"><span data-stu-id="cebc0-159">Users can choose a specific size or let Azure PowerShell choose the _best option_ based on the resource the budget.</span></span>

- <span data-ttu-id="cebc0-160">Formato de salida: actualmente, Azure PowerShell devuelve `PSObject`s y se producen pocas salidas de consola.</span><span class="sxs-lookup"><span data-stu-id="cebc0-160">Output Format - Azure PowerShell currently returns `PSObject`s and there is little console output.</span></span> <span data-ttu-id="cebc0-161">Puede que Azure PowerShell tenga que mostrar algo de información al usuario sobre los "valores predeterminados inteligentes" usados.</span><span class="sxs-lookup"><span data-stu-id="cebc0-161">Azure PowerShell may need to display some information to the user regarding the "smart defaults" used.</span></span>

## <a name="try-using-the-experiments"></a><span data-ttu-id="cebc0-162">Comprobación de los experimentos</span><span class="sxs-lookup"><span data-stu-id="cebc0-162">Try using the experiments</span></span>

### <a name="install"></a><span data-ttu-id="cebc0-163">Instalación</span><span class="sxs-lookup"><span data-stu-id="cebc0-163">Install</span></span>

```powershell
Install-Module AzureRM.Compute.Experiments
```

### <a name="create-a-vm"></a><span data-ttu-id="cebc0-164">Creación de una VM</span><span class="sxs-lookup"><span data-stu-id="cebc0-164">Create a VM</span></span>

```powershell
$job = New-AzVm -Name MyVm -AsJob
Receive-Job $job
```

### <a name="send-us-feedback"></a><span data-ttu-id="cebc0-165">Envíenos comentarios</span><span class="sxs-lookup"><span data-stu-id="cebc0-165">Send Us Feedback</span></span>

```powershell
Send-Feedback
```
