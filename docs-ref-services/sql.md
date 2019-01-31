---
title: Módulos de Azure SQL para Node.js
description: Referencia de los módulos de Azure SQL para Node.js
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: sql-database
ms.subservice: development
ms.openlocfilehash: 00ba5984b5f8aef85570c54f23efefd1d741ca57
ms.sourcegitcommit: 0e294f7c4dcdfae9df18ff3e82b6563680ef2519
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55046435"
---
# <a name="azure-sql-modules-for-nodejs"></a>Módulos de Azure SQL para Node.js

Trabaje con datos almacenados en [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) en Node.js.
La biblioteca de administración proporciona una interfaz para que sea fácil administrar bases de datos Microsoft Azure SQL Database.

## <a name="client-package"></a>Paquete del cliente

### <a name="install-the-npm-module"></a>Instalación del módulo npm

Instale el módulo npm de cliente de SQL Server.

```bash
npm install tedious
```

### <a name="example"></a>Ejemplo

En este ejemplo se va a conectar a una base de datos de SQL Server y va a realizar una consulta simple.

```javascript
const Connection = require('tedious').Connection;
const Request = require('tedious').Request;

const config = {
  userName: 'your-username',
  password: 'your-password',
  server: 'path-to-server',
  options: {
    database: 'database-name',
    encrypt: true
  }
};

const connection = new Connection(config);
connection.on('connect', err => {
  err ? console.log(err) : executeStatement();
});

const query = 'SELECT * from TableName';
const executeStatement = () => {
  const request = new Request(query, (err, rowCount) => {
    err ? console.log(err) : console.log(rowCount);
  });

  request.on('row', columns => {
    columns.forEach(column => console.log(column.value));
  });

  connection.execSql(request);
};
```

## <a name="management-package"></a>Paquete de administración

### <a name="install-npm-modules"></a>Instalación de módulos npm

Instale el módulo npm de administración de Azure SQL Server.

```
npm install azure-arm-sql
```   

### <a name="example"></a>Ejemplo

Autentíquese, cree un cliente y muestre todos los servidores.

```javascript
const msRestAzure = require('ms-rest-azure');
const SQLManagement = require('azure-arm-sql');

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new SQLManagement(credentials, 'your-subscription-id');
    return client.servers.list();
  })
  .then(servers => console.dir(servers, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>Ejemplos

[!INCLUDE [node-sql-samples](../docs-ref-conceptual/includes/sql-samples.md)]

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
