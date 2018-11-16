---
title: Módulos de Azure Service Fabric para Node.js
description: Referencia de los módulos de Azure Service Fabric para Node.js
author: rwike77
ms.author: ryanwi
manager: timlt
ms.date: 11/12/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Fabric
ms.openlocfilehash: 3fd2f73bc6fddf01548bbb92cce540775d4c7c76
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2018
ms.locfileid: "51438409"
---
# <a name="azure-service-fabric-modules-for-nodejs"></a>Módulos de Azure Service Fabric para Node.js

## <a name="overview"></a>Información general

Azure Service Fabric es una plataforma de sistemas distribuidos que facilita el empaquetado, la implementación y la administración de microservicios y contenedores escalables y confiables.

Más información acerca de [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).

## <a name="management-package"></a>Paquete de administración

### <a name="install-the-npm-module"></a>Instalación del módulo npm

Instale el módulo npm de Azure Service Fabric.

```bash
npm install azure-arm-servicefabric
```

### <a name="example"></a>Ejemplo

En este ejemplo se muestra cómo enumerar los clústeres para una suscripción de Azure.

```javascript
const msRestAzure = require('ms-rest-azure');
const ServiceFabricManagement = require('azure-arm-servicefabric');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new ServiceFabricManagement(
      credentials,
      subscriptionId
    );
    return client.clusters.list();
  })
  .then(clusters => {
    console.log('List of clusters:');
    console.dir(clusters, { depth: null, colors: true });
  });
```

## <a name="samples"></a>Ejemplos

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
