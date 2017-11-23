---
title: "Módulos de Azure SQL para Node.js"
description: "Referencia de los módulos de Azure SQL para Node.js"
keywords: Azure, Node, SDK, API, nodejs, javascript, sql
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: sql-database
ms.openlocfilehash: 65ee90b4e6ca248b9d19a3685163211ca547cad4
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="azure-sql-modules-for-nodejs"></a><span data-ttu-id="f0c91-104">Módulos de Azure SQL para Node.js</span><span class="sxs-lookup"><span data-stu-id="f0c91-104">Azure SQL modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="f0c91-105">Información general</span><span class="sxs-lookup"><span data-stu-id="f0c91-105">Overview</span></span>

<span data-ttu-id="f0c91-106">Trabaje con datos almacenados en [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) en Node.js.</span><span class="sxs-lookup"><span data-stu-id="f0c91-106">Work with data stored in [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) from Node.js.</span></span>
<span data-ttu-id="f0c91-107">La biblioteca de administración proporciona una interfaz para que sea fácil administrar bases de datos Microsoft Azure SQL Database.</span><span class="sxs-lookup"><span data-stu-id="f0c91-107">The management library provides an interface to make it easy to manage Microsoft Azure SQL databases.</span></span>

## <a name="client-package"></a><span data-ttu-id="f0c91-108">Paquete del cliente</span><span class="sxs-lookup"><span data-stu-id="f0c91-108">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="f0c91-109">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="f0c91-109">Install the npm module</span></span>

<span data-ttu-id="f0c91-110">Instale el módulo npm de cliente de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f0c91-110">Install the SQL Server client npm module</span></span>

```bash
npm install tedious
```

### <a name="example"></a><span data-ttu-id="f0c91-111">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="f0c91-111">Example</span></span>

<span data-ttu-id="f0c91-112">En este ejemplo se va a conectar a una base de datos de SQL Server y va a realizar una consulta simple.</span><span class="sxs-lookup"><span data-stu-id="f0c91-112">This example connects to a SQL Server database and perform a simple query.</span></span>

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

## <a name="management-package"></a><span data-ttu-id="f0c91-113">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="f0c91-113">Management package</span></span>

### <a name="install-npm-modules"></a><span data-ttu-id="f0c91-114">Instalación de módulos npm</span><span class="sxs-lookup"><span data-stu-id="f0c91-114">Install npm modules</span></span>

<span data-ttu-id="f0c91-115">Instale el módulo npm de administración de Azure SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f0c91-115">Install the Azure SQL Server management npm module</span></span>

```
npm install azure-arm-sql
```   

### <a name="example"></a><span data-ttu-id="f0c91-116">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="f0c91-116">Example</span></span>

<span data-ttu-id="f0c91-117">Autentíquese, cree un cliente y muestre todos los servidores.</span><span class="sxs-lookup"><span data-stu-id="f0c91-117">Authenticate, create a client, and list all servers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="f0c91-118">Muestras</span><span class="sxs-lookup"><span data-stu-id="f0c91-118">Samples</span></span>

[!INCLUDE [node-sql-samples](../docs-ref-conceptual/includes/sql-samples.md)]

<span data-ttu-id="f0c91-119">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="f0c91-119">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
