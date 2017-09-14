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
# <a name="azure-storage-modules-for-nodejs"></a>Módulos de Azure Storage para Node.js

## <a name="overview"></a>Información general

Utilice el módulo de cliente de Azure Storage para:

- Leer y escribir objetos y archivos de [Azure Blob Storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage)
- Enviar y recibir mensajes entre aplicaciones conectadas en la nube con [Azure Queue Storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)
- Leer y escribir datos estructurados grandes con [Azure Table Storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)

Cree, actualice y administre cuentas y consultas de Azure Storage y vuelva a generar las claves de acceso de las aplicaciones Node.js con los módulos de administración.

## <a name="client-package"></a>Paquete del cliente

### <a name="install-the-npm-module"></a>Instalación del módulo npm

Instale el módulo npm de cliente de Azure Storage.

```bash
npm install azure-storage
```

### <a name="example"></a>Ejemplo

En este ejemplo se crea un contenedor de almacenamiento y se carga un archivo local `data.txt` en él.

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

## <a name="management-package"></a>Paquete de administración

### <a name="install-the-npm-module"></a>Instalación del módulo npm 

Instale el módulo npm de administración de Azure Storage.

```bash
npm install azure-arm-storage
```

### <a name="example"></a>Ejemplo

En este ejemplo se enumeran las cuentas de almacenamiento.

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

## <a name="samples"></a>Muestras

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/storage-samples.md)]

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
