---
title: "Módulos de Azure Scheduler para Node.js"
description: "Referencia de los módulos de Azure Scheduler para Node.js"
keywords: Azure,SDK,API,Scheduler, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Scheduler
ms.openlocfilehash: 3070612721dc434b8c3d7c3200f0666755fd4ce8
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="azure-scheduler-modules-for-nodejs"></a><span data-ttu-id="b5d2d-104">Módulos de Azure Scheduler para Node.js</span><span class="sxs-lookup"><span data-stu-id="b5d2d-104">Azure Scheduler modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="b5d2d-105">Información general</span><span class="sxs-lookup"><span data-stu-id="b5d2d-105">Overview</span></span>

<span data-ttu-id="b5d2d-106">Azure Scheduler crea, mantiene e invoca el trabajo programado a través de HTTP, HTTPS, una cola de almacenamiento o el servicio [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview).</span><span class="sxs-lookup"><span data-stu-id="b5d2d-106">Azure Scheduler creates, maintains, and invokes scheduled work via HTTP, HTTPS, a storage queue, or the [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

<span data-ttu-id="b5d2d-107">Más información sobre [Azure Scheduler](/azure/scheduler/scheduler-intro).</span><span class="sxs-lookup"><span data-stu-id="b5d2d-107">Learn more about [Azure Scheduler](/azure/scheduler/scheduler-intro).</span></span>

## <a name="management-package"></a><span data-ttu-id="b5d2d-108">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="b5d2d-108">Management package</span></span>

<span data-ttu-id="b5d2d-109">Cree, mantenga e invoque el trabajo programado a través de diversos canales de comunicación con la API de administración.</span><span class="sxs-lookup"><span data-stu-id="b5d2d-109">Create, maintain, and invoke scheduled work across various communication channels with the management API.</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b5d2d-110">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="b5d2d-110">Install the npm module</span></span>

<span data-ttu-id="b5d2d-111">Instale el módulo npm de Azure Scheduler.</span><span class="sxs-lookup"><span data-stu-id="b5d2d-111">Install the Azure Scheduler npm module</span></span>

```bash
npm install azure-arm-scheduler
```

### <a name="example"></a><span data-ttu-id="b5d2d-112">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b5d2d-112">Example</span></span>

<span data-ttu-id="b5d2d-113">En este ejemplo se enumeran los programadores actuales.</span><span class="sxs-lookup"><span data-stu-id="b5d2d-113">This examples lists the current schedulers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="b5d2d-114">Muestras</span><span class="sxs-lookup"><span data-stu-id="b5d2d-114">Samples</span></span>

<span data-ttu-id="b5d2d-115">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="b5d2d-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
