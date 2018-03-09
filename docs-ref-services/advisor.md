---
title: "Módulos de Azure Advisor para Node.js"
description: "Referencia de los módulos de Azure Advisor para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Advisor
ms.openlocfilehash: aad3b292c6304159f68a81270e671cd335c972ec
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2018
---
# <a name="azure-advisor-modules-for-nodejs"></a><span data-ttu-id="43d0a-103">Módulos de Azure Advisor para Node.js</span><span class="sxs-lookup"><span data-stu-id="43d0a-103">Azure Advisor modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="43d0a-104">Información general</span><span class="sxs-lookup"><span data-stu-id="43d0a-104">Overview</span></span>

<span data-ttu-id="43d0a-105">Asistente de Azure es un consultor en la nube personalizado que le ayudará a realizar procedimientos recomendadas para optimizar las implementaciones de Azure.</span><span class="sxs-lookup"><span data-stu-id="43d0a-105">Azure Advisor is a personalized cloud consultant that helps you follow best practices to optimize your Azure deployments.</span></span> <span data-ttu-id="43d0a-106">Advisor analiza la configuración de recursos y la telemetría de uso, y recomienda soluciones que pueden ayudar a mejoran la rentabilidad, el rendimiento, la alta disponibilidad y la seguridad de los recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="43d0a-106">Advisor analyzes your resource configuration and usage telemetry and then recommends solutions that can help you improve the cost effectiveness, performance, high availability, and security of your Azure resources.</span></span>

<span data-ttu-id="43d0a-107">Con Advisor, puede:</span><span class="sxs-lookup"><span data-stu-id="43d0a-107">With Advisor, you can:</span></span>
- <span data-ttu-id="43d0a-108">Obtener sugerencias de procedimientos recomendados proactivas, prácticas y personalizadas,</span><span class="sxs-lookup"><span data-stu-id="43d0a-108">Get proactive, actionable, and personalized best practices recommendations.</span></span>
- <span data-ttu-id="43d0a-109">Mejorar el rendimiento, la seguridad y la alta disponibilidad de los recursos, al mismo tiempo que identifica oportunidades para reducir el gasto general de Azure, y</span><span class="sxs-lookup"><span data-stu-id="43d0a-109">Improve the performance, security, and high availability of your resources, as you identify opportunities to reduce your overall Azure spend.</span></span>
- <span data-ttu-id="43d0a-110">Obtener recomendaciones con acciones propuestas en línea.</span><span class="sxs-lookup"><span data-stu-id="43d0a-110">Get recommendations with proposed actions inline.</span></span>

## <a name="management-package"></a><span data-ttu-id="43d0a-111">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="43d0a-111">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="43d0a-112">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="43d0a-112">Install the npm module</span></span>

<span data-ttu-id="43d0a-113">Instale el módulo npm de Azure Advisor.</span><span class="sxs-lookup"><span data-stu-id="43d0a-113">Install the Azure Advisor npm module</span></span>

```bash
npm install azure-arm-advisor
```

### <a name="example"></a><span data-ttu-id="43d0a-114">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="43d0a-114">Example</span></span>

<span data-ttu-id="43d0a-115">En este ejemplo se muestra la lista de recomendaciones de Azure Advisor.</span><span class="sxs-lookup"><span data-stu-id="43d0a-115">This example displays the list of recommendations from Azure Advisor.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const advisorManagement = require('azure-arm-advisor');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new advisorManagement(credentials, subscriptionId);
  client.recommendations.list().then(recommendations => {
    console.log('List of recommendations:');
    console.dir(recommendations, {depth: null, colors: true});
  });
});
```

## <a name="samples"></a><span data-ttu-id="43d0a-116">Muestras</span><span class="sxs-lookup"><span data-stu-id="43d0a-116">Samples</span></span>

<span data-ttu-id="43d0a-117">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="43d0a-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>