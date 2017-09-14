---
title: "Módulos de Azure Virtual Machines para Node.js"
description: "Referencia de los módulos de Azure Virtual Machines para Node.js"
keywords: "Azure, Node, SDK, API, máquina virtual, vm, nodejs, javascript"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 816714f5c286ee82f61502978c5d811e9f283432
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="azure-virtual-machine-modules-for-nodejs"></a><span data-ttu-id="783bc-104">Módulos de Azure Virtual Machines para Node.js</span><span class="sxs-lookup"><span data-stu-id="783bc-104">Azure Virtual Machine Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="783bc-105">Información general</span><span class="sxs-lookup"><span data-stu-id="783bc-105">Overview</span></span>

<span data-ttu-id="783bc-106">Defina, configure e implemente nuevas máquinas virtuales Windows y Linux y los conjunto de escalado de máquinas virtuales desde el código con los módulos de administración de Azure para Node.js.</span><span class="sxs-lookup"><span data-stu-id="783bc-106">Define, configure, and deploy new Windows and Linux virtual machines and virtual machine scale sets from your code with the Azure management modules for Node.js.</span></span> <span data-ttu-id="783bc-107">Los módulos le permiten iniciar y detener las máquinas virtuales existentes y asociar o desasociar discos en máquinas virtuales detenidas de su suscripción de Azure.</span><span class="sxs-lookup"><span data-stu-id="783bc-107">The modules let you start and stop existing virtual machines and attach or detach disks to stopped VMs in your Azure subscription.</span></span>

## <a name="management-package"></a><span data-ttu-id="783bc-108">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="783bc-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="783bc-109">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="783bc-109">Install the npm module</span></span>

<span data-ttu-id="783bc-110">Instale el módulo npm de Azure Compute.</span><span class="sxs-lookup"><span data-stu-id="783bc-110">Install the Azure Compute npm module</span></span>

```bash
npm install azure-arm-compute
```   

### <a name="example"></a><span data-ttu-id="783bc-111">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="783bc-111">Example</span></span>

<span data-ttu-id="783bc-112">En el ejemplo siguiente se muestra cómo iniciar sesión en Azure, crear un cliente de administración y enumerar todas las imágenes de máquina virtual para la ubicación especificada, el publicador, la oferta y la SKU.</span><span class="sxs-lookup"><span data-stu-id="783bc-112">The following example illustrates how to log in to Azure, create a management client, and list all VM images for the specified location, publisher, offer, and SKU.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const computeManagementClient = require('azure-arm-compute');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new computeManagementClient(credentials, subscriptionId);

  client.virtualMachineImages
    .list(
        'westus',                   // location
        'MicrosoftWindowsServer',   // publisher name
        'WindowsServer',            // offer
        '2012-R2-Datacenter'        // sku
    )
    .then(result => console.log(result));
});
```

## <a name="samples"></a><span data-ttu-id="783bc-113">Muestras</span><span class="sxs-lookup"><span data-stu-id="783bc-113">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

<span data-ttu-id="783bc-114">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="783bc-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
