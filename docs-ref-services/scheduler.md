---
title: Módulos de Azure Scheduler para Node.js
description: Referencia de los módulos de Azure Scheduler para Node.js
author: rloutlaw
ms.author: ROutlaw
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Scheduler
ms.openlocfilehash: 9a842919fddb3d6448d5a4e951dc58dd0d3211e0
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2018
ms.locfileid: "51399039"
---
# <a name="azure-scheduler-modules-for-nodejs"></a><span data-ttu-id="18c1c-103">Módulos de Azure Scheduler para Node.js</span><span class="sxs-lookup"><span data-stu-id="18c1c-103">Azure Scheduler modules for Node.js</span></span>

<span data-ttu-id="18c1c-104">Azure Scheduler crea, mantiene e invoca el trabajo programado a través de HTTP, HTTPS, una cola de almacenamiento o el servicio [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview).</span><span class="sxs-lookup"><span data-stu-id="18c1c-104">Azure Scheduler creates, maintains, and invokes scheduled work via HTTP, HTTPS, a storage queue, or the [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

<span data-ttu-id="18c1c-105">Más información sobre [Azure Scheduler](/azure/scheduler/scheduler-intro).</span><span class="sxs-lookup"><span data-stu-id="18c1c-105">Learn more about [Azure Scheduler](/azure/scheduler/scheduler-intro).</span></span>

## <a name="management-package"></a><span data-ttu-id="18c1c-106">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="18c1c-106">Management package</span></span>

<span data-ttu-id="18c1c-107">Cree, mantenga e invoque el trabajo programado a través de diversos canales de comunicación con la API de administración.</span><span class="sxs-lookup"><span data-stu-id="18c1c-107">Create, maintain, and invoke scheduled work across various communication channels with the management API.</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="18c1c-108">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="18c1c-108">Install the npm module</span></span>

<span data-ttu-id="18c1c-109">Instale el módulo npm de Azure Scheduler.</span><span class="sxs-lookup"><span data-stu-id="18c1c-109">Install the Azure Scheduler npm module</span></span>

```bash
npm install azure-arm-scheduler
```

### <a name="example"></a><span data-ttu-id="18c1c-110">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="18c1c-110">Example</span></span>

<span data-ttu-id="18c1c-111">En este ejemplo se enumeran los programadores actuales.</span><span class="sxs-lookup"><span data-stu-id="18c1c-111">This examples lists the current schedulers.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure')
const SchedulerManagement = require('azure-arm-scheduler')

msRestAzure.interactiveLogin().then(credentials => {
    // Create a scheduler from the login credentials
    let client = new SchedulerManagement(credentials, 'your-subscription-id')
    // Get the full list of current jobs for the subscription
    return client.jobCollections.listBySubscription()
}).then(currentJobs => {
    console.log("Current jobs:")
    console.dir(currentJobs, {depth:null, colors:true})
}).catch(error => {
    console.log("An error occurred:")
    console.dir(error, {depth:null, colors:true})
})
```

## <a name="samples"></a><span data-ttu-id="18c1c-112">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="18c1c-112">Samples</span></span>

<span data-ttu-id="18c1c-113">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="18c1c-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
