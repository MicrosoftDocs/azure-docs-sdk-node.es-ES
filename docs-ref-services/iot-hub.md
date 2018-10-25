---
title: Módulos de Azure IoT Hub para Node.js
description: Referencia de los módulos de Azure IoT Hub para Node.js
author: dominicbetts
ms.author: dobett
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: IoT Hub
ms.openlocfilehash: 1f83e016023722f149384ac015726e9257a9f3af
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "49702850"
---
# <a name="azure-iot-hub-modules-for-nodejs"></a>Módulos de Azure IoT Hub para Node.js

Azure IoT Hub es un servicio totalmente administrado que permite la comunicación bidireccional fiable y segura entre millones de dispositivos IoT y un back-end de soluciones. Azure IoT Hub:
- Proporciona varias opciones de comunicación de dispositivo a la nube y de la nube al dispositivo, como métodos de solicitud y respuesta, mensajería unidireccional y transferencia de archivos.
- Proporciona enrutamiento de mensajes declarativos integrado a otros servicios de Azure.
- Proporciona almacenamiento consultable para metadatos del dispositivo e información de estado sincronizada.
- Habilita las comunicaciones seguras y el control de acceso con claves de seguridad por dispositivo o certificados X.509.
- Proporciona una supervisión exhaustiva para la conectividad de dispositivos y los eventos de administración de identidad de dispositivos.
- Incluye bibliotecas de dispositivos para las plataformas y los lenguajes más populares.

Utilice npm para instalar los módulos de Azure IoT Hub para Node.js.

## <a name="management-package"></a>Paquete de administración

### <a name="install-the-npm-module"></a>Instalación del módulo npm

Instale el módulo npm de Azure IoT Hub.

```bash
npm install azure-arm-iothub
```

### <a name="example"></a>Ejemplo

En este ejemplo se va a crear un centro de IoT y se le dará un nombre.

```javascript
const msRestAzure = require('ms-rest-azure');
const IoTHubClient = require('azure-arm-iothub');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const hubName = 'your-hub';
const location = 'East US';

// Describe the IoT hub you want to create
const hubDescription = {
  name: hubName,
  location: location,
  subscriptionid: subscriptionId,
  resourcegroup: resourceGroup,
  sku: { name: 'S1', capacity: 2 },
  properties: {
    enableFileUploadNotifications: false,
    ipFilterRules: [{ filterName: 'ipfilterrule', action: 'accept', ipMask: '0.0.0.0/0' }],
    operationsMonitoringProperties: {
      events: {
        C2DCommands: 'Error',
        DeviceTelemetry: 'Error',
        DeviceIdentityOperations: 'Error',
        Connections: 'Error, Information'
      }
    },
    features: 'None'
  }
};

msRestAzure.interactiveLogin().then(credentials => {
  const client = new IoTHubClient(credentials, subscriptionId);

  client.iotHubResource
    .createOrUpdate(resourceGroup, hubName, hubDescription)
    .then(hubDescriptionResult => console.log(hubDescriptionResult))
    .catch(err => console.error(err));
});
```

En este ejemplo se va a obtener el centro de IoT existente, por su nombre.

```javascript
const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const hubName = 'your-hub';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new IoTHubClient(credentials, subscriptionId);

  client.iotHubResource
    .get(resourceGroup, hubName)
    .then(hubDescriptionResult => console.log(hubDescriptionResult))
    .catch(err => console.error(err));
});
```

## <a name="samples"></a>Ejemplos

- [Get started with the Raspberry Pi Azure IoT Starter Kit](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/) (Introducción a Starter Kit de IoT de Azure de Raspberry Pi)
- [Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/) (Anomalías de vibración de tweets detectadas por los servicios Azure IoT en los datos de un Intel Edison que ejecuta Node.js)

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
