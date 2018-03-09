---
title: "Módulos de Azure Analysis Services para Node.js"
description: "Referencia de los módulos de Azure Analysis Services para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Analysis Services
ms.openlocfilehash: 7dd9ac4a2a4939b66f5a91d048e49fb59cd547c0
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2018
---
# <a name="azure-analysis-services-modules-for-nodejs"></a><span data-ttu-id="89c32-103">Módulos de Azure Analysis Services para Node.js</span><span class="sxs-lookup"><span data-stu-id="89c32-103">Azure Analysis Services modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="89c32-104">Información general</span><span class="sxs-lookup"><span data-stu-id="89c32-104">Overview</span></span>
<span data-ttu-id="89c32-105">Este paquete proporciona un módulo Node.js que permite administrar fácilmente Microsoft Azure Analysis Services.</span><span class="sxs-lookup"><span data-stu-id="89c32-105">This package provides a Node.js module that makes it easy to manage Microsoft Azure Analysis Services.</span></span>

## <a name="management-package"></a><span data-ttu-id="89c32-106">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="89c32-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="89c32-107">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="89c32-107">Install the npm module</span></span>

<span data-ttu-id="89c32-108">Instale el módulo npm de Azure Analysis Services.</span><span class="sxs-lookup"><span data-stu-id="89c32-108">Install the Azure Analysis Services npm module</span></span>

```bash
npm install azure-arm-analysisservices
```

### <a name="example"></a><span data-ttu-id="89c32-109">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="89c32-109">Example</span></span>

<span data-ttu-id="89c32-110">En este ejemplo se enumeran todos los servidores de Analysis Services disponibles.</span><span class="sxs-lookup"><span data-stu-id="89c32-110">This example lists all available Analysis Service servers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="89c32-111">Muestras</span><span class="sxs-lookup"><span data-stu-id="89c32-111">Samples</span></span>

<span data-ttu-id="89c32-112">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="89c32-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>