---
title: "Módulos de Azure Traffic Manager para Node.js"
description: "Referencia de los módulos de Azure Traffic Manager para Node.js"
keywords: Azure,SDK,API,Traffic Manager, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Traffic Manager
ms.openlocfilehash: a74818b9a92bc6ec781b6d47921a7ef43e90cd31
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="azure-traffic-manager-modules-for-nodejs"></a><span data-ttu-id="1530b-104">Módulos de Azure Traffic Manager para Node.js</span><span class="sxs-lookup"><span data-stu-id="1530b-104">Azure Traffic Manager modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="1530b-105">Información general</span><span class="sxs-lookup"><span data-stu-id="1530b-105">Overview</span></span>

<span data-ttu-id="1530b-106">Microsoft Azure Traffic Manager permite controlar la distribución del tráfico de los usuarios para puntos de conexión de servicio en distintos centros de datos.</span><span class="sxs-lookup"><span data-stu-id="1530b-106">Microsoft Azure Traffic Manager allows you to control the distribution of user traffic for service endpoints in different datacenters.</span></span> <span data-ttu-id="1530b-107">Entre los puntos de conexión de servicio compatibles con Traffic Manager, se incluyen máquinas virtuales de Azure, Web Apps y servicios en la nube.</span><span class="sxs-lookup"><span data-stu-id="1530b-107">Service endpoints supported by Traffic Manager include Azure VMs, Web Apps, and cloud services.</span></span> <span data-ttu-id="1530b-108">También puede utilizar el Administrador de tráfico con puntos de conexión externos, que no forman parte de Azure.</span><span class="sxs-lookup"><span data-stu-id="1530b-108">You can also use Traffic Manager with external, non-Azure endpoints.</span></span>

<span data-ttu-id="1530b-109">Más información acerca de [Azure Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span><span class="sxs-lookup"><span data-stu-id="1530b-109">Learn more about [Azure Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="1530b-110">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="1530b-110">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="1530b-111">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="1530b-111">Install the npm module</span></span>

<span data-ttu-id="1530b-112">Instale el módulo npm de Azure Traffic Manager.</span><span class="sxs-lookup"><span data-stu-id="1530b-112">Install the Azure traffic manager npm module</span></span>

```bash
npm install azure-arm-trafficmanager
```

### <a name="example"></a><span data-ttu-id="1530b-113">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1530b-113">Example</span></span>

<span data-ttu-id="1530b-114">En este ejemplo se enumeran todas las instancias de Traffic Manager para un grupo de recursos determinado.</span><span class="sxs-lookup"><span data-stu-id="1530b-114">This example lists all Traffic Managers for a given resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="1530b-115">Muestras</span><span class="sxs-lookup"><span data-stu-id="1530b-115">Samples</span></span>

<span data-ttu-id="1530b-116">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="1530b-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
