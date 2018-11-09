---
title: Módulos de Azure Service Map para Node.js
description: Referencia de los módulos de Azure Service Map para Node.js
author: bwren
ms.author: bwren
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Map
ms.openlocfilehash: 494d948896d65dd67b06f455386f500346862beb
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/08/2018
ms.locfileid: "51190924"
---
# <a name="azure-service-map-modules-for-nodejs"></a>Módulos de Azure Service Map para Node.js

Mapa de servicio detecta automáticamente los componentes de la aplicación en sistemas Windows y Linux y asigna la comunicación entre servicios. Service Map muestra las conexiones entre servidores, procesos y puertos en cualquier arquitectura conectada TCP sin necesidad de ninguna configuración más allá de la instalación de un agente.

Más información acerca de [Azure Service Map](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map).

## <a name="management-package"></a>Paquete de administración

### <a name="install-the-npm-module"></a>Instalación del módulo npm

Instale el módulo npm de Azure Service Map.

```bash
npm install azure-arm-servicemap
```

### <a name="example"></a>Ejemplo

En este ejemplo se enumeran todos los mapas de servicio para el área de trabajo y el grupo de recursos especificados.

```javascript
const msRestAzure = require('ms-rest-azure');
const serviceMapManagement = require('azure-arm-servicemap');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const workspace = 'your-workspace';
let serviceMapClient;

msRestAzure.interactiveLogin().then(credentials => {
  serviceMapClient = new serviceMapManagement(credentials, subscriptionId);
  serviceMapClient.machineGroups
    .listByWorkspace(resourceGroup, workspace)
    .then(machineGroups => console.log('Retrieved machine groups: ', machineGroups));
});
```

## <a name="samples"></a>Ejemplos

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
