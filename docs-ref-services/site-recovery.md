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
# <a name="azure-site-recovery-modules-for-nodejs"></a><span data-ttu-id="e79e0-103">Módulos de Azure Site Recovery para Node.js</span><span class="sxs-lookup"><span data-stu-id="e79e0-103">Azure Site Recovery modules for Node.js</span></span>

<span data-ttu-id="e79e0-104">Site Recovery le permite automatizar la replicación de máquinas virtuales de Azure entre regiones, de máquinas virtuales locales y de servidores físicos en Azure, así como de máquinas locales en un centro de datos secundario.</span><span class="sxs-lookup"><span data-stu-id="e79e0-104">Site Recovery allows you to automate replication of Azure VMs between regions, on-premises virtual machines and physical servers to Azure, and on-premises machines to a secondary datacenter.</span></span>

<span data-ttu-id="e79e0-105">Aprenda más sobre [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).</span><span class="sxs-lookup"><span data-stu-id="e79e0-105">Learn more about [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="e79e0-106">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="e79e0-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="e79e0-107">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="e79e0-107">Install the npm module</span></span>

<span data-ttu-id="e79e0-108">Instale el módulo npm de Azure Site Recovery.</span><span class="sxs-lookup"><span data-stu-id="e79e0-108">Install the Azure Site Recovery service npm module</span></span>

```bash
npm install azure-arm-recoveryservices
```

### <a name="example"></a><span data-ttu-id="e79e0-109">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="e79e0-109">Example</span></span>

<span data-ttu-id="e79e0-110">En este ejemplo se muestra el servicio Site Recovery para un grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="e79e0-110">This example lists the Site Recovery service for a resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="e79e0-111">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="e79e0-111">Samples</span></span>

<span data-ttu-id="e79e0-112">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="e79e0-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
