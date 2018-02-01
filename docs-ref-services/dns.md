---
title: "Módulos de Azure DNS para Node.js"
description: "Referencia de los módulos de Azure DNS para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DNS
ms.openlocfilehash: c1ffacb3dd6b836303c5fcb2c18d7d68d2390ec7
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2018
---
# <a name="azure-dns-modules-for-nodejs"></a>Módulos de Azure DNS para Node.js

Utilice Azure DNS para hospedar sus dominios del Sistema de nombres de dominio (DNS) en Azure. Puede administrar sus registros de DNS usando las mismas credenciales, el mismo plan de facturación y el mismo contrato de soporte técnico que utiliza para los demás servicios de Azure. Integre sin problemas los servicios basados en Azure con las correspondientes actualizaciones de DNS y optimice el proceso de implementación de un extremo a otro.

## <a name="management-package"></a>Paquete de administración

### <a name="install-the-npm-module"></a>Instalación del módulo npm

Instale el módulo npm de Azure DNS.

```bash
npm install azure-arm-dns
```

### <a name="example"></a>Ejemplo

En este ejemplo se enumeran las zonas de administración de DNS.

```javascript
const msRestAzure = require('ms-rest-azure');
const DNSManagement = require('azure-arm-dns');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DNSManagement(credentials, subscriptionId);
    return client.zones.list();
  })
  .then(zones => console.dir(zones, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>Muestras

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
