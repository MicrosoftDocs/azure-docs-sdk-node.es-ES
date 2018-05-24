---
title: Módulos de Azure Virtual Network para Node.js
description: Referencia de los módulos de Azure Virtual Network para Node.js
author: jimdial
ms.author: jdial
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Virtual Network
ms.openlocfilehash: 456839dbecb9ddd1ad0d4b3f8aa7570a04c100b1
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="azure-virtual-network-modules-for-nodejs"></a>Módulos de Azure Virtual Network para Node.js

## <a name="overview"></a>Información general

El servicio de Azure Virtual Network le permite conectar de forma segura los recursos de Azure con redes virtuales. Una red virtual es una representación de su propia red en la nube. Una red virtual es un aislamiento lógico de la nube de Azure dedicada a su suscripción. También puede conectar redes virtuales a la red local.

Más información acerca de [Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).

## <a name="management-package"></a>Paquete de administración

### <a name="install-the-npm-module"></a>Instalación del módulo npm

Instale el módulo npm de Azure Virtual Network.

```bash
npm install azure-arm-network
```

### <a name="example"></a>Ejemplo

En este ejemplo se obtiene y se imprime la lista de redes virtuales.

```javascript
const msRestAzure = require('ms-rest-azure');
const NetworkManagementClient = require('azure-arm-network');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new NetworkManagementClient(credentials, subscriptionId);
    return client.virtualNetworks.list(resourceGroup);
  })
  .then(networkList => {
    console.log('List of virtual networks:');
    console.dir(networkList, { depth: null, colors: true });
  });

```

## <a name="samples"></a>Ejemplos

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
