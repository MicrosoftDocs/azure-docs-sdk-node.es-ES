---
title: Módulos de Azure Commerce para Node.js
description: Referencia de los módulos de Azure Commerce para Node.js
author: rloutlaw
ms.author: ROutlaw
manager: angrobew
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Commerce
ms.openlocfilehash: 33e290343f9188a1f78e53f6b8ed89594e2d9b46
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34260448"
---
# <a name="azure-commerce-modules-for-nodejs"></a>Módulos de Azure Commerce para Node.js

## <a name="overview"></a>Información general

Use las API de Azure Commerce para extraer datos de uso y de recursos e incorporarlos en las herramientas de análisis de datos de su preferencia. Las API de RateCard y de uso de recursos de Azure pueden ayudarlo a predecir y administrar los costos de forma precisa. Las API se implementan como proveedor de recursos, como parte de la familia de API expuesta por Azure Resource Manager.

## <a name="management-package"></a>Paquete de administración

### <a name="install-the-npm-module"></a>Instalación del módulo npm

Instale el módulo npm de Azure Commerce.

```bash
npm install azure-arm-commerce
```

### <a name="example"></a>Ejemplo

En este ejemplo se recuperan los datos de consumo de Azure estimados para el último mes.

```javascript
const msRestAzure = require('ms-rest-azure');
const CommerceManagement = require('azure-arm-commerce');

const endDate = new Date();
endDate.setUTCHours(0, 0, 0, 0);
const startDate = new Date();
startDate.setMonth(startDate.getMonth() - 1);
startDate.setUTCHours(0, 0, 0, 0);

const subscriptionId = 'your-subscription-id';
const usageOptions = {
  showDetails: true,
  granularity: 'Daily'
};

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new CommerceManagement(credentials, subscriptionId);
    return client.usageAggregates.list(startDate, endDate, usageOptions);
  })
  .then(usage => {
    console.dir(usage, { depth: null, colors: true });
  });
```

## <a name="samples"></a>Ejemplos

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
