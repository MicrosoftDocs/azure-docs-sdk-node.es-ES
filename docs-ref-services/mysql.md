---
title: "Módulos de Azure MySQL para Node.js"
description: "Referencia de los módulos de Azure MySQL para Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: mysql
ms.openlocfilehash: c78f61d0f76b6a40ad85ae0e7d9101349666eb0b
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2018
---
# <a name="azure-mysql-modules-for-nodejs"></a><span data-ttu-id="aea0c-103">Módulos de Azure MySQL para Node.js</span><span class="sxs-lookup"><span data-stu-id="aea0c-103">Azure MySQL modules for Node.js</span></span>

<span data-ttu-id="aea0c-104">La biblioteca de cliente recomendada para acceder a Azure Database for MySQL es la [biblioteca de conexión de Node.js para Azure Database for MySQL](https://github.com/sidorares/node-mysql2) de código abierto.</span><span class="sxs-lookup"><span data-stu-id="aea0c-104">The recommended client library for accessing Azure Database for MySQL is the open-source [Node.js connection library for Azure Database for MySQL](https://github.com/sidorares/node-mysql2).</span></span> 

<span data-ttu-id="aea0c-105">Más información acerca de [Azure Database for MySQL](https://docs.microsoft.com/azure/MySQL/)</span><span class="sxs-lookup"><span data-stu-id="aea0c-105">Learn more about [Azure Database for MySQL](https://docs.microsoft.com/azure/MySQL/)</span></span>

## <a name="client-package"></a><span data-ttu-id="aea0c-106">Paquete del cliente</span><span class="sxs-lookup"><span data-stu-id="aea0c-106">Client Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="aea0c-107">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="aea0c-107">Install the npm module</span></span>

<span data-ttu-id="aea0c-108">Utilice npm para instalar el módulo de cliente MySQL.</span><span class="sxs-lookup"><span data-stu-id="aea0c-108">Use npm to install the MySQL client module.</span></span>

```bash
npm install mysql2
```   

### <a name="example"></a><span data-ttu-id="aea0c-109">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="aea0c-109">Example</span></span>

<span data-ttu-id="aea0c-110">En este ejemplo se conecta a una base de datos MySQL y se realiza una consulta simple para recuperar todos los clientes.</span><span class="sxs-lookup"><span data-stu-id="aea0c-110">This example connects to a MySQL database and performs a simple query to retrieve all customers.</span></span>

```javascript
const mysql = require('mysql2');

const connection = mysql.createConnection({
  host: 'mysqldemo.mysql.database.azure.com',
  user: 'myadmin@mysqldemo',
  password: 'your_password',
  database: 'my_db',
  port: 3306,
  ssl: true
});

connection.connect();
const query = 'SELECT * FROM customers';
connection.query(query, (err, res) =>
  console.log(`We have ${res.length} customers`)
);

connection.end();
```

## <a name="samples"></a><span data-ttu-id="aea0c-111">Muestras</span><span class="sxs-lookup"><span data-stu-id="aea0c-111">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/mysql-samples.md)]

<span data-ttu-id="aea0c-112">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="aea0c-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>