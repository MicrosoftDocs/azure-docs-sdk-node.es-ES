---
title: "Módulos de Azure Container Registry para Node.js"
description: "Referencia de los módulos de Azure Container Registry para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Registry
ms.openlocfilehash: dda0e9bbfaa8a3e060f3b8f820d5bab315662629
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2018
---
# <a name="azure-container-registry-modules-for-nodejs"></a><span data-ttu-id="5fac0-103">Módulos de Azure Container Registry para Node.js</span><span class="sxs-lookup"><span data-stu-id="5fac0-103">Azure Container Registry modules for Node.js</span></span>

<span data-ttu-id="5fac0-104">Azure Container Registry es un servicio administrado de Docker Registry basado en Docker Registry 2.0 de código abierto.</span><span class="sxs-lookup"><span data-stu-id="5fac0-104">Azure Container Registry is a managed Docker registry service based on the open-source Docker Registry 2.0.</span></span> <span data-ttu-id="5fac0-105">Cree y mantenga los registros de Azure Container para almacenar y administrar las imágenes privadas del contenedor Docker.</span><span class="sxs-lookup"><span data-stu-id="5fac0-105">Create and maintain Azure container registries to store and manage your private Docker container images.</span></span> <span data-ttu-id="5fac0-106">Use registros de contenedor en Azure con el desarrollo de contenedor y las canalizaciones de implementación existentes y apóyese en el conjunto de la experiencia de la comunidad de Docker.</span><span class="sxs-lookup"><span data-stu-id="5fac0-106">Use container registries in Azure with your existing container development and deployment pipelines, and draw on the body of Docker community expertise.</span></span>

## <a name="management-package"></a><span data-ttu-id="5fac0-107">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="5fac0-107">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="5fac0-108">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="5fac0-108">Install the npm module</span></span>

<span data-ttu-id="5fac0-109">Instale el módulo npm de Azure Container Registry.</span><span class="sxs-lookup"><span data-stu-id="5fac0-109">Install the Azure container registry npm module</span></span>

```bash
npm install azure-arm-containerregistry
```

### <a name="example"></a><span data-ttu-id="5fac0-110">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="5fac0-110">Example</span></span>

<span data-ttu-id="5fac0-111">En este ejemplo se obtiene una lista de los contenedores disponibles.</span><span class="sxs-lookup"><span data-stu-id="5fac0-111">This example gets a list of the available containers.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ContainerRegistryManagement = require('azure-arm-containerregistry');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const manager = new ContainerRegistryManagement(
      credentials,
      subscriptionId
    );
    return manager.registries.list();
  })
  .then(registries => {
    console.log('List of registries:');
    console.dir(registries, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="5fac0-112">Muestras</span><span class="sxs-lookup"><span data-stu-id="5fac0-112">Samples</span></span>

<span data-ttu-id="5fac0-113">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="5fac0-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>