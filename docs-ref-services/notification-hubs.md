---
title: Módulos de Azure Notification Hubs para Node.js
description: Referencia de los módulos de Azure Notification Hubs para Node.js
author: rloutlaw
ms.author: ROutlaw
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Notification Hubs
ms.openlocfilehash: 30b8caa07111f9ceb5fa58f92649e4670aa6bee6
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34261724"
---
# <a name="azure-notification-hubs-modules-for-nodejs"></a>Módulos de Azure Notification Hubs para Node.js

Azure Notification Hubs proporciona un motor de inserción fácil de usar, multiplataforma y escalado horizontalmente. Con una única llamada de API multiplataforma puede enviar fácilmente notificaciones push específicas y personalizadas a cualquier plataforma móvil desde cualquier back-end local o en la nube.

Notification Hubs funciona muy bien tanto para escenarios empresariales como de consumidores. Estos son algunos ejemplos de para qué utilizan los clientes Notification Hubs:
- Enviar notificaciones de noticias de última hora a millones de usuarios con baja latencia.
- Enviar cupones basados en la ubicación a segmentos de usuarios interesados.
- Enviar notificaciones relacionadas con eventos a usuarios o grupos para aplicaciones de medios, deportivas, de finanzas o de juegos.
- Insertar contenido promocional en aplicaciones para ponerse en contacto y comercializar con clientes.
- Informar a los usuarios sobre eventos empresariales como, por ejemplo, nuevos mensajes o elementos de trabajo.
- Enviar códigos para Multi-Factor Authentication.

## <a name="management-package"></a>Paquete de administración

### <a name="install-the-npm-module"></a>Instalación del módulo npm

Instale el módulo de Azure Notification Hubs. 

```bash
npm install azure-arm-notificationhubs
```

### <a name="example"></a>Ejemplo

En este ejemplo se enumeran todos los centros de notificaciones.

 ```javascript
const msRestAzure = require('ms-rest-azure');
const notificationHubsManagementClient = require('azure-arm-notificationhubs');

const subscriptionId = 'your-subscription-id';
const notificationHubNamespace = 'your-hub-namespace';
const resourceGroup = 'your-resource-group';
let notificationHubsClient;

msRestAzure.interactiveLogin().then(credentials => {
  notificationHubsClient = new notificationHubsManagementClient(credentials, subscriptionId);
  notificationHubsClient.notificationHubs
    .list(resourceGroup, notificationHubNamespace)
    .then(notificationHubs => console.log('Retrieved notification hubs: ', notificationHubs));
});
```

## <a name="samples"></a>Ejemplos

* [App Service Mobile completed quickstart for Node.js backend](https://azure.microsoft.com/resources/samples/app-service-mobile-nodejs-backend-quickstart/) (Inicio rápido a App Service Mobile completo para back-end de Node.js)
* [Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/) (Anomalías de vibración de tweets detectadas por los servicios Azure IoT en los datos de un Intel Edison que ejecuta Node.js)

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
