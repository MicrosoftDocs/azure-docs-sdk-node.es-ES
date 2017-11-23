---
title: "Módulos de Azure Operational Insights para Node.js"
description: "Referencia de los módulos de Azure Operational Insights para Node.js"
keywords: Azure,SDK,API,Operational Insights, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Operational Insights
ms.openlocfilehash: e7f7ee30509125a131346039c1245eb9fa6cb6b1
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="azure-operational-insights-modules-for-nodejs"></a><span data-ttu-id="c2fd8-104">Módulos de Azure Operational Insights para Node.js</span><span class="sxs-lookup"><span data-stu-id="c2fd8-104">Azure Operational Insights Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="c2fd8-105">Información general</span><span class="sxs-lookup"><span data-stu-id="c2fd8-105">Overview</span></span>

## <a name="management-package"></a><span data-ttu-id="c2fd8-106">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="c2fd8-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="c2fd8-107">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="c2fd8-107">Install the npm module</span></span>

<span data-ttu-id="c2fd8-108">Utilice npm para instalar los módulos de Azure Operational Insights para Node.js.</span><span class="sxs-lookup"><span data-stu-id="c2fd8-108">Use npm to install the Azure Operational Insights module for Node.js</span></span>

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a><span data-ttu-id="c2fd8-109">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="c2fd8-109">Example</span></span> 

<span data-ttu-id="c2fd8-110">En este ejemplo se crea un cliente, se conecta a Operational Insights y recupera una lista de áreas de trabajo por un grupo de recursos especificado.</span><span class="sxs-lookup"><span data-stu-id="c2fd8-110">This example creates a client, connects to Operational Insights and retreives a list of workspaces by a specified resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const OperationalInsightsManagement = require('azure-arm-operationalinsights');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = new OperationalInsightsManagement(
        credentials,
        subscriptionId
    );
    return client.workspaces.listByResourceGroup('resource-group-name');
})
.then(workspaces => {
    console.log(workspaces);
});
``` 

## <a name="samples"></a><span data-ttu-id="c2fd8-111">Muestras</span><span class="sxs-lookup"><span data-stu-id="c2fd8-111">Samples</span></span>

<span data-ttu-id="c2fd8-112">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="c2fd8-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
