---
title: Módulos de Azure Service Bus para Node.js
description: Referencia de los módulos de Azure Service Bus para Node.js
author: sethmanheim
ms.author: sethm
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Bus
ms.openlocfilehash: 76d7c615cbe64fa38f9c28ea8dfc6d1c854bb0c9
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2018
ms.locfileid: "51380359"
---
# <a name="azure-service-bus-modules-for-nodejs"></a><span data-ttu-id="57a50-103">Módulos de Azure Service Bus para Node.js</span><span class="sxs-lookup"><span data-stu-id="57a50-103">Azure Service Bus Modules for Node.js</span></span>

<span data-ttu-id="57a50-104">Azure Service Bus es una plataforma en la nube de mensajería asincrónica que le permite enviar datos entre sistemas desacoplados.</span><span class="sxs-lookup"><span data-stu-id="57a50-104">Azure Service Bus is an asynchronous messaging cloud platform that enables you to send data between decoupled systems.</span></span>

<span data-ttu-id="57a50-105">Aprenda más sobre [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).</span><span class="sxs-lookup"><span data-stu-id="57a50-105">Learn more about [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="57a50-106">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="57a50-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="57a50-107">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="57a50-107">Install the npm module</span></span>

<span data-ttu-id="57a50-108">Utilice npm para instalar el módulo de Azure Service Bus para Node.js.</span><span class="sxs-lookup"><span data-stu-id="57a50-108">Use npm to install the Azure Service Bus module for Node.js</span></span>

```bash
npm install azure-arm-sb
```

### <a name="example"></a><span data-ttu-id="57a50-109">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="57a50-109">Example</span></span>

<span data-ttu-id="57a50-110">En este ejemplo se crea a un cliente y después se enumeran todos los espacios de nombres de Service Bus asociados a una suscripción determinada.</span><span class="sxs-lookup"><span data-stu-id="57a50-110">This example creates a client and then lists all Service Bus namespaces associated with a given subscription.</span></span>

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

## <a name="samples"></a><span data-ttu-id="57a50-111">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="57a50-111">Samples</span></span>

<span data-ttu-id="57a50-112">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="57a50-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
