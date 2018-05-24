---
title: Módulos de Azure CDN para Node.js
description: Referencia de los módulos de Azure CDN para Node.js
author: dksimpson
ms.author: v-deasim
manager: v-laurab
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: CDN
ms.openlocfilehash: b330eeedc178f20064b4a6b1c3f4f7d266590f11
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="azure-cdn-modules-for-nodejs"></a>Módulos de Azure CDN para Node.js

## <a name="overview"></a>Información general

Microsoft Azure Content Delivery Network (CDN) ofrece a los desarrolladores una solución global para entregar contenido con alto ancho de banda que se hospeda en Azure o en cualquier otra ubicación. Con la red CDN, puede almacenar en caché objetos disponibles públicamente cargados desde Almacenamiento de blobs de Azure, una aplicación web, una máquina virtual, una carpeta de la aplicación u otra ubicación HTTP/HTTPS. La caché de CDN puede mantenerse en ubicaciones estratégicas, con el fin de proporcionar el ancho de banda máximo para entregar contenido a los usuarios. La red CDN se suele usar para entregar el contenido estático, como imágenes, hojas de estilo, documentos, archivos, scripts de cliente y páginas HTML.

## <a name="management-package"></a>Paquete de administración

### <a name="install-the-npm-module"></a>Instalación del módulo npm

Instale el módulo npm de Azure CDN.

```bash
npm install azure-arm-cdn
```

### <a name="example"></a>Ejemplo

En este ejemplo se muestran todos los perfiles de la red CDN.

```javascript
const msRestAzure = require('ms-rest-azure');
const cdnManagementClient = require('azure-arm-cdn');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const cdnClient = new cdnManagementClient(credentials, subscriptionId);
  cdnClient.profiles
    .list()
    .then(profilesList => console.log('Retrieved profiles list: ', profilesList));
});
```

## <a name="samples"></a>Ejemplos

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
