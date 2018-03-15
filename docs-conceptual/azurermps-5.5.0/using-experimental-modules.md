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
ms.openlocfilehash: c11e4503c07b0a0c4a71021bc511da723098188e
ms.sourcegitcommit: 20af779cd523c758d40e23d60eb989a4ef982d5c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2018
---
# <a name="using-experimental-azure-powershell-modules"></a>Uso de los módulos experimentales de Azure PowerShell

Haciendo especial hincapié en las herramientas de desarrollador (especialmente las CLI) de Azure, el equipo de Azure PowerShell está realizando experimentos para mejorar la experiencia de este servicio.

## <a name="experimentation-methodology"></a>Metodología de experimentación

Para facilitar la experimentación, vamos a crear nuevos módulos de Azure PowerShell que implementan la funcionalidad de Azure SDK existente de nuevas y sencillas maneras. En la mayoría de los casos los cmdlets son idénticos a los cmdlets existentes. Sin embargo, los cmdlets experimentales proporcionan una notación abreviada y valores predeterminados más inteligentes que facilitan la creación y administración de los recursos de Azure.

Estos módulos se pueden instalar en paralelo con módulos de Azure PowerShell existentes. Los nombres de cmdlet se han abreviado para proporcionar nombres más cortos y evitar conflictos de nombres con los cmdlets no experimentales existentes.

Los módulos experimentales usan la siguiente convención de nomenclatura: `AzureRM.*.Experiments`. Esta convención de nomenclatura es similar a la nomenclatura de los módulos de la versión preliminar: `AzureRM.*.Preview`. Los módulos de la versión preliminar son diferentes a los módulos experimentales. Los módulos de la versión preliminar implementan la nueva funcionalidad de los servicios de Azure que solo está disponible como oferta en esta versión. Los módulos de la versión preliminar reemplazan los módulos de Azure PowerShell existentes y usan el mismo cmdlet y los mismos nombres de parámetro.

## <a name="how-to-install-an-experimental-module"></a>Instalación de un módulo experimental

Los módulos experimentales se publican en la Galería de PowerShell al igual que los módulos de Azure PowerShell existentes. Para ver una lista de módulos experimentales, ejecute el siguiente comando:

```powershell
Find-Module AzureRM.*.Experiments
```

```Output
Version Name                         Repository Description
------- ----                         ---------- -----------
1.0.25  AzureRM.Compute.Experiments  PSGallery  Azure Compute experiments for VM creation
1.0.0   AzureRM.Websites.Experiments PSGallery  Create and deploy web applications using Azure App Services.
```

Para instalar el módulo experimental, use los siguientes comandos desde una sesión de PowerShell con privilegios elevados:

```powershell
Install-Module AzureRM.Compute.Experiments
Install-Module AzureRM.Websites.Experiments
```

### <a name="documentation-and-support"></a>Documentación y soporte técnico

La documentación está incluida en el paquete de instalación y se accede a ella mediante el cmdlet `Get-Help`. No se ha publicado ninguna documentación oficial para los módulos experimentales.

Le recomendamos que pruebe estos módulos. Sus comentarios nos permiten mejorar la facilidad de uso y dar una respuesta mejor a sus necesidades. Sin embargo, al ser experimental, el soporte técnico para estos módulos es limitado. Las preguntas o notificaciones de problemas se pueden enviar mediante la creación de un [problema](https://github.com/Azure/azure-powershell/issues) en el repositorio de GitHub.

## <a name="experiments-and-areas-of-improvement"></a>Experimentos y áreas de mejora

Estas mejoras se seleccionaron basándose en diferenciadores clave de productos de la competencia. Por ejemplo, la CLI de Azure 2.0 ha hecho hincapié en basar los comandos en _escenarios_ en lugar de en _áreas expuestas de API_.
La CLI de Azure 2.0 usa un cierto número de valores predeterminados inteligentes que hacen que los escenarios "introductorios" sean más fáciles para los usuarios finales.

### <a name="core-improvements"></a>Principales mejoras

Las mejoras principales se consideran como de "sentido común" y basta con experimentar un poco para decidirse a la implementación de estas actualizaciones.

- Cmdlets basados en escenarios: **todos* los cmdlets se deben designar en torno a escenarios, no en torno al servicio REST de Azure.

- Nombres más cortos: incluye los nombres de los cmdlets (por ejemplo, `New-AzureRmVM` => `New-AzVm`) y los nombres de los parámetros (por ejemplo, `-ResourceGroupName` => `-Rg`). Usa alias para una mejor compatibilidad con los cmdlets "anteriores". Proporciona conjuntos de parámetros _compatibles con versiones anteriores_.

- Valores predeterminados inteligentes: crea valores predeterminados inteligentes para rellenar los campos de información "obligatorios". Por ejemplo: 
  - Grupo de recursos
  - Ubicación
  - Recursos dependientes

### <a name="experimental-improvements"></a>Mejoras experimentales

Las mejoras experimentales presentan un cambio significativo que el equipo quiere validar a través de la experimentación.

- Tipos simples: la creación de escenarios se debe apartar de los tipos y objetos de configuración complejos. Simplifique la configuración hasta uno o dos parámetros.

- "Creación inteligente": todos los escenarios de creación que implementan la "creación inteligente" _no_ tienen parámetros obligatorios: Azure PowerShell elegirá toda la información necesaria de forma dogmática.

- Parámetros atenuados: en muchos casos, puede que algunos parámetros estén "atenuados" o sean parcialmente opcionales. Si el parámetro no se especifica, se pregunta al usuario si desea que el parámetro se genere en su lugar. También es razonable que los parámetros atenuados deduzcan un valor basándose en el contexto con el consentimiento del usuario.
  Por ejemplo, es razonable que los parámetros atenuados sugieran el valor usado más recientemente.

- Modificador `-Auto`: el modificador `-Auto` proporcionaría un modo de "participación" para que los usuarios obtengan los _valores predeterminados para todas las opciones_ al tiempo que se mantiene la integridad de los parámetros obligatorios en la ruta de acceso principal.

### <a name="feature-specific-switches"></a>Modificadores específicos de las características

Por ejemplo, el escenario de "Creación de aplicación web" podría tener un modificador `-Git` o `-AddRemote` que agregaría automáticamente un "azure" remoto a un repositorio de git existente.

- Valores predeterminados configurables: los usuarios deben tener la capacidad de restablecer los valores predeterminados para ciertos parámetros ubicuos como `-ResourceGroupName` y `-Location`.

- Valores predeterminados de tamaño: los "tamaños" de los recursos pueden ser confusos para los usuarios ya que muchos proveedores de recursos utilizan nombres diferentes (por ejemplo, "Standard\_DS1\_v2" o "S1"). Sin embargo, la mayoría de los usuarios se preocupa más por el costo. Por lo tanto, tiene sentido definir tamaños "universales" basados en una programación de precios. Los usuarios pueden elegir un tamaño específico o dejar que Azure PowerShell elija la _mejor opción_ en función del presupuesto de recursos.

- Formato de salida: actualmente, Azure PowerShell devuelve `PSObject`s y se producen pocas salidas de consola. Puede que Azure PowerShell tenga que mostrar algo de información al usuario sobre los "valores predeterminados inteligentes" usados.
