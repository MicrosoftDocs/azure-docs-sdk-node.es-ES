---
title: "Módulos de Azure Cosmos DB para Node.js"
description: "Referencia de los módulos de Azure Cosmos DB para Node.js"
keywords: Azure,SDK,API,Cosmos DB, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cosmos DB
ms.openlocfilehash: 1f545f89b5304b611dbe1ed9cb86052c112f13c1
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="azure-cosmos-db-modules-for-nodejs"></a>Módulos de Azure Cosmos DB para Node.js

## <a name="overview"></a>Información general

Azure Cosmos DB es la base de datos multimodelo de distribución global de Microsoft. Azure Cosmos DB permite escalar de forma elástica e individual el rendimiento y el almacenamiento en cualquiera de las regiones geográficas de Azure. Ofrece garantía de rendimiento, latencia, disponibilidad y coherencia con acuerdos de nivel de servicio (SLA) integrales, algo que no ofrece ningún otro servicio de base de datos.

Azure Cosmos DB contiene un motor de base de datos con escritura optimizada, regulado por recursos, independiente del esquema que admite varios modelos de datos de forma nativa: de valores clave, documentos, gráficos y columnas. También admite muchas API para acceder a datos, como MongoDB, DocumentDB SQL, Gremlin (versión preliminar) y Azure Tables (versión preliminar), de forma extensible.

## <a name="management-package"></a>Paquete de administración

### <a name="install-the-npm-module"></a>Instalación del módulo npm 

Instale el módulo npm de Azure Cosmos DB.

```bash
npm install azure-arm-documentdb
```

### <a name="example"></a>Ejemplo

En este ejemplo se enumeran todas las cuentas de Cosmos DB.

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

## <a name="samples"></a>Muestras

* [Desarrollo de una aplicación Node.js con Azure Cosmos DB - DocumentDB](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/)
* [Desarrollo de una aplicación Node.js con Azure Cosmos DB - Gremlin](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/)

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
