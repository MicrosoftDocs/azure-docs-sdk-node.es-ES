---
title: "Módulos de Azure PostgreSQL para Node.js"
description: "Referencia de los módulos de Azure PostgreSQL para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: postgresql
ms.openlocfilehash: d8a2c7fe90746def7e50a7af3a0f470213eed197
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2018
---
# <a name="azure-postgresql-modules-for-nodejs"></a><span data-ttu-id="c7d65-103">Módulos de Azure PostgreSQL para Node.js</span><span class="sxs-lookup"><span data-stu-id="c7d65-103">Azure PostgreSQL modules for Node.js</span></span>

<span data-ttu-id="c7d65-104">La biblioteca de cliente recomendada para acceder a Azure Database for PostgreSQL es la [biblioteca de conexión de Node.js para Azure Database for PostgreSQL](https://www.npmjs.com/package/pg) de código abierto.</span><span class="sxs-lookup"><span data-stu-id="c7d65-104">The recommended client library for accessing Azure Database for PostgreSQL is the open-source [Node.js connection library for Azure Database for PostgreSQL](https://www.npmjs.com/package/pg).</span></span> <span data-ttu-id="c7d65-105">Esta biblioteca es un cliente de PostgreSQL sin bloqueo para Node.js, que admite JavaScript puro y enlaces libpq nativo opcionales.</span><span class="sxs-lookup"><span data-stu-id="c7d65-105">This library is a non-blocking PostgreSQL client for Node.js, supporting pure JavaScript and optional native libpq bindings.</span></span>

<span data-ttu-id="c7d65-106">Más información acerca de [Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/)</span><span class="sxs-lookup"><span data-stu-id="c7d65-106">Learn more about [Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/)</span></span>

## <a name="client-package"></a><span data-ttu-id="c7d65-107">Paquete del cliente</span><span class="sxs-lookup"><span data-stu-id="c7d65-107">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="c7d65-108">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="c7d65-108">Install the npm module</span></span>

<span data-ttu-id="c7d65-109">Utilice npm para instalar el módulo de cliente de PostgreSQL.</span><span class="sxs-lookup"><span data-stu-id="c7d65-109">Use npm to install the PostgreSQL client module.</span></span>

```bash
npm install pg
```   

### <a name="example"></a><span data-ttu-id="c7d65-110">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="c7d65-110">Example</span></span>

<span data-ttu-id="c7d65-111">En este ejemplo se abre una conexión de cliente y ejecuta una consulta simple.</span><span class="sxs-lookup"><span data-stu-id="c7d65-111">This example opens a client connection and executes a simple query.</span></span>

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

## <a name="samples"></a><span data-ttu-id="c7d65-112">Muestras</span><span class="sxs-lookup"><span data-stu-id="c7d65-112">Samples</span></span>

[!INCLUDE [node-postgresql-samples](../docs-ref-conceptual/includes/postgresql-samples.md)]

<span data-ttu-id="c7d65-113">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="c7d65-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
