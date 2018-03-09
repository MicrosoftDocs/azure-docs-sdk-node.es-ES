---
title: "Módulos de Azure Search para Node.js"
description: "Referencia de los módulos de Azure Search para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Search
ms.openlocfilehash: bf99013b4479548d07531358bc5103b4e6ac7977
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2018
---
# <a name="azure-search-modules-for-nodejs"></a><span data-ttu-id="ec3dd-103">Módulos de Azure Search para Node.js</span><span class="sxs-lookup"><span data-stu-id="ec3dd-103">Azure Search modules for Node.js</span></span>

<span data-ttu-id="ec3dd-104">Azure Search es una solución de búsqueda como servicio en la nube que delega la administración de los servidores y la infraestructura a Microsoft, dejando así un servicio listo para usar que puede completar con sus propios datos y usar para buscar en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ec3dd-104">Azure Search is a cloud search-as-a-service solution that delegates server and infrastructure management to Microsoft, leaving you with a ready-to-use service that you can populate with your data and then use to add search to your application.</span></span>

<span data-ttu-id="ec3dd-105">Más información sobre [Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search).</span><span class="sxs-lookup"><span data-stu-id="ec3dd-105">Learn more about [Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search).</span></span>

## <a name="management-package"></a><span data-ttu-id="ec3dd-106">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="ec3dd-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="ec3dd-107">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="ec3dd-107">Install the npm module</span></span>

<span data-ttu-id="ec3dd-108">Instale el módulo npm de Azure Search.</span><span class="sxs-lookup"><span data-stu-id="ec3dd-108">Install the Azure Search npm module</span></span>

```bash
npm install azure-arm-search
```

### <a name="example"></a><span data-ttu-id="ec3dd-109">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ec3dd-109">Example</span></span>

<span data-ttu-id="ec3dd-110">En este ejemplo se crea un nuevo servicio Search en Azure y muestra los recursos de su grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="ec3dd-110">This example creates a new Search service in Azure, and lists the resources in its resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const SearchManagement = require('azure-arm-search');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'yourResourceGroup';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new SearchManagement(credentials, subscriptionId);
    return client.services.listByResourceGroup(resourceGroup);
  })
  .then(services => console.dir(services, { depth: null, colors: true }))
  .catch(err => {
    console.log('An error ocurred');
    console.dir(err, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="ec3dd-111">Muestras</span><span class="sxs-lookup"><span data-stu-id="ec3dd-111">Samples</span></span>

<span data-ttu-id="ec3dd-112">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="ec3dd-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>