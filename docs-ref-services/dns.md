---
title: "Módulos de Azure DNS para Node.js"
description: "Referencia de los módulos de Azure DNS para Node.js"
keywords: Azure SDK, API, DNS, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DNS
ms.openlocfilehash: 679c2d494b99244961f2fee61b0813c81eb8a8de
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2017
---
# <a name="azure-dns-modules-for-nodejs"></a><span data-ttu-id="d6c43-104">Módulos de Azure DNS para Node.js</span><span class="sxs-lookup"><span data-stu-id="d6c43-104">Azure DNS modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="d6c43-105">Información general</span><span class="sxs-lookup"><span data-stu-id="d6c43-105">Overview</span></span>

<span data-ttu-id="d6c43-106">Utilice Azure DNS para hospedar sus dominios del Sistema de nombres de dominio (DNS) en Azure.</span><span class="sxs-lookup"><span data-stu-id="d6c43-106">Use Azure DNS to host your Domain Name System (DNS) domains in Azure.</span></span> <span data-ttu-id="d6c43-107">Puede administrar sus registros de DNS usando las mismas credenciales, el mismo plan de facturación y el mismo contrato de soporte técnico que utiliza para los demás servicios de Azure.</span><span class="sxs-lookup"><span data-stu-id="d6c43-107">Manage your DNS records using the same credentials and billing and support contract as your other Azure services.</span></span> <span data-ttu-id="d6c43-108">Integre sin problemas los servicios basados en Azure con las correspondientes actualizaciones de DNS y optimice el proceso de implementación de un extremo a otro.</span><span class="sxs-lookup"><span data-stu-id="d6c43-108">Seamlessly integrate Azure-based services with corresponding DNS updates and streamline your end-to-end deployment process.</span></span>

## <a name="management-package"></a><span data-ttu-id="d6c43-109">Paquete de administración</span><span class="sxs-lookup"><span data-stu-id="d6c43-109">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="d6c43-110">Instalación del módulo npm</span><span class="sxs-lookup"><span data-stu-id="d6c43-110">Install the npm module</span></span>

<span data-ttu-id="d6c43-111">Instale el módulo npm de Azure DNS.</span><span class="sxs-lookup"><span data-stu-id="d6c43-111">Install the Azure DNS npm module</span></span>

```bash
npm install azure-arm-dns
```

### <a name="example"></a><span data-ttu-id="d6c43-112">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d6c43-112">Example</span></span>

<span data-ttu-id="d6c43-113">En este ejemplo se enumeran las zonas de administración de DNS.</span><span class="sxs-lookup"><span data-stu-id="d6c43-113">This example lists the DNS Management zones.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const DNSManagement = require('azure-arm-dns');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DNSManagement(credentials, subscriptionId);
    return client.zones.list();
  })
  .then(zones => console.dir(zones, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="d6c43-114">Muestras</span><span class="sxs-lookup"><span data-stu-id="d6c43-114">Samples</span></span>

<span data-ttu-id="d6c43-115">Explore más [código de Node.js de ejemplo](https://azure.microsoft.com/resources/samples/?platform=nodejs) que puede usar en sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="d6c43-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
