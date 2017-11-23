---
title: "Módulos de Azure Container Registry para Node.js"
description: "Referencia de los módulos de Azure Container Registry para Node.js"
keywords: Azure,SDK,API,Container Registry, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Registry
ms.openlocfilehash: 6ded68c19971a8fe580f440862d0fe05a1def6a2
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="azure-container-registry-modules-for-nodejs"></a><span data-ttu-id="458ad-104">Módulos de Azure Container Registry para Node.js</span><span class="sxs-lookup"><span data-stu-id="458ad-104">Azure Container Registry modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="458ad-105">Información general</span><span class="sxs-lookup"><span data-stu-id="458ad-105">Overview</span></span>

<span data-ttu-id="458ad-106">Azure Container Registry es un servicio administrado de Docker Registry basado en Docker Registry 2.0 de código abierto.</span><span class="sxs-lookup"><span data-stu-id="458ad-106">Azure Container Registry is a managed Docker registry service based on the open-source Docker Registry 2.0.</span></span> <span data-ttu-id="458ad-107">Cree y mantenga los registros de Azure Container para almacenar y administrar las imágenes privadas del contenedor Docker.</span><span class="sxs-lookup"><span data-stu-id="458ad-107">Create and maintain Azure container registries to store and manage your private Docker container images.</span></span> <span data-ttu-id="458ad-108">Use registros de contenedor en Azure con el desarrollo de contenedor y las canalizaciones de implementación existentes y apóyese en el conjunto de la experiencia de la comunidad de Docker.</span><span class="sxs-lookup"><span data-stu-id="458ad-108">Use container registries in Azure with your existing container development and deployment pipelines, and draw on the body of Docker community expertise.</span></span>

## <a name="management-package"></a><span data-ttu-id="458ad-109">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="458ad-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="458ad-110">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="458ad-110">Install the npm module</span></span>

<span data-ttu-id="458ad-111">Instale el módulo npm de Azure Container Registry.</span><span class="sxs-lookup"><span data-stu-id="458ad-111">Install the Azure container registry npm module</span></span>

```bash
npm install azure-arm-containerregistry
```

### <a name="example"></a><span data-ttu-id="458ad-112">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="458ad-112">Example</span></span>

<span data-ttu-id="458ad-113">En este ejemplo se obtiene una lista de los contenedores disponibles.</span><span class="sxs-lookup"><span data-stu-id="458ad-113">This example gets a list of the available containers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="458ad-114">Muestras</span><span class="sxs-lookup"><span data-stu-id="458ad-114">Samples</span></span>

<span data-ttu-id="458ad-115">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="458ad-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
