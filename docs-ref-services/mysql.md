---
title: Módulos de Azure MySQL para Node.js
description: Referencia de los módulos de Azure MySQL para Node.js
author: ajlam
ms.author: andrela
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: mysql
ms.openlocfilehash: 557645774ecb0ea5e774f99d03251a303ad19660
ms.sourcegitcommit: da60ea91d4215d738b1e0df82066f0fc337ad85a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2018
ms.locfileid: "47358784"
---
# <a name="azure-mysql-modules-for-nodejs"></a>Módulos de Azure MySQL para Node.js

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

## <a name="samples"></a>Ejemplos

[!INCLUDE [node-mysql-samples](../docs-ref-conceptual/includes/mysql-samples.md)]

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
