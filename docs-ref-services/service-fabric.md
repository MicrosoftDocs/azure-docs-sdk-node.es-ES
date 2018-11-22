---
title: Módulos de Azure Service Fabric para Node.js
description: Referencia de los módulos de Azure Service Fabric para Node.js
author: rwike77
ms.author: ryanwi
manager: timlt
ms.date: 11/12/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Fabric
ms.openlocfilehash: 3fd2f73bc6fddf01548bbb92cce540775d4c7c76
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2018
ms.locfileid: "52110069"
---
# <a name="azure-service-fabric-modules-for-nodejs"></a><span data-ttu-id="4c105-103">Módulos de Azure Service Fabric para Node.js</span><span class="sxs-lookup"><span data-stu-id="4c105-103">Azure Service Fabric modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="4c105-104">Información general</span><span class="sxs-lookup"><span data-stu-id="4c105-104">Overview</span></span>

<span data-ttu-id="4c105-105">Azure Service Fabric es una plataforma de sistemas distribuidos que facilita el empaquetado, la implementación y la administración de microservicios y contenedores escalables y confiables.</span><span class="sxs-lookup"><span data-stu-id="4c105-105">Azure Service Fabric is a distributed systems platform that makes it easy to package, deploy, and manage scalable and reliable microservices and containers.</span></span>

<span data-ttu-id="4c105-106">Más información acerca de [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span><span class="sxs-lookup"><span data-stu-id="4c105-106">Learn more about [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="4c105-107">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="4c105-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="4c105-108">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="4c105-108">Install the npm module</span></span>

<span data-ttu-id="4c105-109">Instale el módulo npm de Azure Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="4c105-109">Install the Azure Service Fabric npm module</span></span>

```bash
npm install azure-arm-servicefabric
```

### <a name="example"></a><span data-ttu-id="4c105-110">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="4c105-110">Example</span></span>

<span data-ttu-id="4c105-111">En este ejemplo se muestra cómo enumerar los clústeres para una suscripción de Azure.</span><span class="sxs-lookup"><span data-stu-id="4c105-111">This example shows how you can list the clusters for an Azure subscription.</span></span>

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

## <a name="samples"></a><span data-ttu-id="4c105-112">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="4c105-112">Samples</span></span>

<span data-ttu-id="4c105-113">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="4c105-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
