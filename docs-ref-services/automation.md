---
title: "Módulos de Azure Automation para Node.js"
description: "Referencia de los módulos de Azure Automation para Node.js"
keywords: Azure,SDK,API,Automation, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Automation
ms.openlocfilehash: 96861efce8eb95f567aa25f2304cb271d932d949
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="azure-automation-modules-for-nodejs"></a><span data-ttu-id="dff9b-104">Módulos de Azure Automation para Node.js</span><span class="sxs-lookup"><span data-stu-id="dff9b-104">Azure Automation Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="dff9b-105">Información general</span><span class="sxs-lookup"><span data-stu-id="dff9b-105">Overview</span></span>

<span data-ttu-id="dff9b-106">Azure Automation ofrece a los usuarios una manera de automatizar las tareas manuales, propensas a errores, con una ejecución prolongada y repetidas con frecuencia que se realizan normalmente en un entorno empresarial y en la nube.</span><span class="sxs-lookup"><span data-stu-id="dff9b-106">Azure Automation provides a way for users to automate the manual, long-running, error-prone, and frequently repeated tasks that are commonly performed in a cloud and enterprise environment.</span></span> <span data-ttu-id="dff9b-107">Automation ahorra tiempo y aumenta la confiabilidad de las tareas administrativas periódicas e incluso las programa para que se realicen automáticamente a intervalos regulares.</span><span class="sxs-lookup"><span data-stu-id="dff9b-107">Automation saves time and increases the reliability of regular administrative tasks and even schedules them to be automatically performed at regular intervals.</span></span> <span data-ttu-id="dff9b-108">Puede automatizar procesos mediante runbooks o automatizar la administración de configuración mediante la configuración de estado deseado.</span><span class="sxs-lookup"><span data-stu-id="dff9b-108">You can automate processes using runbooks or automate configuration management using Desired State Configuration.</span></span>

## <a name="management-package"></a><span data-ttu-id="dff9b-109">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="dff9b-109">Management package</span></span>

### <a name="install-the-modules-with-npm"></a><span data-ttu-id="dff9b-110">Instalación de los módulos con npm</span><span class="sxs-lookup"><span data-stu-id="dff9b-110">Install the modules with npm</span></span>

<span data-ttu-id="dff9b-111">Utilice npm para instalar los módulos de Azure Automation para Node.js.</span><span class="sxs-lookup"><span data-stu-id="dff9b-111">Use npm to install the Azure Automation modules for Node.js</span></span>

```bash
npm install azure-arm-automation
```

### <a name="example"></a><span data-ttu-id="dff9b-112">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="dff9b-112">Example</span></span>

<span data-ttu-id="dff9b-113">En este ejemplo se enumeran las cuentas de Automation.</span><span class="sxs-lookup"><span data-stu-id="dff9b-113">This example lists the automation accounts.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const AutomationManagement = require('azure-arm-automation');

const subcriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new AutomationManagement(credentials, subcriptionId);
    return client.automationAccounts.listByResourceGroup(resourceGroup);
  })
  .then(automationAccounts =>
    console.dir(automationAccounts, { depth: null, colors: true })
  )
  .catch(err => console.log(err));

```

## <a name="samples"></a><span data-ttu-id="dff9b-114">Muestras</span><span class="sxs-lookup"><span data-stu-id="dff9b-114">Samples</span></span>

<span data-ttu-id="dff9b-115">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="dff9b-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
