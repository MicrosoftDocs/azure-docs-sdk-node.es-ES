---
title: Bibliotecas de Azure Event Grid para Node.js
description: Referencia de las bibliotecas de Azure Event Grid para Node.js
author: rloutlaw
ms.author: routlaw
manager: angerobe
ms.date: 05/03/2018
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: event-grid
ms.custom: devcenter
ms.openlocfilehash: 165845f0c94b4e6fd0f385f2262903e44845d09a
ms.sourcegitcommit: b4cf45cb23da56718b482cf7fc240c592e15206b
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="azure-event-grid-libraries-for-nodejs"></a><span data-ttu-id="610ea-103">Bibliotecas de Azure Event Grid para Node.js</span><span class="sxs-lookup"><span data-stu-id="610ea-103">Azure Event Grid libraries for Node.js</span></span>

<span data-ttu-id="610ea-104">Cree aplicaciones orientadas a eventos que escuchen y reaccionen a los eventos de los servicios de Azure y orígenes personalizados mediante un control de eventos simple basado en HTTP con Azure Event Grid.</span><span class="sxs-lookup"><span data-stu-id="610ea-104">Build event-driven applications that listen and react to events from Azure services and custom sources using simple HTTP-based event handling with Azure Event Grid.</span></span>

<span data-ttu-id="610ea-105">[Para más información](/azure/event-grid/overview) acerca de Azure Event Grid y empezar a trabajar con el [tutorial de eventos de Azure Blob Storage](/azure/storage/blobs/storage-blob-event-quickstart).</span><span class="sxs-lookup"><span data-stu-id="610ea-105">[Learn more](/azure/event-grid/overview) about Azure Event Grid and get started with the [Azure Blob storage event tutorial](/azure/storage/blobs/storage-blob-event-quickstart).</span></span> 

## <a name="publish-sdk"></a><span data-ttu-id="610ea-106">SDK de publicación</span><span class="sxs-lookup"><span data-stu-id="610ea-106">Publish SDK</span></span>

<span data-ttu-id="610ea-107">Puede crear eventos, autenticar y enviar a temas con el SDK de publicación de Azure Event Grid.</span><span class="sxs-lookup"><span data-stu-id="610ea-107">Create events, authenticate, and post to topics using the Azure Event Grid publish SDK.</span></span>

### <a name="installation"></a><span data-ttu-id="610ea-108">Instalación</span><span class="sxs-lookup"><span data-stu-id="610ea-108">Installation</span></span>

<span data-ttu-id="610ea-109">Agregue el módulo al proyecto con npm:</span><span class="sxs-lookup"><span data-stu-id="610ea-109">Add the module to your project with npm:</span></span>

```bash
npm install azure-eventgrid
```

### <a name="example-code"></a><span data-ttu-id="610ea-110">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="610ea-110">Example code</span></span>

<span data-ttu-id="610ea-111">El segmento de código siguiente, publica un evento ficticio a un tema de Event Grid.</span><span class="sxs-lookup"><span data-stu-id="610ea-111">The following code segment publishes a mock event to a Event Grid topic.</span></span> <span data-ttu-id="610ea-112">Puede recuperar el punto de conexión y las claves de acceso del tema desde Azure Portal o a través de la CLI de Azure:</span><span class="sxs-lookup"><span data-stu-id="610ea-112">You can retrieve the endpoint and topic access keys from the Azure Portal or through the Azure CLI:</span></span>

```azurecli-interactive
endpoint=$(az eventgrid topic show --name <topic_name> -g gridResourceGroup --query "endpoint" --output tsv)
key=$(az eventgrid topic key list --name <topic_name> -g gridResourceGroup --query "key1" --output tsv)
```

```javascript
var EventGridClient = require("azure-eventgrid");
var msRestAzure = require('ms-rest-azure');
var uuid = require('uuid').v4;

let topicCreds = new msRestAzure.TopicCredentials('your-topic-key');
let EGClient = new EventGridClient(topicCreds, 'your-subscription-id');
let topicHostName = 'your-topic-endpoint';
let events = [
   {
   id: uuid(),
   subject: 'TestSubject',
   dataVersion: '1.0',
   eventType: 'Microsoft.MockPublisher.TestEvent',
   data: {
        field1: 'value1',
        filed2: 'value2'
        }
    }
];
return EGClient.publishEvents(topicHostName, events).then((result) => {
   return Promise.resolve(console.log('Published events successfully.'));
 }).catch((err) => {
  console.log('An error ocurred');
  console.dir(err, {depth: null, colors: true});
});
```

