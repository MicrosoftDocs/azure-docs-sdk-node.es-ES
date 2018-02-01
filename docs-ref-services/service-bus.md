---
title: "Módulos de Azure Service Bus para Node.js"
description: "Referencia de los módulos de Azure Service Bus para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Bus
ms.openlocfilehash: 792e51acf2577649432b26e4b840bc1d40b7abaf
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2018
---
# <a name="azure-service-bus-modules-for-nodejs"></a><span data-ttu-id="fca82-103">Módulos de Azure Service Bus para Node.js</span><span class="sxs-lookup"><span data-stu-id="fca82-103">Azure Service Bus Modules for Node.js</span></span>

<span data-ttu-id="fca82-104">Azure Service Bus es una plataforma en la nube de mensajería asincrónica que le permite enviar datos entre sistemas desacoplados.</span><span class="sxs-lookup"><span data-stu-id="fca82-104">Azure Service Bus is an asynchronous messaging cloud platform that enables you to send data between decoupled systems.</span></span>

<span data-ttu-id="fca82-105">Aprenda más sobre [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).</span><span class="sxs-lookup"><span data-stu-id="fca82-105">Learn more about [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="fca82-106">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="fca82-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="fca82-107">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="fca82-107">Install the npm module</span></span>

<span data-ttu-id="fca82-108">Utilice npm para instalar el módulo de Azure Service Bus para Node.js.</span><span class="sxs-lookup"><span data-stu-id="fca82-108">Use npm to install the Azure Service Bus module for Node.js</span></span>

```bash
npm install azure-arm-sb
```

### <a name="example"></a><span data-ttu-id="fca82-109">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="fca82-109">Example</span></span>

<span data-ttu-id="fca82-110">En este ejemplo se crea a un cliente y después se enumeran todos los espacios de nombres de Service Bus asociados a una suscripción determinada.</span><span class="sxs-lookup"><span data-stu-id="fca82-110">This example creates a client and then lists all Service Bus namespaces associated with a given subscription.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ServicebusManagement = require('azure-arm-sb');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = new ServicebusManagement(credentials, subscriptionId);
    client.namespaces.listBySubscription().then(namespaces => {
        namespaces.map(ns => {
            console.log(`found ns : ${ns.name}`);
        });
    });
});
```

## <a name="samples"></a><span data-ttu-id="fca82-111">Muestras</span><span class="sxs-lookup"><span data-stu-id="fca82-111">Samples</span></span>

<span data-ttu-id="fca82-112">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="fca82-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
