---
title: "Módulos de Azure Virtual Network para Node.js"
description: "Referencia de los módulos de Azure Virtual Network para Node.js"
keywords: Azure,SDK,API,Virtual Network, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Virtual Network
ms.openlocfilehash: a17615a832c6dddeb7fef0a8a327dbf86ae281a7
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="azure-virtual-network-modules-for-nodejs"></a><span data-ttu-id="166d6-104">Módulos de Azure Virtual Network para Node.js</span><span class="sxs-lookup"><span data-stu-id="166d6-104">Azure Virtual Network modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="166d6-105">Información general</span><span class="sxs-lookup"><span data-stu-id="166d6-105">Overview</span></span>

<span data-ttu-id="166d6-106">El servicio de Azure Virtual Network le permite conectar de forma segura los recursos de Azure con redes virtuales.</span><span class="sxs-lookup"><span data-stu-id="166d6-106">The Azure Virtual Network service enables you to securely connect Azure resources to each other with virtual networks (VNets).</span></span> <span data-ttu-id="166d6-107">Una red virtual es una representación de su propia red en la nube.</span><span class="sxs-lookup"><span data-stu-id="166d6-107">A VNet is a representation of your own network in the cloud.</span></span> <span data-ttu-id="166d6-108">Una red virtual es un aislamiento lógico de la nube de Azure dedicada a su suscripción.</span><span class="sxs-lookup"><span data-stu-id="166d6-108">A VNet is a logical isolation of the Azure cloud dedicated to your subscription.</span></span> <span data-ttu-id="166d6-109">También puede conectar redes virtuales a la red local.</span><span class="sxs-lookup"><span data-stu-id="166d6-109">You can also connect VNets to your on-premises network.</span></span>

<span data-ttu-id="166d6-110">Más información acerca de [Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).</span><span class="sxs-lookup"><span data-stu-id="166d6-110">Learn more about [Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="166d6-111">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="166d6-111">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="166d6-112">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="166d6-112">Install the npm module</span></span>

<span data-ttu-id="166d6-113">Instale el módulo npm de Azure Virtual Network.</span><span class="sxs-lookup"><span data-stu-id="166d6-113">Install the Azure Virtual Network npm module</span></span>

```bash
npm install azure-arm-network
```

### <a name="example"></a><span data-ttu-id="166d6-114">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="166d6-114">Example</span></span>

<span data-ttu-id="166d6-115">En este ejemplo se obtiene y se imprime la lista de redes virtuales.</span><span class="sxs-lookup"><span data-stu-id="166d6-115">This example gets and prints the list of virtual networks</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const NetworkManagementClient = require('azure-arm-network');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new NetworkManagementClient(credentials, subscriptionId);
    return client.virtualNetworks.list(resourceGroup);
  })
  .then(networkList => {
    console.log('List of virtual networks:');
    console.dir(networkList, { depth: null, colors: true });
  });

```

## <a name="samples"></a><span data-ttu-id="166d6-116">Muestras</span><span class="sxs-lookup"><span data-stu-id="166d6-116">Samples</span></span>

<span data-ttu-id="166d6-117">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="166d6-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
