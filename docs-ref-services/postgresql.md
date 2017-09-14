---
title: "Módulos de Azure PostgreSQL para Node.js"
description: "Referencia de los módulos de Azure PostgreSQL para Node.js"
keywords: Azure, Node, SDK, API, nodejs, javascript, base de datos, PostgreSQL
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: postgresql
ms.openlocfilehash: a5130c96b3ae922358b6898c15510282fbaa97f0
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="azure-postgresql-modules-for-nodejs"></a><span data-ttu-id="f2399-104">Módulos de Azure PostgreSQL para Node.js</span><span class="sxs-lookup"><span data-stu-id="f2399-104">Azure PostgreSQL modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="f2399-105">Información general</span><span class="sxs-lookup"><span data-stu-id="f2399-105">Overview</span></span>

<span data-ttu-id="f2399-106">La biblioteca de cliente recomendada para acceder a Azure Database for PostgreSQL es la [biblioteca de conexión de Node.js para Azure Database for PostgreSQL](https://www.npmjs.com/package/pg) de código abierto.</span><span class="sxs-lookup"><span data-stu-id="f2399-106">The recommended client library for accessing Azure Database for PostgreSQL is the open-source [Node.js connection library for Azure Database for PostgreSQL](https://www.npmjs.com/package/pg).</span></span> <span data-ttu-id="f2399-107">Esta biblioteca es un cliente de PostgreSQL sin bloqueo para Node.js, que admite JavaScript puro y enlaces libpq nativo opcionales.</span><span class="sxs-lookup"><span data-stu-id="f2399-107">This library is a non-blocking PostgreSQL client for Node.js, supporting pure JavaScript and optional native libpq bindings.</span></span>

<span data-ttu-id="f2399-108">Más información acerca de [Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/)</span><span class="sxs-lookup"><span data-stu-id="f2399-108">Learn more about [Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/)</span></span>

## <a name="client-package"></a><span data-ttu-id="f2399-109">Paquete del cliente</span><span class="sxs-lookup"><span data-stu-id="f2399-109">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="f2399-110">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="f2399-110">Install the npm module</span></span>

<span data-ttu-id="f2399-111">Utilice npm para instalar el módulo de cliente de PostgreSQL.</span><span class="sxs-lookup"><span data-stu-id="f2399-111">Use npm to install the PostgreSQL client module.</span></span>

```bash
npm install pg
```   

### <a name="example"></a><span data-ttu-id="f2399-112">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="f2399-112">Example</span></span>

<span data-ttu-id="f2399-113">En este ejemplo se abre una conexión de cliente y ejecuta una consulta simple.</span><span class="sxs-lookup"><span data-stu-id="f2399-113">This example opens a client connection and executes a simple query.</span></span>

```javascript
const pg = require('pg');

const connectionString =
  'postgres://{username}@{server-name}:{password}@{server-name}.postgres.database.azure.com:5432/{database-name}?ssl=true';

const client = new pg.Client(connectionString);
client.connect();

const query = 'SELECT * FROM {table-name}';
client.query(query, (err, res) => {
  console.log(res);
});
```

## <a name="samples"></a><span data-ttu-id="f2399-114">Muestras</span><span class="sxs-lookup"><span data-stu-id="f2399-114">Samples</span></span>

[!INCLUDE [node-postgresql-samples](../docs-ref-conceptual/includes/postgresql-samples.md)]

<span data-ttu-id="f2399-115">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="f2399-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
