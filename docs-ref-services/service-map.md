---
title: Módulos de Azure Service Map para Node.js
description: Referencia de los módulos de Azure Service Map para Node.js
author: bwren
ms.author: bwren
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Map
ms.openlocfilehash: 494d948896d65dd67b06f455386f500346862beb
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/08/2018
ms.locfileid: "51190924"
---
# <a name="azure-service-map-modules-for-nodejs"></a><span data-ttu-id="fa8a0-103">Módulos de Azure Service Map para Node.js</span><span class="sxs-lookup"><span data-stu-id="fa8a0-103">Azure Service Map modules for Node.js</span></span>

<span data-ttu-id="fa8a0-104">Mapa de servicio detecta automáticamente los componentes de la aplicación en sistemas Windows y Linux y asigna la comunicación entre servicios.</span><span class="sxs-lookup"><span data-stu-id="fa8a0-104">Service Map automatically discovers application components on Windows and Linux systems and maps the communication between services.</span></span> <span data-ttu-id="fa8a0-105">Service Map muestra las conexiones entre servidores, procesos y puertos en cualquier arquitectura conectada TCP sin necesidad de ninguna configuración más allá de la instalación de un agente.</span><span class="sxs-lookup"><span data-stu-id="fa8a0-105">Service Map shows connections between servers, processes, and ports across any TCP-connected architecture, with no configuration required other than the installation of an agent.</span></span>

<span data-ttu-id="fa8a0-106">Más información acerca de [Azure Service Map](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map).</span><span class="sxs-lookup"><span data-stu-id="fa8a0-106">Learn more about [Azure Service Map](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map).</span></span>

## <a name="management-package"></a><span data-ttu-id="fa8a0-107">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="fa8a0-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="fa8a0-108">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="fa8a0-108">Install the npm module</span></span>

<span data-ttu-id="fa8a0-109">Instale el módulo npm de Azure Service Map.</span><span class="sxs-lookup"><span data-stu-id="fa8a0-109">Install the Azure Service Map npm module</span></span>

```bash
npm install azure-arm-servicemap
```

### <a name="example"></a><span data-ttu-id="fa8a0-110">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="fa8a0-110">Example</span></span>

<span data-ttu-id="fa8a0-111">En este ejemplo se enumeran todos los mapas de servicio para el área de trabajo y el grupo de recursos especificados.</span><span class="sxs-lookup"><span data-stu-id="fa8a0-111">This example lists all service maps for the specified resource group and workspace.</span></span>

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

## <a name="samples"></a><span data-ttu-id="fa8a0-112">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="fa8a0-112">Samples</span></span>

<span data-ttu-id="fa8a0-113">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="fa8a0-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
