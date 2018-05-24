---
title: Módulos de Azure Traffic Manager para Node.js
description: Referencia de los módulos de Azure Traffic Manager para Node.js
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Traffic Manager
ms.openlocfilehash: 904a6693f557b90f5a1eeeea2367b56f8dfe3ff1
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="azure-traffic-manager-modules-for-nodejs"></a><span data-ttu-id="806c4-103">Módulos de Azure Traffic Manager para Node.js</span><span class="sxs-lookup"><span data-stu-id="806c4-103">Azure Traffic Manager modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="806c4-104">Información general</span><span class="sxs-lookup"><span data-stu-id="806c4-104">Overview</span></span>

<span data-ttu-id="806c4-105">Microsoft Azure Traffic Manager permite controlar la distribución del tráfico de los usuarios para puntos de conexión de servicio en distintos centros de datos.</span><span class="sxs-lookup"><span data-stu-id="806c4-105">Microsoft Azure Traffic Manager allows you to control the distribution of user traffic for service endpoints in different datacenters.</span></span> <span data-ttu-id="806c4-106">Entre los puntos de conexión de servicio compatibles con Traffic Manager, se incluyen máquinas virtuales de Azure, Web Apps y servicios en la nube.</span><span class="sxs-lookup"><span data-stu-id="806c4-106">Service endpoints supported by Traffic Manager include Azure VMs, Web Apps, and cloud services.</span></span> <span data-ttu-id="806c4-107">También puede utilizar el Administrador de tráfico con puntos de conexión externos, que no forman parte de Azure.</span><span class="sxs-lookup"><span data-stu-id="806c4-107">You can also use Traffic Manager with external, non-Azure endpoints.</span></span>

<span data-ttu-id="806c4-108">Más información acerca de [Azure Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span><span class="sxs-lookup"><span data-stu-id="806c4-108">Learn more about [Azure Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="806c4-109">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="806c4-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="806c4-110">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="806c4-110">Install the npm module</span></span>

<span data-ttu-id="806c4-111">Instale el módulo npm de Azure Traffic Manager.</span><span class="sxs-lookup"><span data-stu-id="806c4-111">Install the Azure traffic manager npm module</span></span>

```bash
npm install azure-arm-trafficmanager
```

### <a name="example"></a><span data-ttu-id="806c4-112">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="806c4-112">Example</span></span>

<span data-ttu-id="806c4-113">En este ejemplo se enumeran todas las instancias de Traffic Manager para un grupo de recursos determinado.</span><span class="sxs-lookup"><span data-stu-id="806c4-113">This example lists all Traffic Managers for a given resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const trafficManager = require('azure-arm-trafficmanager');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new trafficManager(credentials, subscriptionId);
  const resourceGroupName = 'resource-group-name';
  client.profiles.listAllInResourceGroup(resourceGroupName).then(profiles => {
    profiles.map(profile => {
      console.log(`found profile : ${profile.name}`);
    });
  });
});
```

## <a name="samples"></a><span data-ttu-id="806c4-114">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="806c4-114">Samples</span></span>

<span data-ttu-id="806c4-115">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="806c4-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
