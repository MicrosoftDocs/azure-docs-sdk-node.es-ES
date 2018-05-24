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
ms.openlocfilehash: 77dd4c30da43af7cace048b43b7997fb1952abf1
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="azure-iot-hub-modules-for-nodejs"></a><span data-ttu-id="89c00-103">Módulos de Azure IoT Hub para Node.js</span><span class="sxs-lookup"><span data-stu-id="89c00-103">Azure IoT Hub modules for Node.js</span></span>

<span data-ttu-id="89c00-104">Azure IoT Hub es un servicio totalmente administrado que permite la comunicación bidireccional fiable y segura entre millones de dispositivos IoT y un back-end de soluciones.</span><span class="sxs-lookup"><span data-stu-id="89c00-104">Azure IoT Hub is a fully managed service that enables reliable and secure bidirectional communications between millions of IoT devices and a solution back end.</span></span> <span data-ttu-id="89c00-105">Azure IoT Hub:</span><span class="sxs-lookup"><span data-stu-id="89c00-105">Azure IoT Hub:</span></span>
- <span data-ttu-id="89c00-106">Proporciona varias opciones de comunicación de dispositivo a la nube y de la nube al dispositivo, como métodos de solicitud y respuesta, mensajería unidireccional y transferencia de archivos.</span><span class="sxs-lookup"><span data-stu-id="89c00-106">Provides multiple device-to-cloud and cloud-to-device communication options, including one-way messaging, file transfer, and request-reply methods.</span></span>
- <span data-ttu-id="89c00-107">Proporciona enrutamiento de mensajes declarativos integrado a otros servicios de Azure.</span><span class="sxs-lookup"><span data-stu-id="89c00-107">Provides built-in declarative message routing to other Azure services.</span></span>
- <span data-ttu-id="89c00-108">Proporciona almacenamiento consultable para metadatos del dispositivo e información de estado sincronizada.</span><span class="sxs-lookup"><span data-stu-id="89c00-108">Provides a queryable store for device metadata and synchronized state information.</span></span>
- <span data-ttu-id="89c00-109">Habilita las comunicaciones seguras y el control de acceso con claves de seguridad por dispositivo o certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="89c00-109">Enables secure communications and access control using per-device security keys or X.509 certificates.</span></span>
- <span data-ttu-id="89c00-110">Proporciona una supervisión exhaustiva para la conectividad de dispositivos y los eventos de administración de identidad de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="89c00-110">Provides extensive monitoring for device connectivity and device identity management events.</span></span>
- <span data-ttu-id="89c00-111">Incluye bibliotecas de dispositivos para las plataformas y los lenguajes más populares.</span><span class="sxs-lookup"><span data-stu-id="89c00-111">Includes device libraries for the most popular languages and platforms.</span></span>

<span data-ttu-id="89c00-112">Utilice npm para instalar los módulos de Azure IoT Hub para Node.js.</span><span class="sxs-lookup"><span data-stu-id="89c00-112">Use npm to install the Azure IoT Hub modules for Node.js</span></span>

## <a name="management-package"></a><span data-ttu-id="89c00-113">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="89c00-113">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="89c00-114">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="89c00-114">Install the npm module</span></span>

<span data-ttu-id="89c00-115">Instale el módulo npm de Azure IoT Hub.</span><span class="sxs-lookup"><span data-stu-id="89c00-115">Install the Azure IoT Hub npm module</span></span>

```bash
npm install azure-arm-iothub
```

### <a name="example"></a><span data-ttu-id="89c00-116">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="89c00-116">Example</span></span>

<span data-ttu-id="89c00-117">En este ejemplo se va a crear un centro de IoT y se le dará un nombre.</span><span class="sxs-lookup"><span data-stu-id="89c00-117">This example creates and names an IoT hub.</span></span>

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

<span data-ttu-id="89c00-118">En este ejemplo se va a obtener el centro de IoT existente, por su nombre.</span><span class="sxs-lookup"><span data-stu-id="89c00-118">This example gets the existing IoT hub, by name.</span></span>

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

## <a name="samples"></a><span data-ttu-id="89c00-119">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="89c00-119">Samples</span></span>

- <span data-ttu-id="89c00-120">[Get started with the Raspberry Pi Azure IoT Starter Kit](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/) (Introducción a Starter Kit de IoT de Azure de Raspberry Pi)</span><span class="sxs-lookup"><span data-stu-id="89c00-120">[Get started with the Raspberry Pi Azure IoT Starter Kit](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/)</span></span>
- <span data-ttu-id="89c00-121">[Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/) (Anomalías de vibración de tweets detectadas por los servicios Azure IoT en los datos de un Intel Edison que ejecuta Node.js)</span><span class="sxs-lookup"><span data-stu-id="89c00-121">[Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)</span></span>

<span data-ttu-id="89c00-122">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="89c00-122">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
