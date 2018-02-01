---
title: "Módulos de Azure Cognitive Services para Node.js"
description: "Referencia de los módulos de Azure Cognitive Services para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cognitive Services
ms.openlocfilehash: df6ea913ca69341fbbb730b75f547ce9c10bd45f
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2018
---
# <a name="azure-cognitive-services-modules-for-nodejs"></a><span data-ttu-id="119d5-103">Módulos de Azure Cognitive Services para Node.js</span><span class="sxs-lookup"><span data-stu-id="119d5-103">Azure Cognitive Services modules for Node.js</span></span>

<span data-ttu-id="119d5-104">Azure Cognitive Services es un conjunto de API, SDK y servicios disponibles para que los desarrolladores creen aplicaciones más inteligentes, interesantes y fáciles de encontrar.</span><span class="sxs-lookup"><span data-stu-id="119d5-104">Azure Cognitive Services is a set of APIs, SDKs, and services available to developers to make their applications more intelligent, engaging and discoverable.</span></span> <span data-ttu-id="119d5-105">Microsoft Cognitive Services se expande en una cartera en constante evolución de Microsoft de API de aprendizaje automático y permite a los desarrolladores agregar fácilmente características inteligentes (como detección de vídeo y emociones; reconocimiento facial, de voz y de visión; y comprensión del habla y del lenguaje) en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="119d5-105">Microsoft Cognitive Services expands on Microsoft’s evolving portfolio of machine learning APIs and enables developers to easily add intelligent features – such as emotion and video detection; facial, speech and vision recognition; and speech and language understanding – into their applications.</span></span> <span data-ttu-id="119d5-106">Nuestra visión está orientada a ofrecer experiencias informáticas más personales y a una productividad mejorada asistida por sistemas que cada vez más pueden ver, oír, hablar, comprender e incluso empezar a razonar.</span><span class="sxs-lookup"><span data-stu-id="119d5-106">Our vision is for more personal computing experiences and enhanced productivity aided by systems that increasingly can see, hear, speak, understand and even begin to reason.</span></span>

## <a name="management-package"></a><span data-ttu-id="119d5-107">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="119d5-107">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="119d5-108">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="119d5-108">Install the npm module</span></span>

<span data-ttu-id="119d5-109">Instale el módulo npm de Azure Cognitive Services.</span><span class="sxs-lookup"><span data-stu-id="119d5-109">Install the Azure Cognitive Services npm module</span></span>

```bash
npm install azure-arm-cognitiveservices
```

### <a name="example"></a><span data-ttu-id="119d5-110">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="119d5-110">Example</span></span>

<span data-ttu-id="119d5-111">En este ejemplo se enumeran todas las cuentas de Cognitive Services.</span><span class="sxs-lookup"><span data-stu-id="119d5-111">This example lists all cognitive service accounts.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const cognitiveServicesManagementClient = require('azure-arm-cognitiveservices');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const cognitiveServicesClient = new cognitiveServicesManagementClient(
      credentials,
      subscriptionId
    );
    return cognitiveServicesClient.cognitiveServicesAccounts.list();
  })
  .then(cognitiveServicesAccounts => {
    console.log('List of accounts:');
    console.dir(cognitiveServicesAccounts, { depth: null, colors: true });    
  });

```

## <a name="samples"></a><span data-ttu-id="119d5-112">Muestras</span><span class="sxs-lookup"><span data-stu-id="119d5-112">Samples</span></span>

<span data-ttu-id="119d5-113">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="119d5-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
