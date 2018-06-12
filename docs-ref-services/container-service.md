---
title: Módulos de Azure Container Service para Node.js
description: Referencia de los módulos de Azure Container Service para Node.js
author: mmacy
ms.author: marsma
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Service
ms.openlocfilehash: 2d0aac2f7f6cc70ab3e40f7b3ccee6f64a011b55
ms.sourcegitcommit: 702a716434eb42f55d8782feb62ae2c6d8147aa9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34689835"
---
# <a name="microsoft-azure-sdk-for-nodejs---containerserviceclient"></a><span data-ttu-id="85ba0-103">SDK de Microsoft Azure para Node.js: ContainerServiceClient</span><span class="sxs-lookup"><span data-stu-id="85ba0-103">Microsoft Azure SDK for Node.js - ContainerServiceClient</span></span>
<span data-ttu-id="85ba0-104">Este proyecto ofrece un paquete Node.js para tener acceso a Azure.</span><span class="sxs-lookup"><span data-stu-id="85ba0-104">This project provides a Node.js package for accessing Azure.</span></span> <span data-ttu-id="85ba0-105">Ahora es compatible con:</span><span class="sxs-lookup"><span data-stu-id="85ba0-105">Right now it supports:</span></span>
- <span data-ttu-id="85ba0-106">**Node.js versión 6.x.x o posterior**</span><span class="sxs-lookup"><span data-stu-id="85ba0-106">**Node.js version 6.x.x or higher**</span></span>

## <a name="features"></a><span data-ttu-id="85ba0-107">Características</span><span class="sxs-lookup"><span data-stu-id="85ba0-107">Features</span></span>


## <a name="how-to-install"></a><span data-ttu-id="85ba0-108">Cómo instalarlo</span><span class="sxs-lookup"><span data-stu-id="85ba0-108">How to Install</span></span>

```bash
npm install azure-arm-containerservice
```

## <a name="how-to-use"></a><span data-ttu-id="85ba0-109">Modo de uso</span><span class="sxs-lookup"><span data-stu-id="85ba0-109">How to use</span></span>

### <a name="authentication-client-creation-and-list-containerservices-as-an-example"></a><span data-ttu-id="85ba0-110">Autenticación, creación de clientes y enumeración de containerServices como ejemplo.</span><span class="sxs-lookup"><span data-stu-id="85ba0-110">Authentication, client creation and list containerServices as an example.</span></span>

```javascript
const msRestAzure = require("ms-rest-azure");
const ContainerServiceClient = require("azure-arm-containerservice");
msRestAzure.interactiveLogin().then((creds) => {
    const subscriptionId = "<Subscription_Id>";
    const client = new ContainerServiceClient(creds, subscriptionId);
    return client.containerServices.list().then((result) => {
      console.log("The result is:");
      console.log(result);
    });
}).catch((err) => {
  console.log('An error ocurred:');
  console.dir(err, {depth: null, colors: true});
});
```

## <a name="related-projects"></a><span data-ttu-id="85ba0-111">Proyectos relacionados</span><span class="sxs-lookup"><span data-stu-id="85ba0-111">Related projects</span></span>

- [<span data-ttu-id="85ba0-112">Microsoft Azure SDK for Node.js (Microsoft Azure SDK para Node.js)</span><span class="sxs-lookup"><span data-stu-id="85ba0-112">Microsoft Azure SDK for Node.js</span></span>](https://github.com/Azure/azure-sdk-for-node)