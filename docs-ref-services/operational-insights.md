---
title: Módulos de Azure Operational Insights para Node.js
description: Referencia de los módulos de Azure Operational Insights para Node.js
author: MGoedtel
ms.author: magoedte
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Operational Insights
ms.openlocfilehash: c8a137c4759982e0551d9048ac271780e6a68afe
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2018
ms.locfileid: "50270978"
---
# <a name="azure-operational-insights-modules-for-nodejs"></a><span data-ttu-id="64414-103">Módulos de Azure Operational Insights para Node.js</span><span class="sxs-lookup"><span data-stu-id="64414-103">Azure Operational Insights Modules for Node.js</span></span>

<span data-ttu-id="64414-104">Utilice npm para instalar los módulos de Azure Operational Insights para Node.js.</span><span class="sxs-lookup"><span data-stu-id="64414-104">Use npm to install the Azure Operational Insights module for Node.js</span></span>

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a><span data-ttu-id="64414-105">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="64414-105">Example</span></span> 

<span data-ttu-id="64414-106">En este ejemplo se crea un cliente, se conecta a Operational Insights y recupera una lista de áreas de trabajo por un grupo de recursos especificado.</span><span class="sxs-lookup"><span data-stu-id="64414-106">This example creates a client, connects to Operational Insights and retreives a list of workspaces by a specified resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="64414-107">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="64414-107">Samples</span></span>

<span data-ttu-id="64414-108">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="64414-108">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
