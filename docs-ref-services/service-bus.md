---
title: Módulos de Azure Service Bus para Node.js
description: Referencia de los módulos de Azure Service Bus para Node.js
author: sethmanheim
ms.author: sethm
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Bus
ms.openlocfilehash: fde02006fcf364071fcb866098dba7fcd3b1c07b
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="azure-service-bus-modules-for-nodejs"></a>Módulos de Azure Service Bus para Node.js

Azure Service Bus es una plataforma en la nube de mensajería asincrónica que le permite enviar datos entre sistemas desacoplados.

Aprenda más sobre [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).

## <a name="management-package"></a>Paquete de administración

### <a name="install-the-npm-module"></a>Instalación del módulo npm

Utilice npm para instalar el módulo de Azure Service Bus para Node.js.

```bash
npm install azure-arm-sb
```

### <a name="example"></a>Ejemplo

En este ejemplo se crea a un cliente y después se enumeran todos los espacios de nombres de Service Bus asociados a una suscripción determinada.

```javascript
const msRestAzure = require('ms-rest-azure');
const ServicebusManagement = require('azure-arm-sb');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = new ServicebusManagement(credentials, subscriptionId);
    client.namespaces.listBySubscription().then(namespaces => {
        namespaces.map(ns => {
            console.log(`found ns : ${ns.name}`);
        });
    });
});
```

## <a name="samples"></a>Ejemplos

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
