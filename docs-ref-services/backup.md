---
title: "Módulos de Azure Backup para Node.js"
description: "Referencia de los módulos de Azure Backup para Node.js"
keywords: Azure,SDK,API,Backup, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Backup
ms.openlocfilehash: 3ff9bff16a520bca461198531fd4c02139d2b293
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="azure-backup-modules-for-nodejs"></a><span data-ttu-id="73a13-104">Módulos de Azure Backup para Node.js</span><span class="sxs-lookup"><span data-stu-id="73a13-104">Azure Backup Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="73a13-105">Información general</span><span class="sxs-lookup"><span data-stu-id="73a13-105">Overview</span></span>

<span data-ttu-id="73a13-106">Azure Backup es el servicio de Azure que puede usar para realizar una copia de seguridad de los datos (protegerlos) y recuperarlos en la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="73a13-106">Azure Backup is the Azure-based service you can use to back up (or protect) and restore your data in the Microsoft cloud.</span></span> <span data-ttu-id="73a13-107">Reemplaza su solución de copia de seguridad local o remota existente por una solución confiable, segura y rentable basada en la nube.</span><span class="sxs-lookup"><span data-stu-id="73a13-107">Azure Backup replaces your existing on-premises or off-site backup solution with a cloud-based solution that is reliable, secure, and cost-competitive.</span></span> <span data-ttu-id="73a13-108">Azure Backup ofrece varios componentes que se descargan e implementan en el equipo o servidor adecuados, o en la nube.</span><span class="sxs-lookup"><span data-stu-id="73a13-108">Azure Backup offers multiple components that you download and deploy on the appropriate computer, server, or in the cloud.</span></span> <span data-ttu-id="73a13-109">El componente, o agente, que se implemente depende de lo que quiera proteger.</span><span class="sxs-lookup"><span data-stu-id="73a13-109">The component, or agent, that you deploy depends on what you want to protect.</span></span> <span data-ttu-id="73a13-110">Todos los componentes de Azure Backup (sin importar si va a proteger los datos de forma local o en la nube) se pueden usar para realizar una copia de seguridad de datos en un almacén de Azure Recovery Services.</span><span class="sxs-lookup"><span data-stu-id="73a13-110">All Azure Backup components (no matter whether you're protecting data on-premises or in the cloud) can be used to back up data to a Recovery Services vault in Azure.</span></span> 

## <a name="management-package"></a><span data-ttu-id="73a13-111">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="73a13-111">Management package</span></span>

### <a name="install-the-modules-with-npm"></a><span data-ttu-id="73a13-112">Instalación de los módulos con npm</span><span class="sxs-lookup"><span data-stu-id="73a13-112">Install the modules with npm</span></span>

<span data-ttu-id="73a13-113">Utilice npm para instalar los módulos de Azure Backup para Node.js.</span><span class="sxs-lookup"><span data-stu-id="73a13-113">Use npm to install the Azure Backup modules for Node.js</span></span>

```bash
npm install azure-arm-recoveryservicesbackup
```

### <a name="example"></a><span data-ttu-id="73a13-114">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="73a13-114">Example</span></span>

<span data-ttu-id="73a13-115">En este ejemplo se muestran los trabajos de recuperación para un almacén y grupo de recursos determinados.</span><span class="sxs-lookup"><span data-stu-id="73a13-115">This example lists the recovery jobs for a given vault and resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="73a13-116">Muestras</span><span class="sxs-lookup"><span data-stu-id="73a13-116">Samples</span></span>

<span data-ttu-id="73a13-117">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="73a13-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
