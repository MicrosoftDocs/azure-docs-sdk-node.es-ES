---
title: Módulos de Azure Site Recovery para Node.js
description: Referencia de los módulos de Azure Site Recovery para Node.js
author: rayne-wiselman
ms.author: raynew
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Site Recovery
ms.openlocfilehash: 470124eb69a48486fa54be6628c028399f0c038e
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34259396"
---
# <a name="azure-site-recovery-modules-for-nodejs"></a>Módulos de Azure Site Recovery para Node.js

Site Recovery le permite automatizar la replicación de máquinas virtuales de Azure entre regiones, de máquinas virtuales locales y de servidores físicos en Azure, así como de máquinas locales en un centro de datos secundario.

Aprenda más sobre [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).

## <a name="management-package"></a>Paquete de administración

### <a name="install-the-npm-module"></a>Instalación del módulo npm

Instale el módulo npm de Azure Site Recovery.

```bash
npm install azure-arm-recoveryservices
```

### <a name="example"></a>Ejemplo

En este ejemplo se muestra el servicio Site Recovery para un grupo de recursos.

```javascript
const msRestAzure = require('ms-rest-azure');
const RecoveryServicesManagement = require('azure-arm-recoveryservices');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RecoveryServicesManagement(credentials, subscriptionId);
    return client.vaults.listByResourceGroup(resourceGroupName);
  })
  .then(vaults => {
    console.log('List of vaults:');
    console.dir(vaults, { depth: null, colors: true });
  });
  
```

## <a name="samples"></a>Ejemplos

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
