---
title: "Módulos PowerBI Embedded de Azure para Node.js"
description: "Referencia de los módulos PowerBI Embedded de Azure para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: PowerBI Embedded
ms.openlocfilehash: 5dbe134acb38787916f48277b2114e199601e128
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2018
---
# <a name="azure-powerbi-embedded-modules-for-nodejs"></a><span data-ttu-id="d06ba-103">Módulos PowerBI Embedded de Azure para Node.js</span><span class="sxs-lookup"><span data-stu-id="d06ba-103">Azure PowerBI Embedded modules for Node.js</span></span>

<span data-ttu-id="d06ba-104">Con el servicio Power BI Embedded de Azure, puede integrar informes de Power BI directamente en la aplicación de nodo para crear o editar gráficos e informes.</span><span class="sxs-lookup"><span data-stu-id="d06ba-104">With the Power BI Embedded Azure service, you can integrate Power BI reports right into your node application to create or edit charts and reports.</span></span>

<span data-ttu-id="d06ba-105">Más información sobre [Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/).</span><span class="sxs-lookup"><span data-stu-id="d06ba-105">Learn more about [Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/).</span></span>

## <a name="management-package"></a><span data-ttu-id="d06ba-106">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="d06ba-106">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="d06ba-107">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="d06ba-107">Install the npm module</span></span>

<span data-ttu-id="d06ba-108">Instale el módulo npm de Azure Power BI.</span><span class="sxs-lookup"><span data-stu-id="d06ba-108">Install the Azure Power BI npm module</span></span>

```bash
npm install azure-arm-powerbiembedded
```

### <a name="example"></a><span data-ttu-id="d06ba-109">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d06ba-109">Example</span></span>

<span data-ttu-id="d06ba-110">En este ejemplo se crea una colección de áreas de trabajo en un grupo de recursos existente.</span><span class="sxs-lookup"><span data-stu-id="d06ba-110">This example creates a workspace collection in an existing resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const PowerBIEmbeddedManagementClient = require('azure-arm-powerbiembedded');

const creationOptions = {
  location: 'northcentralus',
  tags: {
    key1: 'value1',
    key2: 'value2'
  },
  sku: {
    name: 'S1',
    teir: 'Standard'
  }
};

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group-name';
const workspace = 'workspace-collection-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new PowerBIEmbeddedManagementClient(
      credentials,
      subscriptionId
    );
    return client.workspaceCollections.create(
      resourceGroup,
      workspace,
      creationOptions
    );
  })
  .then(workspaces => console.dir(workspaces, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="d06ba-111">Muestras</span><span class="sxs-lookup"><span data-stu-id="d06ba-111">Samples</span></span>

<span data-ttu-id="d06ba-112">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="d06ba-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>