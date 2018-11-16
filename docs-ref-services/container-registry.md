---
title: Módulos de Azure Container Registry para Node.js
description: Referencia de los módulos de Azure Container Registry para Node.js
author: mmacy
ms.author: marsma
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Registry
ms.openlocfilehash: f24fa268f9c471925a1bdf0cbae8044d97bc7679
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2018
ms.locfileid: "51477929"
---
# <a name="azure-container-registry-modules-for-nodejs"></a>Módulos de Azure Container Registry para Node.js

Azure Container Registry es un servicio administrado de Docker Registry basado en Docker Registry 2.0 de código abierto. Cree y mantenga los registros de Azure Container para almacenar y administrar las imágenes privadas del contenedor Docker. Use registros de contenedor en Azure con el desarrollo de contenedor y las canalizaciones de implementación existentes y apóyese en el conjunto de la experiencia de la comunidad de Docker.

## <a name="management-package"></a>Paquete de administración

### <a name="install-the-npm-module"></a>Instalación del módulo npm

Instale el módulo npm de Azure Container Registry.

```bash
npm install azure-arm-containerregistry
```

### <a name="example"></a>Ejemplo

En este ejemplo se obtiene una lista de los contenedores disponibles.

```javascript
const msRestAzure = require('ms-rest-azure');
const ContainerRegistryManagement = require('azure-arm-containerregistry');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const manager = new ContainerRegistryManagement(
      credentials,
      subscriptionId
    );
    return manager.registries.list();
  })
  .then(registries => {
    console.log('List of registries:');
    console.dir(registries, { depth: null, colors: true });
  });
```

## <a name="samples"></a>Ejemplos

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
