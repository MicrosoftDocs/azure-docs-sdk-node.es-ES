---
title: Módulos de Azure DevTest Labs para Node.js
description: Referencia de los módulos de Azure DevTest Labs para Node.js
author: craigcaseyMSFT
ms.author: v-craic
manager: v-laurab
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DevTest Labs
ms.openlocfilehash: 5bd010d26ca11f9909191f25128b9bdb89811fd5
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="azure-devtest-labs-modules-for-nodejs"></a>Módulos de Azure DevTest Labs para Node.js

Azure DevTest Labs es un servicio que ayuda a los desarrolladores y evaluadores a crear rápidamente entornos de Azure al tiempo que se optimizan los recursos y se controlan los costos. Puede probar la versión más reciente de la aplicación aprovisionando rápidamente entornos de Windows y Linux mediante plantillas y artefactos reutilizables. Integre fácilmente la canalización de la implementación con DevTest Labs para aprovisionar entornos a petición. Escale verticalmente las pruebas de carga mediante el aprovisionamiento de varios agentes de prueba y cree entornos previamente aprovisionados con fines de capacitación y demostración.

## <a name="management-package"></a>Paquete de administración

### <a name="install-the-npm-module"></a>Instalación del módulo npm

Instale el módulo npm Azure DevTest Labs.

```bash
npm install azure-arm-devtestlabs
```

### <a name="example"></a>Ejemplo

En este ejemplo se obtienen e imprimen los detalles de un laboratorio.

```javascript
const msRestAzure = require('ms-rest-azure');
const DevTestLabsClient = require('azure-arm-devtestlabs');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';
const labName = 'your-lab-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DevTestLabsClient(credentials, subscriptionId);
    return client.labOperations.getResource(resourceGroupName, labName);
  })
  .then(lab => {
    console.log('Details of lab:');
    console.dir(lab, { depth: null, colors: true });
  });


```

## <a name="samples"></a>Ejemplos

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
