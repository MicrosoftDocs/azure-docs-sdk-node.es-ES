---
title: "Módulos de Azure Virtual Machines para Node.js"
description: "Referencia de los módulos de Azure Virtual Machines para Node.js"
keywords: "Azure, Node, SDK, API, máquina virtual, vm, nodejs, javascript"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 816714f5c286ee82f61502978c5d811e9f283432
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="azure-virtual-machine-modules-for-nodejs"></a>Módulos de Azure Virtual Machines para Node.js

## <a name="overview"></a>Información general

Defina, configure e implemente nuevas máquinas virtuales Windows y Linux y los conjunto de escalado de máquinas virtuales desde el código con los módulos de administración de Azure para Node.js. Los módulos le permiten iniciar y detener las máquinas virtuales existentes y asociar o desasociar discos en máquinas virtuales detenidas de su suscripción de Azure.

## <a name="management-package"></a>Paquete de administración

### <a name="install-the-npm-module"></a>Instalación del módulo npm

Instale el módulo npm de Azure Compute.

```bash
npm install azure-arm-compute
```   

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo iniciar sesión en Azure, crear un cliente de administración y enumerar todas las imágenes de máquina virtual para la ubicación especificada, el publicador, la oferta y la SKU.

```javascript
const msRestAzure = require('ms-rest-azure');
const computeManagementClient = require('azure-arm-compute');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new computeManagementClient(credentials, subscriptionId);

  client.virtualMachineImages
    .list(
        'westus',                   // location
        'MicrosoftWindowsServer',   // publisher name
        'WindowsServer',            // offer
        '2012-R2-Datacenter'        // sku
    )
    .then(result => console.log(result));
});
```

## <a name="samples"></a>Muestras

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
