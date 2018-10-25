---
title: Módulos de Azure Monitor para Node.js
description: Referencia de los módulos de Azure Monitor para Node.js
author: rbouche
ms.author: robb
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Monitor
ms.openlocfilehash: fb2cc5ba927fe03fb5fe3114919ed1b0b6e969ae
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "49670780"
---
# <a name="azure-monitor-modules-for-nodejs"></a><span data-ttu-id="1993b-103">Módulos de Azure Monitor para Node.js</span><span class="sxs-lookup"><span data-stu-id="1993b-103">Azure Monitor modules for Node.js</span></span>

<span data-ttu-id="1993b-104">Las aplicaciones de nube son complejas y tienen muchas partes móviles.</span><span class="sxs-lookup"><span data-stu-id="1993b-104">Cloud applications are complex with many moving parts.</span></span> <span data-ttu-id="1993b-105">La supervisión proporciona datos para garantizar que la aplicación permanece en funcionamiento en un estado correcto.</span><span class="sxs-lookup"><span data-stu-id="1993b-105">Monitoring provides data to ensure that your application stays up and running in a healthy state.</span></span> <span data-ttu-id="1993b-106">También ayuda a evitar posibles problemas o a solucionar los existentes.</span><span class="sxs-lookup"><span data-stu-id="1993b-106">It also helps you to stave off potential problems or troubleshoot past ones.</span></span> <span data-ttu-id="1993b-107">Además, puede usar datos de supervisión para obtener un conocimiento más profundo sobre su aplicación.</span><span class="sxs-lookup"><span data-stu-id="1993b-107">In addition, you can use monitoring data to gain deep insights about your application.</span></span> <span data-ttu-id="1993b-108">Este conocimiento puede ayudarle a mejorar el rendimiento o mantenimiento de la aplicación, o a automatizar acciones que de lo contrario requerirían intervención manual.</span><span class="sxs-lookup"><span data-stu-id="1993b-108">That knowledge can help you to improve application performance or maintainability, or automate actions that would otherwise require manual intervention.</span></span>

## <a name="management-package"></a><span data-ttu-id="1993b-109">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="1993b-109">Management Package</span></span>

### <a name="install-npm-module"></a><span data-ttu-id="1993b-110">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="1993b-110">Install npm module</span></span>

```bash
npm install azure-arm-monitor
```

### <a name="example"></a><span data-ttu-id="1993b-111">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1993b-111">Example</span></span>

<span data-ttu-id="1993b-112">En este ejemplo de código se imprimen todas las reglas de alertas asociadas a un grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="1993b-112">This code example prints all the alerting rules associated with a resource group.</span></span>

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

### <a name="samples"></a><span data-ttu-id="1993b-113">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="1993b-113">Samples</span></span>

<span data-ttu-id="1993b-114">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="1993b-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
