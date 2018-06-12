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
# <a name="microsoft-azure-sdk-for-nodejs---containerserviceclient"></a>SDK de Microsoft Azure para Node.js: ContainerServiceClient
Este proyecto ofrece un paquete Node.js para tener acceso a Azure. Ahora es compatible con:
- **Node.js versión 6.x.x o posterior**

## <a name="features"></a>Características


## <a name="how-to-install"></a>Cómo instalarlo

```bash
npm install azure-arm-containerservice
```

## <a name="how-to-use"></a>Modo de uso

### <a name="authentication-client-creation-and-list-containerservices-as-an-example"></a>Autenticación, creación de clientes y enumeración de containerServices como ejemplo.

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

## <a name="related-projects"></a>Proyectos relacionados

- [Microsoft Azure SDK for Node.js (Microsoft Azure SDK para Node.js)](https://github.com/Azure/azure-sdk-for-node)