<span data-ttu-id="610ea-113">Este ejemplo muestra cómo controlar un evento de Azure Storage:</span><span class="sxs-lookup"><span data-stu-id="610ea-113">This sample shows how to handle an event from Azure Storage:</span></span>

```javascript
var http = require('http');

module.exports = function (context, req) {
    context.log('JavaScript HTTP trigger function begun');
    var validationEventType = "Microsoft.EventGrid.SubscriptionValidationEvent";
    var storageBlobCreatedEvent = "Microsoft.Storage.BlobCreated";

    for (var events in req.body) {
        var body = req.body[events];
        // Deserialize the event data into the appropriate type based on event type  
        if (body.data && body.eventType == validationEventType) {
            context.log("Got SubscriptionValidation event data, validation code: " + body.data.validationCode + " topic: " + body.topic);

            // Do any additional validation (as required) and then return back the below response
            var code = body.data.validationCode;
            context.res = { status: 200, body: { "ValidationResponse": code } };
        }

        else if (body.data && body.eventType == storageBlobCreatedEvent) {
            var blobCreatedEventData = body.data;
            context.log("Relaying received blob created event payload:" + JSON.stringify(blobCreatedEventData));
        }
    }
    context.done();
};
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="610ea-114">Explorar las API de cliente</span><span class="sxs-lookup"><span data-stu-id="610ea-114">Explore the client APIs</span></span>](/javascript/api/overview/azure/eventgrid/client)

## <a name="management-sdk"></a><span data-ttu-id="610ea-115">SDK de administración</span><span class="sxs-lookup"><span data-stu-id="610ea-115">Management SDK</span></span>

<span data-ttu-id="610ea-116">El SDK de administración permite crear, actualizar y eliminar instancias, temas y suscripciones de Event Grid.</span><span class="sxs-lookup"><span data-stu-id="610ea-116">Create, update, or delete Event Grid instances, topics, and subscriptions with the management SDK.</span></span>

### <a name="installation"></a><span data-ttu-id="610ea-117">Instalación</span><span class="sxs-lookup"><span data-stu-id="610ea-117">Installation</span></span>

```
npm install azure-arm-eventgrid
```

### <a name="example-code"></a><span data-ttu-id="610ea-118">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="610ea-118">Example code</span></span>

<span data-ttu-id="610ea-119">El siguiente código crea el tema de Event Grid `topic1` y devuelve las claves de acceso asociadas al tema recién creado.</span><span class="sxs-lookup"><span data-stu-id="610ea-119">The following code creates an Event Grid topic `topic1` and returns the access keys associated with the newly created topic.</span></span>

```javascript
var msRestAzure = require('ms-rest-azure');
var EventGridManagementClient = require("azure-arm-eventgrid");

msRestAzure.interactiveLogin(function(err, credentials) {
    // Created the management client
    let EGMClient = new EventGridManagementClient(credentials, 'your-subscription-id');
    let topicResponse;
    // created an enventgrid topic
    return EGMClient.topics.createOrUpdate('resourceGroup', 'topic1', { location: 'westus' }).then((topicResponse) => {
        return Promise.resolve(console.log('Created topic ', topicResponse));
    }).then(() => {
        // listed the access keys
        return EGMClient.topics.listSharedAccessKeys('resourceGroup', 'topic1')}
)};
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="610ea-120">Explorar las API de administración</span><span class="sxs-lookup"><span data-stu-id="610ea-120">Explore the management APIs</span></span>](/javascript/api/overview/azure/eventgrid/management)

## <a name="learn-more"></a><span data-ttu-id="610ea-121">Más información</span><span class="sxs-lookup"><span data-stu-id="610ea-121">Learn more</span></span>

- [<span data-ttu-id="610ea-122">Recepción de eventos mediante el SDK de Event Grid</span><span class="sxs-lookup"><span data-stu-id="610ea-122">Receive events using the Event Grid SDK</span></span>](/azure/event-grid/receive-events)