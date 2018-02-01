---
title: "Módulos de Azure Redis Cache para Node.js"
description: "Referencia de los módulos de Azure Redis Cache para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Redis Cache
ms.openlocfilehash: 5d3a410fefcf6840181701763346fbfe08fe023b
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2018
---
# <a name="azure-redis-cache-modules-for-nodejs"></a><span data-ttu-id="b9067-103">Módulos de Azure Redis Cache para Node.js</span><span class="sxs-lookup"><span data-stu-id="b9067-103">Azure Redis Cache modules for Node.js</span></span>

<span data-ttu-id="b9067-104">Azure Redis Cache se basa en el popular proyecto Redis de código abierto.</span><span class="sxs-lookup"><span data-stu-id="b9067-104">Azure Redis Cache is based on the popular open source Redis project.</span></span> <span data-ttu-id="b9067-105">Ofrece acceso a una instancia de Redis segura y dedicada, administrada por Microsoft y accesible desde sus aplicaciones de Azure.</span><span class="sxs-lookup"><span data-stu-id="b9067-105">It gives you access to a secure, dedicated Redis instance, managed by Microsoft and accessible from your Azure apps.</span></span>

<span data-ttu-id="b9067-106">Redis es un almacén de pares clave-valor avanzado, donde las claves pueden contener estructuras de datos tales como cadenas, algoritmos hash, listas, conjuntos y conjuntos ordenados.</span><span class="sxs-lookup"><span data-stu-id="b9067-106">Redis is an advanced key-value store, where keys can contain data structures such as strings, hashes, lists, sets, and sorted sets.</span></span> <span data-ttu-id="b9067-107">Redis admite un conjunto de operaciones atómicas con estos tipos de datos.</span><span class="sxs-lookup"><span data-stu-id="b9067-107">Redis supports a set of atomic operations on these data types.</span></span>

<span data-ttu-id="b9067-108">Obtenga más información acerca de [Azure Redis Cache](https://docs.microsoft.com/azure/redis-cache/).</span><span class="sxs-lookup"><span data-stu-id="b9067-108">Learn more about [Azure Redis Cache](https://docs.microsoft.com/azure/redis-cache/).</span></span>

## <a name="client-package"></a><span data-ttu-id="b9067-109">Paquete del cliente</span><span class="sxs-lookup"><span data-stu-id="b9067-109">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b9067-110">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="b9067-110">Install the npm module</span></span>

<span data-ttu-id="b9067-111">Utilice npm para instalar el módulo Redis para Node.js.</span><span class="sxs-lookup"><span data-stu-id="b9067-111">Use npm to install the Redis module for Node.js</span></span>

```bash
npm install redis
```

### <a name="example"></a><span data-ttu-id="b9067-112">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b9067-112">Example</span></span>

<span data-ttu-id="b9067-113">En este ejemplo se conecta a una instancia de Azure Redis Cache, almacena un par de clave/valor y, después, lee el valor almacenado por su clave.</span><span class="sxs-lookup"><span data-stu-id="b9067-113">This example connects to an Azure Redis Cache instance, stores a key/value pair and then reads the stored value by its key.</span></span>

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

## <a name="management-package"></a><span data-ttu-id="b9067-114">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="b9067-114">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b9067-115">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="b9067-115">Install the npm module</span></span>

<span data-ttu-id="b9067-116">Utilice npm para instalar los módulos de Azure Redis Cache para Node.js.</span><span class="sxs-lookup"><span data-stu-id="b9067-116">Use npm to install the Azure Redis Cache modules for Node.js</span></span>

```bash
npm install azure-arm-rediscache
```

### <a name="example"></a><span data-ttu-id="b9067-117">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b9067-117">Example</span></span>

<span data-ttu-id="b9067-118">En este ejemplo se autentica en Azure y se enumeran todas las instancias de Redis Cache en un grupo de recursos especificado.</span><span class="sxs-lookup"><span data-stu-id="b9067-118">This example authenticates to Azure and lists all Redis Cache instances in a specified resource group.</span></span>

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


## <a name="samples"></a><span data-ttu-id="b9067-119">Muestras</span><span class="sxs-lookup"><span data-stu-id="b9067-119">Samples</span></span>

* [<span data-ttu-id="b9067-120">Uso de Azure Redis Cache con Node.js</span><span class="sxs-lookup"><span data-stu-id="b9067-120">How to use Azure Redis Cache with Node.js</span></span>](https://docs.microsoft.com/azure/redis-cache/cache-nodejs-get-started)

<span data-ttu-id="b9067-121">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="b9067-121">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
