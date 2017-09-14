---
title: "Módulos de Azure Commerce para Node.js"
description: "Referencia de los módulos de Azure Commerce para Node.js"
keywords: Azure,SDK,API,Commerce, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Commerce
ms.openlocfilehash: b337e070ee7da0b852d8cad1d4e163d7f8130857
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="azure-commerce-modules-for-nodejs"></a><span data-ttu-id="623c3-104">Módulos de Azure Commerce para Node.js</span><span class="sxs-lookup"><span data-stu-id="623c3-104">Azure Commerce modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="623c3-105">Información general</span><span class="sxs-lookup"><span data-stu-id="623c3-105">Overview</span></span>

<span data-ttu-id="623c3-106">Use las API de Azure Commerce para extraer datos de uso y de recursos e incorporarlos en las herramientas de análisis de datos de su preferencia.</span><span class="sxs-lookup"><span data-stu-id="623c3-106">Use Azure Commerce APIs to pull usage and resource data into your preferred data analysis tools.</span></span> <span data-ttu-id="623c3-107">Las API de RateCard y de uso de recursos de Azure pueden ayudarlo a predecir y administrar los costos de forma precisa.</span><span class="sxs-lookup"><span data-stu-id="623c3-107">The Azure Resource Usage and RateCard APIs can help you accurately predict and manage your costs.</span></span> <span data-ttu-id="623c3-108">Las API se implementan como proveedor de recursos, como parte de la familia de API expuesta por Azure Resource Manager.</span><span class="sxs-lookup"><span data-stu-id="623c3-108">The APIs are implemented as a Resource Provider and part of the family of APIs exposed by the Azure Resource Manager.</span></span>

## <a name="management-package"></a><span data-ttu-id="623c3-109">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="623c3-109">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="623c3-110">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="623c3-110">Install the npm module</span></span>

<span data-ttu-id="623c3-111">Instale el módulo npm de Azure Commerce.</span><span class="sxs-lookup"><span data-stu-id="623c3-111">Install the Azure Commerce npm module</span></span>

```bash
npm install azure-arm-commerce
```

### <a name="example"></a><span data-ttu-id="623c3-112">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="623c3-112">Example</span></span>

<span data-ttu-id="623c3-113">En este ejemplo se recuperan los datos de consumo de Azure estimados para el último mes.</span><span class="sxs-lookup"><span data-stu-id="623c3-113">This example retrieves your estimated Azure consumption data for the last month.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const CommerceManagement = require('azure-arm-commerce');

const endDate = new Date();
endDate.setUTCHours(0, 0, 0, 0);
const startDate = new Date();
startDate.setMonth(startDate.getMonth() - 1);
startDate.setUTCHours(0, 0, 0, 0);

const subscriptionId = 'your-subscription-id';
const usageOptions = {
  showDetails: true,
  granularity: 'Daily'
};

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new CommerceManagement(credentials, subscriptionId);
    return client.usageAggregates.list(startDate, endDate, usageOptions);
  })
  .then(usage => {
    console.dir(usage, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="623c3-114">Muestras</span><span class="sxs-lookup"><span data-stu-id="623c3-114">Samples</span></span>

<span data-ttu-id="623c3-115">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="623c3-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
