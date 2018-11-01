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
ms.openlocfilehash: 18eae632b41b71bc64b052852b677507da2678e9
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2018
ms.locfileid: "50287888"
---
# <a name="azure-notification-hubs-modules-for-nodejs"></a><span data-ttu-id="5b2df-103">Módulos de Azure Notification Hubs para Node.js</span><span class="sxs-lookup"><span data-stu-id="5b2df-103">Azure Notification Hubs modules for Node.js</span></span>

<span data-ttu-id="5b2df-104">Azure Notification Hubs proporciona un motor de inserción fácil de usar, multiplataforma y escalado horizontalmente.</span><span class="sxs-lookup"><span data-stu-id="5b2df-104">Azure Notification Hubs provide an easy-to-use, multi-platform, scaled-out push engine.</span></span> <span data-ttu-id="5b2df-105">Con una única llamada de API multiplataforma puede enviar fácilmente notificaciones push específicas y personalizadas a cualquier plataforma móvil desde cualquier back-end local o en la nube.</span><span class="sxs-lookup"><span data-stu-id="5b2df-105">With a single cross-platform API call, you can easily send targeted and personalized push notifications to any mobile platform from any cloud or on-premises backend.</span></span>

<span data-ttu-id="5b2df-106">Notification Hubs funciona muy bien tanto para escenarios empresariales como de consumidores.</span><span class="sxs-lookup"><span data-stu-id="5b2df-106">Notification Hubs works great for both enterprise and consumer scenarios.</span></span> <span data-ttu-id="5b2df-107">Estos son algunos ejemplos de para qué utilizan los clientes Notification Hubs:</span><span class="sxs-lookup"><span data-stu-id="5b2df-107">Here are a few examples customers use Notification Hubs for:</span></span>
- <span data-ttu-id="5b2df-108">Enviar notificaciones de noticias de última hora a millones de usuarios con baja latencia.</span><span class="sxs-lookup"><span data-stu-id="5b2df-108">Send breaking news notifications to millions with low latency.</span></span>
- <span data-ttu-id="5b2df-109">Enviar cupones basados en la ubicación a segmentos de usuarios interesados.</span><span class="sxs-lookup"><span data-stu-id="5b2df-109">Send location-based coupons to interested user segments.</span></span>
- <span data-ttu-id="5b2df-110">Enviar notificaciones relacionadas con eventos a usuarios o grupos para aplicaciones de medios, deportivas, de finanzas o de juegos.</span><span class="sxs-lookup"><span data-stu-id="5b2df-110">Send event-related notifications to users or groups for media/sports/finance/gaming applications.</span></span>
- <span data-ttu-id="5b2df-111">Insertar contenido promocional en aplicaciones para ponerse en contacto y comercializar con clientes.</span><span class="sxs-lookup"><span data-stu-id="5b2df-111">Push promotional contents to apps to engage and market to customers.</span></span>
- <span data-ttu-id="5b2df-112">Informar a los usuarios sobre eventos empresariales como, por ejemplo, nuevos mensajes o elementos de trabajo.</span><span class="sxs-lookup"><span data-stu-id="5b2df-112">Notify users of enterprise events like new messages and work items.</span></span>
- <span data-ttu-id="5b2df-113">Enviar códigos para Multi-Factor Authentication.</span><span class="sxs-lookup"><span data-stu-id="5b2df-113">Send codes for multi-factor authentication.</span></span>

## <a name="management-package"></a><span data-ttu-id="5b2df-114">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="5b2df-114">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="5b2df-115">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="5b2df-115">Install the npm module</span></span>

<span data-ttu-id="5b2df-116">Instale el módulo de Azure Notification Hubs.</span><span class="sxs-lookup"><span data-stu-id="5b2df-116">Install the Azure Notification Hubs module</span></span> 

```bash
npm install azure-arm-notificationhubs
```

### <a name="example"></a><span data-ttu-id="5b2df-117">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="5b2df-117">Example</span></span>

<span data-ttu-id="5b2df-118">En este ejemplo se enumeran todos los centros de notificaciones.</span><span class="sxs-lookup"><span data-stu-id="5b2df-118">This example lists all notification hubs.</span></span>

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

## <a name="samples"></a><span data-ttu-id="5b2df-119">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="5b2df-119">Samples</span></span>

* <span data-ttu-id="5b2df-120">[App Service Mobile completed quickstart for Node.js backend](https://azure.microsoft.com/resources/samples/app-service-mobile-nodejs-backend-quickstart/) (Inicio rápido a App Service Mobile completo para back-end de Node.js)</span><span class="sxs-lookup"><span data-stu-id="5b2df-120">[App Service Mobile completed quickstart for Node.js backend](https://azure.microsoft.com/resources/samples/app-service-mobile-nodejs-backend-quickstart/)</span></span>
* <span data-ttu-id="5b2df-121">[Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/) (Anomalías de vibración de tweets detectadas por los servicios Azure IoT en los datos de un Intel Edison que ejecuta Node.js)</span><span class="sxs-lookup"><span data-stu-id="5b2df-121">[Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)</span></span>

<span data-ttu-id="5b2df-122">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="5b2df-122">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
