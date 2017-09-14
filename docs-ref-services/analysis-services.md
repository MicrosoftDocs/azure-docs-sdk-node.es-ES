---
title: "Módulos de Azure Analysis Services para Node.js"
description: "Referencia de los módulos de Azure Analysis Services para Node.js"
keywords: Azure,SDK,API,Analysis Services, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Analysis Services
ms.openlocfilehash: ff38883eed2de5d95fb5bd5fd951c6b9564a4b35
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="azure-analysis-services-modules-for-nodejs"></a><span data-ttu-id="15247-104">Módulos de Azure Analysis Services para Node.js</span><span class="sxs-lookup"><span data-stu-id="15247-104">Azure Analysis Services modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="15247-105">Información general</span><span class="sxs-lookup"><span data-stu-id="15247-105">Overview</span></span>
<span data-ttu-id="15247-106">Este paquete proporciona un módulo Node.js que permite administrar fácilmente Microsoft Azure Analysis Services.</span><span class="sxs-lookup"><span data-stu-id="15247-106">This package provides a Node.js module that makes it easy to manage Microsoft Azure Analysis Services.</span></span>

## <a name="management-package"></a><span data-ttu-id="15247-107">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="15247-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="15247-108">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="15247-108">Install the npm module</span></span>

<span data-ttu-id="15247-109">Instale el módulo npm de Azure Analysis Services.</span><span class="sxs-lookup"><span data-stu-id="15247-109">Install the Azure Analysis Services npm module</span></span>

```bash
npm install azure-arm-analysisservices
```

### <a name="example"></a><span data-ttu-id="15247-110">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="15247-110">Example</span></span>

<span data-ttu-id="15247-111">En este ejemplo se enumeran todos los servidores de Analysis Services disponibles.</span><span class="sxs-lookup"><span data-stu-id="15247-111">This example lists all available Analysis Service servers.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const analysisServicesManagement = require('azure-arm-analysisservices');

const subscriptionId = 'your-subscription-id';
let analysisServicesClient;

msRestAzure.interactiveLogin().then(credentials => {
  analysisServicesClient = new analysisServicesManagement(credentials, subscriptionId);

  analysisServicesClient.servers
    .list()
    .then(servers => console.log('Retrieved analysis services servers: ', servers));
});
```

## <a name="samples"></a><span data-ttu-id="15247-112">Muestras</span><span class="sxs-lookup"><span data-stu-id="15247-112">Samples</span></span>

<span data-ttu-id="15247-113">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="15247-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
