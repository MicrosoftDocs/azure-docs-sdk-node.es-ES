---
title: Módulos de Azure Scheduler para Node.js
description: Referencia de los módulos de Azure Scheduler para Node.js
author: rloutlaw
ms.author: ROutlaw
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Scheduler
ms.openlocfilehash: 9a842919fddb3d6448d5a4e951dc58dd0d3211e0
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2018
ms.locfileid: "50406481"
---
# <a name="azure-scheduler-modules-for-nodejs"></a>Módulos de Azure Scheduler para Node.js

Azure Scheduler crea, mantiene e invoca el trabajo programado a través de HTTP, HTTPS, una cola de almacenamiento o el servicio [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview).

Más información sobre [Azure Scheduler](/azure/scheduler/scheduler-intro).

## <a name="management-package"></a>Paquete de administración

Cree, mantenga e invoque el trabajo programado a través de diversos canales de comunicación con la API de administración.

### <a name="install-the-npm-module"></a>Instalación del módulo npm

Instale el módulo npm de Azure Scheduler.

```bash
npm install azure-arm-scheduler
```

### <a name="example"></a>Ejemplo

En este ejemplo se enumeran los programadores actuales.

```javascript
const msRestAzure = require('ms-rest-azure')
const SchedulerManagement = require('azure-arm-scheduler')

msRestAzure.interactiveLogin().then(credentials => {
    // Create a scheduler from the login credentials
    let client = new SchedulerManagement(credentials, 'your-subscription-id')
    // Get the full list of current jobs for the subscription
    return client.jobCollections.listBySubscription()
}).then(currentJobs => {
    console.log("Current jobs:")
    console.dir(currentJobs, {depth:null, colors:true})
}).catch(error => {
    console.log("An error occurred:")
    console.dir(error, {depth:null, colors:true})
})
```

## <a name="samples"></a>Ejemplos

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
