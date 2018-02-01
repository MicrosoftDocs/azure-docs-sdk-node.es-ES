---
title: "Módulos de Azure Monitor para Node.js"
description: "Referencia de los módulos de Azure Monitor para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Monitor
ms.openlocfilehash: 37caeb2d7b6d757cbe8bb14b6d4909a7c67a37db
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2018
---
# <a name="azure-monitor-modules-for-nodejs"></a><span data-ttu-id="17396-103">Módulos de Azure Monitor para Node.js</span><span class="sxs-lookup"><span data-stu-id="17396-103">Azure Monitor modules for Node.js</span></span>

<span data-ttu-id="17396-104">Las aplicaciones de nube son complejas y tienen muchas partes móviles.</span><span class="sxs-lookup"><span data-stu-id="17396-104">Cloud applications are complex with many moving parts.</span></span> <span data-ttu-id="17396-105">La supervisión proporciona datos para garantizar que la aplicación permanece en funcionamiento en un estado correcto.</span><span class="sxs-lookup"><span data-stu-id="17396-105">Monitoring provides data to ensure that your application stays up and running in a healthy state.</span></span> <span data-ttu-id="17396-106">También ayuda a evitar posibles problemas o a solucionar los existentes.</span><span class="sxs-lookup"><span data-stu-id="17396-106">It also helps you to stave off potential problems or troubleshoot past ones.</span></span> <span data-ttu-id="17396-107">Además, puede usar datos de supervisión para obtener un conocimiento más profundo sobre su aplicación.</span><span class="sxs-lookup"><span data-stu-id="17396-107">In addition, you can use monitoring data to gain deep insights about your application.</span></span> <span data-ttu-id="17396-108">Este conocimiento puede ayudarle a mejorar el rendimiento o mantenimiento de la aplicación, o a automatizar acciones que de lo contrario requerirían intervención manual.</span><span class="sxs-lookup"><span data-stu-id="17396-108">That knowledge can help you to improve application performance or maintainability, or automate actions that would otherwise require manual intervention.</span></span>

## <a name="management-package"></a><span data-ttu-id="17396-109">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="17396-109">Management Package</span></span>

### <a name="install-npm-module"></a><span data-ttu-id="17396-110">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="17396-110">Install npm module</span></span>

```bash
npm install azure-arm-monitor
```

### <a name="example"></a><span data-ttu-id="17396-111">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17396-111">Example</span></span>

<span data-ttu-id="17396-112">En este ejemplo de código se imprimen todas las reglas de alertas asociadas a un grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="17396-112">This code example prints all the alerting rules associated with a resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const monitorManagementClient = require('azure-arm-monitor');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new monitorManagementClient(credentials, subscriptionId);
    client.alertRules.listByResourceGroup(resourceGroupName, rules => {
      console.log('List of rules:');
      console.dir(rules, { depth: null, colors: true });
    })
  });

```

### <a name="samples"></a><span data-ttu-id="17396-113">Muestras</span><span class="sxs-lookup"><span data-stu-id="17396-113">Samples</span></span>

<span data-ttu-id="17396-114">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="17396-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
