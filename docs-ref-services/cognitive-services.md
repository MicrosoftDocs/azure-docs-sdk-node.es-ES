---
title: "Módulos de Azure Cognitive Services para Node.js"
description: "Referencia de los módulos de Azure Cognitive Services para Node.js"
keywords: Azure,SDK,API,Cognitive Services, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cognitive Services
ms.openlocfilehash: fba98930fccaf4fa40dd1d0224031276f5fb7f84
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="azure-cognitive-services-modules-for-nodejs"></a>Módulos de Azure Cognitive Services para Node.js

## <a name="overview"></a>Información general

Azure Cognitive Services es un conjunto de API, SDK y servicios disponibles para que los desarrolladores creen aplicaciones más inteligentes, interesantes y fáciles de encontrar. Microsoft Cognitive Services se expande en una cartera en constante evolución de Microsoft de API de aprendizaje automático y permite a los desarrolladores agregar fácilmente características inteligentes (como detección de vídeo y emociones; reconocimiento facial, de voz y de visión; y comprensión del habla y del lenguaje) en sus aplicaciones. Nuestra visión está orientada a ofrecer experiencias informáticas más personales y a una productividad mejorada asistida por sistemas que cada vez más pueden ver, oír, hablar, comprender e incluso empezar a razonar.

## <a name="management-package"></a>Paquete de administración

### <a name="install-the-npm-module"></a>Instalación del módulo npm

Instale el módulo npm de Azure Cognitive Services.

```bash
npm install azure-arm-cognitiveservices
```

### <a name="example"></a>Ejemplo

En este ejemplo se enumeran todas las cuentas de Cognitive Services.

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

## <a name="samples"></a>Muestras

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
