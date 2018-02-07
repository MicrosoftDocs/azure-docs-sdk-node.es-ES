---
title: "Módulos de Azure Virtual Machines para Node.js"
description: "Guía de referencia de los módulos de Azure Virtual Machines para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 608a915499d7c32c2c8b04464f716fa4fd17243d
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2018
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
        'Canonical',   // publisher name
        'UbuntuServer',            // offer
        '16.04-LTS'        // sku
    )
    .then(result => console.log(result));
});
```

## <a name="samples"></a>Muestras

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
