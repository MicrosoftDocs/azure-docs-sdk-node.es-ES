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
# <a name="azure-postgresql-modules-for-nodejs"></a>Módulos de Azure PostgreSQL para Node.js

## <a name="overview"></a>Información general

La biblioteca de cliente recomendada para acceder a Azure Database for PostgreSQL es la [biblioteca de conexión de Node.js para Azure Database for PostgreSQL](https://www.npmjs.com/package/pg) de código abierto. Esta biblioteca es un cliente de PostgreSQL sin bloqueo para Node.js, que admite JavaScript puro y enlaces libpq nativo opcionales.

Más información acerca de [Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/)

## <a name="client-package"></a>Paquete del cliente

### <a name="install-the-npm-module"></a>Instalación del módulo npm

Utilice npm para instalar el módulo de cliente de PostgreSQL.

```bash
npm install pg
```   

### <a name="example"></a>Ejemplo

En este ejemplo se abre una conexión de cliente y ejecuta una consulta simple.

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

## <a name="samples"></a>Muestras

[!INCLUDE [node-postgresql-samples](../docs-ref-conceptual/includes/postgresql-samples.md)]

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
