---
title: Módulos de Azure DevTest Labs para Node.js
description: Referencia de los módulos de Azure DevTest Labs para Node.js
author: craigcaseyMSFT
ms.author: v-craic
manager: v-laurab
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DevTest Labs
ms.openlocfilehash: 4528bf6a09bc86d23bfec982988added1aa3e257
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/08/2018
ms.locfileid: "51192378"
---
# <a name="azure-devtest-labs-modules-for-nodejs"></a><span data-ttu-id="89cfc-103">Módulos de Azure DevTest Labs para Node.js</span><span class="sxs-lookup"><span data-stu-id="89cfc-103">Azure DevTest Labs modules for Node.js</span></span>

<span data-ttu-id="89cfc-104">Azure DevTest Labs es un servicio que ayuda a los desarrolladores y evaluadores a crear rápidamente entornos de Azure al tiempo que se optimizan los recursos y se controlan los costos.</span><span class="sxs-lookup"><span data-stu-id="89cfc-104">Azure DevTest Labs is a service that helps developers and testers quickly create environments in Azure while minimizing waste and controlling cost.</span></span> <span data-ttu-id="89cfc-105">Puede probar la versión más reciente de la aplicación aprovisionando rápidamente entornos de Windows y Linux mediante plantillas y artefactos reutilizables.</span><span class="sxs-lookup"><span data-stu-id="89cfc-105">You can test the latest version of your application by quickly provisioning Windows and Linux environments using reusable templates and artifacts.</span></span> <span data-ttu-id="89cfc-106">Integre fácilmente la canalización de la implementación con DevTest Labs para aprovisionar entornos a petición.</span><span class="sxs-lookup"><span data-stu-id="89cfc-106">Easily integrate your deployment pipeline with DevTest Labs to provision on-demand environments.</span></span> <span data-ttu-id="89cfc-107">Escale verticalmente las pruebas de carga mediante el aprovisionamiento de varios agentes de prueba y cree entornos previamente aprovisionados con fines de capacitación y demostración.</span><span class="sxs-lookup"><span data-stu-id="89cfc-107">Scale up your load testing by provisioning multiple test agents, and create pre-provisioned environments for training and demos.</span></span>

## <a name="management-package"></a><span data-ttu-id="89cfc-108">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="89cfc-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="89cfc-109">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="89cfc-109">Install the npm module</span></span>

<span data-ttu-id="89cfc-110">Instale el módulo npm Azure DevTest Labs.</span><span class="sxs-lookup"><span data-stu-id="89cfc-110">Install the Azure DevTest Labs npm module</span></span>

```bash
npm install azure-arm-devtestlabs
```

### <a name="example"></a><span data-ttu-id="89cfc-111">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="89cfc-111">Example</span></span>

<span data-ttu-id="89cfc-112">En este ejemplo se obtienen e imprimen los detalles de un laboratorio.</span><span class="sxs-lookup"><span data-stu-id="89cfc-112">This example gets and prints the details of a lab.</span></span>

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

## <a name="samples"></a><span data-ttu-id="89cfc-113">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="89cfc-113">Samples</span></span>

<span data-ttu-id="89cfc-114">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="89cfc-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
