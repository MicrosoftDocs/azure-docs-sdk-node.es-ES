---
title: "Módulos de Azure Redis Cache para Node.js"
description: "Referencia de los módulos de Azure Redis Cache para Node.js"
keywords: Azure,SDK,API,Redis Cache, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Redis Cache
ms.openlocfilehash: 8a10e522e39461697b740750b63fc82a6cc320ec
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="azure-redis-cache-modules-for-nodejs"></a>Módulos de Azure Redis Cache para Node.js

## <a name="overview"></a>Información general

Azure Redis Cache se basa en el popular proyecto Redis de código abierto. Ofrece acceso a una instancia de Redis segura y dedicada, administrada por Microsoft y accesible desde sus aplicaciones de Azure.

Redis es un avanzado almacén de pares clave-valor, donde las claves pueden contener estructuras de datos tales como cadenas, objetos hash, listas, conjuntos y conjuntos ordenados. Redis admite un conjunto de operaciones atómicas con estos tipos de datos.

Aprenda más sobre [Azure Redis Cache](https://docs.microsoft.com/azure/redis-cache/).

## <a name="client-package"></a>Paquete del cliente

### <a name="install-the-npm-module"></a>Instalación del módulo npm

Utilice npm para instalar el módulo Redis para Node.js.

```bash
npm install redis
```

### <a name="example"></a>Ejemplo

En este ejemplo se conecta a una instancia de Azure Redis Cache, almacena un par de clave/valor y, después, lee el valor almacenado por su clave.

```javascript
const redis = require('redis');

const client = redis.createClient(6380, '<name>.redis.cache.windows.net', {
  auth_pass: '<key>',
  tls: { servername: '<name>.redis.cache.windows.net' }
});

client.set('key1', 'value', (err, reply) => {
  console.log(reply);
});

client.get('key1', (err, reply) => {
  console.log(reply);
});
```

## <a name="management-package"></a>Paquete de administración

### <a name="install-the-npm-module"></a>Instalación del módulo npm

Utilice npm para instalar los módulos de Azure Redis Cache para Node.js.

```bash
npm install azure-arm-rediscache
```

### <a name="example"></a>Ejemplo

En este ejemplo se autentica en Azure y se enumeran todas las instancias de Redis Cache en un grupo de recursos especificado.

```javascript
const msRestAzure = require('ms-rest-azure');
const AzureMgmtRedisCache = require('azure-arm-rediscache');

msRestAzure.interactiveLogin().then(credentials => {
  const client = new AzureMgmtRedisCache(credentials, 'my-subscription-id');
  client.redis.listByResourceGroup('testResourceGroup').then(result => {
    console.log(result);
  });
});
```


## <a name="samples"></a>Muestras

* [Uso de Azure Redis Cache con Node.js](https://docs.microsoft.com/azure/redis-cache/cache-nodejs-get-started)

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
