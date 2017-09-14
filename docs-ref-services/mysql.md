---
title: "Módulos de Azure MySQL para Node.js"
description: "Referencia de los módulos de Azure MySQL para Node.js"
keywords: Azure, Node, SDK, API, nodejs, javascript, base de datos, MySQL
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: mysql
ms.openlocfilehash: 3efc0fcccb7cb01711ad1ce98e9ff9a2d87b77fe
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="azure-mysql-modules-for-nodejs"></a>Módulos de Azure MySQL para Node.js

## <a name="overview"></a>Información general

La biblioteca de cliente recomendada para acceder a Azure Database for MySQL es la [biblioteca de conexión de Node.js para Azure Database for MySQL](https://github.com/sidorares/node-mysql2) de código abierto. 

Más información acerca de [Azure Database for MySQL](https://docs.microsoft.com/azure/MySQL/)

## <a name="client-package"></a>Paquete del cliente

### <a name="install-the-npm-module"></a>Instalación del módulo npm

Utilice npm para instalar el módulo de cliente MySQL.

```bash
npm install mysql2
```   

### <a name="example"></a>Ejemplo

En este ejemplo se conecta a una base de datos MySQL y se realiza una consulta simple para recuperar todos los clientes.

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

## <a name="samples"></a>Muestras

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/mysql-samples.md)]

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
