---
title: "Código de ejemplo para el uso de bases de datos de Azure con Node.js"
description: "Código de ejemplo que muestra el uso de bases de datos de Azure con Node.js"
author: tomarcher
manager: douge
ms.devlang: nodejs
ms.topic: article
ms.service: azure-nodejs
ms.date: 06/17/2017
ms.author: tarcher
ms.openlocfilehash: 8292a8fd0353ae84ac2b1622e5c622e60be04c9b
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="sample-code-for-using-azure-databases-with-nodejs"></a><span data-ttu-id="b3e40-103">Código de ejemplo para el uso de bases de datos de Azure con Node.js</span><span class="sxs-lookup"><span data-stu-id="b3e40-103">Sample code for using Azure databases with Node.js</span></span>

<span data-ttu-id="b3e40-104">El código de ejemplo siguiente muestra cómo usar las bases de datos de Azure con Node.js.</span><span class="sxs-lookup"><span data-stu-id="b3e40-104">The following sample code illustrate using Azure databases with Node.js.</span></span>

<span data-ttu-id="b3e40-105">Si se necesita código para otras tareas, puede examinar la lista completa de [ejemplos de Node.js de Azure](https://azure.microsoft.com/resources/samples/?term=nodejs).</span><span class="sxs-lookup"><span data-stu-id="b3e40-105">If you need code for other tasks, you can browse the full list of [Azure Node.js samples](https://azure.microsoft.com/resources/samples/?term=nodejs).</span></span>

| | |
|---|---|
| <span data-ttu-id="b3e40-106">**Cosmos DB**</span><span class="sxs-lookup"><span data-stu-id="b3e40-106">**Cosmos DB**</span></span> ||
| [<span data-ttu-id="b3e40-107">Uso de Azure Cosmos DB y API Graph</span><span class="sxs-lookup"><span data-stu-id="b3e40-107">Use the Azure Cosmos DB and Graph API</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/) | <span data-ttu-id="b3e40-108">Muestra cómo utilizar Azure Cosmos DB con la API Graph para almacenar y tener acceso a datos desde una aplicación Node.js.</span><span class="sxs-lookup"><span data-stu-id="b3e40-108">Shows you how to use the Azure Cosmos DB with the Graph API to store and access data from a Node.js application.</span></span> |
| [<span data-ttu-id="b3e40-109">Uso de Azure Cosmos DB y API de Documento DB</span><span class="sxs-lookup"><span data-stu-id="b3e40-109">Use the Azure Cosmos DB and Document DB API</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/) | <span data-ttu-id="b3e40-110">Muestra cómo utilizar Azure Cosmos DB con la API de DocumentDB para almacenar y acceder a datos desde una aplicación Node.js.</span><span class="sxs-lookup"><span data-stu-id="b3e40-110">Shows you how to use the Azure Cosmos DB with the DocumentDB API to store and access data from a Node.js application.</span></span> |
| <span data-ttu-id="b3e40-111">**DocumentDB**</span><span class="sxs-lookup"><span data-stu-id="b3e40-111">**DocumentDB**</span></span> ||
| [<span data-ttu-id="b3e40-112">Desarrollo de aplicaciones web con Node.js y Express mediante DocumentDB</span><span class="sxs-lookup"><span data-stu-id="b3e40-112">Web application development with Node.js and Express using DocumentDB</span></span>](https://azure.microsoft.com/resources/samples/documentdb-node-todo-app/) | <span data-ttu-id="b3e40-113">Se muestra cómo usar Azure DocumentDB para almacenar datos desde una aplicación Node.js Express en Azure y obtener acceso a ellos.</span><span class="sxs-lookup"><span data-stu-id="b3e40-113">Shows how to use Azure DocumentDB to store and access data from a Node.js Express application on Azure.</span></span> |
| [<span data-ttu-id="b3e40-114">Desarrollo de una aplicación de consola Node.js mediante DocumentDB</span><span class="sxs-lookup"><span data-stu-id="b3e40-114">Developing a Node.js console app using DocumentDB</span></span>](https://azure.microsoft.com/resources/samples/documentdb-node-getting-started/) | <span data-ttu-id="b3e40-115">En este ejemplo se muestra cómo empezar a trabajar rápidamente con el servicio Microsoft Azure DocumentDB y Node.js.</span><span class="sxs-lookup"><span data-stu-id="b3e40-115">This sample shows you how get started quickly with Microsoft Azure DocumentDB service and Node.js.</span></span> |
| <span data-ttu-id="b3e40-116">**MongoDB**</span><span class="sxs-lookup"><span data-stu-id="b3e40-116">**MongoDB**</span></span> ||
| [<span data-ttu-id="b3e40-117">Aplicación web Node.js y MongoDB en Azure</span><span class="sxs-lookup"><span data-stu-id="b3e40-117">Node.js and MongoDB web app in Azure</span></span>](https://azure.microsoft.com/resources/samples/meanjs/) | <span data-ttu-id="b3e40-118">Aplicación de ejemplo que puede usar con el tutorial, [Compilación de una aplicación web Node.js y MongoDB en Azure](http://docs.microsoft.com/azure/app-service-web/app-service-web-tutorial-nodejs-mongodb-app?toc=/azure/node/toc.json&bc=/azure/node/toc.json).</span><span class="sxs-lookup"><span data-stu-id="b3e40-118">Sample application that you can use to follow along with the tutorial, [Build a Node.js and MongoDB web app in Azure](http://docs.microsoft.com/azure/app-service-web/app-service-web-tutorial-nodejs-mongodb-app?toc=/azure/node/toc.json&bc=/azure/node/toc.json).</span></span> |
| <span data-ttu-id="b3e40-119">**SQL Database**</span><span class="sxs-lookup"><span data-stu-id="b3e40-119">**SQL Database**</span></span> ||
| <span data-ttu-id="b3e40-120">[Azure SQL Database: Use Node.js to connect and query data](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-nodejs) (Azure SQL Database: uso de Node.js para conectar y consultar datos)</span><span class="sxs-lookup"><span data-stu-id="b3e40-120">[Azure SQL Database: Use Node.js to connect and query data](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-nodejs)</span></span> | <span data-ttu-id="b3e40-121">Muestra cómo conectarse a una base de datos de Azure SQL Database mediante Node.jsy, posteriormente, usar instrucciones Transact-SQL para consultar, insertar, actualizar y eliminar datos de la base de datos desde las plataformas Windows, Ubuntu Linux y Mac.</span><span class="sxs-lookup"><span data-stu-id="b3e40-121">Demonstrates how to connect to an Azure SQL database using Node.js; then use Transact-SQL statements to query, insert, update, and delete data in the database from Windows, Ubuntu Linux, and Mac platforms.</span></span> |