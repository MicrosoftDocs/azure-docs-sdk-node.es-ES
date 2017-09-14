---
title: "Módulos de Azure Logic Apps para Node.js"
description: "Referencia de los módulos de Azure Logic Apps para Node.js"
keywords: Azure,SDK,API,Logic Apps, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Logic Apps
ms.openlocfilehash: 70380dbf1fd199ba4909975b05ade72efaa4e0ec
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="azure-logic-apps-modules-for-nodejs"></a>Módulos de Azure Logic Apps para Node.js

## <a name="overview"></a>Información general
Logic Apps es una manera de simplificar e implementar integraciones escalables y flujos de trabajo en la nube. Proporciona un diseñador visual para modelar y automatizar el proceso en una serie de pasos denominada flujo de trabajo. Hay muchos conectores locales y en la nube para la integración rápida en servicios y protocolos. Una aplicación lógica comienza con un desencadenador (como "Cuando se agrega una cuenta a Dynamics CRM") y después la activación puede comenzar muchas combinaciones de acciones, conversiones y lógicas de condiciones.

Algunas ventajas de Logic Apps:
- Ahorro de tiempo al diseñar procesos complejos gracias a las herramientas de diseño que se entienden fácilmente
- Implementación inigualable de patrones y flujos de trabajo, que de lo contrario, serían difíciles de implementar en el código
- Introducción rápida desde plantillas
- Personalización de aplicaciones lógicas con API, código y acciones propios
- Conexión y sincronización de sistemas dispares locales y en la nube
- Generación del servidor de BizTalk, API Management, Azure Functions y Azure Service Bus compatible con integración de primera clase

Logic Apps es una iPaaS (plataforma de integración como servicio) totalmente administrada que permite a los desarrolladores despreocuparse del hospedaje, la escalabilidad, la disponibilidad y la administración. Logic Apps se escala automáticamente según las necesidades.

## <a name="management-package"></a>Paquete de administración

### <a name="install-the-npm-module"></a>Instalación del módulo npm

Instale el módulo de Azure Logic Apps para Node.js.

```bash
npm install azure-arm-logic
```

### <a name="example"></a>Ejemplo

```javascript
const msRestAzure = require('ms-rest-azure');
const LogicManagement = require('azure-arm-logic');

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const subscriptionId = 'subscription-id';
    const client = new LogicManagement(credentials, subscriptionId);
    return client.workflows.listBySubscription();
  })
  .then(workflows => console.log(workflows));
```

### <a name="samples"></a>Muestras

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
