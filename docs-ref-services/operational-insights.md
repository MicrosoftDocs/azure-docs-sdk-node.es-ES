---
title: "Módulos de Azure Operational Insights para Node.js"
description: "Referencia de los módulos de Azure Operational Insights para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Operational Insights
ms.openlocfilehash: 7baa7f2f976cec9d9592231f193eede87a122532
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2018
---
# <a name="azure-operational-insights-modules-for-nodejs"></a><span data-ttu-id="f9f64-103">Módulos de Azure Operational Insights para Node.js</span><span class="sxs-lookup"><span data-stu-id="f9f64-103">Azure Operational Insights Modules for Node.js</span></span>

<span data-ttu-id="f9f64-104">Utilice npm para instalar los módulos de Azure Operational Insights para Node.js.</span><span class="sxs-lookup"><span data-stu-id="f9f64-104">Use npm to install the Azure Operational Insights module for Node.js</span></span>

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a><span data-ttu-id="f9f64-105">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="f9f64-105">Example</span></span> 

<span data-ttu-id="f9f64-106">En este ejemplo se crea un cliente, se conecta a Operational Insights y recupera una lista de áreas de trabajo por un grupo de recursos especificado.</span><span class="sxs-lookup"><span data-stu-id="f9f64-106">This example creates a client, connects to Operational Insights and retreives a list of workspaces by a specified resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="f9f64-107">Muestras</span><span class="sxs-lookup"><span data-stu-id="f9f64-107">Samples</span></span>

<span data-ttu-id="f9f64-108">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="f9f64-108">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
