---
title: Módulos de Azure Traffic Manager para Node.js
description: Referencia de los módulos de Azure Traffic Manager para Node.js
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Traffic Manager
ms.openlocfilehash: 2a32eed460c6076011fdcf31d77200502ef61a3d
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "49675760"
---
# <a name="azure-traffic-manager-modules-for-nodejs"></a>Módulos de Azure Traffic Manager para Node.js

## <a name="overview"></a>Información general

Microsoft Azure Traffic Manager permite controlar la distribución del tráfico de los usuarios para puntos de conexión de servicio en distintos centros de datos. Entre los puntos de conexión de servicio compatibles con Traffic Manager, se incluyen máquinas virtuales de Azure, Web Apps y servicios en la nube. También puede utilizar el Administrador de tráfico con puntos de conexión externos, que no forman parte de Azure.

Más información acerca de [Azure Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).

## <a name="management-package"></a>Paquete de administración

### <a name="install-the-npm-module"></a>Instalación del módulo npm

Instale el módulo npm de Azure Traffic Manager.

```bash
npm install azure-arm-trafficmanager
```

### <a name="example"></a>Ejemplo

En este ejemplo se enumeran todas las instancias de Traffic Manager para un grupo de recursos determinado.

```javascript
const msRestAzure = require('ms-rest-azure');
const trafficManager = require('azure-arm-trafficmanager');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new trafficManager(credentials, subscriptionId);
  const resourceGroupName = 'resource-group-name';
  client.profiles.listAllInResourceGroup(resourceGroupName).then(profiles => {
    profiles.map(profile => {
      console.log(`found profile : ${profile.name}`);
    });
  });
});
```

## <a name="samples"></a>Ejemplos

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
