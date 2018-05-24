---
title: Módulos de Azure Virtual Machines para Node.js
description: Guía de referencia de los módulos de Azure Virtual Machines para Node.js
author: iainfoulds
ms.author: iainfou
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 891b441d25369db0f0a67d791d527e6644415434
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="azure-virtual-machine-modules-for-nodejs"></a><span data-ttu-id="57841-103">Módulos de Azure Virtual Machines para Node.js</span><span class="sxs-lookup"><span data-stu-id="57841-103">Azure Virtual Machine Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="57841-104">Información general</span><span class="sxs-lookup"><span data-stu-id="57841-104">Overview</span></span>

<span data-ttu-id="57841-105">Defina, configure e implemente nuevas máquinas virtuales Windows y Linux y los conjunto de escalado de máquinas virtuales desde el código con los módulos de administración de Azure para Node.js.</span><span class="sxs-lookup"><span data-stu-id="57841-105">Define, configure, and deploy new Windows and Linux virtual machines and virtual machine scale sets from your code with the Azure management modules for Node.js.</span></span> <span data-ttu-id="57841-106">Los módulos le permiten iniciar y detener las máquinas virtuales existentes y asociar o desasociar discos en máquinas virtuales detenidas de su suscripción de Azure.</span><span class="sxs-lookup"><span data-stu-id="57841-106">The modules let you start and stop existing virtual machines and attach or detach disks to stopped VMs in your Azure subscription.</span></span>

## <a name="management-package"></a><span data-ttu-id="57841-107">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="57841-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="57841-108">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="57841-108">Install the npm module</span></span>

<span data-ttu-id="57841-109">Instale el módulo npm de Azure Compute.</span><span class="sxs-lookup"><span data-stu-id="57841-109">Install the Azure Compute npm module</span></span>

```bash
npm install azure-arm-compute
```   

### <a name="example"></a><span data-ttu-id="57841-110">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="57841-110">Example</span></span>

<span data-ttu-id="57841-111">En el ejemplo siguiente se muestra cómo iniciar sesión en Azure, crear un cliente de administración y enumerar todas las imágenes de máquina virtual para la ubicación especificada, el publicador, la oferta y la SKU.</span><span class="sxs-lookup"><span data-stu-id="57841-111">The following example illustrates how to log in to Azure, create a management client, and list all VM images for the specified location, publisher, offer, and SKU.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const computeManagementClient = require('azure-arm-compute');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new computeManagementClient(credentials, subscriptionId);

  client.virtualMachineImages
    .list(
        'westus',                   // location
        'Canonical',   // publisher name
        'UbuntuServer',            // offer
        '16.04-LTS'        // sku
    )
    .then(result => console.log(result));
});
```

## <a name="samples"></a><span data-ttu-id="57841-112">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="57841-112">Samples</span></span>

[!INCLUDE [node-virtualmachines-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

<span data-ttu-id="57841-113">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="57841-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
