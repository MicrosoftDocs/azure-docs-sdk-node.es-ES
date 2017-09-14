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
# <a name="azure-cosmos-db-modules-for-nodejs"></a><span data-ttu-id="df8f6-104">Módulos de Azure Cosmos DB para Node.js</span><span class="sxs-lookup"><span data-stu-id="df8f6-104">Azure Cosmos DB Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="df8f6-105">Información general</span><span class="sxs-lookup"><span data-stu-id="df8f6-105">Overview</span></span>

<span data-ttu-id="df8f6-106">Azure Cosmos DB es la base de datos multimodelo de distribución global de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="df8f6-106">Azure Cosmos DB is Microsoft's globally distributed, multi-model database.</span></span> <span data-ttu-id="df8f6-107">Azure Cosmos DB permite escalar de forma elástica e individual el rendimiento y el almacenamiento en cualquiera de las regiones geográficas de Azure.</span><span class="sxs-lookup"><span data-stu-id="df8f6-107">Azure Cosmos DB enables you to elastically and independently scale throughput and storage across any number of Azure's geographic regions.</span></span> <span data-ttu-id="df8f6-108">Ofrece garantía de rendimiento, latencia, disponibilidad y coherencia con acuerdos de nivel de servicio (SLA) integrales, algo que no ofrece ningún otro servicio de base de datos.</span><span class="sxs-lookup"><span data-stu-id="df8f6-108">It offers throughput, latency, availability, and consistency guarantees with comprehensive service level agreements (SLAs), something no other database service can offer.</span></span>

<span data-ttu-id="df8f6-109">Azure Cosmos DB contiene un motor de base de datos con escritura optimizada, regulado por recursos, independiente del esquema que admite varios modelos de datos de forma nativa: de valores clave, documentos, gráficos y columnas.</span><span class="sxs-lookup"><span data-stu-id="df8f6-109">Azure Cosmos DB contains a write optimized, resource governed, schema-agnostic database engine that natively supports multiple data models: key-value, documents, graphs, and columnar.</span></span> <span data-ttu-id="df8f6-110">También admite muchas API para acceder a datos, como MongoDB, DocumentDB SQL, Gremlin (versión preliminar) y Azure Tables (versión preliminar), de forma extensible.</span><span class="sxs-lookup"><span data-stu-id="df8f6-110">It also supports many APIs for accessing data including MongoDB, DocumentDB SQL, Gremlin (preview), and Azure Tables (preview), in an extensible manner.</span></span>

## <a name="management-package"></a><span data-ttu-id="df8f6-111">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="df8f6-111">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="df8f6-112">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="df8f6-112">Install the npm module</span></span> 

<span data-ttu-id="df8f6-113">Instale el módulo npm de Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="df8f6-113">Install the Azure Cosmos DB npm module</span></span>

```bash
npm install azure-arm-documentdb
```

### <a name="example"></a><span data-ttu-id="df8f6-114">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="df8f6-114">Example</span></span>

<span data-ttu-id="df8f6-115">En este ejemplo se enumeran todas las cuentas de Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="df8f6-115">This example lists all Cosmos DB accounts.</span></span>

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

## <a name="samples"></a><span data-ttu-id="df8f6-116">Muestras</span><span class="sxs-lookup"><span data-stu-id="df8f6-116">Samples</span></span>

* [<span data-ttu-id="df8f6-117">Desarrollo de una aplicación Node.js con Azure Cosmos DB - DocumentDB</span><span class="sxs-lookup"><span data-stu-id="df8f6-117">Developing a Node.js app using Azure Cosmos DB - DocumentDB</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/)
* [<span data-ttu-id="df8f6-118">Desarrollo de una aplicación Node.js con Azure Cosmos DB - Gremlin</span><span class="sxs-lookup"><span data-stu-id="df8f6-118">Developing a Node.js app using Azure Cosmos DB - Gremlin</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/)

<span data-ttu-id="df8f6-119">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="df8f6-119">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
