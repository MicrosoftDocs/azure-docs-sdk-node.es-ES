---
title: "Módulos de Azure Service Map para Node.js"
description: "Referencia de los módulos de Azure Service Map para Node.js"
keywords: Azure,SDK,API,Service Map, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Map
ms.openlocfilehash: 330cbceb07ba8bea65c1059a1edb3cd9c69653bc
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="azure-service-map-modules-for-nodejs"></a><span data-ttu-id="21203-104">Módulos de Azure Service Map para Node.js</span><span class="sxs-lookup"><span data-stu-id="21203-104">Azure Service Map modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="21203-105">Información general</span><span class="sxs-lookup"><span data-stu-id="21203-105">Overview</span></span>

<span data-ttu-id="21203-106">Mapa de servicio detecta automáticamente los componentes de la aplicación en sistemas Windows y Linux y asigna la comunicación entre servicios.</span><span class="sxs-lookup"><span data-stu-id="21203-106">Service Map automatically discovers application components on Windows and Linux systems and maps the communication between services.</span></span> <span data-ttu-id="21203-107">Service Map muestra las conexiones entre servidores, procesos y puertos en cualquier arquitectura conectada TCP sin necesidad de ninguna configuración más allá de la instalación de un agente.</span><span class="sxs-lookup"><span data-stu-id="21203-107">Service Map shows connections between servers, processes, and ports across any TCP-connected architecture, with no configuration required other than the installation of an agent.</span></span>

<span data-ttu-id="21203-108">Más información acerca de [Azure Service Map](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map).</span><span class="sxs-lookup"><span data-stu-id="21203-108">Learn more about [Azure Service Map](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map).</span></span>

## <a name="management-package"></a><span data-ttu-id="21203-109">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="21203-109">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="21203-110">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="21203-110">Install the npm module</span></span>

<span data-ttu-id="21203-111">Instale el módulo npm de Azure Service Map.</span><span class="sxs-lookup"><span data-stu-id="21203-111">Install the Azure Service Map npm module</span></span>

```bash
npm install azure-arm-servicemap
```

### <a name="example"></a><span data-ttu-id="21203-112">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="21203-112">Example</span></span>

<span data-ttu-id="21203-113">En este ejemplo se enumeran todos los mapas de servicio para el área de trabajo y el grupo de recursos especificados.</span><span class="sxs-lookup"><span data-stu-id="21203-113">This example lists all service maps for the specified resource group and workspace.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const serviceMapManagement = require('azure-arm-servicemap');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const workspace = 'your-workspace';
let serviceMapClient;

msRestAzure.interactiveLogin().then(credentials => {
  serviceMapClient = new serviceMapManagement(credentials, subscriptionId);
  serviceMapClient.machineGroups
    .listByWorkspace(resourceGroup, workspace)
    .then(machineGroups => console.log('Retrieved machine groups: ', machineGroups));
});
```

## <a name="samples"></a><span data-ttu-id="21203-114">Muestras</span><span class="sxs-lookup"><span data-stu-id="21203-114">Samples</span></span>

<span data-ttu-id="21203-115">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="21203-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
