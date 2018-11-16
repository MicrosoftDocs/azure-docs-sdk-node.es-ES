---
title: Módulos de Azure Relay para Node.js
description: Referencia de los módulos de Azure Relay para Node.js
author: sethmanheim
ms.author: sethm
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Relay
ms.openlocfilehash: e0bb24ac422d71bd8c957e94cceffd57bf121e48
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2018
ms.locfileid: "51465999"
---
# <a name="azure-relay-modules-for-nodejs"></a><span data-ttu-id="9bc89-103">Módulos de Azure Relay para Node.js</span><span class="sxs-lookup"><span data-stu-id="9bc89-103">Azure Relay modules for Node.js</span></span>

<span data-ttu-id="9bc89-104">El servicio Azure Relay crea aplicaciones híbridas, ya que permite exponer de forma segura los servicios que se encuentran en una red corporativa en la nube pública sin tener que abrir una conexión de firewall y sin que sea necesario realizar cambios intrusivos en una infraestructura de red corporativa.</span><span class="sxs-lookup"><span data-stu-id="9bc89-104">The Azure Relay service creates hybrid applications by enabling you to securely expose services that reside within a corporate enterprise network to the public cloud, without having to open a firewall connection, or require intrusive changes to a corporate network infrastructure.</span></span> <span data-ttu-id="9bc89-105">Relay admite diversos protocolos de transporte y estándares de servicios web.</span><span class="sxs-lookup"><span data-stu-id="9bc89-105">Relay supports a variety of different transport protocols and web services standards.</span></span>

<span data-ttu-id="9bc89-106">Más información acerca de [Azure Relay](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).</span><span class="sxs-lookup"><span data-stu-id="9bc89-106">Learn more about [Azure Relay](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).</span></span>

## <a name="management-package"></a><span data-ttu-id="9bc89-107">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="9bc89-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="9bc89-108">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="9bc89-108">Install the npm module</span></span>

<span data-ttu-id="9bc89-109">Instale el módulo npm de Azure Relay.</span><span class="sxs-lookup"><span data-stu-id="9bc89-109">Install the Azure Relay npm module</span></span>

```bash
npm install azure-arm-relay
```

### <a name="example"></a><span data-ttu-id="9bc89-110">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="9bc89-110">Example</span></span>

<span data-ttu-id="9bc89-111">En este ejemplo se enumeran los espacios de nombres para un cliente de Relay.</span><span class="sxs-lookup"><span data-stu-id="9bc89-111">This example lists the namespaces for a Relay client.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const RelayManagement = require('azure-arm-relay');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RelayManagement(credentials, subscriptionId);
    return client.namespaces.list();
  })
  .then(namespaces => {
    console.dir(namespaces, { depth: null, colors: true });
  })
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="9bc89-112">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="9bc89-112">Samples</span></span>

<span data-ttu-id="9bc89-113">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="9bc89-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
