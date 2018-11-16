---
title: Módulos de Azure Cosmos DB para Node.js
description: Referencia de los módulos de Azure Cosmos DB para Node.js
author: SnehaGunda
ms.author: sngun
manager: kfile
ms.date: 03/20/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cosmos DB
ms.openlocfilehash: 2e2813bb3b213de4066b2a3bc971586667a83f68
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2018
ms.locfileid: "51439439"
---
# <a name="azure-cosmos-db-modules-for-nodejs"></a>Módulos de Azure Cosmos DB para Node.js

Azure Cosmos DB es la base de datos multimodelo de distribución global de Microsoft. Azure Cosmos DB permite escalar de forma elástica e individual el rendimiento y el almacenamiento en cualquiera de las regiones geográficas de Azure. Ofrece garantía de rendimiento, latencia, disponibilidad y coherencia con acuerdos de nivel de servicio (SLA) integrales, algo que no ofrece ningún otro servicio de base de datos.

Azure Cosmos DB contiene un motor de base de datos con escritura optimizada, regulado por recursos, independiente del esquema que admite varios modelos de datos de forma nativa: de valores clave, documentos, gráficos y columnas. También admite muchas API para acceder a datos, como MongoDB, SQL, Gremlin/Graph, Azure Tables y Cassandra (versión preliminar), de forma extensible.

## <a name="management-package"></a>Paquete de administración

### <a name="install-the-npm-module"></a>Instalación del módulo npm 

Instale el módulo npm de Azure Cosmos DB.

```bash
npm install azure-arm-documentdb
```

### <a name="example"></a>Ejemplo

En este ejemplo, se enumeran todas las cuentas de Azure Cosmos DB.

```javascript
const msRestAzure = require('ms-rest-azure');
const documentDBManagementClient = require('azure-arm-documentdb');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const documentDbClient = new documentDBManagementClient(credentials, subscriptionId);
  documentDbClient.databaseAccounts
    .list()
    .then(databaseAccounts => console.log('Retrieved database accounts: ', databaseAccounts));
});
```

## <a name="samples"></a>Ejemplos

* [Desarrollo de una aplicación Node.js con Azure Cosmos DB](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/)
* [Desarrollo de una aplicación Node.js con Azure Cosmos DB - Gremlin](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/)

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
