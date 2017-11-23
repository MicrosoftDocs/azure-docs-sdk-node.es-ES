---
title: "Módulos de Azure Storage para Node.js"
description: "Referencia de los módulos de Azure Storage para Node.js"
keywords: Azure, Node, SDK, API, Storage, nodejs, javascript
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: storage
ms.openlocfilehash: 61d3f3bb49d10e63a353c474067a155223bb6c76
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="azure-storage-modules-for-nodejs"></a><span data-ttu-id="0a63f-104">Módulos de Azure Storage para Node.js</span><span class="sxs-lookup"><span data-stu-id="0a63f-104">Azure Storage modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="0a63f-105">Información general</span><span class="sxs-lookup"><span data-stu-id="0a63f-105">Overview</span></span>

<span data-ttu-id="0a63f-106">Utilice el módulo de cliente de Azure Storage para:</span><span class="sxs-lookup"><span data-stu-id="0a63f-106">Use the Azure Storage client module to:</span></span>

- <span data-ttu-id="0a63f-107">Leer y escribir objetos y archivos de [Azure Blob Storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage)</span><span class="sxs-lookup"><span data-stu-id="0a63f-107">Read and write objects and files from [Azure Blob storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage)</span></span>
- <span data-ttu-id="0a63f-108">Enviar y recibir mensajes entre aplicaciones conectadas en la nube con [Azure Queue Storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)</span><span class="sxs-lookup"><span data-stu-id="0a63f-108">Send and receive messages between cloud-connected applications with [Azure Queue storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)</span></span>
- <span data-ttu-id="0a63f-109">Leer y escribir datos estructurados grandes con [Azure Table Storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)</span><span class="sxs-lookup"><span data-stu-id="0a63f-109">Read and write large structured data with [Azure Table storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)</span></span>

<span data-ttu-id="0a63f-110">Cree, actualice y administre cuentas y consultas de Azure Storage y vuelva a generar las claves de acceso de las aplicaciones Node.js con los módulos de administración.</span><span class="sxs-lookup"><span data-stu-id="0a63f-110">Create, update, and manage Azure Storage accounts and query and regenerate access keys from your Node.js apps with the management modules.</span></span>

## <a name="client-package"></a><span data-ttu-id="0a63f-111">Paquete del cliente</span><span class="sxs-lookup"><span data-stu-id="0a63f-111">Client Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="0a63f-112">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="0a63f-112">Install the npm module</span></span>

<span data-ttu-id="0a63f-113">Instale el módulo npm de cliente de Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="0a63f-113">Install the Azure storage client npm module</span></span>

```bash
npm install azure-storage
```

### <a name="example"></a><span data-ttu-id="0a63f-114">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0a63f-114">Example</span></span>

<span data-ttu-id="0a63f-115">En este ejemplo se crea un contenedor de almacenamiento y se carga un archivo local `data.txt` en él.</span><span class="sxs-lookup"><span data-stu-id="0a63f-115">This example create a storage container and uploads a local file `data.txt` to it.</span></span>

```javascript
const azure = require('azure-storage');
const blobService = azure.createBlobService(storageConnectionString);

const container = 'taskcontainer';
const task = 'taskblob';
const filename = 'data.txt';

blobService.createContainerIfNotExists(container, error => {
  if (error) return console.log(error);
  blobService.createBlockBlobFromLocalFile(
    container,
    task,
    filename,
    (error, result) => {
      if (error) return console.log(error);
      console.dir(result, { depth: null, colors: true });
    }
  );
});
```

## <a name="management-package"></a><span data-ttu-id="0a63f-116">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="0a63f-116">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="0a63f-117">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="0a63f-117">Install the npm module</span></span> 

<span data-ttu-id="0a63f-118">Instale el módulo npm de administración de Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="0a63f-118">Install the Azure storage management npm module</span></span>

```bash
npm install azure-arm-storage
```

### <a name="example"></a><span data-ttu-id="0a63f-119">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0a63f-119">Example</span></span>

<span data-ttu-id="0a63f-120">En este ejemplo se enumeran las cuentas de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="0a63f-120">This example list the storage accounts.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const storageManagementClient = require('azure-arm-storage');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new storageManagementClient(
      credentials,
      subscriptionId
    );
    return client.storageAccounts.list();
  })
  .then(accounts => console.dir(accounts, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="0a63f-121">Muestras</span><span class="sxs-lookup"><span data-stu-id="0a63f-121">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/storage-samples.md)]

<span data-ttu-id="0a63f-122">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="0a63f-122">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
