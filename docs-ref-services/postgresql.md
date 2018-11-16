---
title: Módulos de Azure PostgreSQL para Node.js
description: Referencia de los módulos de Azure PostgreSQL para Node.js
author: rachel-msft
ms.author: raagyema
manager: sukamat
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: postgresql
ms.openlocfilehash: ed9373b767684e4893ca84de1030d062178b7ea4
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2018
ms.locfileid: "51465699"
---
# <a name="azure-postgresql-modules-for-nodejs"></a>Módulos de Azure PostgreSQL para Node.js

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

## <a name="samples"></a>Ejemplos

[!INCLUDE [node-postgresql-samples](../docs-ref-conceptual/includes/postgresql-samples.md)]

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
