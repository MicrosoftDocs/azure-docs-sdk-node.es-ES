---
title: Módulos de Azure Event Hubs para Node.js
description: Referencia de los módulos de Azure Event Hubs para Node.js
author: sethmanheim
ms.author: sethm
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Event Hub
ms.openlocfilehash: cf50d0e69e336dac9addc85625599fbbefd1902e
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2018
ms.locfileid: "50381462"
---
# <a name="azure-event-hub-modules-for-nodejs"></a><span data-ttu-id="20d70-103">Módulos de Azure Event Hubs para Node.js</span><span class="sxs-lookup"><span data-stu-id="20d70-103">Azure Event Hub modules for Node.js</span></span>

<span data-ttu-id="20d70-104">Azure Event Hubs es una plataforma de streaming de datos y servicio de ingesta de eventos de gran escalabilidad que es capaz de recibir y procesar millones de eventos por segundo.</span><span class="sxs-lookup"><span data-stu-id="20d70-104">Azure Event Hubs is a highly scalable data streaming platform and event ingestion service capable of receiving and processing millions of events per second.</span></span> <span data-ttu-id="20d70-105">Event Hubs puede procesar y almacenar eventos, datos o telemetría generados por dispositivos y software distribuido.</span><span class="sxs-lookup"><span data-stu-id="20d70-105">Event Hubs can process and store events, data, or telemetry produced by distributed software and devices.</span></span> <span data-ttu-id="20d70-106">Los datos enviados a un centro de eventos se pueden transformar y almacenar con cualquier proveedor de análisis en tiempo real o adaptadores de procesamiento por lotes y almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="20d70-106">Data sent to an event hub can be transformed and stored using any real-time analytics provider or batching/storage adapters.</span></span> <span data-ttu-id="20d70-107">Con la capacidad para ofrecer competencias de publicación y suscripción con una latencia baja y a gran escala, Event Hubs sirve como una "vía de entrada" para los macrodatos.</span><span class="sxs-lookup"><span data-stu-id="20d70-107">With the ability to provide publish-subscribe capabilities with low latency and at massive scale, Event Hubs serves as the "on ramp" for Big Data.</span></span>

## <a name="management-package"></a><span data-ttu-id="20d70-108">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="20d70-108">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="20d70-109">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="20d70-109">Install the npm module</span></span> 

<span data-ttu-id="20d70-110">Utilice npm para instalar los módulos de Azure Event Hubs para Node.js.</span><span class="sxs-lookup"><span data-stu-id="20d70-110">Use npm to install the Azure Event Hub modules for Node.js</span></span>

```bash
npm install azure-arm-eventhub
```

### <a name="example"></a><span data-ttu-id="20d70-111">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="20d70-111">Example</span></span>

<span data-ttu-id="20d70-112">En este ejemplo se recupera información sobre un centro de eventos existente.</span><span class="sxs-lookup"><span data-stu-id="20d70-112">This example retrieves information about an existing event hub.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const EventHubManagement = require('azure-arm-eventhub');

const resourceGroupName = 'testRG';
const namespaceName = 'testNS';
const eventHubName = 'testEH';
const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new EventHubManagement(credentials, subscriptionId);
    return client.eventHubs.get(resourceGroupName, namespaceName, eventHubName);
  })
  .then(zones => console.dir(zones, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="20d70-113">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="20d70-113">Samples</span></span>

<span data-ttu-id="20d70-114">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="20d70-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
