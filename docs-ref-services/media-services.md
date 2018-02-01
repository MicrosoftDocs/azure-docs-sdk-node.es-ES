---
title: "Módulos de Azure Media Services para Node.js"
description: "Referencia de los módulos de Azure Media Services para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Media Services
ms.openlocfilehash: 77a6716d4ef0d566690325a86e85d66c5ac234d6
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2018
---
# <a name="azure-media-services-modules-for-nodejs"></a><span data-ttu-id="5c8df-103">Módulos de Azure Media Services para Node.js</span><span class="sxs-lookup"><span data-stu-id="5c8df-103">Azure Media Services modules for Node.js</span></span>

<span data-ttu-id="5c8df-104">Azure Media Services es una plataforma extensible basada en la nube que permite a los desarrolladores compilar aplicaciones escalables de administración y entrega de contenido multimedia.</span><span class="sxs-lookup"><span data-stu-id="5c8df-104">Azure Media Services is an extensible cloud-based platform that enables developers to build scalable media management and delivery applications.</span></span> <span data-ttu-id="5c8df-105">Media Services se basa en las API de REST, que permiten cargar, almacenar, codificar y empaquetar de forma segura contenido de audio o vídeo para la entrega bajo demanda y de streaming en vivo a varios clientes (por ejemplo, televisión, PC y dispositivos móviles).</span><span class="sxs-lookup"><span data-stu-id="5c8df-105">Media Services is based on REST APIs that enable you to securely upload, store, encode, and package video or audio content for both on-demand and live streaming delivery to various clients (for example, TV, PC, and mobile devices).</span></span>

<span data-ttu-id="5c8df-106">Con Azure Media Services, puede:</span><span class="sxs-lookup"><span data-stu-id="5c8df-106">With Azure Media Services, you can:</span></span>
- <span data-ttu-id="5c8df-107">Crear flujos de trabajo de un extremo a otro usando solamente Media Services.</span><span class="sxs-lookup"><span data-stu-id="5c8df-107">Build end-to-end workflows using entirely Media Services.</span></span> 
- <span data-ttu-id="5c8df-108">Utilizar componentes de terceros para algunas partes del flujo de trabajo.</span><span class="sxs-lookup"><span data-stu-id="5c8df-108">Use third-party components for some parts of your workflow.</span></span> <span data-ttu-id="5c8df-109">Por ejemplo, codifique mediante un codificador de terceros.</span><span class="sxs-lookup"><span data-stu-id="5c8df-109">For example, encode using a third-party encoder.</span></span> <span data-ttu-id="5c8df-110">A continuación, cargue, proteja, empaquete y entregue con Media Services.</span><span class="sxs-lookup"><span data-stu-id="5c8df-110">Then, upload, protect, package, deliver using Media Services.</span></span>
- <span data-ttu-id="5c8df-111">Transmitir el contenido en directo o entregar el contenido a petición.</span><span class="sxs-lookup"><span data-stu-id="5c8df-111">Stream your content live or deliver content on-demand.</span></span> <span data-ttu-id="5c8df-112">El tema también incluye vínculos a otros temas de interés.</span><span class="sxs-lookup"><span data-stu-id="5c8df-112">The topic also links to other relevant topics.</span></span>

## <a name="management-package"></a><span data-ttu-id="5c8df-113">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="5c8df-113">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="5c8df-114">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="5c8df-114">Install the npm module</span></span>

<span data-ttu-id="5c8df-115">Instale el módulo npm de Azure Media Services.</span><span class="sxs-lookup"><span data-stu-id="5c8df-115">Install the Azure media services npm module</span></span>

```bash
npm install azure-arm-mediaservices
```

### <a name="example"></a><span data-ttu-id="5c8df-116">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="5c8df-116">Example</span></span>

<span data-ttu-id="5c8df-117">En este ejemplo se enumeran todos los servicios de multimedia de un grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="5c8df-117">This example lists all media services for a resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const mediaServicesManagement = require('azure-arm-mediaservices');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
let mediaServicesClient;

msRestAzure.interactiveLogin().then(credentials => {
  mediaServicesClient = new mediaServicesManagement(credentials, subscriptionId);
  mediaServicesClient.mediaServiceOperations
    .listByResourceGroup(resourceGroup)
    .then(mediaServices => console.log('Retrieved media services: ', mediaServices));
});
```

## <a name="samples"></a><span data-ttu-id="5c8df-118">Muestras</span><span class="sxs-lookup"><span data-stu-id="5c8df-118">Samples</span></span>

<span data-ttu-id="5c8df-119">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="5c8df-119">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
