---
title: "Módulos de Azure DevTest Labs para Node.js"
description: "Referencia de los módulos de Azure DevTest Labs para Node.js"
keywords: Azure,SDK,API,DevTest Labs, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DevTest Labs
ms.openlocfilehash: 933ce8971e02c2898d296112282169b8c7dca1c7
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="azure-devtest-labs-modules-for-nodejs"></a><span data-ttu-id="5bb2d-104">Módulos de Azure DevTest Labs para Node.js</span><span class="sxs-lookup"><span data-stu-id="5bb2d-104">Azure DevTest Labs modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="5bb2d-105">Información general</span><span class="sxs-lookup"><span data-stu-id="5bb2d-105">Overview</span></span>

<span data-ttu-id="5bb2d-106">Azure DevTest Labs es un servicio que ayuda a los desarrolladores y evaluadores a crear rápidamente entornos de Azure al tiempo que se optimizan los recursos y se controlan los costos.</span><span class="sxs-lookup"><span data-stu-id="5bb2d-106">Azure DevTest Labs is a service that helps developers and testers quickly create environments in Azure while minimizing waste and controlling cost.</span></span> <span data-ttu-id="5bb2d-107">Puede probar la versión más reciente de la aplicación aprovisionando rápidamente entornos de Windows y Linux mediante plantillas y artefactos reutilizables.</span><span class="sxs-lookup"><span data-stu-id="5bb2d-107">You can test the latest version of your application by quickly provisioning Windows and Linux environments using reusable templates and artifacts.</span></span> <span data-ttu-id="5bb2d-108">Integre fácilmente la canalización de la implementación con DevTest Labs para aprovisionar entornos a petición.</span><span class="sxs-lookup"><span data-stu-id="5bb2d-108">Easily integrate your deployment pipeline with DevTest Labs to provision on-demand environments.</span></span> <span data-ttu-id="5bb2d-109">Escale verticalmente las pruebas de carga mediante el aprovisionamiento de varios agentes de prueba y cree entornos previamente aprovisionados con fines de capacitación y demostración.</span><span class="sxs-lookup"><span data-stu-id="5bb2d-109">Scale up your load testing by provisioning multiple test agents, and create pre-provisioned environments for training and demos.</span></span>

## <a name="management-package"></a><span data-ttu-id="5bb2d-110">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="5bb2d-110">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="5bb2d-111">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="5bb2d-111">Install the npm module</span></span>

<span data-ttu-id="5bb2d-112">Instale el módulo npm Azure DevTest Labs.</span><span class="sxs-lookup"><span data-stu-id="5bb2d-112">Install the Azure DevTest Labs npm module</span></span>

```bash
npm install azure-arm-devtestlabs
```

### <a name="example"></a><span data-ttu-id="5bb2d-113">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="5bb2d-113">Example</span></span>

<span data-ttu-id="5bb2d-114">En este ejemplo se obtienen e imprimen los detalles de un laboratorio.</span><span class="sxs-lookup"><span data-stu-id="5bb2d-114">This example gets and prints the details of a lab.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const DevTestLabsClient = require('azure-arm-devtestlabs');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';
const labName = 'your-lab-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DevTestLabsClient(credentials, subscriptionId);
    return client.labOperations.getResource(resourceGroupName, labName);
  })
  .then(lab => {
    console.log('Details of lab:');
    console.dir(lab, { depth: null, colors: true });
  });


```

## <a name="samples"></a><span data-ttu-id="5bb2d-115">Muestras</span><span class="sxs-lookup"><span data-stu-id="5bb2d-115">Samples</span></span>

<span data-ttu-id="5bb2d-116">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="5bb2d-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
