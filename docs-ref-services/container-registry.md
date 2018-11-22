---
title: Módulos de Azure Container Registry para Node.js
description: Referencia de los módulos de Azure Container Registry para Node.js
author: mmacy
ms.author: marsma
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Registry
ms.openlocfilehash: f24fa268f9c471925a1bdf0cbae8044d97bc7679
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2018
ms.locfileid: "52155020"
---
# <a name="azure-container-registry-modules-for-nodejs"></a><span data-ttu-id="a7bd2-103">Módulos de Azure Container Registry para Node.js</span><span class="sxs-lookup"><span data-stu-id="a7bd2-103">Azure Container Registry modules for Node.js</span></span>

<span data-ttu-id="a7bd2-104">Azure Container Registry es un servicio administrado de Docker Registry basado en Docker Registry 2.0 de código abierto.</span><span class="sxs-lookup"><span data-stu-id="a7bd2-104">Azure Container Registry is a managed Docker registry service based on the open-source Docker Registry 2.0.</span></span> <span data-ttu-id="a7bd2-105">Cree y mantenga los registros de Azure Container para almacenar y administrar las imágenes privadas del contenedor Docker.</span><span class="sxs-lookup"><span data-stu-id="a7bd2-105">Create and maintain Azure container registries to store and manage your private Docker container images.</span></span> <span data-ttu-id="a7bd2-106">Use registros de contenedor en Azure con el desarrollo de contenedor y las canalizaciones de implementación existentes y apóyese en el conjunto de la experiencia de la comunidad de Docker.</span><span class="sxs-lookup"><span data-stu-id="a7bd2-106">Use container registries in Azure with your existing container development and deployment pipelines, and draw on the body of Docker community expertise.</span></span>

## <a name="management-package"></a><span data-ttu-id="a7bd2-107">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="a7bd2-107">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="a7bd2-108">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="a7bd2-108">Install the npm module</span></span>

<span data-ttu-id="a7bd2-109">Instale el módulo npm de Azure Container Registry.</span><span class="sxs-lookup"><span data-stu-id="a7bd2-109">Install the Azure container registry npm module</span></span>

```bash
npm install azure-arm-containerregistry
```

### <a name="example"></a><span data-ttu-id="a7bd2-110">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a7bd2-110">Example</span></span>

<span data-ttu-id="a7bd2-111">En este ejemplo se obtiene una lista de los contenedores disponibles.</span><span class="sxs-lookup"><span data-stu-id="a7bd2-111">This example gets a list of the available containers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="a7bd2-112">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="a7bd2-112">Samples</span></span>

<span data-ttu-id="a7bd2-113">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="a7bd2-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
