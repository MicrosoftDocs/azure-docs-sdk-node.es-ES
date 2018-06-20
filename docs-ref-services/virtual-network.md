---
title: Módulos de Azure Virtual Network para Node.js
description: Referencia de los módulos de Azure Virtual Network para Node.js
author: jimdial
ms.author: jdial
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Virtual Network
ms.openlocfilehash: 456839dbecb9ddd1ad0d4b3f8aa7570a04c100b1
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34260704"
---
# <a name="azure-virtual-network-modules-for-nodejs"></a><span data-ttu-id="08c12-103">Módulos de Azure Virtual Network para Node.js</span><span class="sxs-lookup"><span data-stu-id="08c12-103">Azure Virtual Network modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="08c12-104">Información general</span><span class="sxs-lookup"><span data-stu-id="08c12-104">Overview</span></span>

<span data-ttu-id="08c12-105">El servicio de Azure Virtual Network le permite conectar de forma segura los recursos de Azure con redes virtuales.</span><span class="sxs-lookup"><span data-stu-id="08c12-105">The Azure Virtual Network service enables you to securely connect Azure resources to each other with virtual networks (VNets).</span></span> <span data-ttu-id="08c12-106">Una red virtual es una representación de su propia red en la nube.</span><span class="sxs-lookup"><span data-stu-id="08c12-106">A VNet is a representation of your own network in the cloud.</span></span> <span data-ttu-id="08c12-107">Una red virtual es un aislamiento lógico de la nube de Azure dedicada a su suscripción.</span><span class="sxs-lookup"><span data-stu-id="08c12-107">A VNet is a logical isolation of the Azure cloud dedicated to your subscription.</span></span> <span data-ttu-id="08c12-108">También puede conectar redes virtuales a la red local.</span><span class="sxs-lookup"><span data-stu-id="08c12-108">You can also connect VNets to your on-premises network.</span></span>

<span data-ttu-id="08c12-109">Más información acerca de [Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).</span><span class="sxs-lookup"><span data-stu-id="08c12-109">Learn more about [Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="08c12-110">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="08c12-110">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="08c12-111">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="08c12-111">Install the npm module</span></span>

<span data-ttu-id="08c12-112">Instale el módulo npm de Azure Virtual Network.</span><span class="sxs-lookup"><span data-stu-id="08c12-112">Install the Azure Virtual Network npm module</span></span>

```bash
npm install azure-arm-network
```

### <a name="example"></a><span data-ttu-id="08c12-113">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="08c12-113">Example</span></span>

<span data-ttu-id="08c12-114">En este ejemplo se obtiene y se imprime la lista de redes virtuales.</span><span class="sxs-lookup"><span data-stu-id="08c12-114">This example gets and prints the list of virtual networks</span></span>

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

## <a name="samples"></a><span data-ttu-id="08c12-115">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="08c12-115">Samples</span></span>

<span data-ttu-id="08c12-116">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="08c12-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
