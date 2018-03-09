---
title: "Módulos de Azure Commerce para Node.js"
description: "Referencia de los módulos de Azure Commerce para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Commerce
ms.openlocfilehash: 0597765543cd838049d3946b90ae128875edd4e5
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2018
---
# <a name="azure-commerce-modules-for-nodejs"></a><span data-ttu-id="34c55-103">Módulos de Azure Commerce para Node.js</span><span class="sxs-lookup"><span data-stu-id="34c55-103">Azure Commerce modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="34c55-104">Información general</span><span class="sxs-lookup"><span data-stu-id="34c55-104">Overview</span></span>

<span data-ttu-id="34c55-105">Use las API de Azure Commerce para extraer datos de uso y de recursos e incorporarlos en las herramientas de análisis de datos de su preferencia.</span><span class="sxs-lookup"><span data-stu-id="34c55-105">Use Azure Commerce APIs to pull usage and resource data into your preferred data analysis tools.</span></span> <span data-ttu-id="34c55-106">Las API de RateCard y de uso de recursos de Azure pueden ayudarlo a predecir y administrar los costos de forma precisa.</span><span class="sxs-lookup"><span data-stu-id="34c55-106">The Azure Resource Usage and RateCard APIs can help you accurately predict and manage your costs.</span></span> <span data-ttu-id="34c55-107">Las API se implementan como proveedor de recursos, como parte de la familia de API expuesta por Azure Resource Manager.</span><span class="sxs-lookup"><span data-stu-id="34c55-107">The APIs are implemented as a Resource Provider and part of the family of APIs exposed by the Azure Resource Manager.</span></span>

## <a name="management-package"></a><span data-ttu-id="34c55-108">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="34c55-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="34c55-109">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="34c55-109">Install the npm module</span></span>

<span data-ttu-id="34c55-110">Instale el módulo npm de Azure Commerce.</span><span class="sxs-lookup"><span data-stu-id="34c55-110">Install the Azure Commerce npm module</span></span>

```bash
npm install azure-arm-commerce
```

### <a name="example"></a><span data-ttu-id="34c55-111">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="34c55-111">Example</span></span>

<span data-ttu-id="34c55-112">En este ejemplo se recuperan los datos de consumo de Azure estimados para el último mes.</span><span class="sxs-lookup"><span data-stu-id="34c55-112">This example retrieves your estimated Azure consumption data for the last month.</span></span>

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

## <a name="samples"></a><span data-ttu-id="34c55-113">Muestras</span><span class="sxs-lookup"><span data-stu-id="34c55-113">Samples</span></span>

<span data-ttu-id="34c55-114">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="34c55-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>