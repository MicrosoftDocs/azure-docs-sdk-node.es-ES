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
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/08/2018
ms.locfileid: "51062084"
---
# <a name="azure-cosmos-db-modules-for-nodejs"></a><span data-ttu-id="3f4b6-103">Módulos de Azure Cosmos DB para Node.js</span><span class="sxs-lookup"><span data-stu-id="3f4b6-103">Azure Cosmos DB Modules for Node.js</span></span>

<span data-ttu-id="3f4b6-104">Azure Cosmos DB es la base de datos multimodelo de distribución global de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3f4b6-104">Azure Cosmos DB is Microsoft's globally distributed, multi-model database.</span></span> <span data-ttu-id="3f4b6-105">Azure Cosmos DB permite escalar de forma elástica e individual el rendimiento y el almacenamiento en cualquiera de las regiones geográficas de Azure.</span><span class="sxs-lookup"><span data-stu-id="3f4b6-105">Azure Cosmos DB enables you to elastically and independently scale throughput and storage across any number of Azure's geographic regions.</span></span> <span data-ttu-id="3f4b6-106">Ofrece garantía de rendimiento, latencia, disponibilidad y coherencia con acuerdos de nivel de servicio (SLA) integrales, algo que no ofrece ningún otro servicio de base de datos.</span><span class="sxs-lookup"><span data-stu-id="3f4b6-106">It offers throughput, latency, availability, and consistency guarantees with comprehensive service level agreements (SLAs), something no other database service can offer.</span></span>

<span data-ttu-id="3f4b6-107">Azure Cosmos DB contiene un motor de base de datos con escritura optimizada, regulado por recursos, independiente del esquema que admite varios modelos de datos de forma nativa: de valores clave, documentos, gráficos y columnas.</span><span class="sxs-lookup"><span data-stu-id="3f4b6-107">Azure Cosmos DB contains a write optimized, resource governed, schema-agnostic database engine that natively supports multiple data models: key-value, documents, graphs, and columnar.</span></span> <span data-ttu-id="3f4b6-108">También admite muchas API para acceder a datos, como MongoDB, SQL, Gremlin/Graph, Azure Tables y Cassandra (versión preliminar), de forma extensible.</span><span class="sxs-lookup"><span data-stu-id="3f4b6-108">It also supports many APIs for accessing data including MongoDB, SQL, Gremlin/Graph, Azure Tables, and Cassandra (preview) in an extensible manner.</span></span>

## <a name="management-package"></a><span data-ttu-id="3f4b6-109">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="3f4b6-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="3f4b6-110">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="3f4b6-110">Install the npm module</span></span> 

<span data-ttu-id="3f4b6-111">Instale el módulo npm de Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="3f4b6-111">Install the Azure Cosmos DB npm module.</span></span>

```bash
npm install azure-arm-documentdb
```

### <a name="example"></a><span data-ttu-id="3f4b6-112">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="3f4b6-112">Example</span></span>

<span data-ttu-id="3f4b6-113">En este ejemplo, se enumeran todas las cuentas de Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="3f4b6-113">This example lists all Azure Cosmos DB accounts.</span></span>

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

## <a name="samples"></a><span data-ttu-id="3f4b6-114">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="3f4b6-114">Samples</span></span>

* [<span data-ttu-id="3f4b6-115">Desarrollo de una aplicación Node.js con Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="3f4b6-115">Developing a Node.js app using Azure Cosmos DB</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/)
* [<span data-ttu-id="3f4b6-116">Desarrollo de una aplicación Node.js con Azure Cosmos DB - Gremlin</span><span class="sxs-lookup"><span data-stu-id="3f4b6-116">Developing a Node.js app using Azure Cosmos DB - Gremlin</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/)

<span data-ttu-id="3f4b6-117">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="3f4b6-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
