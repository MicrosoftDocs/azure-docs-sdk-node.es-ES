---
title: Módulos de Azure Backup para Node.js
description: Referencia de los módulos de Azure Backup para Node.js
author: markgalioto
ms.author: markgal
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: Backup
ms.openlocfilehash: 9234285d32bc465eeb86d13514783e1de4e5ef1b
ms.sourcegitcommit: 34172ad11850839ddd81d02841807e07f3761425
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58052787"
---
# <a name="azure-backup-modules-for-nodejs"></a>Módulos de Azure Backup para Node.js

## <a name="overview"></a>Información general

Azure Backup es el servicio de Azure que puede usar para realizar una copia de seguridad de los datos (protegerlos) y recuperarlos en la nube de Microsoft. Reemplaza su solución de copia de seguridad local o remota existente por una solución confiable, segura y rentable basada en la nube. Azure Backup ofrece varios componentes que se descargan e implementan en el equipo o servidor adecuados, o en la nube. El componente, o agente, que se implemente depende de lo que quiera proteger. Todos los componentes de Azure Backup (sin importar si va a proteger los datos de forma local o en la nube) se pueden usar para realizar una copia de seguridad de datos en un almacén de Azure Recovery Services. 

## <a name="management-package"></a>Paquete de administración

### <a name="install-the-modules-with-npm"></a>Instalación de los módulos con npm

Utilice npm para instalar los módulos de Azure Backup para Node.js.

```bash
npm install azure-arm-recoveryservicesbackup
```

### <a name="example"></a>Ejemplo

En este ejemplo se muestran los trabajos de recuperación para un almacén y grupo de recursos determinados.

```javascript
const msRestAzure = require('ms-rest-azure');
const RecoveryServicesBackupManagement = require('azure-arm-recoveryservicesbackup');

const subcriptionId = 'your-subscription-id';
const vault = 'your-recovery-service-vault';
const resourceGroupName = 'your-resource-group';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RecoveryServicesBackupManagement(
      credentials,
      subcriptionId
    );
    return client.jobs.list(vault, resourceGroupName);
  })
  .then(jobs => console.dir(jobs, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>Ejemplos

Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.
