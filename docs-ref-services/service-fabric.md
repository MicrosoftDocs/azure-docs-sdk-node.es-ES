---
title: "Módulos de Azure Service Fabric para Node.js"
description: "Referencia de los módulos de Azure Service Fabric para Node.js"
keywords: Azure,SDK,API,Service Fabric, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Fabric
ms.openlocfilehash: d3de9af4e8ca834963cf2ac0275ed02b8021f29f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="azure-service-fabric-modules-for-nodejs"></a><span data-ttu-id="24f91-104">Módulos de Azure Service Fabric para Node.js</span><span class="sxs-lookup"><span data-stu-id="24f91-104">Azure Service Fabric modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="24f91-105">Información general</span><span class="sxs-lookup"><span data-stu-id="24f91-105">Overview</span></span>

<span data-ttu-id="24f91-106">Azure Service Fabric es una plataforma de sistemas distribuidos que facilita el empaquetado, la implementación y la administración de microservicios y contenedores escalables y confiables.</span><span class="sxs-lookup"><span data-stu-id="24f91-106">Azure Service Fabric is a distributed systems platform that makes it easy to package, deploy, and manage scalable and reliable microservices and containers.</span></span>

<span data-ttu-id="24f91-107">Más información acerca de [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span><span class="sxs-lookup"><span data-stu-id="24f91-107">Learn more about [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="24f91-108">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="24f91-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="24f91-109">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="24f91-109">Install the npm module</span></span>

<span data-ttu-id="24f91-110">Instale el módulo npm de Azure Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="24f91-110">Install the Azure Service Fabric npm module</span></span>

```bash
npm install azure-arm-servicefabric
```

### <a name="example"></a><span data-ttu-id="24f91-111">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="24f91-111">Example</span></span>

<span data-ttu-id="24f91-112">En este ejemplo se muestra cómo enumerar los clústeres para una suscripción de Azure.</span><span class="sxs-lookup"><span data-stu-id="24f91-112">This example shows how you can list the clusters for an Azure subscription.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ServiceFabricManagement = require('azure-arm-servicefabric');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new ServiceFabricManagement(
      credentials,
      subscriptionId
    );
    return client.clusters.list();
  })
  .then(clusters => {
    console.log('List of clusters:');
    console.dir(clusters, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="24f91-113">Muestras</span><span class="sxs-lookup"><span data-stu-id="24f91-113">Samples</span></span>

<span data-ttu-id="24f91-114">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="24f91-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
