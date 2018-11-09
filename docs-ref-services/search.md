---
title: Módulos de Azure Search para Node.js
description: Referencia de los módulos de Azure Search para Node.js
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Search
ms.openlocfilehash: a9c34a57d7964de1713ebf4d6c0f9c000df33042
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/08/2018
ms.locfileid: "51173104"
---
# <a name="azure-search-modules-for-nodejs"></a>Módulos de Azure Search para Node.js

Azure Search es una solución de búsqueda como servicio en la nube que delega la administración de los servidores y la infraestructura a Microsoft, dejando así un servicio listo para usar que puede completar con sus propios datos y usar para buscar en la aplicación.

Más información sobre [Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search).

## <a name="management-package"></a>Paquete de administración

### <a name="install-the-npm-module"></a>Instalación del módulo npm

Instale el módulo npm de Azure Search.

```bash
npm install azure-arm-search
```

### <a name="example"></a>Ejemplo

En este ejemplo se crea un nuevo servicio Search en Azure y muestra los recursos de su grupo de recursos.

```javascript
const msRestAzure = require('ms-rest-azure');
const SearchManagement = require('azure-arm-search');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'yourResourceGroup';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new SearchManagement(credentials, subscriptionId);
    return client.services.listByResourceGroup(resourceGroup);
  })
  .then(services => console.dir(services, { depth: null, colors: true }))
  .catch(err => {
    console.log('An error ocurred');
    console.dir(err, { depth: null, colors: true });
  });
```

## <a name="samples"></a>Ejemplos

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
