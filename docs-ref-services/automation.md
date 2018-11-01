---
title: Módulos de Azure Automation para Node.js
description: Referencia de los módulos de Azure Automation para Node.js
author: eamonoreilly
ms.author: eamono
manager: nirb
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Automation
ms.openlocfilehash: f364bb09c97c1262f640a4b48514c6abaee5f14a
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2018
ms.locfileid: "50406421"
---
# <a name="azure-automation-modules-for-nodejs"></a><span data-ttu-id="a8935-103">Módulos de Azure Automation para Node.js</span><span class="sxs-lookup"><span data-stu-id="a8935-103">Azure Automation Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="a8935-104">Información general</span><span class="sxs-lookup"><span data-stu-id="a8935-104">Overview</span></span>

<span data-ttu-id="a8935-105">Azure Automation ofrece a los usuarios una manera de automatizar las tareas manuales, propensas a errores, con una ejecución prolongada y repetidas con frecuencia que se realizan normalmente en un entorno empresarial y en la nube.</span><span class="sxs-lookup"><span data-stu-id="a8935-105">Azure Automation provides a way for users to automate the manual, long-running, error-prone, and frequently repeated tasks that are commonly performed in a cloud and enterprise environment.</span></span> <span data-ttu-id="a8935-106">Automation ahorra tiempo y aumenta la confiabilidad de las tareas administrativas periódicas e incluso las programa para que se realicen automáticamente a intervalos regulares.</span><span class="sxs-lookup"><span data-stu-id="a8935-106">Automation saves time and increases the reliability of regular administrative tasks and even schedules them to be automatically performed at regular intervals.</span></span> <span data-ttu-id="a8935-107">Puede automatizar procesos mediante runbooks o automatizar la administración de configuración mediante la configuración de estado deseado.</span><span class="sxs-lookup"><span data-stu-id="a8935-107">You can automate processes using runbooks or automate configuration management using Desired State Configuration.</span></span>

## <a name="management-package"></a><span data-ttu-id="a8935-108">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="a8935-108">Management package</span></span>

### <a name="install-the-modules-with-npm"></a><span data-ttu-id="a8935-109">Instalación de los módulos con npm</span><span class="sxs-lookup"><span data-stu-id="a8935-109">Install the modules with npm</span></span>

<span data-ttu-id="a8935-110">Utilice npm para instalar los módulos de Azure Automation para Node.js.</span><span class="sxs-lookup"><span data-stu-id="a8935-110">Use npm to install the Azure Automation modules for Node.js</span></span>

```bash
npm install azure-arm-automation
```

### <a name="example"></a><span data-ttu-id="a8935-111">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a8935-111">Example</span></span>

<span data-ttu-id="a8935-112">En este ejemplo se enumeran las cuentas de Automation.</span><span class="sxs-lookup"><span data-stu-id="a8935-112">This example lists the automation accounts.</span></span>

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

## <a name="samples"></a><span data-ttu-id="a8935-113">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="a8935-113">Samples</span></span>

<span data-ttu-id="a8935-114">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="a8935-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
