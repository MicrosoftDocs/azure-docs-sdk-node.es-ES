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
# <a name="azure-sql-modules-for-nodejs"></a><span data-ttu-id="2f32f-103">Módulos de Azure SQL para Node.js</span><span class="sxs-lookup"><span data-stu-id="2f32f-103">Azure SQL modules for Node.js</span></span>

<span data-ttu-id="2f32f-104">Trabaje con datos almacenados en [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) en Node.js.</span><span class="sxs-lookup"><span data-stu-id="2f32f-104">Work with data stored in [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) from Node.js.</span></span>
<span data-ttu-id="2f32f-105">La biblioteca de administración proporciona una interfaz para que sea fácil administrar bases de datos Microsoft Azure SQL Database.</span><span class="sxs-lookup"><span data-stu-id="2f32f-105">The management library provides an interface to make it easy to manage Microsoft Azure SQL databases.</span></span>

## <a name="client-package"></a><span data-ttu-id="2f32f-106">Paquete del cliente</span><span class="sxs-lookup"><span data-stu-id="2f32f-106">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="2f32f-107">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="2f32f-107">Install the npm module</span></span>

<span data-ttu-id="2f32f-108">Instale el módulo npm de cliente de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2f32f-108">Install the SQL Server client npm module</span></span>

```bash
npm install tedious
```

### <a name="example"></a><span data-ttu-id="2f32f-109">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="2f32f-109">Example</span></span>

<span data-ttu-id="2f32f-110">En este ejemplo se va a conectar a una base de datos de SQL Server y va a realizar una consulta simple.</span><span class="sxs-lookup"><span data-stu-id="2f32f-110">This example connects to a SQL Server database and perform a simple query.</span></span>

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

## <a name="management-package"></a><span data-ttu-id="2f32f-111">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="2f32f-111">Management package</span></span>

### <a name="install-npm-modules"></a><span data-ttu-id="2f32f-112">Instalación de módulos npm</span><span class="sxs-lookup"><span data-stu-id="2f32f-112">Install npm modules</span></span>

<span data-ttu-id="2f32f-113">Instale el módulo npm de administración de Azure SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2f32f-113">Install the Azure SQL Server management npm module</span></span>

```
npm install azure-arm-sql
```   

### <a name="example"></a><span data-ttu-id="2f32f-114">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="2f32f-114">Example</span></span>

<span data-ttu-id="2f32f-115">Autentíquese, cree un cliente y muestre todos los servidores.</span><span class="sxs-lookup"><span data-stu-id="2f32f-115">Authenticate, create a client, and list all servers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="2f32f-116">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="2f32f-116">Samples</span></span>

[!INCLUDE [node-sql-samples](../docs-ref-conceptual/includes/sql-samples.md)]

<span data-ttu-id="2f32f-117">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="2f32f-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
